.. _mobile network: https://megasyst.readthedocs.io/en/latest/1_common.html#carrier-identifiers

=====================
Mobile Subscriptions
=====================

We divide subscription's activation process on 3 flows: 
  1. Click flow, also known as HE flow, 3G flow or WAP flow;
  2. PIN flow, also known as PIN-submit or WEB flow or App flow;
  3. SMS flow, also known as SMS MO flow, SMS MT flow , SMS flow or App flow;

You can use URL with **.html** or **.json** suffix.

Starting subscription on Click flow
-----------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page;
  2. User redirects to http://{BASE_URL}/start/{KEYWORD}?{YOUR_CUSTOM_PARAMS};
  3. User accepts subscription service terms and conditions by clicking confirmation button;
  4. Megasyst's platform checks the confirmation parameters on http://{BASE_URL}/callback
  5. Megasyst's platform redirects user to the callback URL of the service with YOUR_CUSTOM_PARAMS and result parameters (for JSON requests these data returns directly without redirect):
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`_
    * **country**, country
    * **event** = **SUBSCRIPTION**
    * **flow** = **CLICK**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **status_code**, additional information about operation result (optional)
    * **subscriber**, end user identifier or MSISDN

**YOUR_CUSTOM_PARAMS** can contains any parameters that you wish to see in asynchronous notifications in **data** parameter, also it can contains custom **callback** or **callback_on_error** URLs.

  Example::
 
    ad_channel=SYSTEM& 
    carrier=12345& 
    country=XX& 
    event=SUBSCRIPTION& 
    flow=CLICK& 
    id=12345678901234567890& 
    keyword=KEYWORD& 
    service=MYSERVICE& 
    status=SUCCESSFUL& 
    subscriber=12345678900

  5. Megasyst notificates merchant by HTTP with following parameters:
  
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`_
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, order request data in format "{KEYWORD}?{YOUR_CUSTOM_PARAMS}"
    * **event** = **SUBSCRIPTION**
    * **flow** = **CLICK**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **ip**, end user IP address
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **previous_order**, previous order identifier if it exists
    * **price**, partner earning amount (not included if payment is separate)
    * **payment_schedule**, period of time for renew the premium subscription service (EVERYDAY, EVERYWEEK, WORKDAYS or other string value)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **SUCCESSFUL** (other values indicate the inability to subscribe for some reason)
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
    * **user_agent**, end user browser agent
 
  Example::
 
     ad_channel=SYSTEM& 
     carrier=12345& 
     country=XX& 
     currency=XXX& 
     data=KEYWORD?your=custom_param& 
     event=SUBSCRIPTION& 
     flow=CLICK& 
     free_period=86400& 
     id=12345678901234567890& 
     ip=1.2.3.4& 
     keyword=KEYWORD& 
     price=0.1& 
     payment_schedule=EVERYDAY& 
     service=MYSERVICE& 
     sn=1234& 
     status=SUCCESSFUL& 
     subscriber=12345678900& 
     subscriber_currency=XXX& 
     subscriber_price=0.1& 
     time=2020-01-01+01%3A01%3A01+UTC
     user_agent=Mozilla/5.0+(Macintosh;+Intel+Mac+OS+X+10_15_5)+AppleWebKit/605.1.15+(KHTML,+like+Gecko)
     
  6. User receives confirmation SMS with subscription service information.

Starting subscription on PIN flow
-----------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page or in app;
  2. User redirects to http://{BASE_URL}/start/{KEYWORD}?{YOUR_CUSTOM_PARAMS};
  3. User inputs its MSISDN and selects its network in a web form and click a button to send a confirmation code (this step can be skipped if YOUR_CUSTOM_PARAMS has **subscriber** and **carrier** parameters);
  4. User inputs its code from SMS in a web form and click a button to confirm the subscription process (this step can be skipped for JSON requests with **pin** parameter in YOUR_CUSTOM_PARAMS);
  5. Megasyst's platform checks the confirmation code on http://{BASE_URL}/callback (with **pin** parameter)
  6. Megasyst's platform redirects user to the callback URL of the service with YOUR_CUSTOM_PARAMS and result parameters (for JSON requests these data returns directly without redirect):
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`_
    * **country**, country
    * **event** = **SUBSCRIPTION**
    * **flow** = **PIN**
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **service**, premium service identifier
    * **status** = **SUCCESSFUL** or **ALREADY_SUBSCRIBED**, other values indicate the inability to subscribe for some reason
    * **status_code**, additional information about operation result (optional)
    * **subscriber**, end user identifier or MSISDN

**YOUR_CUSTOM_PARAMS** can contains any parameters that you wish to see in asynchronous notifications in **data** parameter, also it can contains custom **callback** or **callback_on_error** URLs.

  Example::
 
    ad_channel=SYSTEM& 
    carrier=12345& 
    country=XX& 
    event=SUBSCRIPTION& 
    flow=PIN& 
    id=12345678901234567890& 
    keyword=TRIGGER& 
    service=MYSERVICE& 
    status=SUCCESSFUL& 
    subscriber=12345678900

  6. Megasyst notificates merchant by HTTP with following parameters:
  
    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`_
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, order request data in format "{KEYWORD}?{YOUR_CUSTOM_PARAMS}"
    * **event** = **SUBSCRIPTION**
    * **flow** = **PIN**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **ip**, end user IP address
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **previous_order**, previous order identifier if it exists
    * **price**, partner earning amount (not included if payment is separate)
    * **payment_schedule**, period of time for renew the premium subscription service (EVERYDAY, EVERYWEEK, WORKDAYS or other string value)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **SUCCESSFUL** (other values indicate the inability to subscribe for some reason)
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
    * **user_agent**, end user browser agent

  Example::
 
     ad_channel=SYSTEM& 
     carrier=12345& 
     country=XX& 
     currency=XXX& 
     data=TRIGGER?your=custom_param_value& 
     event=SUBSCRIPTION& 
     flow=PIN& 
     free_period=86400& 
     id=12345678901234567890& 
     ip=1.2.3.4& 
     keyword=TRIGGER& 
     price=0.1& 
     payment_schedule=EVERYDAY& 
     service=MYSERVICE& 
     sn=1234& 
     status=SUCCESSFUL& 
     subscriber=12345678900& 
     subscriber_currency=XXX& 
     subscriber_price=0.1& 
     time=2020-01-01+01%3A01%3A01+UTC
     user_agent=Mozilla/5.0+(Macintosh;+Intel+Mac+OS+X+10_15_5)+AppleWebKit/605.1.15+(KHTML,+like+Gecko)

  7. User receives confirmation SMS with subscription service information.


Starting subscription via SMS flow (MO SMS)
----------------------------------------------

Common steps:
  1. User wants to subscribe the premium service on merchant's landing page or in app;
  2. User sends SMS with a keyword to a short number;
  3. Megasyst notificates merchant by HTTP with following parameters:

    * **ad_channel**, ad channel identifier (by default: SYSTEM)
    * **carrier**, `mobile network`_
    * **country**, country
    * **currency**, partner earning currency (not included if payment is separate)
    * **data**, SMS body
    * **event** = **SUBSCRIPTION**
    * **flow** = **SMS**
    * **free_period**, free time for using the premium service (in seconds)
    * **id**, event identifier
    * **keyword**, trigger keyword
    * **need_mt_sms** = **1** (if this order needs additional MT SMS from partner)
    * **previous_order**, previous order identifier if it exists
    * **price**, partner earning amount (not included if payment is separate)
    * **payment_schedule**, period of time for renew the premium subscription service (EVERYDAY, EVERYWEEK, WORKDAYS or other string value)
    * **service**, premium service identifier
    * **sn**, mobile service number
    * **status** = **SUCCESSFUL** (other values indicate the inability to subscribe for some reason)
    * **subscriber**, end user identifier or MSISDN
    * **subscriber_currency**: end user currency (not included if payment is separate)
    * **subscriber_price**: end user price (not included if payment is separate)
    * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
  Example::
 
     ad_channel=SYSTEM& 
     carrier=12345& 
     country=XX& 
     currency=XXX& 
     data=trigger+123& 
     event=SUBSCRIPTION& 
     flow=SMS& 
     free_period=86400& 
     id=12345678901234567890& 
     keyword=TRIGGER& 
     price=0.1& 
     payment_schedule=EVERYDAY& 
     service=MYSERVICE& 
     sn=1234& 
     status=SUCCESSFUL&
     subscriber=12345678900& 
     subscriber_currency=XXX& 
     subscriber_price=0.1& 
     time=2020-01-01+01%3A01%3A01+UTC

  4. User receives confirmation SMS with service subscription information.

  
Renewal of subscription
-----------------------

Megasyst notificates merchants by HTTP with following parameters:

  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, `mobile network`_
  * **country**, country
  * **currency**, partner earning currency
  * **delay** = **DELAYED** (presents only if payment was postponed)
  * **data**, same data from the subscription order
  * **event** = **RENEWAL**
  * **flow** = **CLICK** or **PIN** or **SMS** or **USSD**
  * **id**, event identifier
  * **ip**, end user IP address (if it's known)
  * **keyword**, trigger keyword
  * **order**, id of subscription order
  * **previous_order**, previous order identifier if it exists
  * **price**, partner earning amount
  * **service**, premium service identifier
  * **share** = **FULL** or **PART** (presents only for successful payments)
  * **sn**, mobile service number
  * **status** = **SUCCESSFUL** (if funds are not deducted then FAILED or WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **subscriber_currency**: end user currency
  * **subscriber_price**: end user price
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
  * **user_agent**, end user browser agent (if it's known)
 
Example::
 
   ad_channel=SYSTEM& 
   carrier=12345& 
   country=XX& 
   currency=XXX& 
   data=trigger+123& 
   event=RENEWAL& 
   flow=MOSMS& 
   id=12345678901234567891& 
   keyword=TRIGGER& 
   order=12345678901234567890& 
   price=0.1& 
   service=MYSERVICE& 
   sn=1234& 
   status=SUCCESSFUL& 
   subscriber=12345678900& 
   subscriber_currency=XXX& 
   subscriber_price=0.1& 
   time=2020-01-01+01%3A01%3A01+UTC

In case of subscription renewal, user could be notified with SMS, however it depends on the exact carrier(s) subscription rules.

Deactivation of subscription
----------------------------
User may stop/deactivate active subscription at any time.
Megasyst notificates partners by HTTP with next parameters:

  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, `mobile network`_
  * **country**, country
  * **data**, SMS body or URL with parameters
  * **event** = **UNSUBSCRIPTION**
  * **flow** = **SMS**
  * **id**, event identifier
  * **keyword**, trigger keyword
  * **previous_order**, previous order identifier if it exists
  * **previous_order_data**, SMS body or URL with parameters if it exists
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = **SUCCESSFUL** (other values indicate the inability to stop subscription for some reason)
  * **subscriber**, end user identifier or MSISDN
  * **time**, time string (YYYY-MM-DD HH:MM\:SS UTC)
 
Example::
 
   ad_channel=SYSTEM& 
   carrier=12345& 
   country=XX& 
   data=trigger+123& 
   event=UNSUBSCRIPTION& 
   flow=SMS& 
   id=12345678901234567892& 
   keyword=TRIGGER& 
   previous_order=12345678901234567890& 
   service=MYSERVICE& 
   sn=1234& 
   status=SUCCESSFUL& 
   subscriber=12345678900& 
   time=2020-01-01+01%3A01%3A01+UTC

User receives confirmation SMS about unsubscription.

Subcriber status checking via API request
-----------------------------------------

Merchant can check a subscriber status via HTTP API by request with authorization token in the header.

Request format:
  1. URL part
    - **GET /subscriptions/{SERVICE}/{SUBSCRIBER}**
  2. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**

**SERVICE** - the subscription service identifier

**SUBSCRIBER** - numeric phone number or another identifier of subscriber.

Optional GET parameters:

**sn** - mobile service number

Response format:
  1. Header part
    - **HTTP 200** (or other values in case of errors)
  2. Body part is JSON object of
    - **status** = **SUBSCRIBED** or **UNSUBSCRIBED**
    - **order_time** - last order time (if subscribed)
    - **payment_time** - last successful payment (if subscribed)
    - **error**, error message if exists
    
Deactivation via API request
----------------------------

Some connections allow you to deactivate subscriptions using the HTTP API request.
Please consult the availability of this option with your manager!

Every deactivation request should be send via HTTP API by request with authorization token in the header.

Request format:
  1. URL part
    - **POST /stop/{SUBSCRIBER}**
    **SUBSCRIBER** - numeric phone number or another identifier of subscriber.
  2. Request parameters must contain "**service**" (subscription service identifier) or "**sn**" (mobile service number) parameter
  3. Header part
    - **Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**

Response format:
  1. Header part
    - **HTTP 200** (or other values in case of errors)
  2. Body part is JSON object of
    - **status** = **SUCCESSFUL** or **FAILED**
    - **error**, error message if exists

For a quick test you can use CURL tool in next format:

   curl -X POST -H "Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" "{BASE_URL}/stop/{SUBSCRIBER}?service={SERVICE}"

