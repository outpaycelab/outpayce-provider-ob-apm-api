The Provider API Frontend Notification documentation describes

* **Handling the additional data in Callback Message.
* **Handling the Signature Encryption

### Handling Additional Data:

Post completion of user action on Payment Page to confirm the order, Provider will call back the merchant along with the following additional parameters:

| Sr No. | Naming                     | Sample Value    | Mandatory/Conditional/Optional | Description                           |
|-------|----------------------------|-----------------|------------------------------|---------------------------------------|
| 1     | version                    | v1             | Mandatory                     | Version of the Message                 |
| 2     | status                     | AUTHORIZATION_SUCCESS | Mandatory          | Status of the payment                 |
| 3     | externalId                 | 6767577         | Optional                      | PSP reference of the payment          |
| 4     | paymentAmount              | 123.45          | Mandatory                      | The payment amount specified in minor units (without decimal separator) |
| 5     | paymentCurrency            | EUR            | Mandatory                     | The three-letter capitalized ISO currency code (using ISO 4217) |
| 6     | paymentMerchantReference   | VEPQQBAPPP301474106055 | Mandatory        | Merchant Reference of the payment     |
| 7     | merchantSignature          | 37rd37fjog893hjr234d00und | Mandatory     | The merchant signature in Base64 encoded format |
| 8     | paymentMethod              | Klarna, iDEAL, PayPal, etc | Optional          | Method of payment used               |
| 9     | resultCode                 | 477            | Conditional                   | Error code (Canned Number) in case of failure in payment |

The status field constitutes the following enum values:

* **AUTHORIZATION_SUCCESS
* **AUTHORIZATION_PENDING
* **AUTHORIZATION_FAILURE
* **AUTHORIZATION_CANCELLATION
* **AUTHORIZATON_DENIAL

### Handling Signature Mechanism:

HMAC (SHA256) will compute the signature over the query params (ASCII-sorted) and shared key shared during implementation.

Properties included in the signature:

- externalId
- paymentAmount
- paymentCurrency
- paymentMerchantReference
- paymentMethod
- status
- version
- resultCode

Concatenate all property name/values where:

1. A name/value is separated by an equals (=) sign.
2. Name/value pairs are separated by an ampersand (&) sign.
3. Names are in alphabetical order.

#### Signature Creation Python Script:
The secret key used: 0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF

The signature is to be generated using the HMAC-SHA256 Mechanism.
First, the base string is to be created in the ASCII-sorted and then the same string is to be used to create signature.
(For example,  base string will look like this:
externalId=6767577&paymentAmount=123&paymentCurrency=VND&paymentMerchantReference=VEPQQBAPMB301474106055&paymentMethod=VIETQR&status=AUTHORIZATION_SUCCESS&version=v1)
The generated signature is base64 encoded and passed in the field "merchantSignature".

-------------------------------------------------------------------------------------------------------------------------
import hmac
import hashlib
import base64
import binascii

def buildPayload(post_data):
   return '&'.join(sorted(['='.join(item) for item in post_data.items()]))
post_data = {
    'version':  'v1',
    'paymentAmount': '123',
    'paymentCurrency': 'VND',
    'paymentMerchantReference': 'VEPQQBAPMB301474106055',
    'externalId': '6767577',
    'status': 'AUTHORIZATION_SUCCESS',
    'paymentMethod': 'VIETQR',
}

payload = buildPayload(post_data)
print("payload= ",payload)
secret_key = "0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF"
signature = base64.b64encode(hmac.new(binascii.a2b_hex(secret_key), payload.encode(), hashlib.sha256).digest())
print("signature= ",signature)

-------------------------------------------------------------------------------------------------------------------------

## Questions

Check the [_Discussions_](https://github.com/outpaycelab/outpayce-provider-ob-apm-api/discussions) tab to ask any questions related to technical or functional topics.

For discussions related to any other topic, the usual channels should be used.
