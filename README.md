# First Data Hosted Checkout Payment Pages, for Zen Cart

## Integrations

This supports Global Gateway e4 merchants who wish to use Payment Pages to do Hosted Checkout, which collects payment offsite temporarily before redirecting the customer back to the store to complete the order.

## Installation

### PHP Files
Currently no core files are changed, so you can just upload the files in `/includes/` into the relevant `/includes/` directories and subdirectories within your store.

**Note: You should not copy the README.md, LICENSE or changelog.txt files to your live server.**
 

### Admin module configuration
In your store's Admin->Modules->Payment screen, enter the Page ID, Transaction Key, and Response Key from your GGe4 Payment Page "security" settings tab. See the Security section below for help on where to locate this information.


## Hosted Checkout Pages Configuration

1. Log into your First Data GGe4 account
2. Choose Payment Pages
3. Click on the desired Page ID

There are 9 pages of settings available. The following are the ones that you need to pay attention to:

`1`. General 
 - Page Title - Whatever you want this page to be named. This will be the title shown on the payment page.
 - "Return to your Store" URL - the URL to your store.

`8`. Appearance
 - Header Logo: Upload a Logo if you wish to brand your payment page 

`9`. Security 
 - You will need to enter these settings into your First Data HCO module configuration settings in your Zen Cart Admin:
  - Payment Page ID
  - Transaction Key
  - Response Key

Finally, click `Save Changes` to save all the settings you've altered.

--
### Optional
`4`. Receipt Page
 - Return Link Method: This is set to AUTO-POST inside all transactions sent by this module, regardless of this setting.


 - "Receipt Link URL" - This module automatically sends the correct URL with each transaction. It will be set to your store's checkout_process page, which is at:

     `https://your_domain.com/index.php?main_page=checkout_process`
     
     [NOTE: The module sets this URL inside each transaction, so technically you can leave this blank.]



## Level 3 Processing Support
Level 3 Processing is usually only necessary if you are processing Government credit cards.

Zen Cart already passes all the Level 3 data, but if you want to benefit from it, you need to enable Level 3 data support in 3 places:

1. In your First Data Terminal. (Login to the GlobalGateway account, click on Home, then Terminals, then your business name, then the terminal (if more than one, choose the one for ECOMM / ecommerce). Then enable the Level 3 feature, and save.)

2. In your Hosted Checkout Page settings: Go to your Payment Pages screen, click on the page ID. Then on the General tab, check the box for Enable Level 3 Processing, and click Save.

3. In this payment module. Go to your Zen Cart Admin->Modules->Payment screen, click on Hosted Checkout Pages, Edit, and set "Enable Level 3 Processing" to 'Yes'.


NOTE: MasterCard Level 1 (Consumer) cards won't allow Level 3 data for settlement, so might be rejected AFTER the transaction is initially approved. If this happens to you regularly, then you may need to turn OFF all Level 3 support in the module. The downside is you may pay higher interchange rates for those Level 3 transactions as a result. This is a limitation by MasterCard.



## Testing

Testing can be done with a "real" account, if you simply set your module to Testing mode in your Zen Cart Admin. This will let you do test purchases without actually charging a real credit card.  

This is enough for most peoples' use. 

TEST CREDIT CARD NUMBERS: https://support.payeezy.com/hc/en-us/articles/204504235-Using-test-credit-card-numbers

When ready to "go live", simply set the module to "Production" instead of "Testing" in your Zen Cart Admin.


## Sandbox for Developers Only
If you are a developer and will be doing extensive testing of transactions in a store that's not "real", you may wish to create a Sandbox account for this purpose. The sandbox account is a completely different set of credentials, and completely different Hosted Pages than what your "real" account uses. 

To obtain a Developers Sandbox account, request one via https://provisioning.demo.globalgatewaye4.firstdata.com/signup/ ... again, this is for Developer purposes only.

Then use the Security Keys from the Sandbox account when configuring the payment module in your Zen Cart Admin. Also choose Sandbox mode in the module settings so that it knows to send transactions to a special server. 

If you mix up sandbox vs "real" credentials, you will get security errors when attempting to perform transactions.
