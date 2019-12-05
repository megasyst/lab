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

Example of notification in WWW data format:

  ad_channel=SYSTEM&carrier=12301&country=XX&currency=XXX&data=trigger+test&event=OTP&id=12345678901234567890&method=SMS&price=0.1&service=MYSERVICE&sn=1234&subscriber=123456789012&subscriber_currency=XXX&subscriber_price=1.0&timestamp=2020-20-20+01%3A01%3A01+%2B0000&trigger=TRIGGER

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
