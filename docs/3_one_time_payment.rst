======================
One time payment (OTP)
======================

Order via PIN validation method with JSON API
---------------------------------------------

1. Sending PIN to user

1.1. API request: http://{BASE_URL}/otp/{KEYWORD}.json?subscriber={MSISDN}

    * **KEYWORD**, trigger keyword
    * **MSISDN**, end user identifier or MSISDN
    
1.2. API response (JSON)

    * **ad_channel**, promo channel identifier if exists
    * **carrier**, mobile network (concatenated MCC and MNC)
    * **country**, country (2 uppercase letters)
    * **event** = **OTP**
    * **flow** = **PIN**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **PIN_WAITING**, other values indicate the inability to sending PIN for some reason
    * **status_code**, additional information about operation result (optional)
    * **subscriber**, end user identifier or MSISDN
    
2. Checking PIN and making payment

2.1. API request: http://{BASE_URL}/otp/{KEYWORD}.json?subscriber={MSISDN}&pin={PIN}

    * **KEYWORD**, trigger keyword
    * **MSISDN**, end user identifier or MSISDN
    * **PIN**, PIN code from the SMS which was sent by phase 1
    
2.2. API response (JSON)

    * **ad_channel**, promo channel identifier if exists
    * **carrier**, mobile network (concatenated MCC and MNC)
    * **country**, country (2 uppercase letters)
    * **event** = **OTP**
    * **flow** = **PIN**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL**, other values indicate the inability to subscribe for some reason
    * **status_code**, additional information about operation result (optional)
    * **subscriber**, end user identifier or MSISDN
    
3. Megasyst additionally notificates merchant by HTTP with following parameters

 * **ad_channel**, ad channel identifier (by default: SYSTEM)
 * **carrier**, mobile network
 * **country**, country
 * **currency**, partner earning currency (not included for billing by MT SMS)
 * **data**, SMS body or other data
 * **event** = **OTP**
 * **flow** = **PIN**
 * **id**, event identifier
 * **keyword**, trigger keyword
 * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
 * **price**, partner earning amount (not included for billing by MT SMS)
 * **service**, premium service identifier
 * **sn**, mobile service number
 * **status** = **SUCCESSFUL** (if funds should be deducted but not deducted then **FAILED** or **WAITING**)
 * **subscriber**, end user identifier or MSISDN
 * **subscriber_currency**: end user currency (not included for billing by MT SMS)
 * **subscriber_price**: end user price (not included for billing by MT SMS)
 * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)

 Example::
 
 ad_channel=SYSTEM& 
 carrier=12301& 
 country=XX& 
 currency=XXX& 
 data=keyword123& 
 event=OTP& 
 flow=PIN& 
 id=12345678901234567890& 
 keyword=KEYWORD& 
 need_mt_sms=1& 
 price=0.1& 
 service=MYSERVICE& 
 sn=1234& 
 status=SUCCESSFUL& 
 subscriber=123456789012& 
 subscriber_currency=XXX& 
 subscriber_price=1.0& 
 time=2020-01-01+01%3A01%3A01+UTC

Order via SMS, USSD
-------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency (not included for billing by MT SMS)
  * **data**, SMS body or other data
  * **event** = **OTP**
  * **flow** = **CLICK** or **PIN** or **SMS** or **USSD**
  * **id**, event identifier
  * **keyword**, trigger keyword
  * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
  * **price**, partner earning amount (not included for billing by MT SMS)
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = **SUCCESSFUL** (if funds should be deducted but not deducted then **FAILED** or **WAITING**)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency (not included for billing by MT SMS)
  * **subscriber_price**: end user price (not included for billing by MT SMS)
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)

**Example of notification in WWW data format:** ::

  ad_channel=SYSTEM& 
  carrier=12301& 
  country=XX& 
  currency=XXX& 
  data=keyword+123& 
  event=OTP& 
  flow=SMS& 
  id=12345678901234567890& 
  keyword=KEYWORD& 
  need_mt_sms=1& 
  price=0.1& 
  service=MYSERVICE& 
  sn=1234& 
  status=SUCCESSFUL& 
  subscriber=123456789012& 
  subscriber_currency=XXX& 
  subscriber_price=1.0& 
  time=2020-01-01+01%3A01%3A01+UTC

MT SMS delivery report for MT based billing
-------------------------------------------

The platform notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, partner earning currency
  * **data**, SMS body or other data
  * **event** = **OTP**
  * **flow** = **SMS**
  * **id**, event identifier
  * **keyword**, trigger keyword
  * **order**, id of OTP order
  * **price**, partner earning amount
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = **FAILED** or **SUCCESSFUL** or **WAITING** (based on MT SMS delivery status)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency
  * **subscriber_price**: end user price
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)

**Example of notification in WWW data format:** ::

  ad_channel=SYSTEM& 
  carrier=12301& 
  country=XX& 
  currency=XXX& 
  data=keyword+123& 
  event=OTP& 
  flow=SMS& 
  id=12345678901234567890& 
  keyword=KEYWORD& 
  price=0.1& 
  service=MYSERVICE& 
  sn=1234& 
  status=SUCCESSFUL& 
  subscriber=123456789012& 
  subscriber_currency=XXX& 
  subscriber_price=1.0& 
  time=2020-01-01+01%3A01%3A01+UTC
