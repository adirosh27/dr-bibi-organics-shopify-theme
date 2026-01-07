# Shopify to GoDaddy Migration - Quick Start

## ⚠️ CRITICAL: Read This First!

### What You're About To Do

You are replacing your **fully functional Shopify e-commerce store** with a **static HTML website** that does NOT have:
- ❌ Automated payment processing
- ❌ Shopping cart checkout
- ❌ Customer accounts
- ❌ Order tracking
- ❌ Inventory management

### What You WILL Have

- ✅ Beautiful product showcase website
- ✅ Contact forms (orders submitted via email)
- ✅ Manual order processing (you handle payments separately)
- ✅ Much lower monthly costs (no Shopify fees)

---

## Is This Right For You?

**✅ YES, migrate if:**
- You have low order volume (can handle orders manually)
- You want to save $39-299/month in Shopify fees
- You're comfortable processing payments via PayPal invoice, Venmo, etc.
- Orders are simple (mainly one product)

**❌ NO, keep Shopify if:**
- You need automated payment processing
- You have high order volume (100+ orders/month)
- You need customer accounts and order history
- You require professional e-commerce features

---

## 3-Step Quick Start

### Step 1: Backup Everything from Shopify (30 minutes)

**In Shopify Admin (admin.shopify.com):**

1. **Export Customers:**
   - Customers → Export → CSV → Save file

2. **Export Orders:**
   - Orders → Export → All orders → CSV → Save file

3. **Export Products:**
   - Products → Export → CSV → Save file

4. **Export Reviews (if using Judge.me):**
   - Apps → Judge.me → Export reviews

5. **Download product images** from Shopify

**Save everything to a folder named: `shopify-backup-[date]`**

---

### Step 2: Upload to GoDaddy (1-2 hours)

**A. Access GoDaddy:**
1. Log in to GoDaddy.com
2. My Products → Web Hosting → Manage → cPanel Admin

**B. Upload Files:**
1. Click **File Manager** → Navigate to `public_html`
2. Delete any existing files
3. Upload ALL files from `dr-bibi-organics` folder:
   - All .html files
   - .htaccess
   - robots.txt
   - sitemap.xml
   - /emails/ folder
   - /Photos/ folder
   - /Video/ folder

**C. Verify Structure:**
```
public_html/
├── .htaccess
├── index.html
├── product.html
├── contact.html
├── checkout.html
└── [all other files]
```

---

### Step 3: Switch DNS & Go Live (15 min + wait time)

**A. Get Your GoDaddy Server IP:**
- In cPanel, look for "Server Information"
- Find "Shared IP Address" (looks like: 123.45.67.89)
- **Write this down**

**B. Update DNS:**

**If domain is at GoDaddy:**
1. My Products → Domains → drbibiorganics.com → DNS
2. Edit A Record:
   - Name: `@`
   - Points to: [Your GoDaddy IP]
   - TTL: 1 Hour
3. Save

**If domain is elsewhere:**
1. Log in to your domain registrar
2. Find DNS settings for drbibiorganics.com
3. Update A record to point to GoDaddy IP

**C. Remove Domain from Shopify:**
1. Shopify Admin → Settings → Domains
2. Click drbibiorganics.com → Remove domain

**D. Wait for DNS Propagation:**
- Check: https://dnschecker.org/
- Wait: 1-48 hours (usually 2-4 hours)

**E. Install SSL Certificate:**
1. In cPanel → Security → SSL/TLS Status
2. Select drbibiorganics.com and www.drbibiorganics.com
3. Click "Run AutoSSL"
4. Wait 10 minutes

**F. Enable HTTPS Redirect:**
1. File Manager → public_html → .htaccess → Edit
2. Find lines around line 117:
   ```
   # RewriteCond %{HTTPS} off
   # RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   ```
3. Remove the `#` symbols:
   ```
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
   ```
4. Save

---

## Testing Checklist

Once DNS has propagated and site is live:

- [ ] Homepage loads: https://drbibiorganics.com
- [ ] All pages work: /product, /contact, /checkout, /faqs
- [ ] Forms submit and you receive emails at Support@drbibiorganics.com
- [ ] Images display correctly
- [ ] Shopping cart adds items
- [ ] Checkout form submits order details via email
- [ ] Mobile responsive (test on phone)
- [ ] SSL certificate shows green padlock
- [ ] HTTP redirects to HTTPS

---

## After Migration: How Orders Work Now

### Old Way (Shopify):
1. Customer adds to cart
2. Customer checks out with credit card
3. Shopify processes payment automatically
4. You receive order notification
5. You ship product

### New Way (Static Site):
1. Customer adds to cart
2. Customer fills out checkout form
3. **Form submits to your email: Support@drbibiorganics.com**
4. **You send PayPal invoice / payment link manually**
5. Customer pays via PayPal/Venmo/Zelle
6. You ship product

**You'll need:**
- PayPal Business account (for invoicing)
- OR Stripe payment links
- OR Venmo/Zelle for payment collection
- System to track orders manually (spreadsheet)

---

## Timeline

**Estimated total time:**
- Backup Shopify: 30-60 minutes
- Upload to GoDaddy: 1-2 hours
- DNS switch: 15 minutes (+ 2-48 hours wait)
- SSL setup: 15 minutes
- Testing: 1 hour
- **Total active work: 3-4 hours**
- **Total calendar time: 1-3 days**

**Recommended schedule:**
- **Friday afternoon:** Backup Shopify + Upload to GoDaddy
- **Saturday morning:** Switch DNS (low traffic time)
- **Saturday-Sunday:** Monitor DNS propagation
- **Sunday evening:** SSL setup + final testing
- **Monday:** Live on new site, monitor closely

---

## Emergency Rollback

**If something goes wrong:**

1. **Don't panic** - Keep Shopify active for 30 days
2. **In DNS**, change A record back to Shopify IP
3. **In Shopify** Settings → Domains → Reconnect domain
4. **Wait** for DNS to propagate back (2-4 hours)

**That's why:** Don't cancel Shopify until you're 100% sure the new site works!

---

## Common Questions

**Q: Will I lose my Google rankings?**
A: Rankings may fluctuate for 2-4 weeks while Google re-indexes. The .htaccess file includes 301 redirects to preserve most SEO.

**Q: What happens to my customer data?**
A: It's in the CSV files you exported. Import to an email marketing tool (MailChimp, Klaviyo, etc.) to keep emailing customers.

**Q: What happens to my reviews?**
A: Judge.me reviews are tied to Shopify. You exported them as CSV but can't easily display on static site without manual coding.

**Q: Can I still accept credit cards?**
A: Not directly on the site. You can send payment links via Stripe, Square, or PayPal invoices after receiving checkout form submissions.

**Q: How much will I save?**
A: Shopify Basic = $39/month, GoDaddy hosting = $5-10/month. Savings: ~$30-35/month or $360-420/year.

**Q: What if I get overwhelmed with manual orders?**
A: You can add Gumroad, ThriveCart, or other simple checkout tools later, or migrate back to Shopify.

---

## Support Contacts

**GoDaddy Support:**
- Phone: 480-505-8877 (24/7)
- Live Chat in dashboard

**Shopify Support** (before canceling):
- Phone: 1-855-772-7482

**Your Website Forms:**
- All forms send to: Support@drbibiorganics.com
- Check this email multiple times daily for orders!

---

## Files You Need

Everything is in this folder:
- `SHOPIFY-TO-GODADDY-MIGRATION.md` - Full detailed guide
- `.htaccess` - Server configuration (includes Shopify redirects)
- All .html files - Your new website
- `robots.txt` & `sitemap.xml` - SEO files

---

## Ready to Start?

**Before you begin:**
- [ ] Read full migration guide: `SHOPIFY-TO-GODADDY-MIGRATION.md`
- [ ] Backup ALL Shopify data
- [ ] Have GoDaddy hosting ready
- [ ] Set up payment processing alternative (PayPal, etc.)
- [ ] Block out 3-4 hours for the migration
- [ ] Choose low-traffic time (weekend recommended)

**Then:**
1. Follow Step 1 (Backup)
2. Follow Step 2 (Upload)
3. Follow Step 3 (DNS Switch)
4. Test everything thoroughly
5. Monitor for 30 days before canceling Shopify

---

**Good luck! You've got this! 🚀**

*For detailed instructions, see: SHOPIFY-TO-GODADDY-MIGRATION.md*
