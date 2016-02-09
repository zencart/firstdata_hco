# First Data Hosted Checkout Payment Pages, for Zen Cart

## Integrations

This supports Global Gateway e4 merchants who wish to use Payment Pages to do Hosted Checkout, which collects payment offsite temporarily before redirecting the customer back to the store to complete the order.

## Installation

### PHP Files
Currently no core files are changed, so you can just upload the files in `/includes/` into the relevant `/includes/` directories and subdirectories within your store.

**Note: You should not copy the README.md, LICENSE or changelog.txt files to your live server.**
 
### Admin module configuration
When installing the payment module from your admin > modules > payment, copy the Page ID, Transaction Key, and Response Key from your GGe4 Payment Page "security" settings tab.

