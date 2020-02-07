=====================
Mobile Subscriptions
=====================

We divide subscription's activation process on 3 flows: 
  1. Click flow, also known as HE flow, 3G flow or WAP flow;
  2. PIN flow, also known as PIN-submit or WEB flow or App flow;
  3. SMS flow, also known as SMS MO flow, SMS MT flow , SMS flow or App flow;


Starting subscription on Click flow
-----------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page;
  2. User redirects to http://pay.megasyst.com/start/{KEYWORD}?{ANY_PREMIUM_SERVICE_CUSTOM_PARAMS};
  3. User accepts subscription service terms and conditions by clicking confirmation button;
  4. Megasyst's platform redirects user to the callback URL of the service with ANY_PREMIUM_SERVICE_CUSTOM_PARAMS and result parameters:
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **event** = **SUBSCRIPTION**
    * **flow** = **CLICK**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **subscriber**, end user identifier or MSISDN
   
  Example::
 
    ad_channel=SYSTEM& carrier=12345& country=XX& event=SUBSCRIPTION& flow=CLICK& id=12345678901234567890& keyword=KEYWORD& service=MYSERVICE& status=SUCCESSFUL& subscriber=12345678900

  5. Megasyst notificates merchant by HTTP with following parameters:
  
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, order request data
    * **event** = **SUBSCRIPTION**
    * **flow** = **CLICK**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **price**, partner earning amount (not included if payment is separate)
    * **renewal_period**, period of time for renew the premium subscription service (in seconds)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& carrier=12345& country=XX& currency=XXX& data=keyword& event=SUBSCRIPTION& flow=CLICK& free_period=86400& id=12345678901234567890& keyword=KEYWORD& price=0.1& renewal_period=86400& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=12345678900& subscriber_currency=XXX& subscriber_price=0.1& time=2020-01-01+01%3A01%3A01+UTC

  6. User receives confirmation SMS with subscription service information.

Starting subscription on PIN flow
-----------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page or in app;
  2. User redirects to http://pay.megasyst.com/start/{KEYWORD}?{ANY_PREMIUM_SERVICE_CUSTOM_PARAMS};
  3. User inputs its MSISDN in a web form and click a button to send a confirmation code;
  4. User inputs its code from SMS in a web form and click a button to confirm the subscription process;
  5. Megasyst's platform redirects user to the callback URL of the service with ANY_PREMIUM_SERVICE_CUSTOM_PARAMS and result parameters:
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **event** = **SUBSCRIPTION**
    * **flow** = **PIN**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **subscriber**, end user identifier or MSISDN
   
  Example::
 
    ad_channel=SYSTEM& carrier=12345& country=XX& event=SUBSCRIPTION& flow=PIN& id=12345678901234567890& keyword=TRIGGER& service=MYSERVICE& status=SUCCESSFUL& subscriber=12345678900

  6. Megasyst notificates merchant by HTTP with following parameters:
  
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, order request data
    * **event** = **SUBSCRIPTION**
    * **flow** = **PIN**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **price**, partner earning amount (not included if payment is separate)
    * **renewal_period**, period of time for renew the premium subscription service (in seconds)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& carrier=12345& country=XX& currency=XXX& data=trigger& event=SUBSCRIPTION& flow=PIN& free_period=86400& id=12345678901234567890& keyword=TRIGGER& price=0.1& renewal_period=86400& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=12345678900& subscriber_currency=XXX& subscriber_price=0.1& time=2020-01-01+01%3A01%3A01+UTC
     
  7. User receives confirmation SMS with subscription service information.


Starting subscription via SMS flow (MO SMS)
----------------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page or in app;
  2. User sends SMS with a keyword to a short number;
  3. Megasyst notificates merchant by HTTP with following parameters:

    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, SMS body
    * **event** = **SUBSCRIPTION**
    * **flow** = **MOSMS**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **price**, partner earning amount (not included if payment is separate)
    * **renewal_period**, period of time for renew the premium subscription service (in seconds)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& carrier=12345& country=XX& currency=XXX& data=trigger+123& event=SUBSCRIPTION& flow=MOSMS& free_period=86400& id=12345678901234567890& keyword=TRIGGER& price=0.1& renewal_period=86400& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=12345678900& subscriber_currency=XXX& subscriber_price=0.1& time=2020-01-01+01%3A01%3A01+UTC

  4. User receives confirmation SMS with service subscription information.

  
Renewal of subscription
-----------------------

Megasyst notificates merchants by HTTP with following parameters:

    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **currency**, partner earning currency
    * **data**, SMS body or other data
    * **event** = **RENEWAL**
    * **flow** = **CLICK** or **MOSMS** or **MTSMS** or **PIN** or **USSD**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **price**, partner earning amount
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency
    * **subscriber_price**: end user price
    * **subscription**, id of subscription order
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& carrier=12345& country=XX& currency=XXX& data=trigger+123& event=RENEWAL& flow=MOSMS& id=12345678901234567891& keyword=TRIGGER& price=0.1& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=12345678900& subscriber_currency=XXX& subscriber_price=0.1& subscription=12345678901234567890& time=2020-01-01+01%3A01%3A01+UTC

In case of subscription renewal, user could be notified with SMS, however it depends on the exact carrier(s) subscription rules.

Deactivation of subscription
------------------------
User may stop/deactivate active subscription at any time.
Megasyst notificates partners by HTTP with next parameters:

    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile network
    * **country**, country
    * **data**, SMS body
    * **event** = **UNSUBSCRIPTION**
    * **flow** = **MOSMS**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **FAILED** or **SUCCESSFUL** or **WAITING**
    * **subscriber**, end user identifier or MSISDN
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& carrier=12345& country=XX& data=trigger+123& event=UNSUBSCRIPTION& flow=MOSMS& id=12345678901234567890& keyword=TRIGGER& service=MYSERVICE& sn=1234& status=SUCCESSFUL& subscriber=12345678900& time=2020-01-01+01%3A01%3A01+UTC

User receives confirmation SMS about unsubscription.
