======================
One time payment (OTP)
======================

Order via CLICK, MO SMS, PIN, USSD
----------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency
  * **data**, SMS text
  * **event**, (OTP)
  * **id**, event identifier
  * **method**, order method (CLICK, PIN, SMS, USSD)
  * **price**, partner earning amount (0 for MT based billing)
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency
  * **subscriber_price**: end user price (0 for MT based billing)
  * **timestamp**, integer timestamp
  * **trigger**, start keyword

MT SMS delivery report for MT based billing
-------------------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency
  * **data**, SMS text
  * **event**, (OTP)
  * **id**, event identifier
  * **method**, order method (DLR)
  * **price**, partner earning amount
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency
  * **subscriber_price**: end user price
  * **timestamp**, integer timestamp
  * **trigger**, start keyword
