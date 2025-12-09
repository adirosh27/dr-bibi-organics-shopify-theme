# Email Automation Setup Guide
## Abandoned Cart Recovery & Post-Purchase Email Sequences

This guide will help you set up automated email sequences for Dr. Bibi Organics to recover abandoned carts and nurture customers post-purchase.

---

## 📧 Email Templates Created

### Abandoned Cart Sequence (3 emails)
1. **Email 1** (`abandoned-cart-1.html`) - Sent 1 hour after cart abandonment
   - Subject: "You left something behind..."
   - Reminds customer about their cart with product details

2. **Email 2** (`abandoned-cart-2.html`) - Sent 24 hours after abandonment
   - Subject: "Still thinking it over?"
   - Includes testimonials and key benefits

3. **Email 3** (`abandoned-cart-3.html`) - Sent 48 hours after abandonment
   - Subject: "Last chance: 10% OFF inside 🎁"
   - Creates urgency with discount code and expiration

### Post-Purchase Sequence (4 emails)
1. **Email 1** (`post-purchase-1-thank-you.html`) - Sent immediately after purchase
   - Subject: "Welcome to the family! 🎉"
   - Order confirmation with what to expect

2. **Email 2** (`post-purchase-2-how-to-use.html`) - Sent 5-7 days after purchase
   - Subject: "Get maximum results from your Butter Oasis"
   - Comprehensive usage guide and pro tips

3. **Email 3** (`post-purchase-3-review-request.html`) - Sent 14 days after purchase
   - Subject: "How's your skin feeling? ⭐"
   - Review request with 15% discount incentive

4. **Email 4** (`post-purchase-4-reorder-reminder.html`) - Sent 90 days after purchase
   - Subject: "Time for a refill? Save 20% today"
   - Reorder reminder with loyal customer discount

---

## 🛠️ Setup Options

### Option 1: Shopify Email (Recommended for Shopify stores)

Since you're using Shopify checkout, you can set up abandoned cart emails directly in Shopify:

#### Abandoned Cart Recovery in Shopify:

1. **Go to Settings > Notifications** in your Shopify admin
2. Click on "Abandoned checkouts"
3. Enable abandoned cart emails
4. Customize the email templates with the HTML from `emails/abandoned-cart-*.html`
5. Set up the sequence:
   - Email 1: 1 hour delay
   - Email 2: 24 hours delay
   - Email 3: 48 hours delay with discount code

#### Post-Purchase Emails in Shopify:

1. **Go to Marketing > Automations**
2. Create a new automation workflow
3. Set trigger: "Order placed"
4. Add email steps with delays:
   - Step 1: Send immediately (thank you)
   - Step 2: Wait 5 days, send how-to guide
   - Step 3: Wait 14 days, send review request
   - Step 4: Wait 90 days, send reorder reminder

### Option 2: Klaviyo (Best for advanced segmentation)

Klaviyo integrates seamlessly with Shopify and offers powerful automation:

#### Setup Steps:

1. **Install Klaviyo** from Shopify App Store
2. **Create Abandoned Cart Flow:**
   - Go to Flows > Create Flow > Abandoned Cart
   - Add 3 email steps at 1hr, 24hr, 48hr intervals
   - Upload HTML templates
   - Add dynamic discount code for email 3

3. **Create Post-Purchase Flow:**
   - Go to Flows > Create Flow > Post-Purchase
   - Add 4 email steps with appropriate delays
   - Enable condition: "Has received order" before sending

4. **Configure Dynamic Content:**
   - Use Klaviyo variables for personalization:
     - `{{ person.first_name }}` for customer name
     - `{{ event.OrderNumber }}` for order number
     - `{{ item.Name }}` for product name

#### Klaviyo Variable Replacements:
```
{{CUSTOMER_NAME}} → {{ person.first_name }}
{{ORDER_NUMBER}} → {{ event.OrderNumber }}
{{CART_RECOVERY_URL}} → {{ event.extra.checkout_url }}
{{REVIEW_URL}} → Your review page URL
{{SHOP_URL}} → {{ organization.url }}
```

### Option 3: Mailchimp

1. **Connect Mailchimp to Shopify**
2. **Create Abandoned Cart Automation:**
   - Go to Automations > Abandoned Cart
   - Set up 3-email sequence
   - Import HTML templates

3. **Create Customer Journey for Post-Purchase:**
   - Trigger: Customer makes purchase
   - Add 4 email steps with delays

### Option 4: Other Email Services

Most email marketing platforms (ActiveCampaign, Omnisend, Drip, etc.) support:
- Abandoned cart tracking
- Purchase triggers
- Timed delays
- Dynamic content

Consult your platform's documentation for specific setup instructions.

---

## 🔧 Template Customization

Before sending, replace these placeholders in the HTML templates:

### Required Replacements:
- `{{CUSTOMER_NAME}}` - Customer's first name
- `{{ORDER_NUMBER}}` - Shopify order number
- `{{CART_RECOVERY_URL}}` - Link to abandoned cart checkout
- `{{REVIEW_URL}}` - Link to your review/testimonial page
- `{{SHOP_URL}}` - Your shop URL (https://drbibiorganics.com)
- `{{DELIVERY_DATE}}` - Estimated delivery date
- `{{SHIPPING_ADDRESS}}` - Customer's shipping address
- `{{TRACK_ORDER_URL}}` - Order tracking link
- `{{UNSUBSCRIBE_URL}}` - Unsubscribe link (required by law)

### Discount Codes:
Make sure to create these discount codes in Shopify:
- `SAVE10` - 10% off for abandoned cart email 3
- `LOYAL20` - 20% off for reorder reminder email

**To create discount codes in Shopify:**
1. Go to Discounts > Create discount
2. Set discount type (percentage)
3. Set usage limits if desired
4. Set expiration dates

---

## 📊 Best Practices

### Abandoned Cart Emails:
- ✅ Send within 1 hour for best results
- ✅ Keep subject lines personal and non-pushy
- ✅ Include product images and clear CTA
- ✅ Add urgency in final email (discount expires)
- ✅ Make unsubscribe easy to maintain trust

### Post-Purchase Emails:
- ✅ Thank customers immediately after purchase
- ✅ Provide value (education, tips) before asking for reviews
- ✅ Time review requests for when product has been used (14 days)
- ✅ Incentivize reviews with discount codes
- ✅ Send reorder reminders based on product lifespan

### Email Deliverability:
- ✅ Authenticate your domain (SPF, DKIM, DMARC)
- ✅ Use a professional email address (Support@drbibiorganics.com)
- ✅ Test emails before launching
- ✅ Monitor open rates and adjust timing
- ✅ Clean your email list regularly

### A/B Testing Ideas:
- Subject lines
- Discount amounts (10% vs 15% vs 20%)
- Email timing (1hr vs 2hr for first email)
- CTA button text and colors

---

## 📈 Expected Results

Based on e-commerce industry benchmarks:

### Abandoned Cart Recovery:
- **Average recovery rate:** 10-15%
- **Email 1 (1 hour):** 4-5% conversion
- **Email 2 (24 hours):** 3-4% conversion
- **Email 3 (48 hours with discount):** 2-3% conversion

### Post-Purchase Sequence:
- **Review request:** 10-20% response rate
- **Reorder reminder:** 5-10% conversion rate
- **Customer lifetime value:** +30-50% increase

**Example:**
- 100 abandoned carts/month
- 12 recovered sales at $70 = $840/month
- Annual abandoned cart recovery: ~$10,000

---

## 🧪 Testing Your Emails

### Before Launch:
1. **Send test emails to yourself**
   - Check all links work
   - Verify images load
   - Test on mobile and desktop
   - Check in multiple email clients (Gmail, Outlook, Apple Mail)

2. **Test dynamic content**
   - Verify all variables populate correctly
   - Check discount codes apply properly
   - Test cart recovery links

3. **Check compliance**
   - Ensure unsubscribe link is present and working
   - Add physical mailing address in footer
   - Follow CAN-SPAM Act requirements

### Tools for Testing:
- [Litmus](https://litmus.com) - Email preview across clients
- [Email on Acid](https://www.emailonacid.com) - Email testing
- [Mail Tester](https://www.mail-tester.com) - Spam score checking

---

## 📞 Support

If you need help setting up these email sequences:

1. **Shopify Support:** help.shopify.com
2. **Klaviyo Support:** community.klaviyo.com
3. **Email me directly:** Reply to any Dr. Bibi Organics email

---

## 🎯 Next Steps

1. ☐ Choose your email platform (Shopify Email, Klaviyo, etc.)
2. ☐ Create discount codes in Shopify (`SAVE10`, `LOYAL20`)
3. ☐ Set up abandoned cart tracking
4. ☐ Import and customize email templates
5. ☐ Configure email sequences with proper timing
6. ☐ Test all emails thoroughly
7. ☐ Launch and monitor performance
8. ☐ Optimize based on open rates and conversions

---

## 📋 Quick Reference: Email Timing

| Email | Timing | Purpose |
|-------|--------|---------|
| Abandoned Cart 1 | 1 hour | Gentle reminder |
| Abandoned Cart 2 | 24 hours | Social proof & benefits |
| Abandoned Cart 3 | 48 hours | Urgency + 10% discount |
| Post-Purchase 1 | Immediate | Order confirmation |
| Post-Purchase 2 | 5-7 days | Usage guide |
| Post-Purchase 3 | 14 days | Review request |
| Post-Purchase 4 | 90 days | Reorder with 20% off |

---

Good luck with your email automation! These sequences should significantly boost your conversion rates and customer lifetime value. 🚀
