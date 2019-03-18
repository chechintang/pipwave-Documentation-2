## Capture Payment {#capture-payment}

Used to capture credit card payment eg. Adyen if merchant opt for manual capture in payment settings. The capture API will only fired if the transaction is still under AUTHORISATION status.

**Method**: POST

**Action**: capture-payment

### Request {#request} 

**Format**: POST data

* **action**
`required` : &nbsp;**string (32)** 	

|  **Remark** | **Sample** |
| --- | :---: |
| The action of this call, must be hardcoded to “capture-payment” | capture-payment |
    
------------------------------------------------------------------

* **timestamp**
`required` : &nbsp;**timestamp** 	

| **Remark** | **Sample** |
| --- | :---: |
| The timestamp for this API call | - |

------------------------------------------------------------------

* **api_key** 
`required` : &nbsp;**string (32)**
    
| **Remark** | **Sample** |
| --- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |
 
------------------------------------------------------------------
* **pw_id**
`required` : &nbsp;**string (32)**

| **Remark** | **Sample** |
| --- | :---: |
| Pipwave’s transaction reference ID, either this or txn_id must be sent | 123456 |
 
------------------------------------------------------------------
* **txn_id** : &nbsp;**string (255)**

| **Remark** | **Sample** |
| --- | :---: |
| Merchant’s transaction ID, either this or pw_id must be sent | 123456 |



------------------------------------------------------------------
* **capture_amount** : &nbsp;**decimal (11, 2)**

| **Remark** | **Sample** |
| --- | :---: |
| <ul><li>If not provided, full authorised amount will be captured.</li><li>If PG not supporting partial capture, full capture will be done. </li></ul>| - | 

------------------------------------------------------------------
 
### Response {#response}

**Format**: JSON

* **status** : &nbsp;**string (5)**

| **Remark** | **Sample** |
| --- | :---: |
| Status of the request. Refer to appendix for list of possible values | 0 |

------------------------------------------------------------------

* **message** : &nbsp;**string (255)**

| **Remark** | **Sample** |
| --- | :---: |
| Error message, if any | - |


### Signature {#signature}

The data involved in generating the signature for this API are:

*   timestamp
*   action
*   api_key
*   pw_id
*   txn_id, if provided
*   capture_amount, if provided
*   api_secret