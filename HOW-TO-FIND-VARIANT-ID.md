# How to Find Your Shopify Variant ID
## 5 Different Methods - One Will Work!

---

## Method 1: From Your Live Product Page (EASIEST)

1. **Go to your live Shopify store**: https://drbibiorganics.com
2. **Navigate to your Butter Oasis product page**
3. **Right-click anywhere** on the page → **"View Page Source"**
4. **Press Ctrl+F** (or Cmd+F on Mac) to search
5. **Search for**: `"variant"`
6. **Look for a long number** that looks like: `"id":50253534298387`
7. **Copy that number** - that's your variant ID!

**Example of what you'll see:**
```json
"variants":[{"id":50253534298387,"title":"Default","option1":"Default"...
```

The number `50253534298387` is your variant ID.

---

## Method 2: Direct JSON URL (SUPER EASY)

1. **Find your product URL** - Example: `https://drbibiorganics.com/products/butter-oasis-balm`
2. **Add `.json` to the end**: `https://drbibiorganics.com/products/butter-oasis-balm.json`
3. **Open that URL in your browser**
4. **Look for**: `"variants":[{"id":`
5. **The number after `"id":` is your variant ID**

**Example:**
```json
{
  "product": {
    "id": 9876543210,
    "title": "Butter Oasis Moisturizing Balm",
    "variants": [
      {
        "id": 50253534298387,  ← THIS NUMBER!
        "title": "Default Title",
        "price": "70.00"
      }
    ]
  }
}
```

---

## Method 3: From Shopify Admin Product Page

1. **Log in to Shopify Admin**: https://admin.shopify.com/
2. **Click "Products"** in the left sidebar
3. **Click on "Butter Oasis Moisturizing Balm"** (or your product name)
4. **Look at the URL in your browser address bar**
5. You'll see something like: `admin.shopify.com/store/YOUR-STORE/products/9876543210`
6. **Scroll down on the page to the "Variants" section**
7. If you see a variant listed, **click on it**
8. **Look at the new URL** - it will show: `.../products/9876543210/variants/50253534298387`
9. **Copy the last number** (50253534298387) - that's your variant ID!

**Note**: If you don't see a "Variants" section and it just says "This product has one variant", that's okay - continue to Method 4.

---

## Method 4: Using Browser Console (FOR TECH-SAVVY)

1. **Go to your product page**: https://drbibiorganics.com/products/butter-oasis-balm
2. **Right-click → "Inspect"** (or press F12)
3. **Click on the "Console" tab**
4. **Paste this code** and press Enter:

```javascript
fetch(window.location.href + '.json')
  .then(response => response.json())
  .then(data => {
    console.log('YOUR VARIANT ID:', data.product.variants[0].id);
    alert('Your Variant ID is: ' + data.product.variants[0].id);
  });
```

5. **An alert will pop up** with your variant ID!
6. **Copy that number**

---

## Method 5: From Shopify Add to Cart Button

1. **Go to your live product page**
2. **Right-click on the "Add to Cart" button** → **"Inspect"**
3. **Look at the HTML code** that appears
4. **Search for** `variant` or `data-variant-id` or `value=`
5. **You'll see a long number** - that's your variant ID!

**Example HTML you might see:**
```html
<input type="hidden" name="id" value="50253534298387">
```
or
```html
<button data-variant-id="50253534298387">Add to Cart</button>
```

The number `50253534298387` is your variant ID!

---

## Method 6: Contact Shopify Support

If none of the above work:

1. **Contact Shopify Support Chat** (in your Shopify admin, bottom right)
2. **Ask them**: "What is the variant ID for my product 'Butter Oasis Moisturizing Balm'?"
3. They'll give it to you instantly!

---

## What If I Have Multiple Variants?

If you have multiple sizes/versions (e.g., 4oz, 8oz):

**Each variant has its own ID:**
- Butter Oasis 4oz: `50253534298387`
- Butter Oasis 8oz: `50253534298388`
- Bundle: `50253534298389`

**For now**: Just get the ID for your main/default product variant.

**Later**: You can add logic to handle multiple variants.

---

## Common Issues

**Q: I see multiple numbers, which one is correct?**
A: The variant ID is usually 11-14 digits long and appears after `"id":` in the variants section.

**Q: I only see a product ID, not a variant ID**
A: Product ID and Variant ID are different. Variant ID is usually longer. Look specifically in the "variants" array.

**Q: My product doesn't have variants**
A: That's okay! Shopify still creates a "default" variant. Use Method 2 (.json URL) to find it.

**Q: The number has quotes around it**
A: Just copy the number without the quotes.

---

## Once You Have Your Variant ID

**Write it down here:**

```
MY VARIANT ID: _____________________
```

**Then:**
1. Open `product.html` in a text editor
2. Press Ctrl+F and search for: `SHOPIFY_VARIANT_ID`
3. Replace the existing number with YOUR variant ID
4. Save the file
5. Upload to Shopify or GoDaddy

---

## Still Can't Find It?

**Try this quick test:**

1. Go to: https://drbibiorganics.com/cart/clear (clears your cart)
2. Go to your product page
3. Add product to cart
4. Go to: https://drbibiorganics.com/cart
5. Right-click → View Page Source
6. Search for "variant"
7. You'll see your variant ID in the cart data!

---

**Need more help?** Let me know which method you tried and what you're seeing!

*Last Updated: January 6, 2026*
