# Shopify Theme Update Guide
## Applying Your New Design to Your Existing Shopify Store

**Goal**: Keep your Shopify store fully functional BUT update it with this beautiful new design

**What You Keep**:
- ✅ All e-commerce functionality
- ✅ Shopping cart & checkout
- ✅ Payment processing
- ✅ Customer accounts
- ✅ Order management
- ✅ Judge.me reviews
- ✅ All Shopify apps

**What Changes**:
- 🎨 Brand new design (colors, fonts, layout)
- 🎨 Updated product page
- 🎨 Improved homepage
- 🎨 Better mobile experience
- 🎨 Modern, clean aesthetic

---

## Table of Contents

1. [Quick Overview](#quick-overview)
2. [Best Approach: Option Comparison](#best-approach-option-comparison)
3. [Option 1: Theme Customizer (Easiest)](#option-1-theme-customizer-easiest)
4. [Option 2: Page Builder App (Recommended)](#option-2-page-builder-app-recommended)
5. [Option 3: Custom Theme Development](#option-3-custom-theme-development)
6. [Option 4: Hire a Shopify Developer](#option-4-hire-a-shopify-developer)
7. [Design Assets Reference](#design-assets-reference)

---

## Quick Overview

### Your New Design Features

**Design System:**
- **Colors**: Emerald (#4A9B7F), Forest (#2D5F4F), Ivory (#FFFEF9), Gold (#C8A882)
- **Fonts**: Playfair Display (headings), Jost (body)
- **Style**: Modern luxury, natural, organic, clinical-yet-approachable

**Key Pages in Static HTML:**
1. **Homepage** - Hero, benefits, testimonials, story, newsletter
2. **Product Page** - Detailed product info, cart, reviews, FAQ
3. **Contact Page** - Contact form
4. **Checkout Page** - Custom checkout design
5. **Legal Pages** - Privacy, terms, return policy, FAQs

**Challenge**: Convert these HTML pages to work within Shopify's theme system while keeping all e-commerce functionality.

---

## Best Approach: Option Comparison

### Option 1: Theme Customizer (DIY - Free)
**Time**: 8-16 hours
**Cost**: $0
**Difficulty**: Medium
**Best for**: People comfortable with Shopify admin

✅ Pros:
- Free
- No coding required
- Works with existing theme
- Can do it yourself

❌ Cons:
- Limited to theme's capabilities
- Won't look exactly like the HTML
- Time-consuming
- May need to compromise on design

### Option 2: Page Builder App (DIY - Paid)
**Time**: 4-8 hours
**Cost**: $20-40/month
**Difficulty**: Easy-Medium
**Best for**: Want exact design match without coding

✅ Pros:
- Drag-and-drop interface
- Can recreate HTML design closely
- No coding needed
- Professional results

❌ Cons:
- Monthly subscription
- Slight learning curve
- May slow down site slightly

**Recommended Apps:**
- **PageFly** ($24/month) - Most powerful
- **GemPages** ($29/month) - Great for product pages
- **Shogun** ($39/month) - User-friendly

### Option 3: Custom Theme (DIY - Free but Advanced)
**Time**: 20-40 hours
**Cost**: $0
**Difficulty**: Advanced (requires coding)
**Best for**: Developers or those who want full control

✅ Pros:
- Complete control
- Exact match to HTML design
- No ongoing costs
- Best performance

❌ Cons:
- Requires Shopify Liquid knowledge
- Time-intensive
- Complex
- Easy to break things

### Option 4: Hire Developer (Professional)
**Time**: 1-2 weeks (dev time)
**Cost**: $500-2,000
**Difficulty**: None (for you)
**Best for**: Want perfect results without effort

✅ Pros:
- Professional results
- Exact HTML recreation
- No work for you
- Optimized performance

❌ Cons:
- Expensive
- Need to find reliable developer
- Takes 1-2 weeks

---

## Option 1: Theme Customizer (Easiest - Start Here)

This approach updates your current Shopify theme using the built-in customizer.

### Step 1: Backup Your Current Theme

1. **In Shopify Admin**, go to **Online Store** → **Themes**
2. Find your current live theme
3. Click **Actions** → **Duplicate**
4. Rename duplicate: "Backup - [Date]"

**Why**: If you mess up, you can restore this backup instantly.

### Step 2: Enter Theme Customizer

1. On your live theme, click **Customize**
2. You'll see a preview of your site with editing options on the left

### Step 3: Update Colors (30 minutes)

**New Color Palette**:
- Primary (Emerald): `#4A9B7F`
- Secondary (Forest): `#2D5F4F`
- Background (Ivory): `#FFFEF9`
- Accent (Gold): `#C8A882`
- Text (Charcoal): `#1F2937`

**How to update:**
1. In customizer, go to **Theme settings** → **Colors**
2. Update each color to match above palette
3. Update button colors to emerald/forest gradient
4. Update background to ivory

### Step 4: Update Typography (15 minutes)

**New Fonts**:
- Headings: **Playfair Display** (serif)
- Body: **Jost** (sans-serif)

**How to update:**
1. **Theme settings** → **Typography**
2. Set **Heading font** to: Playfair Display (or similar serif like Cormorant, Lora)
3. Set **Body font** to: Jost (or similar sans-serif like Work Sans, Inter)
4. Adjust font sizes if needed

### Step 5: Update Homepage Sections (2-4 hours)

Your new HTML homepage has these sections:
1. Hero with video background
2. Benefits section
3. Testimonials
4. Brand story
5. Newsletter signup
6. Exit popup

**Recreate in Shopify:**

**A. Hero Section:**
1. In customizer, find your homepage hero section
2. Update hero image or video
3. Update headline text: "Healing Made Simple, Naturally"
4. Update subheading
5. Update button text: "Shop Butter Oasis"
6. Change button color to emerald

**B. Benefits Section:**
1. Look for "Features" or "Benefits" section
2. Add/edit 3-4 benefit blocks:
   - "24-Hour+ Deep Hydration"
   - "Clinical-Grade Natural Ingredients"
   - "Repairs Damaged Skin Barrier"
   - "Safe for Sensitive Skin"
3. Add icons if your theme supports them

**C. Testimonials:**
1. Add "Testimonials" or "Reviews" section
2. Copy testimonial text from `index.html` (lines 420-550)
3. Add customer names and photos if possible

**D. Brand Story:**
1. Add "Rich text" or "About" section
2. Copy story content from `index.html` (lines 285-330)
3. Add Dr. Bibi's photo

**E. Newsletter Signup:**
1. Add "Newsletter" section at bottom
2. Text: "Get 10% off your first purchase"
3. Connect to your email provider

### Step 6: Update Product Page (1-2 hours)

**Your current Shopify product page** likely has basic layout. Your new HTML design has:
- Large product images
- Detailed description
- Ingredients breakdown
- How to use
- Benefits
- Reviews section
- Add to cart with quantity selector

**Update in Shopify:**
1. **In customizer**, navigate to **Products** → **Default product**
2. Rearrange sections to match HTML layout
3. Update product description with content from `product.html`
4. Add custom sections for:
   - Ingredients (lines 615-700 in product.html)
   - How to use (lines 705-775)
   - Benefits (lines 780-850)

**Product Description HTML:**
Copy the detailed description from `product.html` and paste into your Shopify product description (it accepts HTML).

### Step 7: Update Contact Page (30 minutes)

1. Go to **Pages** in Shopify admin
2. Edit your Contact page
3. Paste the contact form HTML from `contact.html`
4. Or use Shopify's built-in contact form template

### Step 8: Update Footer (30 minutes)

1. In customizer, go to **Footer** section
2. Update footer menu links to match new design:
   - Quick Links: Search, FAQs, Terms, Privacy, Refund Policy
   - Support: Contact Us, Phone number
   - Shop: Product, Our Story, Reviews
3. Update footer text: "Clinical-grade natural skincare crafted with pure African ingredients"

### Step 9: Mobile Optimization (1 hour)

1. In customizer, toggle to **Mobile view** (phone icon)
2. Check all sections on mobile
3. Adjust spacing, font sizes if needed
4. Test buttons are easily tappable
5. Ensure images scale properly

### Step 10: Publish & Test (30 minutes)

1. Click **Save** in customizer
2. **Before publishing**, click **Preview** to see full site
3. Test on desktop and mobile
4. Check all links work
5. Test checkout process
6. When ready, click **Publish**

---

## Option 2: Page Builder App (Recommended for Best Results)

This gives you much more control and can recreate the HTML design almost perfectly.

### Step 1: Choose & Install Page Builder

**Recommended: PageFly** (14-day free trial, then $24/month)

1. **In Shopify Admin**, go to **Apps** → **Shopify App Store**
2. Search for "PageFly"
3. Click **Add app** → Install
4. Grant permissions

**Alternative**: GemPages, Shogun, Replo

### Step 2: Create New Homepage

1. Open **PageFly** app
2. Click **Create New Page**
3. Choose **Regular Page**
4. Name it: "New Homepage"

### Step 3: Build Homepage Using HTML as Reference

**PageFly is drag-and-drop**, so you'll recreate each section:

**A. Hero Section:**
1. Add **Hero** element
2. Background: Upload your hero image/video
3. Headline: "Healing Made Simple, Naturally"
4. Subheading: "Pure African ingredients meet clinical-grade skincare..."
5. Button: "Shop Butter Oasis" → Link to product page
6. Style:
   - Heading font: Playfair Display
   - Button color: Emerald (#4A9B7F)
   - Background overlay if using video

**B. Benefits Section:**
1. Add **Columns** element (3 or 4 columns)
2. Each column:
   - Icon (upload from Font Awesome or use emoji)
   - Heading: "24-Hour+ Deep Hydration"
   - Text: Copy from `index.html` lines 165-185
3. Style with emerald color accents

**C. Product Showcase:**
1. Add **Product** element
2. Select your Butter Oasis product
3. Layout: Image left, info right
4. Add to cart button styled in emerald

**D. Testimonials:**
1. Add **Testimonial** element or **Columns**
2. Create 3 testimonial cards
3. Copy text from `index.html` (lines 420-550)
4. Add 5-star ratings
5. Add customer names

**E. Brand Story:**
1. Add **Text with Image** element
2. Left: Dr. Bibi's story text (copy from index.html lines 285-330)
3. Right: Upload Dr. Bibi's photo
4. Style with serif font for headings

**F. Newsletter:**
1. Add **Newsletter** element
2. Heading: "Join Our Natural Beauty Community"
3. Subheading: "Get 10% off your first purchase"
4. Connect to your email provider (MailChimp, Klaviyo, etc.)

### Step 4: Style Your Page

**Global Styles in PageFly:**
1. Click **General** tab
2. **Typography**:
   - Heading font: Playfair Display
   - Body font: Jost
3. **Colors**:
   - Primary: #4A9B7F (Emerald)
   - Secondary: #2D5F4F (Forest)
   - Background: #FFFEF9 (Ivory)
4. **Buttons**:
   - Background: Gradient from emerald to forest
   - Border radius: 9999px (pill shape)
   - Padding: 16px 32px

### Step 5: Create Product Page

1. In PageFly, click **Create New Page** → **Product Page**
2. Name: "Butter Oasis Product Page"
3. **Build sections** (reference: product.html):

**A. Product Header:**
- Product images (gallery on left)
- Product info on right:
  - Title
  - Price (with strikethrough for original price)
  - 5-star rating
  - Description
  - Quantity selector
  - Add to cart button (emerald)
  - Trust badges (30-day guarantee, free shipping)

**B. Detailed Description:**
- Full product description with HTML formatting
- Copy from product.html lines 560-610

**C. Ingredients Section:**
- 3 columns for 3 ingredients
- Shea butter, Cocoa butter, Argan oil
- Icons + descriptions
- Copy from product.html lines 615-700

**D. How to Use:**
- Step-by-step guide
- Icons for each step
- Copy from product.html lines 705-775

**E. Benefits:**
- Grid layout with benefit cards
- Icons + text
- Copy from product.html lines 780-850

**F. Reviews:**
- Integrate Judge.me app (you already have it)
- Add Judge.me reviews widget
- Style to match design

**G. FAQ:**
- Accordion/collapsible FAQ section
- Copy questions from faqs.html

### Step 6: Publish Pages

1. **Save** each page in PageFly
2. **Set as homepage**: PageFly settings → Set as homepage
3. **Assign product page**: PageFly → Products → Assign to Butter Oasis product

### Step 7: Test Everything

- Test add to cart
- Test checkout flow
- Test on mobile
- Test all links
- Check page speed

---

## Option 3: Custom Theme Development

**For developers only** - This involves creating a custom Shopify theme using Liquid.

### Overview

You'll need to:
1. Set up Shopify CLI
2. Create theme file structure
3. Convert HTML to Liquid templates
4. Integrate with Shopify's cart/checkout system
5. Add Shopify product loops and filters

### File Structure

```
theme/
├── assets/
│   ├── styles.css (your Tailwind styles)
│   └── scripts.js
├── config/
│   └── settings_schema.json
├── layout/
│   └── theme.liquid
├── sections/
│   ├── header.liquid
│   ├── footer.liquid
│   ├── hero.liquid
│   ├── benefits.liquid
│   └── testimonials.liquid
├── snippets/
│   ├── product-card.liquid
│   └── cart-drawer.liquid
└── templates/
    ├── index.liquid (homepage)
    ├── product.liquid
    ├── collection.liquid
    └── page.contact.liquid
```

### Key Conversions

**HTML to Liquid Examples:**

**Static HTML:**
```html
<h1>Butter Oasis Moisturizing Balm</h1>
<p>$70.00</p>
```

**Shopify Liquid:**
```liquid
<h1>{{ product.title }}</h1>
<p>{{ product.price | money }}</p>
```

**Static Cart:**
```html
<button onclick="addToCart()">Add to Cart</button>
```

**Shopify Cart:**
```liquid
<form action="/cart/add" method="post">
  <input type="hidden" name="id" value="{{ product.selected_or_first_available_variant.id }}">
  <button type="submit">Add to Cart</button>
</form>
```

### Resources

- **Shopify Theme Docs**: https://shopify.dev/themes
- **Liquid Reference**: https://shopify.dev/api/liquid
- **Theme Kit**: https://shopify.dev/themes/tools/theme-kit
- **Shopify CLI**: https://shopify.dev/themes/tools/cli

### Estimated Time: 20-40 hours

**Not recommended unless you're a Shopify developer.**

---

## Option 4: Hire a Shopify Developer

### What to Ask For

**Project Brief:**
"Convert custom HTML/CSS design to fully functional Shopify theme. Maintain all current e-commerce functionality (cart, checkout, apps, Judge.me reviews) while implementing new design system."

**Deliverables:**
- Custom Shopify theme based on provided HTML files
- Responsive mobile design
- Integration with existing apps (Judge.me, etc.)
- Product page template
- Homepage sections
- Collection page
- Contact page
- Cart/checkout integration
- Performance optimization
- Training on how to update content

### Where to Find Developers

**Recommended Platforms:**
1. **Shopify Experts**: https://experts.shopify.com/
   - Vetted Shopify specialists
   - Built-in project management
   - Escrow payment protection
   - **Cost**: $1,000-3,000

2. **Upwork**: https://upwork.com/
   - Filter by "Shopify Expert"
   - Check reviews and portfolio
   - **Cost**: $500-2,000

3. **Fiverr**: https://fiverr.com/
   - Search "custom Shopify theme"
   - Check Pro sellers
   - **Cost**: $300-1,500

4. **Storetasker**: https://storetasker.com/
   - Shopify-only marketplace
   - Vetted experts
   - **Cost**: $1,000-3,000

### What to Provide to Developer

1. **All HTML files** from this project
2. **Design assets**:
   - Color palette
   - Fonts (Playfair Display, Jost)
   - Logo files
   - Product images
3. **Access to Shopify store** (Collaborator account)
4. **Current theme backup**
5. **List of required apps** (Judge.me, etc.)
6. **This design guide** for reference

### Timeline

- Initial consultation: 1-2 hours
- Development: 1-2 weeks
- Revisions: 3-5 days
- Testing & launch: 2-3 days
- **Total: 2-3 weeks**

### Cost Breakdown

**Budget Option**: $500-800 (Fiverr, basic customization)
**Mid-Range**: $1,000-1,500 (Upwork, good quality)
**Premium**: $2,000-3,000 (Shopify Experts, best quality)

---

## Design Assets Reference

### Color Palette

```css
/* Primary Colors */
--emerald: #4A9B7F;
--forest: #2D5F4F;

/* Backgrounds */
--ivory: #FFFEF9;
--pearl: #FBF8F3;
--sage: #C4D5CC;
--mint: #D8E8DD;

/* Accents */
--gold: #C8A882;
--bronze: #B8986A;

/* Text */
--charcoal: #1F2937;
--slate: #64748B;
```

### Typography

**Fonts from Google Fonts:**
```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,600;1,700&family=Jost:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

**CSS:**
```css
font-family: 'Playfair Display', serif;  /* Headings */
font-family: 'Jost', sans-serif;         /* Body */
```

### Button Styles

```css
/* Primary Button */
background: linear-gradient(to right, #4A9B7F, #2D5F4F);
color: white;
padding: 12px 32px;
border-radius: 9999px;
font-weight: 600;
box-shadow: 0 4px 14px rgba(74, 155, 127, 0.3);
```

### Spacing

- Container max-width: 1280px (7xl)
- Section padding: 60px (lg:80px)
- Card padding: 32px
- Border radius: 24px (cards), 9999px (buttons)

---

## Recommended Approach (Summary)

**If you have budget ($1,000-2,000):**
→ **Hire a Shopify Expert** - Best results, no effort

**If you want to DIY and get close match:**
→ **Use PageFly or GemPages** - $24-29/month, 4-8 hours work

**If you're on tight budget:**
→ **Use Theme Customizer** - Free, 8-16 hours work, won't be exact match

**If you're a developer:**
→ **Custom theme** - Free, 20-40 hours, perfect match

---

## Next Steps

1. **Choose your approach** from above
2. **Backup your current theme** (always do this first!)
3. **Start with homepage** - Get that looking good first
4. **Then product page** - Most important for sales
5. **Then other pages** - Contact, FAQs, etc.
6. **Test thoroughly** before going live
7. **Get feedback** from friends/colleagues
8. **Launch** when ready!

---

## Important Notes

### Keep These Shopify Features

- **Shopping cart** - Don't replace with static cart
- **Checkout** - Use Shopify's built-in checkout
- **Customer accounts** - Keep login functionality
- **Judge.me reviews** - Integrate with new design
- **Analytics tracking** - Maintain all tracking codes
- **Email marketing** - Keep existing integrations

### What Can Be Replaced

- Design/colors/fonts
- Homepage layout
- Product page layout
- Page content/copy
- Images and videos
- Navigation menu

### Testing Checklist

Before launching your updated theme:

- [ ] Homepage loads correctly on desktop
- [ ] Homepage loads correctly on mobile
- [ ] Product page shows correct product info
- [ ] Add to cart works
- [ ] Cart updates quantities
- [ ] Checkout process works end-to-end
- [ ] Contact form submits
- [ ] All navigation links work
- [ ] Footer links work
- [ ] Images load properly
- [ ] Videos play (if used)
- [ ] Colors match design
- [ ] Fonts match design
- [ ] Judge.me reviews display
- [ ] Mobile menu works
- [ ] Page speed is acceptable (test at pagespeed.web.dev)

---

**Questions?**

- Shopify Support: https://help.shopify.com/
- Shopify Community: https://community.shopify.com/
- PageFly Support: Inside PageFly app
- Theme Developer Hire: https://experts.shopify.com/

**Good luck with your Shopify theme update!** 🎨

*Last Updated: January 6, 2026*
