=====================
SMS Response to order
=====================

Merchant should send MT SMS as response to End-user either for One-time payment or Subscription order, related to own service(s) only.

Usually MT SMS has limits as 1 free SMS for 1 order of service.

No Bulk SMS sending is allowed!

Every MT SMS should be send via HTTP API by request with authorization token in the header.

Request format:
  1. URL part
    - **POST /mailings**
  1. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**
  2. Body part (parameters in WWW serialization format)
    - **body**, text of MT SMS
    - **service**, premium service identifier
    - **subscriber**, end user identifier or MSISDN

Response format:
  1. Header part
    - **HTTP 200**
  2. Body part is JSON object of
    - **status** = **SUCCESSFUL** or **FAILED**
    
