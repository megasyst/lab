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
--------------------------------------

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

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Armenia     AM             Beeline           28301
Armenia     AM             Vivacell (MTS)    28305
Armenia     AM             Ucom              28310
==========  =============  ================  ==========

🇦🇹 Austria
_____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Austria     AT             A1                23201
Austria     AT             Drei              23205
Austria     AT             TMobile           23203
==========  =============  ================  ==========

🇦🇿 Azerbaijan
_____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Azerbaijan  AZ             Azercell          40001
Azerbaijan  AZ             Bakcell           40002
Azerbaijan  AZ             Narmobile         40004
==========  =============  ================  ==========

🇧🇭 Bahrain
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Bahrain     BH             Batelco           42601
Bahrain     BH             Viva              42604
==========  =============  ================  ==========

🇧🇾 Belarus
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Belarus     BY             A1 (Velcom)       25701
Belarus     BY             Life              25704
Belarus     BY             MTS               25702
==========  =============  ================  ==========

🇨🇿 Czech Republic
_________________

==============  =============  ================  ==========
Country         Country ID     Carrier           Carrier ID
==============  =============  ================  ==========
Czech Republic  CZ             O2                23002
==============  =============  ================  ==========

🇪🇬 Egypt
________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Egypt       EG             Orange            60201
Egypt       EG             Vodafone          60202
==========  =============  ================  ==========

🇪🇪 Estonia
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Estonia     EE             Elisa             24802
Estonia     EE             EMT               24801
Estonia     EE             Tele2             24803
==========  =============  ================  ==========

🇬🇪 Georgia
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Georgia     GE             Beeline           28204
Georgia     GE             Geocell           28201
Georgia     GE             Magti             28202
==========  =============  ================  ==========

🇮🇩 Indonesia
____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Indonesia   ID             Telkomsel         51010
==========  =============  ================  ==========

🇮🇶 Iraq
________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Iraq        IQ             AsiaCell          41800
Iraq        IQ             Korek             41840
Iraq        IQ             Zain              41820
==========  =============  ================  ==========

🇮🇹 Italy
________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Italy       IT             Iliad             22250
Italy       IT             Tim               22201
Italy       IT             Tre               22299
Italy       IT             Vodafone          22210
Italy       IT             Wind              22288
==========  =============  ================  ==========

🇯🇴 Jordan
_________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Jordan      JO             Orange            41677
==========  =============  ================  ==========

🇰🇿 Kazakhstan
_____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Kazakhstan  KZ             Altel             40107
Kazakhstan  KZ             Beeline           40101
Kazakhstan  KZ             Kcell             40102
Kazakhstan  KZ             Tele2             40177
==========  =============  ================  ==========

🇰🇪 Kenya
________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Kenya       KE             Telkom            63907
==========  =============  ================  ==========

🇱🇻 Latvia
_________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Latvia      LV             Bite              24705
Latvia      LV             LMT               24701
Latvia      LV             Tele2             24702
==========  =============  ================  ==========

🇱🇹 Lithuania
____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Lithuania   LT             Bite              24602
Lithuania   LT             Tele2             24603
Lithuania   LT             Telia             24601
==========  =============  ================  ==========

🇱🇺 Luxembourg
_____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Luxembourg  LU             LuxGSM            27001
Luxembourg  LU             Tango             27077
Luxembourg  LU             Orange            27099
==========  =============  ================  ==========

🇲🇩 Moldova
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Moldova     MD             IDC               25999
Moldova     MD             Moldcell          25902
Moldova     MD             Orange            25901
Moldova     MD             Unite             25903
==========  =============  ================  ==========

🇲🇦 Morocco
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Morocco     MA             INWI              60402
Morocco     MA             Orange            60400
==========  =============  ================  ==========

🇵🇭 Philippines
______________

===========  =============  ================  ==========
Country      Country ID     Carrier           Carrier ID
===========  =============  ================  ==========
Philippines  PH             Globe             51502
Philippines  PH             Smart             51503
===========  =============  ================  ==========

🇵🇱 Poland
_________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Poland      PL             Orange            26003
Poland      PL             Play              26006
Poland      PL             Plus              26001
Poland      PL             Tmobile           26034
==========  =============  ================  ==========

🇷🇺 Russia
_________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Russia      RU             Beeline           25099
Russia      RU             Megafon           25002
Russia      RU             MTS               25001
Russia      RU             Tele2             25020
==========  =============  ================  ==========

🇷🇸 Serbia
_________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Serbia      RS             Globaltel         22011
Serbia      RS             MTS               22003
Serbia      RS             Telenor           22001
Serbia      RS             VIP               22005
==========  =============  ================  ==========

🇹🇯 Tajikistan
_____________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Tajikistan  TJ             Babilon-Mobile    43604
Tajikistan  TJ             Beeline           43605
Tajikistan  TJ             Megafon           43603
Tajikistan  TJ             Tcell             43601
==========  =============  ================  ==========

🇺🇦 Ukraine
__________

==========  =============  ================  ==========
Country     Country ID     Carrier           Carrier ID
==========  =============  ================  ==========
Ukraine     UA             3Mob              25507
Ukraine     UA             Kyivstar          25502
Ukraine     UA             Lifecell          25506
Ukraine     UA             Vodafone          25501
==========  =============  ================  ==========

