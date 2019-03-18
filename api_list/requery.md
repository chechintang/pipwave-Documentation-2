# Requery

Used to get the latest status of the payment.

**Method**: POST

**Action**: requery

## Request <a id="request"></a>

**Format**: POST data

* **action** `required` : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The action of this call, must be hardcoded to “requery” | requery |

---

* **timestamp** `required` : **timestamp**

| **Remark** | **Sample** |
| :--- | :---: |
| The timestamp for this API call | - |

* **api\_key**`required` : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

* **pw\_id** : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave’s transaction reference ID, either this or txn\_id must be sent | 123456 |

* **txn\_id** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Merchant’s transaction ID, either this or pw\_id must be sent | 123456 |

## Response <a id="response"></a>

**Format**: JSON

* **status** : **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the request. Refer to appendix for list of possible values. | 0 |

* **message** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Error message, if any. | - |

* **api\_key** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

* **pw\_id** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave reference transaction ID | 123456 |

* **txn\_id** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Merchant’s transaction ID, either this or pw\_id must be sent | - |

* **pg\_txn\_id** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Payment gateway's reference transaction ID | - |

* **amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The payment checkout amount | 123 |

* **tax\_exempted\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax-exempted amount from the payment checkout amount | 0 |

* **processing\_fee\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The processing fee amount | 1.2 |

* **shipping\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The shipping fee amount | - |

* **handling\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The handling fee amount | - |

* **tax\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax amount | 2.4 |

* **total\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The total amount for the payment | 126.6 |

* **final\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Final amount for this transaction \(after potential chargeback / refund / adjustments\) | 126.6 |

* **currency\_code** : **string \(3\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The payment currency. Follow ISO 4217 standard. | MYR |

* **transaction\_status** : **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the payment as stored by pipwave. Refer to appendix for list of posssible values. | - |

* **subscription\_token** : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| If payment is subscription type, this data is pipwave’s subscription payment token | 123456 |

* **charge\_index** : **integer**

| **Remark** | **Sample** |
| :--- | :---: |
| Charging index, only subscription payments will include this data, 1 indicates initial payment, subsequent number indicates subsequent charges, in sequence | 1 |

* **payment\_method\_code** : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The payment method code that buyer selected. Refer to appendix for list of possible values. | 123456 |

* **payment\_method\_title** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The title of the payment method. | Paypal |

* **reversible\_payment** : **boolean**

| **Remark** | **Sample** |
| :--- | :---: |
| Is the payment method reversible? | - |

* **settlement\_account** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The identifier of the settlement account that processed the payment. | Default |

* **require\_capture** : **boolean**

| **Remark** | **Sample** |
| :--- | :---: |
| Does this transaction require capture? | - |

* **billing\_info** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| Billing info as acquired by pipwave | - |

* **shipping\_info** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping info as acquired by pipwave | - |

* **tax\_info** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax info | - |

* **tax\_info.tax\_name** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The name of the tax | GST |

* **tax\_info.tax\_country** : **string \(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The country detected by pipwave to apply tax | MY |

* **tax\_info.tax\_base\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| The base rate of the tax configured by Merchant | 6 |

* **tax\_info.tax\_local\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax rate override by region or city, if applicable | null |

* **tax\_info.tax\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| Final tax rate to apply | 6 |

* **tax\_info.items** : **array**

| **Remark** | **Sample** |
| :--- | :---: |
| Array of items sent in initiate-payment, with tax information | - |

* **tax\_info.items.x.item\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax imposed onto this line of item | 0.06 |

* **tax\_info.items.x.item\_tax\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax rate applied to this line of item, after overrides where applicable | 6 |

* **tax\_info.items.x.taxable\_amount** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Taxable amount based on the total against item total | 1 |

* **tax\_info.processing\_fee\_tax\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax rate applied to the processing fee | 6 |

* **tax\_info.processing\_fee\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax imposed onto the processing fee | - |

* **tax\_info.shipping\_amount\_tax\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax rate applied to the shipping amount | - |

* **tax\_info.shipping\_amount\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax imposed onto the shipping amount | - |

* **tax\_info.handling\_amount\_tax\_rate** : **float**

| **Remark** | **Sample** |
| :--- | :---: |
| The tax rate applied to the handling amount | - |

* **tax\_info.handling\_amount\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax imposed onto the handling amount | - |

* **tax\_info.amount\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Tax imposed onto the order amount | - |

* **tax\_info.total\_tax** : **decimal \(11, 2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Total tax imposed onto the checkout total | - |

* **reversible\_payment** : **boolean**

| **Remark** | **Sample** |
| :--- | :---: |
| Is the payment method reversible? | - |

* **require\_capture** : **boolean**

| **Remark** | **Sample** |
| :--- | :---: |
| Does this transaction require capture? | - |

* **transaction\_status** : **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the payment as stored by pipwave. Refer to appendix for list of possible values. | 20160101120000 |

* **mobile\_number** : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s mobile number as verified | 123456789 |

* **mobile\_number\_country\_iso2** : **string \(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer's mobile number country iso2 | MY |

* **mobile\_number\_country\_code** : **string \(8\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer's mobile number country dialing code | 60 |

* **mobile\_number\_verification** : **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Did the verification succeed? One of "verified", "verified previously", "unverified", or "skipped" | - |

* **pipwave\_score** : **integer \(3\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The fraud risk rating for this transaction as processed by pipwave | - |

* **rules\_action** : **string \(16\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The suggested action to undertake for this transaction, can be one of “approve”, “decline” or “review” | approve |

* **rules\_action\_reason** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The reason of above rules\_action, especially for RulesDisabled case. | - |

* **risk\_management\_data** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| The extra risk data | - |

* **matched\_rules** : **array**

| **Remark** | **Sample** |
| :--- | :---: |
| The array of all rules was that matched | - |

* **extra\_param1** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra notification parameter that was configured when Submit Payment Information API is being called | 123456 |

* **extra\_param2** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra notification parameter that was configured when Submit Payment Information API is being called | abcdef |

* **extra\_param3** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Extra notification parameter that was configured when Submit Payment Information API is being called | - |

* **upload\_files** : **array**

| **Remark** | **Sample** |
| :--- | :---: |
| A list of urls to the files uploaded for offline payments. All images are signed for 1 hour only, for integrated system to download and store the image. | - |

* **upload\_remark** : **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The payer's remark on the uploaded files. | - |

* **payment\_data** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| - | - |

* **payment\_data.wallet** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer's payment wallet details will be available if buyer uses wallet to pay | - |

* **payment\_data.wallet.wallet\_id** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Payment wallet ID | - |

* **payment\_data.wallet.wallet\_email** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Payment wallet email | - |

* **payment\_data.credit\_card** : **key-value**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer's payment credit card details will be available if buyer uses credit card to pay | - |

* **payment\_data.credit\_card.formatted\_pan** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card first 6 and last 4 | - |

* **payment\_data.credit\_card.cvv** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card CVV matching result code, refer to appendix for possible values | - |

* **payment\_data.credit\_card.avc** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card AVS matching result code, refer to appendix for possible values | - |

* **payment\_data.credit\_card.threeds** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card Three-D Secure result code, refer to appendix for possible values | - |

* **payment\_data.credit\_card.issuer\_country** : **string\(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card issuer country in ISO Code 2 | - |

* **payment\_data.credit\_card.issuer\_bank** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card issuer bank | - |

* **payment\_data.credit\_card.card\_type** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card type | - |

* **payment\_data.credit\_card.card\_brand** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card brand | - |

* **payment\_data.credit\_card.card\_level** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card level | - |

* **payment\_data.credit\_card.card\_holder\_name** : **string\(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card holder's name | - |

* **payment\_data.credit\_card.card\_expiry\_month** : **string\(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card expiry month | - |

* **payment\_data.credit\_card.card\_expiry\_year** : **string\(4\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Credit card expiry year | - |

## Signature <a id="signature"></a>

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* pw\_id OR txn\_id
* api\_secret

