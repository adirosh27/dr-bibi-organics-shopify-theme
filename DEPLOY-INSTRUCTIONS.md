# Deployment Instructions
## How to Upload Your New Website

**Important**: I can't directly deploy to your Shopify or GoDaddy account (I don't have access).

But I'll show you **exactly** how to do it yourself - it's easier than you think!

---

## Before You Deploy

### Step 1: Find Your Variant ID First!

**You MUST do this before deploying:**

1. Open: `HOW-TO-FIND-VARIANT-ID.md`
2. Follow **Method 2** (easiest - the .json URL method)
3. Write down your variant ID

**Quick Method:**
- Go to: `https://drbibiorganics.com/products/butter-oasis-balm.json`
- Look for: `"variants":[{"id":NUMBERS_HERE`
- Copy those numbers

---

### Step 2: Update product.html with Your Variant ID

1. **Open** `product.html` in Notepad (or any text editor)
2. **Press Ctrl+F** and search for: `SHOPIFY_VARIANT_ID`
3. **You'll find this line** (around line 1153):
   ```javascript
   const SHOPIFY_VARIANT_ID = '50253534298387';
   ```
4. **Replace** `50253534298387` with YOUR variant ID from Step 1
5. **Save** the file

**Example**: If your variant ID is `12345678901234`, change to:
```javascript
const SHOPIFY_VARIANT_ID = '12345678901234';
```

---

## Deployment Option 1: Update Your Shopify Theme (RECOMMENDED)

**This replaces your current Shopify pages with the new design.**

### A. Update Homepage

1. **In Shopify Admin**, go to: **Online Store** → **Themes**
2. Click **Customize** on your live theme
3. Click **Add section** at bottom
4. Choose **Custom Liquid** or **Custom HTML**
5. **Open** `index.html` in Notepad
6. **Select all** (Ctrl+A) and **Copy** (Ctrl+C)
7. **Paste** into Shopify Custom Liquid section
8. Click **Save**
9. Preview to see if it looks good

**Note**: This adds a new section. You may want to remove old homepage sections first.

### B. Update Product Page

**Option B1: Update Product Description (Simplest)**

1. **Shopify Admin** → **Products**
2. Click **Butter Oasis Moisturizing Balm**
3. In the description box, click **< > Show HTML**
4. **Open** `product.html` and copy the content section (the product description HTML)
5. **Paste** into Shopify description
6. **Save**

**Option B2: Create Custom Product Template**

This requires more technical knowledge. See: `SHOPIFY-THEME-UPDATE-GUIDE.md`

### C. Add Custom Pages

**For About/Story Page:**
1. **Online Store** → **Pages** → **Add page**
2. Title: "Our Story"
3. Click **< > Show HTML**
4. Copy content from the About section in `index.html`
5. Paste and **Save**

**For FAQs:**
1. **Add page**
2. Title: "FAQs"
3. Click **< > Show HTML**
4. **Open** `faqs.html` → Select all → Copy
5. Paste and **Save**

---

## Deployment Option 2: Upload to GoDaddy (ALTERNATIVE)

**This hosts the website on GoDaddy, checkout redirects to Shopify.**

### Before You Start:

✅ Variant ID updated in product.html (see Step 2 above)
✅ GoDaddy hosting account ready
✅ Domain configured

### Upload Files:

1. **Log in to GoDaddy**
2. **My Products** → **Web Hosting** → **Manage** → **cPanel Admin**
3. Click **File Manager**
4. Navigate to `public_html`
5. Click **Upload**
6. **Upload these files**:
   - index.html
   - product.html
   - contact.html
   - checkout.html
   - faqs.html
   - search.html
   - thank-you.html
   - All legal pages (privacy, terms, returns, etc.)
   - .htaccess
   - robots.txt
   - sitemap.xml
7. **Create folders**: `emails`, `Photos`, `Video`
8. **Upload contents** to each folder

### Test:

1. Go to: `https://drbibiorganics.com/product.html`
2. Click **Add to Cart**
3. Click **Proceed to Checkout**
4. Should redirect to Shopify checkout ✓

---

## Deployment Option 3: Hybrid Approach (ADVANCED)

**GoDaddy for marketing pages, Shopify for e-commerce:**

### Setup:

1. **GoDaddy hosts**:
   - Homepage (index.html)
   - About page
   - Blog/content

2. **Shopify hosts**:
   - Product pages
   - Cart/Checkout
   - Customer accounts

3. **Link between them**:
   - "Shop Now" buttons → Link to Shopify
   - Navigation menu → Mix of both

### DNS Configuration:

This requires advanced setup. See: `SHOPIFY-TO-GODADDY-MIGRATION.md` for DNS details.

---

## What You Need to Deploy

### Files That MUST Be Updated Before Upload:

**Required:**
- [ ] `product.html` - **UPDATE VARIANT ID FIRST!**

**Recommended:**
- [ ] `index.html` - Check if variant ID is used here too
- [ ] All other HTML files - Should work as-is

### Files That Are Ready As-Is:

✅ All HTML pages (after variant ID update)
✅ .htaccess (configured for GoDaddy)
✅ robots.txt
✅ sitemap.xml
✅ All legal pages
✅ Email templates

---

## Testing Checklist

**After deployment, test these:**

### On Website:
- [ ] Homepage loads correctly
- [ ] Product page loads correctly
- [ ] Images display properly
- [ ] Mobile responsive works
- [ ] Forms submit properly

### E-commerce Flow:
- [ ] Click "Add to Cart" - works?
- [ ] Cart icon shows quantity?
- [ ] Click "Proceed to Checkout"
- [ ] **Redirects to Shopify checkout?** ← MOST IMPORTANT
- [ ] Product appears in Shopify cart?
- [ ] Product details correct (price, name)?
- [ ] Can complete purchase?
- [ ] Order appears in Shopify admin?

### If Checkout Doesn't Work:

**Check these:**
1. Variant ID is correct in product.html
2. Shopify product is published
3. Product is available for sale
4. URL format is correct: `/cart/VARIANT_ID:QUANTITY`

**Test manually:**
- Go to: `https://drbibiorganics.com/cart/YOUR_VARIANT_ID:1`
- Replace YOUR_VARIANT_ID with actual ID
- Should add product to cart automatically

---

## Common Deployment Issues

### Issue: "I updated product.html but changes don't show"

**Solution:**
- Clear browser cache (Ctrl+Shift+R)
- Try in incognito/private window
- Make sure you uploaded the RIGHT file

### Issue: "Variant ID still says 50253534298387"

**Solution:**
- You edited the file but didn't save
- Or you uploaded the OLD version
- Re-edit, save, re-upload

### Issue: "Checkout redirects but cart is empty"

**Solution:**
- Variant ID is wrong
- Try Method 2 in `HOW-TO-FIND-VARIANT-ID.md`
- Double-check the number is exactly correct

### Issue: "Images don't load"

**Solution:**
- Currently using Shopify CDN URLs
- These should work fine
- If not, download images and upload to GoDaddy

---

## Quick Deployment Summary

**What YOU need to do (I can't do this for you):**

1. ✅ **Find variant ID** → `HOW-TO-FIND-VARIANT-ID.md`
2. ✅ **Update product.html** → Replace variant ID (line 1153)
3. ✅ **Save the file**
4. ✅ **Choose deployment method**:
   - **Shopify**: Copy/paste into Shopify admin
   - **GoDaddy**: Upload via FTP or cPanel
5. ✅ **Test the checkout flow**
6. ✅ **Complete test purchase**
7. ✅ **Go live!**

---

## I Can Help You With:

✅ Explaining where to find variant ID
✅ Showing you which file to edit
✅ Explaining what each file does
✅ Troubleshooting errors
✅ Answering questions

## I CANNOT Do:

❌ Log in to your Shopify account
❌ Access your GoDaddy hosting
❌ Upload files for you
❌ Get your variant ID for you

**But I can guide you through each step!**

---

## Need Help?

**Tell me:**
1. Which deployment method you want to use
2. Where you're stuck
3. What error message you see (if any)

**I'll help you through it step-by-step!**

---

## Next Steps RIGHT NOW:

**Step 1**: Open `HOW-TO-FIND-VARIANT-ID.md`
**Step 2**: Use Method 2 to find your variant ID
**Step 3**: Tell me the variant ID
**Step 4**: I'll help you update the file
**Step 5**: You upload to Shopify or GoDaddy
**Step 6**: Test and go live!

Let's do this! 🚀

*Last Updated: January 6, 2026*
