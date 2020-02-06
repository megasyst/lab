===========
SMS sending
===========

Partner can send next types of informational MT SMS:
  1. As response with information by OTP or subscription order
  2. As premium mailing

Response to order
-----------------

Partner can send MT SMS via HTTP API by request with authorization token in the header.

Partner can send messages to subscribers only for their own premium services.

Usually response messages has limits as 1 free SMS for 1 order of service.

Request format:
  1. URL part
    - POST /mailing
  1. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**
  2. Body part (parameters in WWW serialization format)
    - **body**, text of MT SMS
    - **service**, premium service identifier
    - **subscriber**, end user identifier or MSISDN

Premium mailing
---------------

Premium mailing is payable from partner's account.
