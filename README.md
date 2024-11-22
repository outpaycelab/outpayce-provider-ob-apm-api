# Provider API
## Non-Disclosure Agreement Reminder
As Outpayce S.A.U. is part from Amadeus IT Group S.A. all the agreements signed between Amadeus IT Group S.A. and your company are still applicable to all the content available in this [repository]().
## Introduction
The Provider API is a modern REST API for any payment provider needing to connect to Outpayce Xchange Payment Platform. 
In this repository, you will find:
* **Swagger specification**: API definition, its paths and components.
* **Test cases**:  a group of requests to test your configuration using the Postman app.
* **Provider questionnaire**: an excel file containing general and functional questions to better understand the capabilities you support. This file also includes a Network and technical section which will allow us to setup the connectivity between you and Amadeus. 

You will find more information about each of them in their specific folder.
## Context
### Prerequisites
* Connectivity with Amadeus
* Security rights to perform the operations
### Scope
This API covers authorization, reversal, capture and refund operations for Credit Card payments:
  * **Authorization**: This operation will trigger an authorization request on a credit card – various schemes are supported, you can also send extra information as external 3DS data or flight data.
  * **Reversal**: This operation will reverse a previous authorization. It can only be requested for a previously successful authorization. It can be performed for a partial or full amount.
  * **Capture**: This operation will trigger a capture request. It can only be requested for a previously successful authorization request. It can be performed for a partial or full amount.
  * **Refund**: This operation must be consecutive to a successful capture, it consists in partially or fully refunding the previously captured amount to the client. Refund can be partial or full depending on the amount.

 
  
## Integration steps
#### Please follow the differents steps in the table and update their status accordingly. 

| Steps           | Description   |  Status       | 
|----------------|---------------|---------------|
| 1    | Fill the Provider API questionnaire, starting with the Network Connectivity section, as it will allow us to begin the setup as early as possible. [Provider API questionnaire]() | Uncompleted.  | 
| 2    | You can explore the swagger specification to understand the available paths and data structure. Available user guide [here](). Following this specification you can start developing your code.  | Uncompleted. |   
| 3    |  Once the development is finished, you can test it using the Postman collection provided [here](). In this collection you will find requests to trigger your server and check if the answers are what expected. | Uncompleted. |   
| 4    | Unlock the certification phase by sharing your results with us (see note below) in a json file, through test section in [Discussion](). | Uncompleted. |   
| 5    | Once verified, we'll start the certification phase according to the scope filled in the psp questionnaire (vendors, currencies, operation supported, etc).|Uncompleted.  |
| 6    | In parallel, connectivity in test environment will be set up |Uncompleted. |
| 7    | Once connectivity set up is done, E2E testing phase will be executed. |Uncompleted. |
| 8    | Finally, once provider plugin is certified, and E2E flows working on every operation, we will set up the connection on production. |Uncompleted. | 

**Note**: _On step 4, the results expected are a report of the execution of the positive and negative test cases of the sandbox collection, for 1 vendor, 1 currencie. Other vendors and currencies will be covered during the certification phase._

_Please refer to the [collection documentation](https://github.com/outpaycelab/outpayce-provider-nexi-api/tree/main/testcases-postman/collection/) in Postman for 3ds cases specificities (if part of your scope)._

## API Authentication & Security

### Transport Layer Security (TLS):
To ensure communication security, the TLS protocol is designed to provide the following three essential services to all applications running above it:

Encryption: A mechanism to obfuscate what is sent from one host to another. <br>
Authentication: A mechanism to verify the validity of provided identification material.<br>
Integrity: A mechanism to detect message tampering and forgery.<br>
<br>Today Outpayce supports TLS 1.2 and TLS 1.3 versions.<br>


**NB:** For stronger security, **MTLS** (mutual TLS) can be implemented which is the usecase where both communicators have TLS certificate. We also provide IP whitelisting to restrict unauthorized access to the Outpayce system for inbound flow..

### API Authentication:
The authemtications method supported by provider API today are:

#### - Basic HTTP Authentication method:
With this method, one of the request header Authorization is populated with a username/password pair, encoded using Base64.
```` 
Host: <your_host>
Content-Type: application/vnd.amadeus+json 
Authorization: Basic YOUR_CREDENTIALS
````
 ```` YOUR_CREDENTIALS ```` is the BASE_64 combination of your username and password separeted by a colon ````:```` .
 
#### - 0auth:
When using 0Auth, the request header Authorization is populated with the JWT token.
````
Host: <your_host>
Content-Type: application/vnd.amadeus+json 
Authorization: Bearer <JWT_Token>
````
````JWT_Token```` is the token provided and managed by your authorization server after we properly registered to your system and got it with the dedicated endpoint you will expose to us.

#### - API KEY:
When using API key, the request header Authorization is populated with the key previously obtained through the provider system.
````
Host: <your_host>
Content-Type: application/vnd.amadeus+json 
Authorization: <API_KEY>
````

### Timeout Handling

The proposed request timeout is ````30 seconds````.

## Questions
Check the [_Discussions_]() tab to ask any questions related to technical or functional topics.

For discussions related to any other topic, the usual channels should be used.
