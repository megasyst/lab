======================
One time payment (OTP)
======================

Order via CLICK, SMS, PIN, USSD
-------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency (not included for billing by MT SMS)
  * **data**, SMS body or other data
  * **event** = **OTP**
  * **flow** = **CLICK** or **PIN** or **MOSMS** or **USSD**
  * **id**, event identifier
  * **keyword**, trigger keyword
  * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
  * **price**, partner earning amount (not included for billing by MT SMS)
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency (not included for billing by MT SMS)
  * **subscriber_price**: end user price (not included for billing by MT SMS)
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)

**Example of notification in WWW data format:** ::


  ad_channel=SYSTEM& carrier=12301& country=XX& currency=XXX& data=trigger+123& event=OTP& flow=MOSMS& id=12345678901234567890& keyword=TRIGGER& need_mt_sms=1& price=0.1& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=123456789012& subscriber_currency=XXX& subscriber_price=1.0& time=2020-01-01+01%3A01%3A01+UTC

MT SMS delivery report for MT based billing
-------------------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency
  * **data**, SMS body or other data
  * **event** = **OTP**
  * **flow** = **MTSMS**
  * **id**, event identifier
  * **keyword**, trigger keyword
  * **price**, partner earning amount
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency
  * **subscriber_price**: end user price
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)

**Example of notification in WWW data format:** ::


  ad_channel=SYSTEM& carrier=12301& country=XX& currency=XXX& data=trigger+123& event=OTP& flow=MTSMS& id=12345678901234567890& keyword=TRIGGER& price=0.1& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=123456789012& subscriber_currency=XXX& subscriber_price=1.0& time=2020-01-01+01%3A01%3A01+UTC
