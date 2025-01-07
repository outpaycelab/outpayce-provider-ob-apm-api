# Provider API
## Non-Disclosure Agreement Reminder
As Outpayce S.A.U. is part from Amadeus IT Group S.A. all the agreements signed between Amadeus IT Group S.A. and your company are still applicable to all the content available in this [repository](https://github.com/outpaycelab/outpayce-provider-ob-apm-api).
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
  * **Authorization**:This operation will trigger an authorization request on synchronous alternative payment methods (1-step) requiring web-redirection
  * ***Initialization***: This operation will trigger a payment initiation request for a synchronous alternative payment methods – allowing the client to redirect to payment page and complete the payment
  * ***Webhook***: This operation will receive a notification of the final Payment status from the provider and perform futher action
  * ***Inquiry***: This operation will trigger a polling request to provider and retrive the final Payment Status.
  * **Refund**: This operation must be consecutive to a successful authorization & capture, it consists in partially or fully refunding the previously captured amount to the client. Refund can be partial or full depending on the amount.



## Integration
In this repository you will find the necessary documentation prior to integrate into our systems.
1. You can fill the Provider API questionnaire, starting with the Network Connectivity section, as it will allow us to begin the setup as early as possible. [Provider API questionnaire](https://github.com/outpaycelab/outpayce-provider-ob-apm-api/tree/master/questionnaire)
2. You can explore the swagger specification to understand the available paths and data structure. Following this specification you can start developing your code.   
3. Once the development is finished, you can test it using the Postman collection provided. In this collection you will find requests to trigger your server and check if the answers are what expected.   
4. If all the tests are successful you will be able to [share your results with us](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/#sharing-collection-runs) through [_Discussions_](https://github.com/outpaycelab/outpayce-provider-ob-apm-api/discussions/categories/tests).   
5. Once verified, we will set up the connection to your test environments.   
6. Finally, once the connection is certified, we will set up the connection on production.

## Observations
### API Security
Authentication Methods supported in Provider API:
*  ***Basic HTTP Authentication method***: \
With this method, one of the request headers (<ins>*Authorization*</ins>) is populated with a username/password pair, encoded using Base64.

*  ***Transport Layer Security (TLS)***: \
To ensure communication security, the TLS protocol is designed to provide the following three essential services to all applications running above it:
   1. Encryption: A mechanism to obfuscate what is sent from one host to another.
   2. Authentication: A mechanism to verify the validity of provided identification material.
   3. Integrity: A mechanism to detect message tampering and forgery.

   Today we support TLS 1.2 and TLS 1.3 versions.

## Questions
Check the [_Discussions_](https://github.com/outpaycelab/outpayce-provider-ob-apm-api/discussions) tab to ask any questions related to technical or functional topics.

For discussions related to any other topic, the usual channels should be used.
