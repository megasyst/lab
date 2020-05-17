=====================
SMS Response to order
=====================

Merchant should send MT SMS as response to End-user either for One-time payment or Subscription order, related to own service(s) only.
No Bulk SMS sending is allowed!

Every MT SMS should be send via HTTP API by request with authorization token in the header to Megasyst's server.

Request format:
  1. URL part
    - **POST /mailings**
  2. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**
  3. Body part (parameters in WWW serialization format)
    - **body**, text of MT SMS
    - **service**, premium service identifier
    - **subscriber**, end user identifier or MSISDN

Response format:
  1. HTTP response code
    - **200**, if request is processable
    - **403**, if service not found
    - **410**, if subscriber's SMS not found
    - **422**, if request has wrong parameters set
    - **429**, if subscriber was already informed
  2. Body part is JSON object of
    - **status** = **SUCCESSFUL** or **FAILED**
    - **error**, error message (optional)
    
