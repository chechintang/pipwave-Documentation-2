# Submit Payment Information

Used when submitting payment for finalization. It could be used during direct API integration or via SDK / Button integration. Many of the data is optional; If optional data is found to be required after submitting payment information, buyer will be redirected to a Pipwave-controlled page which collects the required information in merchant’s behalf. Initiate Payment API call must be done before payment information can be submitted via Submit Payment Information API call. The Request data of this API call is very similar to Initiate Payment API call, differences being:

1. amount, currency\_code and many other order-related parameters are not in Submit Payment Information API call
2. payment\_method\_code and extra payment parameters within payment\_info is not a parameter in Initiate Payment API call
3. pw\_id must be provided by Submit Payment Information API call, being a pair from Initiate Payment API call
4. Any other overlapping parameters from Submit Payment Information API call will overwrite the data within Initiate Payment API call

**Method**: POST

**Action**: submit-payment

## Request <a id="request"></a>

**Format**: POST data

* **action**

  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The action of this call, must be hardcoded to “submit-payment” | submit-payment |

* **timestamp**

  `required` :  **timestamp**     

| **Remark** | **Sample** |
| :--- | :---: |
| The timestamp for this API call | - |

* **api\_key** 

  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

* **token** 

  `required` :  **string** **\(32\)**  

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave’s payment token | abcdef |

* **payment\_method\_code** :  **string \(32\)\*** 

| **Remark** | **Sample** |
| :--- | :---: |
| The payment method code that buyer selected. Refer to appendix for list of possible values. | - |

* **payment\_info** :   **key-value** **\*Only up to 100 values, must be PG-specific**

| **Remark** | **Sample** |
| :--- | :---: |
| Any other payment information which specific PG requires | - |

* **session\_info** :   **key-value** 

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **session\_info.ip\_address** :   **string \(45\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s IP address, for anti-fraud purposes | 123.123.123.123 |

* **session\_info.language** :   **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Default: en-gb, language to show to buyer. Refer to appendix for list of possible values. | en-gb |

* **buyer\_info** :   **key-value**

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **buyer\_info.email** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s email address | john-doe@pipwave.com |

* **buyer\_info.first\_name** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s first name | Doe |

* **buyer\_info.last\_name** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s last name | John |

* **buyer\_info.contact\_no** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s contact number | 123456789 |

* **buyer\_info.contact\_no\_country\_code** :   **string \(3\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Buyer’s contact number country | 60 |

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

* **billing\_info.address2** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address | - |

* **billing\_info.city** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Billing address city | John Town |

* **billing\_info.state** :   **string \(255\)**

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
| Billing address country ISO2 | Malaysia |

* **billing\_info.country\_iso2** :   **string \(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Billing country ISO2 | MY |

* **billing\_info.contact\_no** :  **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Billing contact number | - |

* **billing\_info.contact\_no\_country\_iso2** :   **string \(2\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Billing contact number country ISO2 | MY |

* **billing\_info.email** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Billing email address | - |

* **shipping\_info** :   **key-value**

| **Remark** | **Sample** |
| :---: | :---: |
| - | - |

* **shipping\_info.name** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping name | John Doe |

* **shipping\_info.address1** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address | 1, Jalan John |

* **shipping\_info.address2** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address | - |

* **shipping\_info.city** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address city | John Town |

* **shipping\_info.state** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address state | Selangor |

* **shipping\_info.zip** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address zip | 12345 |

* **shipping\_info.country** :   **string \(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping address country | Malaysia |

* **shipping\_info.country\_iso2** :   **string \(2\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping country ISO2 | MY |

* **shipping\_info.contact\_no** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping contact number | - |

* **shipping\_info.contact\_no\_country\_iso2** :   **string \(2\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping contact number country ISO2 | MY |

* **shipping\_info.email** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Shipping email address | - |

**\*** - Not required for direct API, but SDK will automatically populate based on buyer’s selections

## Response <a id="response"></a>

**Format**: JSON

* **status** :   **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the request. Refer to appendix for list of possible values. | 0 |

* **message** :   **string \(255\)** 

| **Remark** | **Sample** |
| :--- | :---: |
| Error message, if any | - |

* **redirect\_url** :   **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The next redirect url | [https://merchant.com/success.php?pw\_id=123456&extra\_param1=123456](https://merchant.com/success.php?pw_id=123456&extra_param1=123456) |

* **payment\_status**:   **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the payment. Refer to appendix for list of possible values. | - |

* **payment\_reason** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The reason why the PG status is not successful | - |

## Signature <a id="signature"></a>

There is no need to include signature in this API call.

