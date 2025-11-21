# Sanitred GTM Setup - Quick Start Checklist

## Pre-Installation Checklist

- [ ] Google Tag Manager account created
- [ ] GA4 property set up for sanitred.com
- [ ] Facebook Pixel created (if using Facebook ads)
- [ ] WooCommerce GTM plugin installed (recommended: GTM4WP)

## Installation Checklist

### 1. Import Container
- [ ] Go to tagmanager.google.com
- [ ] Import `sanitred-gtm-container.json`
- [ ] Container imported successfully

### 2. Configure Variables (CRITICAL)
- [ ] Set `const - ga4 measurement id` to your GA4 ID (G-XXXXXXXXXX)
- [ ] Set `const - meta pixel id` to your Facebook Pixel ID (numeric)

### 3. Test Before Publishing
- [ ] Enable Preview mode in GTM
- [ ] Test page view on homepage
- [ ] Test product view
- [ ] Test add to cart
- [ ] Test checkout process
- [ ] Test purchase completion
- [ ] All events firing correctly in GTM Preview

### 4. Verify External Platforms
- [ ] GA4 Real-Time showing events
- [ ] Facebook Events Manager showing pixel fires (if applicable)
- [ ] No JavaScript errors in browser console

### 5. Publish
- [ ] Submit container version
- [ ] Add descriptive version name
- [ ] Publish container
- [ ] Verify live site tracking works

## Post-Launch Checklist

### Week 1
- [ ] Monitor GA4 reports daily
- [ ] Check for unusual drop-offs in funnel
- [ ] Verify purchase data is accurate
- [ ] Compare revenue in GA4 vs WooCommerce

### Week 2
- [ ] Review conversion rates
- [ ] Check for any tracking gaps
- [ ] Verify all product categories tracked
- [ ] Test on mobile devices

### Ongoing Maintenance
- [ ] Monthly review of tracking accuracy
- [ ] Update tags when adding new features
- [ ] Monitor for GTM/GA4 updates
- [ ] Review and clean up unused tags/variables

## Common Issues and Quick Fixes

### Events not firing
**Fix**: Check WooCommerce dataLayer plugin is active and GTM container is published

### No purchase data in GA4
**Fix**: Verify transaction ID is unique and ecommerce object is properly formatted

### Facebook Pixel not working
**Fix**: Ensure Pixel ID is numeric only (no spaces or extra characters)

### Duplicate events
**Fix**: Check for multiple GTM containers or conflicting tracking code

## Need Help?

Refer to `SANITRED-GTM-SETUP.md` for detailed instructions.

## Your Sanitred Tracking IDs

Fill these in for quick reference:

```
GA4 Measurement ID: G-________________
Facebook Pixel ID: ________________
GTM Container ID: GTM-________________
```

## Contact

For technical support with GTM setup, contact your web development team or GTM specialist.
