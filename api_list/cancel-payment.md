## Cancel Payment {#tag-chargeback-payment}

Used to manually cancel a payment that is currently in pending or processing state.

**Method**: POST

**Action**: cancel-payment

### Request {#request}

**Format**: POST data

* **action**
  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| --- | :---: |
| The action of this call, must be hardcoded to “cancel-payment” | cancel-payment |

---

* **timestamp**
  `required` :  **timestamp \(32\)**     

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

* **reason** :  **string \(32\)**     

| **Remark** | **Sample** |
| --- | :---: |
| The reason for the state change, non-mandatory | Buyer cancelled |

---

* ** ref\_tag** :  **string \(32\)**     

| **Remark** | **Sample** |
| --- | :---: |
| The reference of the payment | A12131415 |

---

### Response {#response}

**Format**: JSON

* **status** :  **string \(5\)**

| **Remark** | **Sample** |
| --- | :---: |
| Status of the request. Refer to appendix for list of possible values | 0 |

---

* **message** :  **string \(255\)**

| **Remark** | **Sample** |
| --- | :---: |
| Error message, if any | - |

### Signature {#signature}

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* pw\_id, if provided
* txn\_id, if provided
* reason, if provided
* ref\_tag, if provided
* api\_secret



