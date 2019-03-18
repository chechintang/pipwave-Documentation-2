# API Status Code

| API Code | Reason |
| :--- | :--- |
| 200 | OK |
| 400 | Failed to fulfill request, see message |
| 401 | Invalid API signature |
| 403 | Invalid API key |
| 404 | Invalid action |
| 500 | Generic server error, see message |
| 1001 | Currency not offered by Merchant |
| 1002 | Transaction ID \(txn\_id\) duplicate |
| 2001 | Unsupported payment method, see message |
| 2002 | Token has expired |
| 3001 | Notification with warning \(see pw\_reason data\) |
| 4001 | Payment is already fully refunded |
| 4002 | Payment not finalized yet |
| 4003 | Refunded amount is more than current amount |
| 4004 | Refund not supported |
| 4005 | Partial refund not supported |
| 4006 | The transaction already has a reversal in process. You must wait for the process to complete first. |
| 4501 | No disputed chargeback transaction to reversed |
| 9001 | Parameter error, see message |

