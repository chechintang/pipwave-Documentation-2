# Tag Chargeback Payment

Used to tag payment as chargeback when Merchants receive chargeback notifications via email or other communication channels. Can also be used to finalize a chargeback or revert a chargeback. Only Payments with PAID or PARTIALLY REFUNDED state can be chargeback.

**Method**: POST

**Action**: tag-chargeback

## Request <a id="request"></a>

**Format**: POST data

* **action**

  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The action of this call, must be hardcoded to “tag-chargeback” | tag-chargeback |

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

* **pw\_id** 

  `*required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave’s transaction reference ID, either this or txn\_id must be sent | 123456 |

* **txn\_id** 

  `*required` :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Merchant’s transaction ID, either this or pw\_id must be sent | 123456 |

* **stage** 

  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The stage of chargeback : either “disputed”, “chargeback”, "dispute won", "dispute resolved" or “chargeback reversed”. Payments from PAID or PARTIALLY REFUNDED state can be chargeback-finalized directly. | initiated |

* **reason** 

  `*required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| The reason that the Payment Gateway provided : either “unauthorized”, “non\_receipt”, “not\_as\_described” or “others”. If this reference is being initialized \(opening chargeback case\), then this parameter is required. | unauthorized |

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

## Signature <a id="signature"></a>

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* pw\_id, if provided
* txn\_id, if provided
* stage
* api\_secret

