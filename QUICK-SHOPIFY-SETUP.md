# Quick Shopify Setup - 3 Simple Steps
## Get Your Website Working with Shopify Checkout in 10 Minutes

---

## ✅ Good News!

Your website **ALREADY works** with Shopify checkout!

You just need to update **ONE number** in the code.

---

## Step 1: Get Your Product Variant ID (5 minutes)

### The Easy Way:

1. **Log in to Shopify**: https://admin.shopify.com/
2. Click **Products** in left menu
3. Click **Butter Oasis Moisturizing Balm**
4. Scroll down to **Variants** section
5. Click on your variant (might say "Default" or "4oz")
6. Look at the **URL in your browser**
7. You'll see: `.../products/12345.../variants/50253534298387`
8. **Copy the last number** (50253534298387) ← This is your Variant ID

**Save this number!** You'll need it in the next step.

---

## Step 2: Update product.html (2 minutes)

1. **Open** `product.html` in Notepad or any text editor
2. **Press Ctrl+F** to search
3. **Search for**: `50253534298387`
4. You'll find this line:
   ```javascript
   const SHOPIFY_VARIANT_ID = '50253534298387';
   ```
5. **Replace** `50253534298387` with YOUR variant ID from Step 1
6. **Save** the file

**Example:**
If your variant ID is `12345678901234`, change it to:
```javascript
const SHOPIFY_VARIANT_ID = '12345678901234';
```

---

## Step 3: Test It! (3 minutes)

### Option A: Test Locally First

1. **Double-click** `product.html` to open in browser
2. **Click** "Add to Cart"
3. **Click** "Proceed to Checkout"
4. You should be redirected to: `https://drbibiorganics.com/cart/YOUR_VARIANT_ID:1`
5. Your product should appear in Shopify cart ✓

### Option B: Test on Live Shopify

1. **Upload** product.html to Shopify (or use it as custom page)
2. **Test the same flow**
3. Complete a test purchase

---

## That's It!

**You now have:**
- ✅ Beautiful custom product page
- ✅ Working Add to Cart button
- ✅ Shopping cart functionality
- ✅ Direct checkout to Shopify
- ✅ Shopify processes payments
- ✅ You get orders in Shopify admin

---

## How It Works

**Customer Journey:**

1. **Your Website**: Customer sees beautiful product page
2. **Add to Cart**: Product added to cart (saved in browser)
3. **Proceed to Checkout**: Redirects to Shopify
4. **Shopify Checkout**: Customer completes purchase
5. **You Get Order**: Order appears in Shopify admin

**Behind the Scenes:**
```
Your Website → Customer clicks checkout
↓
Redirects to: drbibiorganics.com/cart/VARIANT_ID:QUANTITY
↓
Shopify adds product to cart automatically
↓
Customer checks out on Shopify
↓
You get the money! 💰
```

---

## What If I Have Multiple Products?

**Current Setup**: Works for single product (Butter Oasis)

**If you add more products later**, you'll need to:
1. Get variant ID for each product
2. Update the JavaScript to handle multiple products
3. Or create separate pages for each product

**For now**: Just focus on getting your main product working!

---

## Where to Host This Website?

### Option 1: Use it as Shopify Custom Theme (Recommended)

**Benefits:**
- Everything in one place
- No domain complications
- Easy to manage

**How:**
- Follow `SHOPIFY-THEME-UPDATE-GUIDE.md`
- Install as custom theme
- Set as live theme

### Option 2: Host on GoDaddy, Use Shopify for Checkout

**Benefits:**
- Keep exact HTML design
- No Shopify limitations

**How:**
- Upload to GoDaddy (follow `GODADDY-MIGRATION-GUIDE.md`)
- Website runs on GoDaddy
- Checkout redirects to Shopify
- Best of both worlds!

---

## Troubleshooting

**Q: Can't find variant ID in Shopify**
A: Make sure product is published. Try: Products → Butter Oasis → Variants → Click variant → Look at URL

**Q: Checkout redirects but cart is empty**
A: Double-check variant ID is exactly correct (no extra spaces, quotes, etc.)

**Q: Price doesn't match**
A: Price comes from Shopify. Update in: Shopify Admin → Products → Butter Oasis → Price

**Q: Want to test without real money**
A: Use Shopify's test mode: Settings → Payments → Enable test mode

---

## Need the Variant ID Right Now?

**Ultra Quick Method:**

1. Go to: https://drbibiorganics.com/products/butter-oasis-balm.json
   (Replace with your actual product handle)
2. Look for: `"variants": [{"id": 50253534298387`
3. That number is your variant ID!

**Or in browser console on product page:**
```javascript
fetch(window.location.href + '.json')
  .then(r => r.json())
  .then(d => console.log('Variant ID:', d.product.variants[0].id))
```

---

## Checklist

Before you start:
- [ ] I have access to Shopify admin
- [ ] I can find my product (Butter Oasis)
- [ ] I have a text editor to edit HTML files

After setup:
- [ ] Got variant ID from Shopify
- [ ] Updated product.html line 1153
- [ ] Saved file
- [ ] Tested add to cart
- [ ] Tested checkout redirect
- [ ] Verified product in Shopify cart
- [ ] Ready to go live!

---

**That's literally it!** Update one number, test, and you're done! 🚀

For detailed explanations, see: `SHOPIFY-INTEGRATION-SETUP.md`

*Last Updated: January 6, 2026*
