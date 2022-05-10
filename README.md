# [Integration] - Inpage Checkout
<img src="https://user-images.githubusercontent.com/38641542/157055925-88fee4a3-1896-4656-beec-fde9a0d25e03.jpg">


# Introduction

Razer Merchant Services Inpage Checkout (previously known as Seamless Iframe Integration) is developed by Razer Merchant Services technical team.

# Notes/ Prerequisite

Razer Merchant Services Sdn. Bhd. is not responsible for any problems that might arise from the use of this module.
Use at your own risk. Please backup any critical data before proceeding. For any query or
assistance, please email to support-sa@razer.com

# Changelog

Submit issue to this repository or email to our support-sa@razer.com


# Contribution

You can contribute to this plugin by sending the pull request to this repository.

# Installations Guidance for Inpage Checkout

Important
--------------------
``
Please do not generate your vcode in JS as this will disclose the merchant verify key.
``

Getting started
---------------

**Register your domain by email to our support : [support-sa@razer.com](mailto:support-sa@razer.com)**

Include below javascript library in your web. URL depends on serve pointing to.

URL
-----
```html
 <!-- URL for jQuery -->
 Production : https://www.onlinepayment.com.my
 Sandbox    : https://sandbox.merchant.razer.com
 UAT        : https://uat.onlinepayment.com.my
```

Example
---------
```html
 <!-- jQuery (necessary for RazerMS Seamless JavaScript plugins) -->

 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
 <script> var API_HOST = "https://www.onlinepayment.com.my"; </script>
 <script src="https://www.onlinepayment.com.my/RMS/API/seamlessiframe/js/2.0/MOLPay_seamlessiframe.deco.js"></script> 
```

```html
<!-- Radio button trigger RazerMS Seamless Iframe -->
<input type="radio" name="payment_options" id="paymentcredit_alb-paymex" value="credit" data-toggle="molpayseamlessiframe" data-mpsmerchantid="MOLPay_seamless_Dev" data-mpschannel="credit" data-mpsamount="1.20" data-mpsorderid="TEST1139669863" data-mpsbill_name="MOLPay Demo" data-mpsccbox="#MOLPAYCC" required />
```
```html
<!-- Div element for iframe to be loaded -->
<div id="MOLPAYCC"></div>
```

Usage
-----

The RazerMS seamless iframe plugin process your button, via data attributes.

<h3>Via data attributes</h3>

Activate a RazerMS seamless iframe without writing JavaScript. Set <code>data-toggle="molpayseamlessiframe"</code> on a controller element, like a radio button, along with a <code>data-mpsamount="1.01"</code> to set value.

```html
<input type="radio" data-toggle="molpayseamlessiframe">Pay by Credit/Debit Card</button> 
```

<h3>Options</h3>

Options can be passed via data attributes or JavaScript. For data attributes, append the option name to <code>data-</code>, as in <code>data-mpsamount=""</code>.

| Name              | Data Type (size) | M/O/C | Description                                                                                                                                                          |
|-------------------|------------------|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mpsmerchantid     | 	an{1..32}       | 	*M*	 | Merchant login username provided by RazerMS.                                                                                                                         |
| mpschannel        | 	an{3..32}       | 	*M*  | Refer to **Appendix C** for more channel code.                                                                                                                       |
| mpsamount         | 	ns{10,2}        | 	*M*  | 	The transaction amount in one bill. **Min accepted amount : 1.01**                                                                                                  |
| mpsorderid        | 	an{1..32}       | 	*M*  | 	Bill / Invoice no. provided by merchant.                                                                                                                            |
| mpsbill_name      | 	a{1..128}       | 	*M*  | 	Buyer name.                                                                                                                                                         |
| mpsbill_email     | 	ans{1..128}     | 	*M*  | 	Buyer email.                                                                                                                                                        |
| mpsbill_mobile    | 	n{1..128}       | 	*M*  | 	Buyer mobile contact number.                                                                                                                                        |
| mpsbill_desc      | 	an{1..200}      | 	*M*  | 	Bill / Description provided by merchant / buyer.                                                                                                                    |
| mpsbill_add_line1 | 	an{1..200}      | 	*O*  | 	The first line of the buyer's address. **(If mpsbill_add_line1 present then all mpsbill_ parameter with Conditional need to be present)**                           |
| mpsbill_add_line2 | 	an{1..200}      | 	*O*  | 	The second line of the buyer's address.                                                                                                                             |
| mpsbill_zip       | 	an{1..10}       | 	*C*  | 	The zipcode of the buyer's address.                                                                                                                                 |
| mpsbill_city      | 	an{1..128}      | 	*C*  | 	The city of the buyer's address                                                                                                                                     |
| mpsbill_state     | 	an{1..64}       | 	*C*  | 	The state of the buyer's address.                                                                                                                                   |
| mpscountry        | 	a{2}            | 	*C*  | 	Buyer country.                                                                                                                                                      |
| mpsship_name      | 	an{1..128}      | 	*C*  | 	The receiver name of the shipping address.                                                                                                                          |
| mpsship_add_line1 | 	an{1..200}      | 	*O*  | 	The first line of the shipping address. **(If mpsship_add_line1 present then all mpsbill_ parameter with conditional need to be present)**                          |
| mpsship_add_line2 | 	an{1..200}      | 	*O*  | 	The second line of the shipping address.                                                                                                                            |
| mpsship_zip       | 	n{1..10}        | 	*C*  | 	The zipcode of the shipping address.                                                                                                                                |
| mpsship_city      | 	an{1..128}      | 	*C*  | 	The city of the shipping address.                                                                                                                                   |
| mpsship_state     | 	an{1..64}       | 	*C*  | 	The state of the shipping address.                                                                                                                                  |
| mpsship_country   | 	a{2}            | 	*C*  | 	The countryof the shipping address.                                                                                                                                 |
| mpsvcode          | 	an{32}          | 	*C*  | This is the data integrity protection hash string provided by merchant.                                                                                              |
| mpscurrency       | 	a{3}            | 	*O*  | Payment currency, E.g. MYR, SGD, USD & etc.                                                                                                                          |
| mpslangcode       | 	a{2}            | 	*O*  | 	Default language, E.g. 'en' for default.<br>Valid value : 'en', 'cn', 'encn'                                                                                        |
| mpsreturnurl      | 	ans{1..200}     | 	*O*  | 	Obsoleted. Used for multiple return URL. All URLs must be registered beforehand with RazerMS.                                                                       |
| non_3ds           | n[0/1]           | *O*   | Applicable to card processing via specific processor using specific currency for pre-approved partner only. <br> Equal to 0 by default and 1 for non-3DS transaction |
| mpstcctype        | a{4}             | *O*   | SALS <br> AUTH (For card payment only, please inform support-sa@razer.com in advanced before starting using pre-auth payment)                                        |
| mpstokenstatus    | n[0/1]           | *O*   | To tokenized the transaction.                                                                                                                                        |
| mpsccbox          | ans              | 	*M*  | 	Element id or class name to show the iframe. E.g. #MOLPAYCC, .MOLPAYCC.                                                                                             |

Appendix A: Data Type Details
--------------------------------
| No  | Code   | Description            |
|-----|--------|------------------------|
| 1.  | a      | Letters, A-Za-z        |
| 2.  | n      | Numbers, 0-9           |
| 3.  | s      | Symbols, .:            |?*,!&_-
| 4.  | {x}    | Fixed length x         |
| 5.  | {y..x} | Length range: y – x    |
| 6.  | {y,x}  | Number range: 0-9. 0-9 |

Appendix B: M/O/C Details
--------------------------------
| No  | Code | Description                         |
|-----|------|-------------------------------------|
| 1.  | M    | Mandatory field.                    |
| 2.  | O    | Optional field, value can be empty. |
| 3.  | C    | Conditional                         |

Appendix C: Channel details (mpschannel)
---------------------------------------
| No  | Code    | Description             | Type        | Supported                                                                                                                                                                                                                                                                                                           |
|-----|---------|-------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.  | credit  | Credit Card/ Debit Card | Credit Card | MY, MYR, CC (TxnType: SALS, AUTH)                                                                                                                                                                                                                                                                                   |
| 2.  | creditT | Credit Card/ Debit Card | Credit Card | Worldwide, MultiCurrency, CC (TxnType: SALS, AUTH)<br>AWG, AUD, BSD, BHD, BBD, BYR, BZD, BRL, BIF, CAD, KYD, CNY, HRK, CZK, DKK, DOP, XCD, EUR, GYD, HKD, HUF, INR, ILS, JMD, JPY, KWD, LTL, MYR, MXN, ANG, NZD, NOK, OMR, PLN, GBP, RON, RUB, SAR, RSD, SGD, ZAR, KRW, SRD, SEK, CHF, TWD, TTD, THB, TRY, AED, USD |

Data attributes for individual RazerMS seamless iframe
----------------------------------------------
Options for individual RazerMS seamless iframe can alternatively be specified through the use of data attributes, as explained above.

Return Parameters
-----------------
- All return parameters are the same as described in RazerMS API for merchants.
- Merchant can use the same return URL script for this seamless iframe integration.
- Once payment is done, the existing page will be replaced by the merchant return URL.


## Resources

- GitHub:     https://github.com/RazerMS
- Website:    https://merchant.razer.com/
- Twitter:    https://twitter.com/Razer_MS
- YouTube:    https://www.youtube.com/c/RazerMerchantServices
- Facebook:   https://www.facebook.com/RazerMerchantServices/
- Instagram:  https://www.instagram.com/RazerMerchantServices/


# Issues

Submit issue to this repository or email to our support-sa@razer.com


# Contact Support

Merchant Technical Support / Customer Care : support-sa@razer.com <br>
Sales/Reseller Enquiry : sales-sa@razer.com <br>
Marketing Campaign : marketing-sa@razer.com <br>
Channel/Partner Enquiry : channel-sa@razer.com <br>
Media Contact : media-sa@razer.com <br>
R&D and Tech-related Suggestion : technical-sa@razer.com <br>
Abuse Reporting : abuse-sa@razer.com
