=====================
SMS Response to order
=====================

Partner can send MT SMS as response with information by OTP or subscription order (only for their own premium services).

Usually response messages has limits as 1 free SMS for 1 order of service.

Sending proceeding via the HTTP API on request with an authorization token in the header.

Request format:
  1. URL part
    - **POST /mailings**
  1. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**
  2. Body part (parameters in WWW serialization format)
    - **body**, text of MT SMS
    - **service**, premium service identifier
    - **type** = **OTP** or **SUBSCRIPTION**
    - **subscriber**, end user identifier or MSISDN

Response format:
  1. Header part
    - **HTTP 200**
  2. Body part is JSON object of
    - **status** = **SUCCESSFUL** or **FAILED**
    
