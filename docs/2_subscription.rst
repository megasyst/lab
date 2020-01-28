=====================
Premium subscriptions
=====================

Starting subscription via SMS
-----------------------------

Common steps:
* Subscriber wants to use the premium service and sees service rules on partner's side
* Subscriber sends SMS with predefined keyword to predefined short number
* Megasyst notificates partner by HTTP (example: `ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&free_period=86400&id=12345678901234567890&renewal_period=86400&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&subscription=12345678901234567890&trigger_data=abc+123&trigger_flow=SMS&trigger_keyword=ABC&trigger_time=2020-01-01+01%3A01%3A01+UTC`):
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = SUBSCRIPTION
  * **free_period**, free time for using the premium service in seconds
  * **id**, event identifier
  * **renewal_period**, period of time for renew the premium subscription service
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **subscriber**, end user identifier or MSISDN
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = SMS
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp
* Megasyst sends SMS to subscriber with instructions for access to the premium service

Starting subscription via web (CLICK/PIN)
-----------------------------------------

Common steps:
* Subscriber wants to use the premium service and sees service rules on partner's side
* Subscriber goes to http://pay.megasyst.com/start/{KEYWORD}?{ANY_PREMIUM_SERVICE_CUSTOM_PARAMS}
* Subscriber accepts or rejects the premium service rules with available technical methods on his network
* Megasyst redirects him to a callback URL from the service settings with ANY_PREMIUM_SERVICE_CUSTOM_PARAMS and result params (example `ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&id=12345678901234567890&service=ABC&status=SUCCESSFUL&subscriber=12345678900&trigger_flow=CLICK&trigger_keyword=ABC`):
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = SUBSCRIPTION
  * **id**, event identifier
  * **service**, premium service identifier
  * **status** = **ALREADY_SUBSCRIBED** | CARRIER_REDIRECTION | COUNTRY_UNAVAILABLE | FREQUENTLY_REQUEST | LONG_CONTENT_REQUEST | MSISDN_WAITING | NETWORK_ERROR | PIN_WAITING | SESSION_UNAVAILABLE | **SUCCESSFUL** | FAILED | SUSPECTED_MSISDN | TRIGGER_UNAVAILABLE | UNHANDLED_EVENT
  * **subscriber**, end user identifier or MSISDN
  * **trigger_flow**, order method (CLICK, PIN, SMS, USSD)
  * **trigger_keyword**, normalized keyword
* Megasyst notificates partner by HTTP (example: `ad_channel=SYSTEM&carrier=12345&country=XX&event=SUBSCRIPTION&free_period=86400&id=12345678901234567890&renewal_period=86400&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&trigger_data=abc+123&trigger_flow=CLICK&trigger_keyword=ABC&trigger_time=2020-01-01+01%3A01%3A01+UTC`):
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = SUBSCRIPTION
  * **free_period**, free time for using the premium service in seconds
  * **id**, event identifier
  * **renewal_period**, period of time for renew the premium subscription service
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = FAILED | **SUCCESSFUL** | WAITING
  * **subscriber**, end user identifier or MSISDN
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = CLICK | PIN
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp
* Megasyst sends welcome SMS to subcriber

Stopping of subscription
------------------------

Megasyst notificates partners by HTTP with next parameters (example `ad_channel=SYSTEM&carrier=12345&country=XX&event=UNSUBSCRIPTION&id=12345678901234567892&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&trigger_data=stop+abc&trigger_flow=SMS&trigger_keyword=STOP&trigger_time=2020-01-01+01%3A01%3A01+UTC`):
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = UNSUBSCRIPTION
  * **id**, event identifier
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = FAILED | **SUCCESSFUL** | WAITING
  * **subscriber**, end user identifier or MSISDN
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = CLICK | PIN | SMS
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp

Subscription renewal
--------------------

Megasyst notificates partners by HTTP with next parameters (example: `ad_channel=SYSTEM&carrier=12345&country=XX&event=RENEWAL&free_period=86400&id=12345678901234567891&renewal_period=86400&service=ABC&sn=1234&status=SUCCESSFUL&subscriber=12345678900&subscription=12345678901234567890&trigger_data=abc+123&trigger_flow=SMS&trigger_keyword=ABC&trigger_time=2020-01-01+01%3A01%3A01+UTC`):
  * **ad_channel**, ad channel identifier (by default: SYSTEM)
  * **carrier**, mobile network
  * **country**, country
  * **event** = UNSUBSCRIPTION
  * **id**, event identifier
  * **service**, premium service identifier
  * **sn**, mobile service number
  * **status** = FAILED | **SUCCESSFUL** | WAITING
  * **subscriber**, end user identifier or MSISDN
  * **subscription**, id of subscription order
  * **trigger_data**, raw keyword or SMS body
  * **trigger_flow** = CLICK | PIN | SMS
  * **trigger_keyword**, normalized keyword
  * **trigger_time**, integer timestamp
