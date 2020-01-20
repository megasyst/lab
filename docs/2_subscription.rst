====================
Premium subscription
====================

Starting of subscription
------------------------

Subscriber can start a subscription using methods available in his country:
  * via SMS with predefined text keyword
  * via web browser by the link http://pay.megasyst.com/start/{KEYWORD}?{YOUR_CUSTOM_PARAMS}

For web based subscription process subscriber will be redirected to a callback URL from the service settings with params:
  * **action** = SUBSCRIPTION | OTP
  * **carrier**
  * **country**
  * **id**, event identifier
  * **msisdn**, phone number of subscriber
  * **network** = CARRIER | COMMON
  * **status**:
    - ALREADY_SUBSCRIBED
    - CARRIER_REDIRECTION
    - COUNTRY_UNAVAILABLE
    - FREQUENTLY_REQUEST
    - LONG_CONTENT_REQUEST
    - MSISDN_WAITING
    - NETWORK_ERROR
    - PIN_WAITING
    - SESSION_UNAVAILABLE
    - SUBSCRIPTION_ACCEPTED
    - SUBSCRIPTION_REJECTED
    - SUSPECTED_MSISDN
    - TRIGGER_UNAVAILABLE
    - UNHANDLED_EVENT
  * **trigger**, service keyword

The platform notificates partners by HTTP with next parameters:
  * **id**, event identifier
  * **timestamp**, integer timestamp
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **event**, (SUBSCRIPTION)
  * **trigger**, start keyword
  * **method**, order method (CLICK, PIN, SMS, USSD)
  * **country**, country
  * **carrier**, mobile network
  * **sn**, mobile service number
  * **body**, SMS text
  * **subscription_id**, order identifier
  * **subscriber_id**, end user identifier or MSISDN
  * **subscriber_price**: end user price
  * **subscriber_currency**: end user currency
  * **free_period**, free time for using the premium service in seconds
  * **renewal_period**, period of time for renew the premium subscription service
  * **ad_channel_id**, ad channel identifier (by default: SYSTEM)
  * **service_id**, premium service identifier
  * **price**, partner earning amount
  * **currency**, partner earning currency

Stopping of subscription
------------------------

The platform notificates partners by HTTP with next parameters:
  * **id**, event identifier
  * **timestamp**, integer timestamp
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **event**, (UNSUBSCRIPTION)
  * **trigger**, start keyword
  * **method**, order method (CLICK, PIN, SMS, USSD)
  * **country**, country
  * **carrier**, mobile network
  * **sn**, mobile service number
  * **body**, SMS text
  * **subscription_id**, order identifier
  * **subscriber_id**, end user identifier or MSISDN
  * **subscriber_price**: end user price
  * **subscriber_currency**: end user currency
  * **ad_channel_id**, ad channel identifier (by default: SYSTEM)
  * **service_id**, premium service identifier

Subscription renewal
--------------------

The platform notificates partners by HTTP with next parameters:
  * **id**, event identifier
  * **timestamp**, integer timestamp
  * **status**, (FAILED, SUCCESSFUL, WAITING)
  * **event**, (RENEWAL)
  * **trigger**, start keyword
  * **method**, order method (CLICK, PIN, SMS, USSD)
  * **country**, country
  * **carrier**, mobile network
  * **sn**, mobile service number
  * **body**, SMS text
  * **subscription_id**, order identifier
  * **subscriber_id**, end user identifier or MSISDN
  * **subscriber_price**: end user price
  * **subscriber_currency**: end user currency
  * **ad_channel_id**, ad channel identifier (by default: SYSTEM)
  * **service_id**, premium service identifier
  * **price**, partner earning amount
  * **currency**, partner earning currency

