# Postman Collection

**What is a Postman collection?**

A Postman collection is a set of predefined requests, each following different paths outlined in the specification. It allows you to test your server configuration, providing detailed information about each request within the Postman app.

## Usage

We recommend importing the Postman collection into the Postman desktop app for access to all functionalities.

1. Download the [Postman app](https://dl.pstmn.io/download/latest/win64).
2. Install the app.
3. Import the files located in the Postman folder.

## Content

Use this tool to test various requests and scenarios while connected to your server. Once all requests are operational, share the report with the results.

### Environment

Complete the environment file with server-related information and payment type details. This can be done through the Postman app or by editing the file. Example values are provided for reference.

### Scenarios

The collection includes the following use cases:

* **Authorization - 1 Step**
  * Positive case
    - 202 Successfully accepted Standard use case
    - 202 Successfully accepted Simple use case

  * Error cases
    - 400 INVALID INPUT PARAM(S) - PLEASE ADJUST REQUEST
    - 400 MISSING REQUIRED INPUT PARAM(S) - PLEASE ADJUST REQUEST
    - 500 INTERNAL PROCESSING ERROR
    - 400 INVALID FORMAT

* **Inquiry/Resumption**
  * Positive case
    - 201 Successfully created Standard use case
    - 201 Successfully created Simple use case
  * Error cases
    - 409 PAYMENT TRANSACTION EXPIRED
    - 502 TIMEOUT ERROR UNKNOWN
    - 424 AUTHORISATION DENIED INSUFFICIENT FUNDS

* **Webhook**

  * Authorization 
  - Successful Authorization
  - Authorization Pending
  - Authorization denial

  * Refund 
  - Refund success
  - Refund failure
  - refund denial


* **Refund**
  * Positive case
    - 201 Successfully created case
  * Error cases
    - 409 PAYMENT TRANSACTION EXPIRED
    - 424 PAYMENT DECLINED
    - 500 SYSTEM UNAVAILABLE

Refer to the collection for detailed information about scenarios and variables.