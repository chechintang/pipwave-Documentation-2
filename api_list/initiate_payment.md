# Initiate Payment

Used when submitting payment for initiation. It could be used during direct API integration or via SDK / Button integration. Payment initiation must be done before payment information can be submitted via Submit Payment Information API call. The Request data of this API call is very similar to Submit Payment Information API call, differences being:

1. amount, currency\_code and many other order-related parameters are not in Submit Payment Information API call
2. payment\_method\_code and extra payment parameters within payment\_info is not a parameter in Initiate Payment API call
3. txn\_id must be provided by Initiate Payment API call, and pw\_id must be provided by Submit Payment Information API call, being a pair from Initiate Payment API call
4. Any other overlapping parameters from Submit Payment Information API call will overwrite the data within Initiate Payment API call

**Method**: POST

**Action**: initiate-payment

## Request <a id="request"></a>

**Format**: POST data

* **action**

  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The action of this call, must be hardcoded to “initiate-payment” | initiate-payment |

* **timestamp**

  `required` :  **timestamp \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The timestamp for this API call | - |

* **api\_key**

  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

* **txn\_id**

  `required` :  **string \(255\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| Unique merchant’s transaction ID | 123456 |

* **amount**

  `required` :  **decimal \(11, 2\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The payment amount, include all fees, after store credit deduction and discounts | 123 |

* **shipping\_amount** :  **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The shipping fee amount | - |

* **handling\_amount** :  **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The handling fee amount | - |

* **tax\_exempted\_amount** :  **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| How much of the payment amount is tax-exempted; Defaults to 0, must be less than or equals to amount | 123 |

* **currency\_code** 

  `required` :  **string \(3\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| The payment currency. Follow ISO 4217 standard. | MYR |

* **short\_description** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Short/summary description of the payment | Payment for games. |

* **prefered\_payment** :  **text** 

| **Remark** | **Sample** |
| :--- | :---: |
| Comma-delimited allowable checkout payment methods to be shown to buyer. Setting this overrides and ignores “prefered\_category” and “exclude\_payment” parameter. Refer to appendix for list of possible values. | paypal |

* **exclude\_payment** :  **text** 

| **Remark** | **Sample** |
| :--- | :---: |
| Comma-delimited payment methods to be excluded from being shown to buyer. Refer to appendix for list of possible values. | skrill,ipay88 |

* **prefered\_category** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Comma-delimited allowable checkout payment channels to be shown to buyer. Refer to appendix for list of possible values. | e-wallet,e-banking |

* **subscription\_info** :  **key-value** 

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **subscription\_info.subscription** :  **boolean** 

| **Remark** | **Sample** |
| :--- | :---: |
| Default: false | true |

* **subscription\_info.subscription\_frequency** :  **string \(32\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| If subscription = true, this parameter becomes required; otherwise it is ignored. Specifies the frequency the subscription fee will be charged again. Refer to appendix for list of possible values | MONTHLY |

* **subscription\_info.subscription\_monthly\_charge\_day** :  **unix datetime** 

| **Remark** | **Sample** |
| :--- | :---: |
| If subscription is monthly, this parameter becomes required; otherwise it is ignored. Specifies the next date for charging, in GMT+0. After that, subsequent monthly charge will be based on this date. | 2016-03-01 00:00:00 |

* **payment\_info** :  **key-value** 

| **Remark** | **Sample** |
| :--- | :---: |
| The payment data information | - |

* **session\_info** :  **key-value** 

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **session\_info.ip\_address** :  **string \(45\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s IP address, for anti-fraud purposes | 123.123.123.123 |

* **session\_info.session\_id** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s session ID with the merchant website, for anti-fraud purposes | yVPWBgovdzwTvJExDFr2hc10IdGlsdCj |

* **session\_info.language** :  **string \(5\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Default: en-gb, language to show to buyer. Refer to appendix for list of possible values | en-gb |

* **buyer\_info** :  **key-value** 

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **buyer\_info.id** 

  `required` :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Used to uniquely identify your buyer for order tagging and reporting purposes | - |

* **buyer\_info.email** 

  `required` :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s email address | john-doe@pipwave.com |

* **buyer\_info.first\_name** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s first name | Doe |

* **buyer\_info.last\_name** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s last name | John |

* **buyer\_info.contact\_no** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s contact number | 123456789 |

* **buyer\_info.contact\_no\_country\_iso2** :  **string \(2\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s contact number country ISO2 | MY |

* **buyer\_info.contact\_no\_country\_code** :  **string \(3\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s contact number country dialing code | 60 |

* **buyer\_info.country\_code** 

  `required` :  **string \(3\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s country code ISO2 | MY |

* **buyer\_info.processing\_fee\_group** :  **string \(64\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s processing fee group, refering to Merchant’s processing fee group group list Reference ID. If no match is found, no processing fee will be imposed | gold |

* **buyer\_info.login\_ip\_address** : **string \(45\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s login IP address | 123.123.123.123 |

* **buyer\_info.signup\_ip\_address** : **string \(45\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s signup IP address | 123.123.123.123 |

* **buyer\_info.signup\_date** : **timestamp**  

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s signup date in unix timestamp | 1543539126 |

* **billing\_info** :  **key-value**  

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **billing\_info.name** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing name | John Doe |

* **billing\_info.address1** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address | 1, Jalan John |

* **billing\_info.address2** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address | - |

* **billing\_info.city** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address city | John Town |

* **billing\_info.state** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address state | Selangor |

* **billing\_info.zip** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address zip | 12345 |

* **billing\_info.country** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address country | Malaysia |

* **billing\_info.country\_iso2** :  **string \(2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing country ISO2 | MY |

* **billing\_info.contact\_no** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing contact number | - |

* **billing\_info.contact\_no\_country\_iso2** :  **string \(2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing contact number country ISO2 | MY |

* **billing\_info.email** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Billing email address | - |

* **shipping\_info** :  **key-value**  

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **shipping\_info.name** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping name | John Doe |

* **shipping\_info.address1** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address | 1, Jalan John |

* **shipping\_info.address2** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address | - |

* **shipping\_info.city** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address city | John Town |

* **shipping\_info.state** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address state | Selangor |

* **shipping\_info.zip** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address zip | 12345 |

* **shipping\_info.country** :  **string \(2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address country | Malaysia |

* **shipping\_info.country\_iso2** :  **string \(2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping country ISO2 | MY |

* **shipping\_info.contact\_no** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping contact number | - |

* **shipping\_info.contact\_no\_country\_iso2** :  **string \(2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping contact number country ISO2 | MY |

* **shipping\_info.email** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping email address | - |

* **item\_info** :  **array** **\*Only up to 20 values, 255 character length for each data** 

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **item\_info.x.name** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Product name | The Theory of Nothing |

* **item\_info.x.description** :  **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Product description | When Hawking Stephen finds the true answer of everything, guess what he finds? |

* **item\_info.x.amount** :  **decimal \(11, 2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Product unit price, after discounts, and, if Merchant handles the tax charges, after tax | 123 |

* **item\_info.x.quantity** :  **decimal \(11, 2\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Quantity of product being purchased | 1 |

* **item\_info.x.category** :  **string \(128\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Product category | - |

* **item\_info.x.is\_tangible\_good** :  **boolean**  

| **Remark** | **Sample** |
| :--- | :---: |
| Is it physical good? True, or false \(for digital/virtual goods\) | true |

* **item\_info.x.sku** 

  `*required`:   **string \(255\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Product code, required if item info row exists | 123456 |

* **subtotal\_info** :   **array** \* Only up to 20 values, 255 character length for each data

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **subtotal\_info.x.name** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Subtotal label | Shipping cost |

* **subtotal\_info.x.value** :   **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Subtotal amount | 0 |

* **api\_override** :   **key-value**

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **api\_override.notification\_url** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Overriding of the notification url set in Merchant center, specifically for this transaction | [https://merchant.com/notification.php](https://merchant.com/notification.php) |

* **api\_override.success\_url** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Overriding of the transaction successful URL set in Merchant center, specifically for this transaction | [https://merchant.com/success.php](https://merchant.com/success.php) |

* **api\_override.fail\_url** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Overriding of the transaction fail URL set in Merchant center, specifically for this transaction | [https://merchant.com/fail.php](https://merchant.com/fail.php) |

* **api\_override.redirect\_extra\_param1** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the success/fail redirect as GET parameters | 123456 |

* **api\_override.redirect\_extra\_param2** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the success/fail redirect as GET parameters | - |

* **api\_override.redirect\_extra\_param3** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the success/fail redirect as GET parameters | - |

* **api\_override.notification\_extra\_param1** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the notification package | 123456 |

* **api\_override.notification\_extra\_param2** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the notification package | abcdef |

* **api\_override.notification\_extra\_param3** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra data to be included with the notification package | - |

* **init\_setting** :   **key-value**

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **init\_setting.skip\_phone\_verification** :   **boolean**

| **Remark** | **Sample** |
| :--- | :---: |
| If merchant account's phone verification is enabled, this flag allows merchant to skip phone verification just for this transaction | true |

### Response <a id="response"></a>

**Format**: JSON

* **status** :  **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the request. Refer to appendix for list of possible values | 0 |

* **message** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Error message, if any | - |

* **token** :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave’s payment token | abcdef |

* **redirect\_url** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The next redirect url | - |

## Signature <a id="signature"></a>

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* txn\_id
* amount
* currency\_code
* api\_secret

