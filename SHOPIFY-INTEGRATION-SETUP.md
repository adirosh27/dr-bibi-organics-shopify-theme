# Shopify Integration Setup Guide
## Connect Your Website to Shopify Checkout

**Good News**: Your website is already 90% set up to work with Shopify checkout!

You just need to configure a few settings and it will work perfectly.

---

## How It Currently Works

Your website has:
- ✅ Add to Cart button
- ✅ Shopping cart with localStorage
- ✅ "View Cart" button that redirects to Shopify
- ✅ "Proceed to Checkout" button

**What happens when customer checks out:**
1. Customer adds product to cart on your website
2. Customer clicks "Proceed to Checkout"
3. They're redirected to **your Shopify store checkout**
4. Shopify handles payment processing
5. You get the order in Shopify admin

---

## Step 1: Get Your Shopify Product Variant ID (5 minutes)

**You need to find this in your Shopify admin:**

### Method 1: From Shopify Admin (Easiest)

1. **Log in to Shopify Admin**: https://admin.shopify.com/
2. Go to **Products**
3. Click on **Butter Oasis Moisturizing Balm**
4. Scroll down to the **Variants** section
5. Click on your variant (e.g., "4oz" or "Default")
6. Look at the URL in your browser address bar
7. You'll see something like: `.../variants/50253534298387`
8. **Copy that number** (50253534298387)

### Method 2: From Product Page URL

1. Go to your live Shopify product page
2. Click **Add to Cart**
3. View the cart
4. Right-click → "Inspect" on the product
5. Look for `data-variant-id` or similar
6. **Copy that number**

### Method 3: Use Shopify API (Advanced)

```javascript
// In browser console on your Shopify product page
fetch('/products/butter-oasis-balm.json')
  .then(r => r.json())
  .then(data => console.log('Variant ID:', data.product.variants[0].id));
```

---

## Step 2: Update product.html with Your Variant ID (2 minutes)

1. **Open**: `product.html` in a text editor
2. **Find line 1153** (around there):
   ```javascript
   const SHOPIFY_VARIANT_ID = '50253534298387'; // Butter Oasis 4oz variant ID
   ```
3. **Replace** `50253534298387` with YOUR actual variant ID from Step 1
4. **Save** the file

**Example:**
```javascript
// If your variant ID is 12345678901234
const SHOPIFY_VARIANT_ID = '12345678901234';
```

---

## Step 3: Verify Your Shopify Domain (1 minute)

1. **Open**: `product.html`
2. **Find line 1152**:
   ```javascript
   const SHOPIFY_DOMAIN = 'https://drbibiorganics.com';
   ```
3. **Confirm** this is your correct Shopify store URL
4. If different, update it to your actual domain

---

## Step 4: Update index.html (If It Has Cart) (2 minutes)

If your homepage also has "Add to Cart" functionality:

1. **Open**: `index.html`
2. **Search for**: `SHOPIFY_VARIANT_ID`
3. **Update** with your variant ID (same as Step 2)
4. **Save**

---

## Step 5: Test the Integration (5 minutes)

### Test on Your Live Shopify Store:

1. **Upload** `product.html` to your Shopify theme:
   - Option A: Add as a custom page template
   - Option B: Replace your existing product page
   - Option C: Host on GoDaddy and link to Shopify for checkout

2. **Test the flow**:
   - Click "Add to Cart" → Should add to cart
   - Open cart → Should show product
   - Click "Proceed to Checkout" → Should go to Shopify checkout
   - Complete fake order (use Shopify's test mode)

3. **Verify**:
   - Product appears in Shopify checkout ✓
   - Price is correct ✓
   - Quantity is correct ✓
   - Customer can complete purchase ✓

---

## Step 6: Handle Multiple Products (If Needed)

**If you have multiple products or variants:**

### Option A: Multiple Variant IDs

Update the JavaScript to handle different variants:

```javascript
// product.html - around line 1152
const PRODUCT_VARIANTS = {
    '4oz': '50253534298387',
    '8oz': '50253534298388',  // Replace with actual ID
    'bundle': '50253534298389' // Replace with actual ID
};

// Then use:
const selectedVariant = PRODUCT_VARIANTS['4oz']; // or get from dropdown
```

### Option B: Dynamic Variant Selection

If customers can choose size/variant:

```javascript
// Add a dropdown in HTML
<select id="variantSelector">
    <option value="50253534298387">4oz - $70</option>
    <option value="50253534298388">8oz - $120</option>
</select>

// Update JavaScript
const selectedVariantId = document.getElementById('variantSelector').value;
```

---

## How the Checkout Flow Works

**Customer Journey:**

1. **Your Website** (product.html):
   - Customer browses beautiful product page
   - Clicks "Add to Cart"
   - Cart stored in browser localStorage
   - Customer can add multiple items

2. **Transition to Shopify**:
   - Customer clicks "Proceed to Checkout"
   - JavaScript builds Shopify cart URL
   - Redirects to: `https://drbibiorganics.com/cart/VARIANT_ID:QUANTITY`

3. **Shopify Checkout**:
   - Customer sees Shopify cart with product(s)
   - Customer enters shipping/payment info
   - Shopify processes payment
   - Customer gets order confirmation

4. **You Receive Order**:
   - Order appears in Shopify Admin
   - You get email notification
   - You fulfill order as normal

---

## Current Code Explanation

**In product.html (lines 1172-1183):**

```javascript
// Proceed to Checkout button
document.getElementById('proceedToCheckout').addEventListener('click', () => {
    const cart = getCart();
    if (cart.length === 0) {
        alert('Your cart is empty');
        return;
    }

    const totalQuantity = cart.reduce((sum, item) => sum + item.quantity, 0);

    // Redirect directly to Shopify with cart items
    window.location.href = `${SHOPIFY_DOMAIN}/cart/${SHOPIFY_VARIANT_ID}:${totalQuantity}`;
});
```

**What this does:**
1. Gets cart from localStorage
2. Counts total quantity
3. Redirects to Shopify cart URL with format: `/cart/VARIANT_ID:QUANTITY`
4. Shopify automatically adds items and shows checkout

---

## Shopify Cart URL Format

Shopify accepts direct cart URLs:

**Single Product:**
```
https://drbibiorganics.com/cart/50253534298387:2
```
(Adds 2 units of variant 50253534298387)

**Multiple Products:**
```
https://drbibiorganics.com/cart/50253534298387:2,50253534298388:1
```
(Adds 2 of first variant, 1 of second)

**Then Checkout:**
```
https://drbibiorganics.com/checkout
```

---

## Where to Host This Website

You have 2 options:

### Option A: Host on Shopify (Recommended)

**Pros:**
- Everything in one place
- No cross-domain issues
- Easier to manage

**How:**
1. Convert HTML files to Shopify theme templates
2. Upload to Shopify as custom theme
3. Set as live theme

**See**: `SHOPIFY-THEME-UPDATE-GUIDE.md`

### Option B: Host on GoDaddy (Headless)

**Pros:**
- Keep beautiful custom design exactly as is
- No Shopify theme limitations

**Cons:**
- Two systems to manage
- Need to ensure domain setup is correct

**How:**
1. Upload HTML files to GoDaddy
2. Website runs on: drbibiorganics.com
3. Checkout redirects to Shopify
4. After purchase, redirect back to GoDaddy site

**Note**: You'd need to set up subdomain or path for Shopify:
- Option 1: shop.drbibiorganics.com (Shopify)
- Option 2: drbibiorganics.com/shop (Shopify)

---

## Troubleshooting

### Issue: "Variant ID not found" error

**Solution:**
- Double-check variant ID is correct
- Make sure product is published in Shopify
- Verify product is in correct sales channel

### Issue: Redirects to Shopify but cart is empty

**Solution:**
- Check variant ID is correct
- Verify URL format: `/cart/VARIANT_ID:QUANTITY`
- Try with quantity 1 to test: `/cart/50253534298387:1`

### Issue: Multiple products not adding to cart

**Solution:**
Current code only supports single product. Need to update to handle multiple products:

```javascript
// Build cart URL with all items
const cartUrl = cart.map(item => `${item.variantId}:${item.quantity}`).join(',');
window.location.href = `${SHOPIFY_DOMAIN}/cart/${cartUrl}`;
```

### Issue: Price doesn't match in Shopify

**Solution:**
- Prices are pulled from Shopify product settings
- Update price in Shopify Admin → Products
- Your website display price is cosmetic (update in HTML)

---

## Next Steps

**Once you have your Variant ID:**

1. ✅ Update `product.html` line 1153 with your variant ID
2. ✅ Save file
3. ✅ Test locally (open product.html in browser)
4. ✅ Click "Add to Cart" → "Proceed to Checkout"
5. ✅ Should redirect to: `https://drbibiorganics.com/cart/YOUR_VARIANT_ID:1`
6. ✅ Verify product appears in Shopify cart

**Then decide:**
- **Option A**: Install as Shopify theme (recommended)
- **Option B**: Host on GoDaddy + link to Shopify checkout

---

## Quick Checklist

**Before Going Live:**

- [ ] Got Shopify product variant ID
- [ ] Updated SHOPIFY_VARIANT_ID in product.html
- [ ] Updated SHOPIFY_DOMAIN if needed
- [ ] Tested add to cart functionality
- [ ] Tested proceed to checkout
- [ ] Verified product appears in Shopify cart
- [ ] Verified price is correct
- [ ] Completed test purchase
- [ ] Confirmed order appears in Shopify admin

---

## Need Help Finding Variant ID?

**Quick way:**

1. Go to your Shopify product page
2. Add product to cart
3. Go to cart
4. Right-click on the page → "View Page Source"
5. Search for "variant" or "product"
6. Look for a long number (usually 11-14 digits)
7. That's your variant ID!

---

**You're almost done!** Just update that variant ID and you'll have a beautiful custom website with full Shopify checkout integration! 🎉

*Last Updated: January 6, 2026*
