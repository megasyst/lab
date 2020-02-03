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
    * **event** = SUBSCRIPTION
    * **id**, event identifier
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **subscriber**, end user identifier or MSISDN
    * **trigger_flow**, order method (CLICK)
    * **trigger_keyword**, normalized keyword
   
  Example::
 
    ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&id=12345678901234567890&service=ABC&status=SUCCESSFUL&subscriber=12345678900&trigger_flow=CLICK&trigger_keyword=ABC
5. Megasyst's platform sends Welcome SMS with service information to user;     

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
    * **event** = SUBSCRIPTION
    * **id**, event identifier
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **subscriber**, end user identifier or MSISDN
    * **trigger_flow**, order method (PIN)
    * **trigger_keyword**, normalized keyword
   
  Example::
  
     ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&id=12345678901234567890&service=ABC&status=SUCCESSFUL&subscriber=12345678900&trigger_flow=PIN&trigger_keyword=ABC
     
  6. Megasyst's platform sends Welcome SMS with service information to user;  


Starting subscription via SMS flow (MO/MT SMS)
----------------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page or in app;
  2. User sends SMS with a keyword to a short number;
  3. Megasyst notificates merchant by HTTP with following parameters:
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, mobile carrier/network operator
    * **country**, country
    * **event** = SUBSCRIPTION
    * **free_period**, free time for using the premium service in seconds
    * **id**, event identifier
    * **renewal_period**, period of time for renew the premium subscription service
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status**, SUCCESSFUL (also could be following statuses: FAILED | WAITING)
    * **subscriber**, end user identifier or MSISDN
    * **trigger_data**, raw keyword or SMS body
    * **trigger_flow** = SMS
    * **trigger_keyword**, normalized keyword
    * **trigger_time**, integer timestamp
 
  Example::
 
     ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&free_period=86400&id=12345678901234567890&renewal_period=86400&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&subscription=12345678901234567890&trigger_data=abc+123&trigger_flow=SMS&trigger_keyword=ABC&trigger_time=2020-01-01+01%3A01%3A01+UTC
   
  4. Megasyst's platform sends SMS to user Welcome SMS with service information;

  
Renewal of subscription
--------------------

Megasyst notificates merchants by HTTP with following parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **currency**, currency of reward
  * **event** = RENEWAL
  * **id**, event identifier
  * **price**, reward amount
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = SUCCESSFUL (also could be following statuses: FAILED | WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**, currency of end user price
  * **subscriber_price**, end user price
  * **subscription**, id of subscription order
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = CLICK | PIN | SMS
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp
  
  Example::
  
    ad_channel=SYSTEM&carrier=12345&country=XX&currency=XXX&event=RENEWAL&id=12345678901234567891&price=1.23&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&subscriber_currency=XXX&subscriber_price=2.34&subscription=12345678901234567890&trigger_data=abc+123&trigger_flow=SMS&trigger_keyword=ABC&trigger_time=2020-01-01+01%3A01%3A01+UTC


Deactivation of subscription
------------------------
User may stop/deactivate active subscription at any time.
Megasyst notificates partners by HTTP with next parameters:
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = UNSUBSCRIPTION
  * **id**, event identifier
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = SUCCESSFUL (also could be following statuses: FAILED | WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = CLICK | PIN | SMS
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp

  Example::

    ad_channel=SYSTEM&carrier=12345&country=XX&event=UNSUBSCRIPTION&id=12345678901234567892&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&trigger_data=stop+abc&trigger_flow=SMS&trigger_keyword=STOP&trigger_time=2020-01-01+01%3A01%3A01+UTC

Megasyst's platform sends SMS to user with information about stop of active subscription service.
