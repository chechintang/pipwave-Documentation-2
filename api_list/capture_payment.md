# Capture Payment

Used to capture credit card payment eg. Adyen if merchant opt for manual capture in payment settings. The capture API will only fired if the transaction is still under AUTHORISATION status.

**Method**: POST

**Action**: capture-payment

## Request <a id="request"></a>

**Format**: POST data

* **action**

  `required` :  **string \(32\)**     

| **Remark** | **Sample** |
| :--- | :---: |
| The action of this call, must be hardcoded to “capture-payment” | capture-payment |

* **timestamp**

  `required` :  **timestamp**     

| **Remark** | **Sample** |
| :--- | :---: |
| The timestamp for this API call | - |

* **api\_key** 

  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave-assigned merchant’s API key | 123456 |

* **pw\_id**

  `required` :  **string \(32\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Pipwave’s transaction reference ID, either this or txn\_id must be sent | 123456 |

* **txn\_id** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Merchant’s transaction ID, either this or pw\_id must be sent | 123456 |

* **capture\_amount** :  **decimal \(11, 2\)**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Remark</b>
      </th>
      <th style="text-align:center"><b>Sample</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>If not provided, full authorised amount will be captured.</p>
        <p>If PG not supporting partial capture, full capture will be done.</p>
      </td>
      <td style="text-align:center">-</td>
    </tr>
  </tbody>
</table>## Response <a id="response"></a>

**Format**: JSON

* **status** :  **string \(5\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Status of the request. Refer to appendix for list of possible values | 0 |

* **message** :  **string \(255\)**

| **Remark** | **Sample** |
| :--- | :---: |
| Error message, if any | - |

## Signature <a id="signature"></a>

The data involved in generating the signature for this API are:

* timestamp
* action
* api\_key
* pw\_id
* txn\_id, if provided
* capture\_amount, if provided
* api\_secret

