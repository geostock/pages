# GeoStock FAQs & Troubleshooting Guide

## Quick Links
- [Common Issues](#common-issues)
- [Installation Guide](#installation-guide)
- [Theme Help](#theme-help)
- [Support Resources](#support-resources)

## Common Issues

### Display Issues
1. **Inventory Not Showing**
   - Check if the snippet is installed
   - Verify snippet position in `product-template.liquid`
   - Clear browser cache and reload

2. **Wrong Inventory Count**
   - Verify store location settings
   - Check cache status
   - Review recent inventory updates

### Location Issues
1. **Location Detection Problems**
   - Check country restrictions
   - Verify geolocation settings
   - Review store location setup

### Pickup Options
1. **Pickup Not Working**
   - Verify pickup locations are set up
   - Check cart warnings configuration
   - Review location availability

## Installation Guide
1. **Automated Setup**
   - Choose "Above Cart" or "Below Cart"
   - Save settings
   - Verify display

2. **Custom Position**
   ```html
   <div id="inventoryLocationInformation">
     <span class="inventoryLocationLoading"></span>
   </div>
   ```
   - Add to `product-template.liquid`
   - Place below product price
   - Save theme changes

## Theme Help
1. **After Theme Update**
   - Verify snippet presence
   - Check theme compatibility
   - Review customization settings

2. **Style Conflicts**
   - Check mobile display
   - Review style settings
   - Verify app conflicts

## Support Resources
- Email: geostock@proton.me
- Response Time: 24-48 hours
- [Documentation](https://jtc-interactive.gitbook.io/inventory-app)
