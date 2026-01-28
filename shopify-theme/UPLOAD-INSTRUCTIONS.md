# How to Upload to Shopify (Hardcoded Version)

These templates are **exact copies** of your Vercel pages - fully hardcoded to look identical.

---

## Files to Upload

| File | Purpose |
|------|---------|
| `templates/product.butter-oasis-hardcoded.liquid` | Product page (exact copy of Vercel) |
| `templates/index.hardcoded.liquid` | Homepage (exact copy of Vercel) |

---

## Step 1: Upload the Product Template

1. Go to **Shopify Admin** → **Online Store** → **Themes**
2. Click **"..."** on your current theme → **Edit code**
3. In the left sidebar, find **Templates** folder
4. Click **Add a new template**
5. Select:
   - Template type: **product**
   - Template name: **butter-oasis-hardcoded**
6. Delete ALL the default content
7. Open `templates/product.butter-oasis-hardcoded.liquid` in a text editor
8. **Copy ALL** the content (Ctrl+A, Ctrl+C)
9. **Paste** into Shopify (Ctrl+V)
10. Click **Save**

---

## Step 2: Assign Template to Product

1. Go to **Products** in your Shopify admin
2. Click on **Butter Oasis** product
3. Scroll down to **Theme template** (right sidebar)
4. Select **product.butter-oasis-hardcoded** from dropdown
5. Click **Save**
6. **Preview** the product page - it should look exactly like Vercel!

---

## Step 3: Upload the Homepage Template

**Option A: Replace your existing homepage**
1. In Shopify code editor, find **Templates** → `index.liquid` or `index.json`
2. If it's `index.json`, you may need to create a new `index.liquid` instead
3. **Backup** your current homepage first (copy content to a file)
4. Replace ALL content with `templates/index.hardcoded.liquid`
5. Click **Save**

**Option B: If your theme uses JSON templates (Online Store 2.0)**
1. You may need to create a custom section instead
2. Or contact me and I can help adapt it for your theme

---

## Step 4: Test Everything

1. Visit your product page → Should look exactly like Vercel
2. Visit your homepage → Should look exactly like Vercel
3. Test Add to Cart → Items should go to Shopify cart
4. Test Proceed to Checkout → Should go to Shopify checkout
5. Test on mobile

---

## What's Different from the Dynamic Templates?

The **hardcoded templates** have:
- All product info (name, price, images, descriptions) directly in the HTML
- All content exactly as it appears on your Vercel site
- No Shopify Liquid variables like `{{ product.price }}`
- Links updated to use Shopify URLs (/products/..., /pages/...)

This means the page will look **identical** to Vercel, but you'll need to manually update the template if you want to change product details.

---

## Troubleshooting

### Page still looks different?
- Make sure you copied ALL the content (use Ctrl+A to select all)
- Check that no content was cut off
- Verify the template is assigned to the product

### Styles not loading?
- The templates include Tailwind CSS via CDN
- They should work without additional CSS files

### Checkout not working?
- The checkout redirects to: `https://drbibiorganics.com/cart/VARIANT_ID:QUANTITY`
- This uses Shopify's native cart
- Make sure your product variant ID is correct (currently: 50253534298387)

### Images not showing?
- Images use your Shopify CDN URLs (drbibiorganics.com/cdn/...)
- They should load automatically
- Local images (Photos folder) need to be uploaded to Shopify Assets

---

## Need to Update Product Info?

Since these are hardcoded, to change:
- **Price**: Search for `$70` and `$95` in the template
- **Product name**: Search for `Butter Oasis`
- **Images**: Search for the image URLs and replace
- **Description**: Find and edit the text directly

---

## Files Summary

```
shopify-theme/
├── templates/
│   ├── product.butter-oasis-hardcoded.liquid  ← USE THIS (exact Vercel copy)
│   ├── index.hardcoded.liquid                  ← USE THIS (exact Vercel copy)
│   ├── product.butter-oasis-full.liquid        ← Old dynamic version
│   └── index.liquid                            ← Old dynamic version
```
