==================
Common information
==================

.. image: http://megasyst.com/images/logo.png

Megasyst Aggregation Platform(MAP) offers any merchant(service-provider) to provide either One-time payment(One-time purchase) or Subscription-based content service(s) by using direct mobile carrier connectivities via API with notifications.

The MAP provides following communication channels:
  * HTTP notifications to merchant servers,
  * HTTP REST API for management and analytics,
  * HTTP redirection API for redirecting mobile users via Click(WAP) or PIN-submit(WiFi) flows,
  * E-mail notifications.

HTTP notifications to merchant servers
-------------------------------------

The MAP notifies merchant by configured HTTP method regarding every significant event(example: starting or stopping of subscription, complaint, withdrawals and etc.) and waits **HTTP 200** status in the response.

HTTP notifications available:
  * HTTP or HTTPS protocol
  * GET or POST method
  * WWW or JSON data format

IMPORTANT

For Country code(provided as two-letter code defined in ISO 3166-1).

Requests from merchant servers
------------------------------

Merchant can send requests to Megasyst's HTTP API with authorization token in the header.

Header format is:
  * Authorization: Partner XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Carrier identifiers
-------------------

🇦🇲 Armenia
__________

================  ==========
Carrier           ID
================  ==========
Beeline           28301
Vivacell (MTS)    28305
Ucom              28310
================  ==========

🇦🇿 Azerbaijan
_____________

================  ==========
Carrier           ID
================  ==========
Azercell          40001
Bakcell           40002
Narmobile         40004
================  ==========

🇧🇭 Bahrain
__________

================  ==========
Carrier           ID
================  ==========
Batelco           42601
Viva              42604
================  ==========

🇧🇾 Belarus
__________

================  ==========
Carrier           ID
================  ==========
A1 (Velcom)       25701
Life              25704
MTS               25702
================  ==========

🇪🇪 Estonia
__________

================  ==========
Carrier           ID
================  ==========
Elisa             24802
EMT               24801
Tele2             24803
================  ==========

🇬🇪 Georgia
__________

================  ==========
Carrier           ID
================  ==========
Beeline           28204
Geocell           28201
Magti             28202
================  ==========

🇮🇶 Iraq
________

================  ==========
Carrier           ID
================  ==========
AsiaCell          41800
Korek             41840
Zain              41820
================  ==========

🇮🇹 Italy
________

================  ==========
Carrier           ID
================  ==========
Iliad             22250
Tim               22201
Tre               22299
Vodafone          22210
Wind              22288
================  ==========

🇰🇿 Kazakhstan
_____________

================  ==========
Carrier           ID
================  ==========
Altel             40107
Beeline           40101
Kcell             40102
Tele2             40177
================  ==========

🇱🇻 Latvia
_________

================  ==========
Carrier           ID
================  ==========
Bite              24705
LMT               24701
Tele2             24702
================  ==========

🇱🇹 Lithuania
____________

================  ==========
Carrier           ID
================  ==========
Bite              24602
Tele2             24603
Telia             24601
================  ==========

🇲🇩 Moldova
__________

================  ==========
Carrier           ID
================  ==========
IDC               25999
Moldcell          25902
Orange            25901
Unite             25903
================  ==========

🇲🇦 Morocco
__________

================  ==========
Carrier           ID
================  ==========
INWI              60402
Orange            60400
================  ==========

🇵🇭 Philippines
______________

================  ==========
Carrier           ID
================  ==========
Globe             51502
Smart             51503
================  ==========

🇵🇱 Poland
_________

================  ==========
Carrier           ID
================  ==========
Orange            26003
Play              26006
Plus              26001
Tmobile           26034
================  ==========

🇷🇺 Russia
_________

================  ==========
Carrier           ID
================  ==========
Beeline           25099
MTS               25001
Megafon           25002
Tele2             25020
================  ==========

🇷🇸 Serbia
_________

================  ==========
Carrier           ID
================  ==========
Globaltel         22011
MTS               22003
Telenor           22001
VIP               22005
================  ==========

🇹🇯 Tajikistan
_____________

================  ==========
Carrier           ID
================  ==========
Babilon-Mobile    43604
Beeline           43605
Megafon           43603
Tcell             43601
================  ==========

🇺🇦 Ukraine
__________

================  ==========
Carrier           ID
================  ==========
3Mob              25507
Kyivstar          25502
Lifecell          25506
Vodafone          25501
================  ==========

