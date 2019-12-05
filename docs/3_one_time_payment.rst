======================
One time payment (OTP)
======================

Order via CLICK, MO SMS, PIN, USSD
----------------------------------

The platform notificates partners by HTTP with next parameters:
  * **id**, event identifier
  * **timestamp**, integer timestamp
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **event**, (OTP)
  * **trigger**, start keyword
  * **method**, order method (CLICK, PIN, SMS, USSD)
  * **country**, country
  * **carrier**, mobile network
  * **sn**, mobile service number
  * **body**, SMS text
  * **subscriber_id**, end user identifier or MSISDN
  * **subscriber_price**: end user price
  * **subscriber_currency**: end user currency
  * **ad_channel_id**, ad channel identifier (by default: SYSTEM)
  * **service_id**, premium service identifier
  * **price**, partner earning amount (0 for MT based billing)
  * **currency**, partner earning currency

MT SMS delivery report for MT based billing
-------------------------------------------

The platform notificates partners by HTTP with next parameters:
  * **id**, event identifier
  * **timestamp**, integer timestamp
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **event**, (OTP)
  * **trigger**, start keyword
  * **method**, (DLR)
  * **country**, country
  * **carrier**, mobile network
  * **sn**, mobile service number
  * **body**, SMS text
  * **sms_id**, order identifier
  * **subscriber_id**, end user identifier or MSISDN
  * **subscriber_price**: end user price
  * **subscriber_currency**: end user currency
  * **ad_channel_id**, ad channel identifier (by default: SYSTEM)
  * **service_id**, premium service identifier
  * **price**, partner earning amount
  * **currency**, partner earning currency
