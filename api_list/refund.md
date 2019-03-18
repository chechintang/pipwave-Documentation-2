## Refund {#refund}

Used to trigger refund process for a particular pw\_id.

**Method**: POST

**Action**: refund

### Request {#request}

**Format**: POST data

* **action** 
  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| --- | :---: |
| The action of this call, must be hardcoded to “refund” | refund |

---

* **op** 
  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| --- | :---: |
| The sub-action of this call - initiate or submit | initiate |

---

* **timestamp**
  `required` :  **timestamp**

| **Remark** | **Sample** |
| --- | :---: |
| The timestamp for this API call | - |

---

* **api\_key**
  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| --- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

---

* **pw\_id**
  `*required` :  **string \(32\)**

| **Remark** | **Sample** |
| --- | :---: |
| Pipwave’s transaction reference ID, either this or txn\_id must be sent | 123456 |

---

* **txn\_id**
  `*required` :  **string \(255\)**

| **Remark** | **Sample** |
| --- | :---: |
| Merchant’s transaction ID, either this or pw\_id must be sent | 123456 |

---

* **refund\_amount** :  **decimal \(11, 2\)**

| **Remark** | **Sample** |
| --- | :---: |
| If not provided, full refund will be affected | - |

---

* **extra\_param** :  **string \(255\)**

| **Remark** | **Sample** |
| --- | :---: |
| Extra params which is required by payment method to process the refund, in JSON format | - |

---

### Response {#response}

**Format**: JSON

* **status** :  **string \(5\)** 

| **Remark** | **Sample** |
| --- | :---: |
| Status of the request. Refer to appendix for list of possible values. | 200 |

---

* **message** :  **string \(255\)** 

| **Remark** | **Sample** |
| --- | :---: |
| Error message, if any | - |

---

* **supports\_refund** :  **boolean** 

| **Remark** | **Sample** |
| --- | :---: |
| Tells if this transaction supports refund | - |

---

* **supports\_partial\_refund** :  **boolean** 

| **Remark** | **Sample** |
| --- | :---: |
| Tells if this transaction supports partial refund | - |

---

* **extra\_params** :  **array** 

| **Remark** | **Sample** |
| --- | :---: |
| If there is any extra parameters required, this section will be filled up | - |

---

* **reverse\_pw\_id** :  **string \(32\)** 

| **Remark** | **Sample** |
| --- | :---: |
| The refund reference ID from pipwave | - |

---

* **pg\_raw\_data ** :  **string** 

| **Remark** | **Sample** |
| --- | :---: |
| JSON of original PG response | - |

### Signature {#signature}

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* op
* pw\_id, if provided
* txn\_id, if provided
* refund\_amount, if provided
* extra\_param, if provided
* api\_secret



