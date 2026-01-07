# GoDaddy Migration Guide
## Moving Dr. Bibi Organics from Vercel to GoDaddy

**Date**: January 6, 2026
**Status**: Ready for Migration

---

## Table of Contents
1. [Pre-Migration Checklist](#pre-migration-checklist)
2. [GoDaddy Setup](#godaddy-setup)
3. [File Upload Process](#file-upload-process)
4. [DNS Configuration](#dns-configuration)
5. [SSL Certificate Setup](#ssl-certificate-setup)
6. [Post-Migration Testing](#post-migration-testing)
7. [Troubleshooting](#troubleshooting)

---

## Pre-Migration Checklist

### What You'll Need
- [ ] GoDaddy hosting account (cPanel or Web Hosting)
- [ ] FTP/SFTP client (FileZilla recommended - free)
- [ ] Domain name: drbibiorganics.com (should already be registered)
- [ ] Backup of all current files (already in this folder)

### Files to Upload (Total: 18 HTML files + assets)

**Main Pages:**
- index.html
- product.html
- contact.html
- checkout.html
- thank-you.html

**Support Pages:**
- faqs.html
- search.html

**Legal Pages:**
- privacy-policy.html
- terms-of-service.html
- return-policy.html
- data-sharing-opt-out.html

**Configuration Files:**
- .htaccess (NEW - created for GoDaddy)
- robots.txt
- sitemap.xml (UPDATED with all pages)

**Folders:**
- /emails/ (7 email template files)
- /Photos/ (product images)
- /Video/ (product video)

**DO NOT UPLOAD:**
- .git/ folder
- .vercel/ folder
- vercel.json
- package.json
- .gitignore
- *.md files (documentation)
- .claude/ folder

---

## GoDaddy Setup

### Step 1: Access Your GoDaddy Hosting

1. Log in to your GoDaddy account at https://www.godaddy.com
2. Go to **My Products**
3. Find your Web Hosting plan
4. Click **Manage** next to your hosting account

### Step 2: Access cPanel

1. From the hosting management page, click **cPanel Admin**
2. You'll be taken to the cPanel dashboard

### Step 3: Locate File Manager

1. In cPanel, scroll down to the **Files** section
2. Click on **File Manager**
3. Navigate to **public_html** folder (this is your web root)

---

## File Upload Process

You have **3 options** for uploading files to GoDaddy:

### Option 1: cPanel File Manager (Easiest for beginners)

1. **In cPanel File Manager**, navigate to `public_html`
2. **Delete default files** (if any):
   - Delete any default `index.html` or `coming soon` pages
3. **Upload files**:
   - Click the **Upload** button at the top
   - Drag and drop all files from your local folder
   - OR use the file selector to upload multiple files
4. **Create folders**:
   - Click **+ Folder** to create:
     - `emails`
     - `Photos`
     - `Video`
   - Enter each folder and upload the respective files

**IMPORTANT**: Make sure `.htaccess` file is uploaded (you may need to enable "Show Hidden Files" in settings)

### Option 2: FTP/SFTP (Recommended for large files)

#### Using FileZilla (Free FTP Client)

1. **Download FileZilla** from https://filezilla-project.org/
2. **Get your FTP credentials** from GoDaddy:
   - In cPanel, go to **Files** → **FTP Accounts**
   - Your FTP hostname is usually: `ftp.yourdomain.com`
   - Username: Your cPanel username
   - Password: Your cPanel password
   - Port: 21 (FTP) or 22 (SFTP - more secure)

3. **Connect with FileZilla**:
   - Open FileZilla
   - Enter:
     - Host: `ftp.drbibiorganics.com` (or IP address from cPanel)
     - Username: `[your cPanel username]`
     - Password: `[your cPanel password]`
     - Port: `21`
   - Click **Quickconnect**

4. **Upload files**:
   - On the left side: Navigate to your local `dr-bibi-organics` folder
   - On the right side: Navigate to `public_html`
   - Select all files and folders on the left
   - Drag them to the right side to upload
   - Wait for upload to complete (may take 5-10 minutes)

### Option 3: ZIP Upload (Fastest for multiple files)

1. **Create a ZIP file** on your computer:
   - Compress all website files into `drbibi-organics.zip`
   - **Exclude**: .git, .vercel, node_modules, .md files
2. **Upload ZIP to cPanel**:
   - In File Manager, go to `public_html`
   - Click **Upload**
   - Upload the ZIP file
3. **Extract ZIP**:
   - Right-click on the uploaded ZIP file
   - Select **Extract**
   - Choose `public_html` as destination
   - Delete the ZIP file after extraction

---

## File Structure on GoDaddy

Your `public_html` folder should look like this:

```
public_html/
├── .htaccess
├── index.html
├── product.html
├── contact.html
├── checkout.html
├── thank-you.html
├── faqs.html
├── search.html
├── privacy-policy.html
├── terms-of-service.html
├── return-policy.html
├── data-sharing-opt-out.html
├── robots.txt
├── sitemap.xml
├── emails/
│   ├── abandoned-cart-1.html
│   ├── abandoned-cart-2.html
│   ├── abandoned-cart-3.html
│   ├── post-purchase-1-thank-you.html
│   ├── post-purchase-2-how-to-use.html
│   ├── post-purchase-3-review-request.html
│   └── post-purchase-4-reorder-reminder.html
├── Photos/
│   └── [all product images]
└── Video/
    └── [product videos]
```

---

## DNS Configuration

### If Domain is Already at GoDaddy

1. **In GoDaddy Dashboard**, go to **My Products**
2. Find **drbibiorganics.com** under Domains
3. Click **DNS** or **Manage DNS**
4. **Verify A Record** points to your hosting:
   - Type: `A`
   - Name: `@`
   - Value: Your server IP (found in cPanel under **Server Information**)
   - TTL: 1 Hour (default)
5. **Verify WWW Record**:
   - Type: `CNAME`
   - Name: `www`
   - Value: `@` or `drbibiorganics.com`
6. **Save changes** (DNS propagation takes 1-48 hours, usually 1-4 hours)

### If Domain is at Another Registrar

1. **Get nameservers** from GoDaddy:
   - In cPanel or hosting dashboard, find your nameservers
   - Usually: `ns1.domaincontrol.com` and `ns2.domaincontrol.com`
2. **Update nameservers** at your domain registrar:
   - Log in to your domain registrar
   - Find DNS or Nameserver settings
   - Replace with GoDaddy nameservers
   - Save and wait for propagation (24-48 hours)

---

## SSL Certificate Setup

### Enable Free SSL (Let's Encrypt)

1. **In cPanel**, go to **Security** section
2. Click **SSL/TLS Status**
3. Find `drbibiorganics.com` and `www.drbibiorganics.com`
4. Click **Run AutoSSL** or **Install SSL Certificate**
5. Wait 5-10 minutes for installation

### Force HTTPS in .htaccess

Once SSL is active, uncomment these lines in `.htaccess`:

```apache
# Uncomment these lines after SSL certificate is installed
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

To uncomment:
1. Go to File Manager → public_html → .htaccess
2. Click **Edit**
3. Remove the `#` symbols from those two lines
4. Save

---

## Post-Migration Testing

### Immediate Testing (Right After Upload)

1. **Test homepage**:
   - Visit: `http://drbibiorganics.com` or `http://your-server-ip`
   - Should load the homepage

2. **Test all pages** (check each one):
   - http://drbibiorganics.com/product.html
   - http://drbibiorganics.com/product (clean URL test)
   - http://drbibiorganics.com/contact
   - http://drbibiorganics.com/checkout
   - http://drbibiorganics.com/faqs

3. **Test images and videos**:
   - Check if product images load
   - Check if hero video plays on homepage

4. **Test forms**:
   - Contact form (sends to Support@drbibiorganics.com)
   - Newsletter signup
   - Exit popup form

5. **Test shopping cart**:
   - Add item to cart
   - Check cart persistence (localStorage)
   - Test checkout flow

### After SSL Setup

1. **Test HTTPS**:
   - Visit: `https://drbibiorganics.com`
   - Check for green padlock in browser
   - No mixed content warnings

2. **Test redirects**:
   - `http://drbibiorganics.com` → should redirect to `https://`
   - `www.drbibiorganics.com` → should redirect to non-www (or vice versa)

### SEO Testing

1. **Test robots.txt**:
   - Visit: `https://drbibiorganics.com/robots.txt`
   - Should display the robots file

2. **Test sitemap**:
   - Visit: `https://drbibiorganics.com/sitemap.xml`
   - Should display XML sitemap

3. **Submit to Google Search Console**:
   - Go to: https://search.google.com/search-console
   - Add property: `https://drbibiorganics.com`
   - Verify ownership (multiple methods available)
   - Submit sitemap: `https://drbibiorganics.com/sitemap.xml`

### Performance Testing

1. **Page Speed Test**:
   - Visit: https://pagespeed.web.dev/
   - Test: `https://drbibiorganics.com`
   - Target: 90+ score

2. **Mobile Responsiveness**:
   - Test on mobile devices
   - Or use browser dev tools (F12 → Device toolbar)

---

## Troubleshooting

### Issue: "403 Forbidden" Error

**Cause**: Usually permissions issue

**Solution**:
1. In File Manager, right-click on `index.html`
2. Select **Permissions**
3. Set to `644` (read/write for owner, read for others)
4. Do the same for all HTML files

### Issue: ".htaccess not working" (URLs still show .html)

**Cause**: `.htaccess` file not uploaded or mod_rewrite disabled

**Solution**:
1. Verify `.htaccess` exists in `public_html`
2. Enable "Show Hidden Files" in File Manager settings
3. Contact GoDaddy support to enable `mod_rewrite` (usually enabled by default)

### Issue: "Images not loading"

**Cause**: Case-sensitive file paths or wrong folder structure

**Solution**:
1. Linux servers are case-sensitive
2. Check that folder names match exactly: `Photos` not `photos`
3. Verify images are in correct folders
4. Check image paths in HTML files

### Issue: "SSL Certificate not installing"

**Cause**: Domain not pointing to server yet

**Solution**:
1. Wait for DNS propagation (check with https://dnschecker.org/)
2. Verify A records point to correct server IP
3. Contact GoDaddy support if issue persists

### Issue: "Forms not sending emails"

**Cause**: FormSubmit.co might have rate limits or issues

**Solution**:
1. Verify email in form action: `Support@drbibiorganics.com`
2. Check spam folder for confirmation emails
3. Test with a different email address
4. FormSubmit is free but has limitations - consider upgrading or using GoDaddy email forms

### Issue: "Clean URLs not working"

**Cause**: `.htaccess` rules not applied

**Solution**:
1. Verify `.htaccess` is in `public_html` (not in a subfolder)
2. Check that file has no typos
3. Clear browser cache
4. Test in incognito/private browsing mode

---

## Important Notes

### URL Changes After Migration

**Before (Vercel)**:
- https://dr-bibi-organics.vercel.app/

**After (GoDaddy)**:
- https://drbibiorganics.com/

**What to Update:**

1. **In all HTML files**: Update any hardcoded Vercel URLs
   - Search for: `dr-bibi-organics.vercel.app`
   - Replace with: `drbibiorganics.com`
   - This should already be using `drbibiorganics.com` in most places

2. **FormSubmit redirect URLs**: Already set to `https://dr-bibi-organics.vercel.app/thank-you`
   - Update to: `https://drbibiorganics.com/thank-you`
   - Files to check:
     - contact.html (line 131)
     - index.html (newsletter form, line 681)
     - index.html (exit popup, line 798)

3. **Exit popup discount emails**: Check auto-response URLs in JavaScript

---

## Performance Optimization (Optional)

### After Migration is Complete

1. **Enable Cloudflare** (Free CDN):
   - Sign up at https://cloudflare.com
   - Add your domain
   - Update nameservers to Cloudflare's
   - Benefit: Faster loading, DDoS protection, free SSL

2. **Optimize Images**:
   - Compress images before upload
   - Use tools like TinyPNG or ImageOptim
   - Consider converting to WebP format

3. **Monitor Performance**:
   - Set up Google Analytics (if not already done)
   - Monitor page speed with PageSpeed Insights
   - Check uptime with UptimeRobot (free)

---

## Rollback Plan

If something goes wrong, you can quickly roll back to Vercel:

1. **Keep Vercel deployment active** for 7 days after migration
2. **Point DNS back to Vercel** if issues arise
3. **All files are backed up** in this local folder

---

## Support Resources

### GoDaddy Support
- Phone: 480-505-8877
- Live Chat: Available in GoDaddy dashboard
- Help Center: https://www.godaddy.com/help

### Technical Questions
- Email: Support@drbibiorganics.com (your own support)
- GoDaddy Community Forums
- Stack Overflow for technical issues

---

## Migration Timeline

**Estimated Total Time**: 2-4 hours (plus DNS propagation)

1. **File Upload**: 30-60 minutes
2. **DNS Configuration**: 5 minutes (+ 1-48 hours propagation)
3. **SSL Setup**: 10-15 minutes
4. **Testing**: 30-60 minutes
5. **Final Verification**: 15-30 minutes

---

## Next Steps After Migration

1. **Update Google Search Console** with new hosting info
2. **Monitor analytics** for any traffic drops
3. **Test all forms** and email deliverability
4. **Check mobile responsiveness**
5. **Run security scan** (GoDaddy offers free security scans)
6. **Set up automated backups** (GoDaddy cPanel has backup tools)

---

## Checklist: Day of Migration

- [ ] Backup all files locally (already done in this folder)
- [ ] Upload all files to GoDaddy public_html
- [ ] Verify file structure matches guide above
- [ ] Update DNS records (if needed)
- [ ] Install SSL certificate
- [ ] Enable HTTPS redirect in .htaccess
- [ ] Test all pages load correctly
- [ ] Test all forms submit properly
- [ ] Test shopping cart functionality
- [ ] Submit new sitemap to Google Search Console
- [ ] Monitor website for 24-48 hours
- [ ] Verify email notifications working
- [ ] Check analytics tracking
- [ ] Test mobile experience
- [ ] Run PageSpeed test
- [ ] Verify SSL certificate is valid

---

**Questions?** Contact GoDaddy support or review this guide again. Good luck with your migration!

*Last Updated: January 6, 2026*
