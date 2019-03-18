# Payment Data Code

## CVV codes <a id="cvv-codes"></a>

| Status | Description |
| :--- | :--- |
| M | Match |
| N | Not match |
| P | Not processed |
| S | Not present |
| U | Issuer unable to process |
| Y | Not provided |

## AVS codes <a id="avs-codes"></a>

| Status | Description |
| :--- | :--- |
| Y | Address and ZIP match |
| A | Address match, ZIP not match |
| S | Not supported |
| R | System unavailable, please retry |
| U | Information unavailable |
| Z | Address not match, ZIP match |
| N | Address and ZIP not match |
| W | MASTERCARD Address match, ZIP not match |
| X | MASTERCARD address and ZIP match |
| B | VISA address match, ZIP not verified |
| P | VISA address not verified, ZIP match |
| C | VISA address and ZIP not verified |
| D | VISA address and ZIP match, international |
| G | VISA address not verified, international transaction |
| I | VISA address not verified, international |
| M | VISA address and ZIP match, international |
| F | VISA address and ZIP match, UK |
| T | DISCOVER address not match, ZIP match |

## 3D Secure codes <a id="threeds-codes"></a>

| Status | Description |
| :--- | :--- |
| 10 | Successfully authenticated |
| 0 | Authentication failed |
| 5 | Buyer / bank not enrolled to 3D Secure |

