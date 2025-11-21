# Sanitred.com - Google Tag Manager Container Setup Guide

## Overview

This GTM container template is customized for **Sanitred.com** WordPress/WooCommerce site. It provides comprehensive tracking across multiple platforms:

- **Google Analytics 4 (GA4)** - Full ecommerce funnel tracking
- **Facebook Pixel (Meta)** - Conversion tracking for ads
- **Server-Side Tracking** - Enhanced data collection via server container

## What's Included

### GA4 Events (11 tags)
- Page views
- Product views (view_item, view_item_list)
- Cart interactions (add_to_cart, view_cart)
- Checkout funnel (begin_checkout, add_shipping_info, add_payment_info)
- Purchase completion

### Facebook Pixel Events (6 tags)
- PageView
- ViewContent
- AddToCart
- InitiateCheckout
- AddPaymentInfo
- Purchase

### Server-Side Data Transfer (6 tags)
- Sends enhanced ecommerce data to server container
- Includes customer billing information
- Event deduplication with event IDs

## Installation Steps

### Step 1: Import the Container

1. Go to Google Tag Manager: https://tagmanager.google.com
2. Select your Sanitred GTM account (or create a new one)
3. Click **Admin** > **Import Container**
4. Upload the `sanitred-gtm-container.json` file
5. Choose import option:
   - **New** - Creates a new container
   - **Existing** - Merges with existing container (use "Merge" option)
6. Click **Confirm**

### Step 2: Configure Required Variables

After importing, you MUST configure these three constant variables:

#### 1. GA4 Measurement ID
- Variable name: `const - ga4 measurement id`
- Navigate to: **Variables** > Find this variable
- Replace `PUT_YOUR_VALUE_HERE` with your GA4 Measurement ID
- Format: `G-XXXXXXXXXX`
- Find your ID in GA4: **Admin** > **Data Streams** > Select your web stream

#### 2. Meta Pixel ID
- Variable name: `const - meta pixel id`
- Replace `PUT_YOUR_VALUE_HERE` with your Facebook Pixel ID
- Format: Numeric (e.g., `1234567890123456`)
- Find your ID in Facebook Events Manager: **Data Sources** > **Pixel**

#### 3. Server Container URL (Optional)
- Variable name: `const - server_container_url`
- Replace `PUT_YOUR_VALUE_HERE` with your server-side GTM URL
- Format: `https://your-server.com` (no trailing slash)
- **Note**: Only needed if using server-side tracking with Stape.io or similar
- Leave as `PUT_YOUR_VALUE_HERE` if not using server-side tracking

### Step 3: Verify WooCommerce Data Layer

This container expects WooCommerce to push ecommerce data to the dataLayer. Ensure you have:

1. **GTM4WP Plugin** (recommended) or
2. **WooCommerce Google Analytics Integration** or
3. **Custom dataLayer implementation**

The container expects these dataLayer events:
- `page_view`
- `view_item`
- `view_item_list`
- `add_to_cart`
- `view_cart`
- `begin_checkout`
- `add_shipping_info`
- `add_payment_info`
- `purchase`

### Step 4: Test the Implementation

1. Click **Preview** in GTM to enter debug mode
2. Visit your Sanitred.com website
3. Test the complete purchase funnel:
   - Browse products
   - Add items to cart
   - Proceed through checkout
   - Complete a test purchase
4. Verify in GTM Preview:
   - All events fire correctly
   - Data is captured properly
   - No errors in console

### Step 5: Verify Tracking

#### GA4 Verification
1. Open GA4 Real-Time reports
2. Perform test actions on site
3. Confirm events appear in real-time view

#### Facebook Pixel Verification
1. Install Facebook Pixel Helper Chrome extension
2. Navigate through your site
3. Verify pixel fires on key pages
4. Check Events Manager for test events

### Step 6: Publish the Container

1. Review all changes in GTM workspace
2. Click **Submit** (top right)
3. Add version name: "Sanitred Initial Setup - [Date]"
4. Add description of changes
5. Click **Publish**

## Important Configuration Notes

### Privacy and Consent

Consider implementing consent management:
- EU visitors require GDPR compliance
- California visitors require CCPA compliance
- Consider adding consent triggers to tags
- Recommended: Cookie Consent Manager plugin for WordPress

### User Data Collection

The container collects billing information:
- Email
- Name
- Phone
- Address
- City, State, ZIP

**Important**: Ensure your privacy policy discloses this data collection.

### Server-Side Tracking (Advanced)

If using server-side tracking:
1. Set up server container (Stape.io, Google Cloud Run, etc.)
2. Configure `const - server_container_url` variable
3. Update Facebook and GA4 tags to use server endpoint
4. This improves data accuracy and bypasses ad blockers

## Troubleshooting

### Events Not Firing
- Check GTM Preview mode for errors
- Verify WooCommerce dataLayer plugin is active
- Check browser console for JavaScript errors
- Ensure GTM container is published

### Missing Ecommerce Data
- Verify WooCommerce integration is pushing data
- Check dataLayer structure in GTM Preview
- Confirm variable values are populated

### Facebook Pixel Not Working
- Verify Pixel ID is correct (numeric only)
- Check for conflicting Facebook Pixel installations
- Use Facebook Pixel Helper to diagnose

## Support and Resources

- [GTM Documentation](https://support.google.com/tagmanager)
- [GA4 Ecommerce Documentation](https://developers.google.com/analytics/devguides/collection/ga4/ecommerce)
- [Facebook Pixel Documentation](https://developers.facebook.com/docs/meta-pixel)
- [WooCommerce GTM Integration](https://wordpress.org/plugins/duracelltomi-google-tag-manager/)

## Credits

This template is based on the Stape.io WooCommerce GTM container template and customized for Sanitred.com.

Original template: https://github.com/stape-io/woocommerce-gtm-container-templates

## Version History

- **v1.0** (2025-11-21) - Initial Sanitred.com customization
  - Updated container name
  - Prepared for Sanitred deployment
  - Added comprehensive setup documentation
