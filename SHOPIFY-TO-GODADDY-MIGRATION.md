# Shopify to GoDaddy Migration Guide
## Replacing Your Shopify Store with Static HTML on GoDaddy

**Current Site**: https://drbibiorganics.com/ (Shopify)
**New Site**: Static HTML hosted on GoDaddy
**Date**: January 6, 2026
**Status**: Ready for Migration

---

## ⚠️ CRITICAL WARNINGS - READ FIRST

### What You Will Lose When Leaving Shopify

**E-commerce Features:**
- ❌ Shopping cart functionality (payment processing)
- ❌ Checkout system
- ❌ Order management
- ❌ Inventory tracking
- ❌ Customer accounts
- ❌ Order history
- ❌ Automated email receipts

**Apps & Integrations:**
- ❌ Judge.me reviews (customer testimonials)
- ❌ Shopify Analytics
- ❌ Built-in SEO tools
- ❌ Abandoned cart recovery
- ❌ Customer database

**Payment Processing:**
- ❌ Credit card processing
- ❌ Apple Pay, Google Pay, Shop Pay
- ❌ PCI compliance handling

### What the New Static Site DOES Have

**✅ Information & Marketing:**
- Product information pages
- Contact forms (via FormSubmit.co)
- Email collection (newsletter signup)
- Exit-intent popups with discount codes
- Mobile-responsive design
- SEO optimization

**✅ Manual Order Processing:**
- Customers fill out checkout form
- You receive order details via email to: Support@drbibiorganics.com
- You manually process payments (phone, email, external payment link)
- You manually fulfill orders

**⚠️ IMPORTANT**: This is NOT a full e-commerce solution. It's a lead-generation and information site with a manual order form.

### Recommended: Test First

**Before replacing your live Shopify store:**
1. Set up GoDaddy hosting on a temporary domain (e.g., `test.drbibiorganics.com`)
2. Test the new site thoroughly
3. Verify all forms work
4. Ensure you're comfortable with manual order processing
5. Then switch the main domain

---

## Table of Contents

1. [Pre-Migration Checklist](#pre-migration-checklist)
2. [Backup Shopify Data](#backup-shopify-data)
3. [GoDaddy Setup](#godaddy-setup)
4. [Upload Website Files](#upload-website-files)
5. [Disconnect from Shopify & Point DNS to GoDaddy](#disconnect-from-shopify--point-dns-to-godaddy)
6. [SSL Certificate Setup](#ssl-certificate-setup)
7. [Post-Migration Testing](#post-migration-testing)
8. [Cancel Shopify Subscription](#cancel-shopify-subscription)
9. [Troubleshooting](#troubleshooting)

---

## Pre-Migration Checklist

### Questions to Answer Before Migrating

- [ ] **Do you understand you'll lose full e-commerce functionality?**
- [ ] **Are you prepared to manually process orders via email?**
- [ ] **Do you have a payment processing alternative?** (PayPal invoice, Venmo, Zelle, etc.)
- [ ] **Have you backed up all Shopify data?** (customers, orders, products)
- [ ] **Do you want to preserve customer reviews?** (need to migrate Judge.me reviews)
- [ ] **Is your domain registered with GoDaddy or elsewhere?**
- [ ] **Do you have GoDaddy hosting set up?**

### What You'll Need

- [ ] GoDaddy hosting account (cPanel or Web Hosting - minimum shared hosting)
- [ ] Domain access (if domain is not at GoDaddy, you'll need registrar login)
- [ ] FTP/SFTP client (FileZilla - free download)
- [ ] Access to your Shopify admin
- [ ] Backup of Shopify data (exports)
- [ ] Alternative payment processing method

---

## Backup Shopify Data

**DO THIS BEFORE ANYTHING ELSE** - You cannot recover this data after canceling Shopify.

### Step 1: Export Customer Data

1. Log in to **Shopify Admin** (https://admin.shopify.com/)
2. Go to **Customers**
3. Click **Export** (top right)
4. Choose: **All customers**
5. Export as: **CSV for Excel, Numbers, or other spreadsheet programs**
6. Click **Export customers**
7. Save file to your computer: `shopify-customers-backup-[date].csv`

### Step 2: Export Orders

1. In Shopify Admin, go to **Orders**
2. Click **Export** (top right)
3. Choose: **All orders**
4. Export as: **CSV for Excel, Numbers, or other spreadsheet programs**
5. Click **Export orders**
6. Save file: `shopify-orders-backup-[date].csv`

### Step 3: Export Products

1. Go to **Products**
2. Click **Export** (top right)
3. Choose: **All products**
4. Click **Export products**
5. Save file: `shopify-products-backup-[date].csv`

### Step 4: Save Customer Reviews (If Using Judge.me)

1. In Shopify Admin, go to **Apps** → **Judge.me**
2. Go to **Reviews** section
3. Click **Export** or **Download reviews**
4. Save as CSV
5. **Note**: You won't be able to display these on the new static site without manual work

### Step 5: Download Product Images

1. All product images from your Shopify store
2. Save to a folder: `shopify-images-backup`
3. **Note**: Your new static site uses images from Shopify CDN URLs - these may stop working after canceling Shopify

### Step 6: Screenshot Important Analytics

1. Go to **Analytics** → **Reports** in Shopify
2. Take screenshots of:
   - Total sales
   - Best-selling products
   - Customer locations
   - Traffic sources
3. Save these for your records

### Step 7: Save Email Marketing Lists

If you use Shopify Email or integrated email apps:
1. Export all subscriber lists
2. Save email addresses for future marketing (MailChimp, Klaviyo, etc.)

---

## GoDaddy Setup

### Step 1: Purchase/Access GoDaddy Hosting

**If you don't have hosting yet:**
1. Go to https://www.godaddy.com
2. Click **Web Hosting**
3. Choose **cPanel Hosting** (recommended) or **WordPress Hosting** (can still host static HTML)
4. Select plan (Economy or Deluxe is sufficient for static site)
5. Purchase hosting

**If domain is not at GoDaddy:**
- You can keep your domain at current registrar
- OR transfer domain to GoDaddy (optional, takes 5-7 days)

### Step 2: Access GoDaddy cPanel

1. Log in to GoDaddy account
2. Go to **My Products**
3. Find **Web Hosting**
4. Click **Manage** → **cPanel Admin**

### Step 3: Locate Your Server IP Address

**You'll need this for DNS setup:**
1. In cPanel, look for **Server Information** or **Stats** section
2. Find **Shared IP Address** - it looks like: `123.45.67.89`
3. **Write this down** - you'll need it for DNS

---

## Upload Website Files

### Option 1: cPanel File Manager (Easiest)

1. **In cPanel**, click **File Manager** (under Files section)
2. Navigate to **public_html** folder
3. **Delete Shopify files** (if any exist - usually empty on new hosting)
4. **Show hidden files**:
   - Click **Settings** (top right)
   - Check **Show Hidden Files (dotfiles)**
   - Click **Save**

5. **Upload all website files**:
   - Click **Upload** button
   - Drag and drop these files:
     ```
     .htaccess
     index.html
     product.html
     contact.html
     checkout.html
     thank-you.html
     faqs.html
     search.html
     privacy-policy.html
     terms-of-service.html
     return-policy.html
     data-sharing-opt-out.html
     robots.txt
     sitemap.xml
     ```
   - Wait for upload to complete

6. **Create folders and upload content**:
   - Click **+ Folder** and create: `emails`
   - Click **+ Folder** and create: `Photos`
   - Click **+ Folder** and create: `Video`
   - Enter each folder and upload respective files

### Option 2: FTP Upload (FileZilla)

**Get FTP credentials from cPanel:**
1. In cPanel, go to **FTP Accounts**
2. Find your main account or create new one
3. Note:
   - FTP Server: `ftp.drbibiorganics.com` (or your domain)
   - Username: Your cPanel username
   - Password: Your cPanel password
   - Port: 21

**Upload via FileZilla:**
1. Download FileZilla from https://filezilla-project.org/
2. Open FileZilla
3. Enter connection details (Host, Username, Password, Port 21)
4. Click **Quickconnect**
5. Left panel: Navigate to your local `dr-bibi-organics` folder
6. Right panel: Navigate to `public_html`
7. Select all files and folders, drag to right panel
8. Wait for upload (5-10 minutes)

---

## Disconnect from Shopify & Point DNS to GoDaddy

**⚠️ CRITICAL STEP** - Your website will go offline briefly during this process (15 minutes to 48 hours depending on DNS propagation).

### Step 1: Determine Where Your Domain is Registered

**Check domain registration:**
1. Go to https://whois.domaintools.com/
2. Search for: `drbibiorganics.com`
3. Note the **Registrar** (where domain is registered)
4. Check **Nameservers** (currently pointing to Shopify)

**Common scenarios:**
- Domain registered at GoDaddy → Easy, manage in GoDaddy
- Domain registered elsewhere → Need to update at that registrar
- Domain registered through Shopify → Need to transfer or update DNS

### Step 2A: If Domain is at GoDaddy

1. Log in to GoDaddy
2. Go to **My Products** → **Domains**
3. Find `drbibiorganics.com`
4. Click **DNS** or **Manage DNS**

5. **Update A Record:**
   - Find existing A record (Type: `A`, Name: `@`)
   - Click **Edit** (pencil icon)
   - Change **Points to** to your GoDaddy server IP (from earlier)
   - TTL: `1 Hour` or `600`
   - Click **Save**

6. **Update WWW Record:**
   - Find CNAME record (Name: `www`)
   - Click **Edit**
   - Points to: `@` or `drbibiorganics.com`
   - Click **Save**

7. **Remove Shopify DNS Records:**
   - Delete any records pointing to `shops.myshopify.com`
   - Delete any AAAA records for Shopify

### Step 2B: If Domain is NOT at GoDaddy

**You have 2 options:**

**Option 1: Update DNS at Current Registrar (Faster)**
1. Log in to your domain registrar (Namecheap, Google Domains, etc.)
2. Find DNS management for `drbibiorganics.com`
3. Update A record:
   - Type: `A`
   - Name/Host: `@` or leave blank
   - Value/Points to: Your GoDaddy server IP
   - TTL: 3600 (1 hour)
4. Update CNAME for www:
   - Type: `CNAME`
   - Name: `www`
   - Value: `@` or your domain
5. Save changes

**Option 2: Change Nameservers to GoDaddy (Slower but cleaner)**
1. In GoDaddy cPanel, find nameservers (usually `ns1.domaincontrol.com` and `ns2.domaincontrol.com`)
2. At your domain registrar, update nameservers
3. Wait 24-48 hours for propagation

### Step 3: Remove Domain from Shopify

**IMPORTANT: Only do this AFTER DNS has been updated**

1. Log in to **Shopify Admin**
2. Go to **Settings** → **Domains**
3. Find `drbibiorganics.com`
4. Click on the domain
5. Click **Remove domain** or **Disconnect domain**
6. Confirm removal

**Warning**: This will immediately break the Shopify site if DNS is still pointing to Shopify.

### Step 4: Wait for DNS Propagation

**How long it takes:**
- Minimum: 15 minutes to 1 hour
- Average: 2-4 hours
- Maximum: 24-48 hours

**Check propagation status:**
- Visit: https://dnschecker.org/
- Enter: `drbibiorganics.com`
- Check if IP matches your GoDaddy server IP

**During this time:**
- Website may be intermittently unavailable
- Some users may see old Shopify site, others see new site
- This is normal

---

## SSL Certificate Setup

**Wait for DNS to fully propagate before installing SSL** (otherwise it will fail).

### Step 1: Install Free SSL Certificate (Let's Encrypt)

1. In **GoDaddy cPanel**, go to **Security** section
2. Click **SSL/TLS Status**
3. Find domains:
   - `drbibiorganics.com`
   - `www.drbibiorganics.com`
4. Select both (checkboxes)
5. Click **Run AutoSSL** or **Install**
6. Wait 5-10 minutes for installation

### Step 2: Force HTTPS (Redirect HTTP to HTTPS)

1. In cPanel **File Manager**, navigate to `public_html`
2. Find `.htaccess` file
3. Right-click → **Edit** or **Code Edit**
4. Find these commented lines (around line 49):

```apache
# Uncomment these lines after SSL certificate is installed
# RewriteCond %{HTTPS} off
# RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

5. **Remove the `#` symbols** to uncomment:

```apache
# Force HTTPS after SSL certificate is installed
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

6. Click **Save Changes**

### Step 3: Test SSL

1. Visit: `https://drbibiorganics.com`
2. Check for green padlock in browser
3. Visit: `http://drbibiorganics.com` (should redirect to HTTPS)

---

## Post-Migration Testing

### Immediate Tests (Right After DNS Propagation)

**Homepage & Navigation:**
- [ ] Visit `https://drbibiorganics.com` - homepage loads
- [ ] All navigation links work
- [ ] Logo and images display correctly
- [ ] Mobile responsive (test on phone)

**All Pages Load:**
- [ ] https://drbibiorganics.com/product
- [ ] https://drbibiorganics.com/contact
- [ ] https://drbibiorganics.com/checkout
- [ ] https://drbibiorganics.com/faqs
- [ ] https://drbibiorganics.com/thank-you
- [ ] All legal pages (privacy, terms, return policy)

**Forms Testing:**
- [ ] Contact form submits (check Support@drbibiorganics.com inbox)
- [ ] Newsletter signup works
- [ ] Exit popup appears and form works
- [ ] Checkout form submits (test with fake data first)

**Shopping Cart:**
- [ ] Add item to cart
- [ ] Cart persists on page refresh
- [ ] Quantities update correctly
- [ ] Proceed to checkout works

**Clean URLs:**
- [ ] `/product` works (without .html)
- [ ] `/contact` works
- [ ] URLs are clean and readable

**SSL & Security:**
- [ ] Green padlock appears in browser
- [ ] No "mixed content" warnings
- [ ] HTTP redirects to HTTPS
- [ ] Both `drbibiorganics.com` and `www.drbibiorganics.com` work

**SEO:**
- [ ] `https://drbibiorganics.com/robots.txt` displays correctly
- [ ] `https://drbibiorganics.com/sitemap.xml` displays correctly
- [ ] Page titles and meta descriptions show in browser tabs

### Email Testing

**Send test orders to yourself:**
1. Fill out checkout form with your own email
2. Submit order
3. Check if email arrives at Support@drbibiorganics.com
4. Verify all order details are included

**Test all forms:**
- Contact form
- Newsletter signup
- Exit popup

### Performance Testing

**Page Speed:**
- Visit https://pagespeed.web.dev/
- Test: `https://drbibiorganics.com`
- Target: 90+ for mobile and desktop

**Mobile Experience:**
- Test on actual mobile device
- All buttons are tappable
- Forms are easy to fill out
- Images load properly

---

## Cancel Shopify Subscription

**⚠️ ONLY DO THIS AFTER:**
- New site is fully live and working
- DNS has propagated completely
- You've tested everything thoroughly
- You've backed up all Shopify data
- You're comfortable with manual order processing

### Step 1: Pause or Cancel Shopify

1. Log in to **Shopify Admin**
2. Go to **Settings** → **Plan**
3. Click **Deactivate store** or **Pause and build**

**Options:**
- **Pause Plan** ($9/month) - Keeps your store data, can reactivate later
- **Cancel Plan** - Deletes everything after billing period ends

**Recommendation:** Pause for 1-2 months first, then cancel if all is working well.

### Step 2: Review Final Bill

- Shopify bills in advance
- You won't get refund for unused time
- Apps may bill separately

### Step 3: Download Final Backups

Before canceling completely:
1. Re-export all data (customers, orders, products)
2. Save copies locally
3. Keep for at least 7 years (tax/legal requirements)

---

## Important Post-Migration Tasks

### Update Google Search Console

1. Go to https://search.google.com/search-console
2. **Add new property**:
   - Click **Add Property**
   - Enter: `https://drbibiorganics.com`
   - Verify ownership (DNS verification recommended)

3. **Submit new sitemap**:
   - Click **Sitemaps** in left menu
   - Add sitemap URL: `https://drbibiorganics.com/sitemap.xml`
   - Click **Submit**

4. **Request re-indexing** of important pages

### Update Google Analytics (If Using)

1. Verify tracking code is in all HTML pages
2. Check if data is coming through
3. Set up goals for form submissions

### Set Up Email Collection

Your new site collects emails via:
- Newsletter signup → Support@drbibiorganics.com
- Exit popup → Support@drbibiorganics.com
- Contact form → Support@drbibiorganics.com

**Consider setting up:**
- Dedicated email marketing tool (MailChimp, ConvertKit, Klaviyo)
- Import your Shopify customer emails
- Set up automated email sequences

### Payment Processing Alternative

Since you won't have Shopify checkout:

**Options:**
1. **PayPal Invoices** - Send invoices manually after receiving checkout form
2. **Venmo/Zelle** - For phone orders
3. **Square Invoices** - Professional invoicing
4. **Stripe Payment Links** - Create payment links, send via email
5. **Consider adding Gumroad/ThriveCart** - Simple checkout solutions

### Monitor Order Forms Daily

- Check Support@drbibiorganics.com multiple times daily
- Respond to orders within 24 hours
- Create a system for tracking orders manually (spreadsheet or CRM)

---

## Troubleshooting

### "Site not loading after DNS change"

**Cause:** DNS hasn't propagated yet

**Solution:**
- Wait longer (up to 48 hours)
- Clear browser cache
- Try different device/network
- Check https://dnschecker.org/

### "Mixed content warning (HTTPS with lock icon crossed out)"

**Cause:** Some resources loading over HTTP instead of HTTPS

**Solution:**
1. Check if using any `http://` links in HTML
2. External resources must use `https://`
3. Images from Shopify CDN should use HTTPS URLs

### "Forms not sending emails"

**Cause:** FormSubmit.co configuration or email blocked

**Solution:**
1. Verify email address in form: `Support@drbibiorganics.com`
2. Check spam folder
3. Verify FormSubmit.co is not rate-limiting
4. Test with different email address

### "Images from Shopify not loading"

**Cause:** Shopify CDN may block after account cancellation

**Solution:**
1. Download all images from Shopify before canceling
2. Upload to GoDaddy hosting
3. Update image URLs in HTML files
4. Use `/Photos/` folder on your GoDaddy server

### "Clean URLs not working (still showing .html)"

**Cause:** .htaccess not working or mod_rewrite disabled

**Solution:**
1. Verify `.htaccess` is in `public_html`
2. Enable "Show Hidden Files" in File Manager
3. Contact GoDaddy support to enable `mod_rewrite` module
4. Clear browser cache

---

## Rollback Plan

If something goes wrong and you need to go back to Shopify:

### Quick Rollback (Within 48 hours)

1. **Don't cancel Shopify yet** - Keep it active during testing
2. In DNS, point A record back to Shopify:
   - GoDaddy DNS or your registrar
   - Change A record back to Shopify IP
3. In Shopify Admin → Settings → Domains
   - Re-connect domain
4. Wait for DNS propagation

### Why You Should Keep Shopify Active During Testing

- Keep Shopify plan active for 30 days after migration
- Test new site thoroughly before canceling Shopify
- Can quickly roll back if issues arise
- Only pause/cancel when 100% confident

---

## SEO Impact & Mitigation

### Potential SEO Issues

**⚠️ Warning:** Changing hosting platforms CAN impact SEO rankings temporarily.

**What may happen:**
- Google needs to re-crawl and re-index your site
- Rankings may fluctuate for 2-4 weeks
- Shopify-specific URLs may break (product handles, collections)

### Mitigation Strategies

**Before Migration:**
1. **Map all Shopify URLs** to new static URLs
2. Set up 301 redirects for important pages (in .htaccess)
3. Ensure new URLs match old structure where possible

**Example Shopify URLs:**
- `drbibiorganics.com/products/butter-oasis-balm` → `drbibiorganics.com/product.html`
- `drbibiorganics.com/collections/all` → `drbibiorganics.com/product.html`

**After Migration:**
1. Submit new sitemap to Google Search Console
2. Request re-indexing of all pages
3. Monitor rankings with Google Search Console
4. Fix any crawl errors immediately

---

## Estimated Timeline

### Full Migration Process

**Day 1-2: Preparation**
- [ ] Backup all Shopify data (2 hours)
- [ ] Set up GoDaddy hosting (30 minutes)
- [ ] Upload website files (1 hour)
- [ ] Test on staging/temp domain (2 hours)

**Day 3: DNS Switch**
- [ ] Update DNS records (15 minutes)
- [ ] Wait for propagation (2-48 hours)
- [ ] Install SSL certificate (15 minutes)
- [ ] Test live site (1 hour)

**Day 4-30: Monitoring**
- [ ] Monitor daily for issues
- [ ] Process manual orders
- [ ] Track analytics
- [ ] Watch for SEO impacts

**Day 30+: Shopify Cancellation**
- [ ] If all is well, pause or cancel Shopify
- [ ] Final data backup
- [ ] Close apps and integrations

---

## Migration Day Checklist

**Morning (9 AM):**
- [ ] Final Shopify data backup
- [ ] Files uploaded to GoDaddy
- [ ] Server IP address confirmed
- [ ] Notified team/stakeholders

**Afternoon (2 PM - Low traffic time recommended):**
- [ ] Update DNS records
- [ ] Remove domain from Shopify
- [ ] Monitor DNS propagation

**Evening:**
- [ ] Test new site when DNS resolves
- [ ] Install SSL certificate
- [ ] Enable HTTPS redirect
- [ ] Final testing checklist
- [ ] Monitor email for test orders

**Next 48 Hours:**
- [ ] Check site every 2-4 hours
- [ ] Respond to any order emails immediately
- [ ] Monitor Google Analytics
- [ ] Watch for customer complaints

---

## Support Resources

### GoDaddy Support
- **Phone:** 480-505-8877 (24/7)
- **Live Chat:** Available in dashboard
- **Help Center:** https://www.godaddy.com/help

### Shopify Support (Before Canceling)
- **Phone:** 1-855-772-7482
- **Email:** support@shopify.com
- **Help Center:** https://help.shopify.com/

### DNS Tools
- **Check propagation:** https://dnschecker.org/
- **WHOIS lookup:** https://whois.domaintools.com/
- **SSL checker:** https://www.ssllabs.com/ssltest/

### Testing Tools
- **PageSpeed:** https://pagespeed.web.dev/
- **Mobile-Friendly:** https://search.google.com/test/mobile-friendly
- **SSL Test:** https://www.ssllabs.com/ssltest/

---

## Final Recommendations

### Before You Migrate

1. **Test the new site on a staging domain first**
2. **Have an alternative payment processing method ready**
3. **Create a system for manual order management**
4. **Consider keeping Shopify for 30 days** (just in case)
5. **Inform customers** of any changes to ordering process
6. **Set up auto-responders** so customers know their order was received

### Consider If This is Right For You

**The new static site is good if:**
- You have low order volume (can handle manually)
- You want to save Shopify fees ($39-$299/month)
- Orders are simple (one main product)
- You're comfortable with manual processes

**Stay with Shopify if:**
- You have high order volume (100+ orders/month)
- You need automated fulfillment
- You require customer accounts/order tracking
- You want professional payment processing
- You need inventory management

---

**Good luck with your migration!**
**Questions?** Contact GoDaddy support or review this guide.

*Last Updated: January 6, 2026*
