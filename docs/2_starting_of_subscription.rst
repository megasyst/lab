========================
Starting of subscription
========================

The platform notificates partners by HTTP with next parameters:
  * id, event identifier
  * timestamp, integer timestamp
  * status, (FAILED, SUCCESSFUL, WAITING)
  * event, (SUBSCRIPTION)
  * trigger, start keyword
  * method, order method (CLICK, PIN, SMS, USSD)
  * country, country
  * carrier, mobile network
  * sn, mobile service number
  * body, SMS text
  * subscription_id, order identifier
  * subscriber_price: end user price
  * subscriber_currency: end user currency
  * subscriber_id, end user identifier or MSISDN
  * free_period, free time for using the premium service in seconds
  * renewal_period, period of time for renew the premium subscription service
  * ad_channel_id, ad channel identifier (by default: SYSTEM)
  * service_id, premium service identifier
  * price, partner earning amount
  * currency, partner earning currency