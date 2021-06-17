======================
One time payment (OTP)
======================

Starting payment process on PIN flow
------------------------------------

Common steps:
  1. User wants to pay the premium service on merchant's landing page or in app;
  2. User redirects to http://{BASE_URL}/start/{KEYWORD}?{YOUR_CUSTOM_PARAMS};
  3. User inputs its MSISDN and selects its network in a web form and click a button to send a confirmation code (this step can be skipped if YOUR_CUSTOM_PARAMS has **subscriber** and **carrier** parameters);
  4. User inputs its code from SMS in a web form and click a button to confirm the payment process (this step can be skipped for JSON requests with **pin** parameter in YOUR_CUSTOM_PARAMS);
  5. Megasyst's platform checks the confirmation code on http://{BASE_URL}/callback (with **pin** parameter)
  6. Megasyst's platform redirects user to the callback URL of the service with YOUR_CUSTOM_PARAMS and result parameters (for JSON requests these data returns directly without redirect):
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`
    * **country**, country
    * **event** = **OTP**
    * **flow** = **PIN**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL**, other values indicate the inability to subscribe for some reason
    * **status_code**, additional information about operation result (optional)
    * **subscriber**, end user identifier or MSISDN

**YOUR_CUSTOM_PARAMS** can contains any parameters that you wish to see in asynchronous notifications in **data** parameter, also it can contains custom **callback** or **callback_on_error** URLs.

  Example::
 
    ad_channel=SYSTEM& 
    carrier=12345& 
    country=XX& 
    event=OTP& 
    flow=PIN& 
    id=12345678901234567890& 
    keyword=TRIGGER& 
    service=MYSERVICE& 
    status=SUCCESSFUL& 
    subscriber=12345678900

  6. Megasyst notificates merchant by HTTP with following parameters:
  
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
