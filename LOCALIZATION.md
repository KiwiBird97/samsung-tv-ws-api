    <p align="center">
    <img src="https://user-images.githubusercontent.com/5860071/47255992-611d9b00-d481-11e8-965d-d9816f254be2.png" width="300px" border="0" />
    <br/>
    <a href="https://github.com/xchwarze/samsung-tv-ws-api/releases/latest">
        <img src="https://img.shields.io/badge/version-2.6.0-brightgreen.svg?style=flat-square" alt="Version">
    </a>
    Samsung Smart TV WS API wrapper
</p>

This project is a library for remote controlling Samsung televisions via a TCP/IP connection.

It currently supports modern (post-2016) TVs with Ethernet or Wi-Fi connectivity. They should be all models with TizenOs.

Based on https://github.com/marysieek/samsung-tv-api work

# Language & Region

## Install

```bash
$ pip3 install samsungtvws[async,encrypted]
```

or

```bash
$ pip3 install "git+https://github.com/xchwarze/samsung-tv-ws-api.git#egg=samsungtvws[async,encrypted]"
```

or...!

```bash
$ git clone https://github.com/xchwarze/samsung-tv-ws-api
$ pip3 install "./samsung-tv-ws-api[async,encrypted]"
```

### Extras

`async` is required if you wish to use asynchronous I/O for all communications with the TV (`SamsungTVAsyncRest` and `SamsungTVWSAsyncRemote`)
`encrypted` is required if you wish to communicate with a TV which only support the v1 API (some J and K models) for sending commands (`SamsungTVEncryptedWSAsyncRemote` and `SamsungTVEncryptedWSAsyncAuthenticator`).



## MRT Option

### Language Set

There are 25 different language sets.

You can check if the features in your language (OSD, input, audio) are supported.

#### Korea

**KOREA**

South Korea

Code   | Native Name | English Name  | Menu? | Keyboard?
------ | ----------- | ------------- | ----- | ---------
KOR    | 한국어        | Korean        | Yes   | Yes
ENG_US | English     | English       | Yes   | Yes


#### Americas

**US**

United States of America

Code   | Native Name | English Name | Menu? | Keyboard?
------ | ----------- | ------------ | ----- | ---------
ENG_US | English     | English      | Yes   | Yes
SPA_US | Español     | Spanish      | Yes   | Yes
FRA_US | Français    | French       | Yes   | Yes
EST    | Eesti       | Estonian     | Yes   | Yes
FIN    | Suomi       | Finnish      | Yes   | Yes
DEU    | Deutsch     | German       | Yes   | Yes
GRE    | Ελληνικά    | Greek        | Yes   | Yes
HUN    | Magyar      | Hungarian    | Yes   | Yes
ITA    | Italiano    | Italian      | Yes   | Yes
LAT    | Latviešu    | Latvian      | Yes   | Yes
LTU    | Lietuvių    | Lithuanian   | Yes   | Yes
NOR    | Norsk       | Norwegian    | Yes   | Yes
POL    | Polski      | Polish       | Yes   | Yes
POR    | Português   | Portuguese   | Yes   | Yes
ROM    | Română      | Romanian     | Yes   | Yes
SER    | Srpski      | Serbian      | Yes   | Yes
SLK    | Slovenčina  | Slovak       | Yes   | Yes
SWE    | Svenska     | Swedish      | Yes   | Yes
BUL    | Български   | Bulgarian    | Yes   | Yes
CRO    | Hrvatski    | Croatian     | Yes   | Yes
CZE    | Čeština     | Czech        | Yes   | Yes
DAN    | Dansk       | Danish       | Yes   | Yes
DUT    | Nederlands  | Dutch        | Yes   | Yes
SLV    | Slovenščina | Slovenian    | Yes   | Yes
ALB    | Shqip       | Albanian     | Yes   | Yes
MKD    | Македонски  | Macedonian   | Yes   | Yes
BOS    | Bosanski    | Bosnian      | Yes   | No
KOR    | 한국어        | Korean       | Yes   | Yes


**CANADA**

Canada

Code   | Native Name | English Name | Menu? | Keyboard?
------ | ----------- | ------------ | ----- | ---------
ENG_US | English     | English      | Yes   | Yes
SPA_US | Español     | Spanish      | Yes   | Yes
FRA_US | Français    | French       | Yes   | Yes

**S_AMERICA**

South America (Mexico, Brazil, and Latin America)

Code   | Native Name | English Name | Menu? | Keyboard?
------ | ----------- | ------------ | ----- | ---------
ENG_US | English     | English      | Yes   | Yes
SPA_US | Español     | Spanish      | Yes   | Yes
POR_US | Português   | Portuguese   | Yes   | Yes


#### Europe

**EU**

Europe

Code | Native Name | English Name  | Menu? | Keyboard?
---- | ----------- | ------------- | ----- | ---------
POR  | Português   | Portuguese    | Yes   | Yes
DAN  | Dansk       | Danish        | Yes   | Yes
SPA  | Español     | Spanish       | Yes   | Yes
ENG  | English     | English       | Yes   | Yes
FRA  | Français    | French        | Yes   | Yes
SWE  | Svenska     | Swedish       | Yes   | Yes
FIN  | Suomi       | Finnish       | Yes   | Yes
ITA  | Italiano    | Italian       | Yes   | Yes
ROM  | Română      | Romanian      | Yes   | Yes
BOS  | Bosanski    | Bosnian       | Yes   | No
CRO  | Hrvatski    | Croatian      | Yes   | Yes
SLV  | Slovenščina | Slovenian     | Yes   | Yes
SER  | Srpski      | Serbian       | Yes   | Yes
ALB  | Shqip       | Albanian      | Yes   | Yes
LAT  | Latviešu    | Latvian       | Yes   | Yes
LTU  | Lietuvių    | Lithuanian    | Yes   | Yes
EST  | Eesti       | Estonian      | Yes   | Yes
HUN  | Magyar      | Hungarian     | Yes   | Yes
NOR  | Norsk       | Norwegian     | Yes   | Yes
SLK  | Slovenčina  | Slovak        | Yes   | Yes
CZE  | Čeština     | Czech         | Yes   | Yes
DUT  | Nederlands  | Dutch         | Yes   | Yes
DEU  | Deutsch     | German        | Yes   | Yes
POL  | Polski      | Polish        | Yes   | Yes
GRE  | Ελληνικά    | Greek         | Yes   | Yes
MKD  | Македонски  | Macedonian    | Yes   | Yes
BUL  | Български   | Bulgarian     | Yes   | Yes
KOR  | 한국어        | Korean        | Yes   | Yes



#### CIS

**CIS**

CIS

Code | Native Name | English Name  | Menu? | Keyboard?
---- | ----------- | ------------- | ----- | ---------
ENG  | English     | English       | Yes   | Yes
FIN  | Suomi       | Finnish       | Yes   | Yes
FRA  | Français    | French        | Yes   | Yes
DEU  | Deutsch     | German        | Yes   | Yes
GRE  | Ελληνικά    | Greek         | Yes   | Yes
HUN  | Magyar      | Hungarian     | Yes   | Yes
ITA  | Italiano    | Italian       | Yes   | Yes
NOR  | Norsk       | Norwegian     | Yes   | Yes
POL  | Polski      | Polish        | Yes   | Yes
POR  | Português   | Portuguese    | Yes   | Yes
ROM  | Română      | Romanian      | Yes   | Yes
RUS  | Русский     | Russian       | Yes   | Yes
SER  | Srpski      | Serbian       | Yes   | Yes
SLK  | Slovenčina  | Slovak        | Yes   | Yes
SPA  | Español     | Spanish       | Yes   | Yes
SWE  | Svenska     | Swedish       | Yes   | Yes
BUL  | Български   | Bulgarian     | Yes   | Yes
CRO  | Hrvatski    | Croatian      | Yes   | Yes
CZE  | Čeština     | Czech         | Yes   | Yes
DAN  | Dansk       | Danish        | Yes   | Yes
DUT  | Nederlands  | Dutch         | Yes   | Yes
SLV  | Slovenščina | Slovenian     | Yes   | Yes
ALB  | Shqip       | Albanian      | Yes   | Yes
MKD  | Македонски  | Macedonian    | Yes   | Yes
UKR  | Українська  | Ukrainian     | Yes   | Yes
KAZ  | Қазақ       | Kazakh        | Yes   | Yes


**CAUCASUS**

Caucasus Regions

Code | Native Name | English Name  | Menu? | Keyboard?
---- | ----------- | ------------- | ----- | ---------
ENG  | English     | English       | Yes   | Yes
FIN  | Suomi       | Finnish       | Yes   | Yes
FRA  | Français    | French        | Yes   | Yes
DEU  | Deutsch     | German        | Yes   | Yes
GRE  | Ελληνικά    | Greek         | Yes   | Yes
HUN  | Magyar      | Hungarian     | Yes   | Yes
ITA  | Italiano    | Italian       | Yes   | Yes
NOR  | Norsk       | Norwegian     | Yes   | Yes
POL  | Polski      | Polish        | Yes   | Yes
POR  | Português   | Portuguese    | Yes   | Yes
ROM  | Română      | Romanian      | Yes   | Yes
RUS  | Русский     | Russian       | Yes   | Yes
SER  | Srpski      | Serbian       | Yes   | Yes
SLK  | Slovenčina  | Slovak        | Yes   | Yes
SPA  | Español     | Spanish       | Yes   | Yes
SWE  | Svenska     | Swedish       | Yes   | Yes
BUL  | Български   | Bulgarian     | Yes   | Yes
CRO  | Hrvatski    | Croatian      | Yes   | Yes
CZE  | Čeština     | Czech         | Yes   | Yes
DAN  | Dansk       | Danish        | Yes   | Yes
DUT  | Nederlands  | Dutch         | Yes   | Yes
SLV  | Slovenščina | Slovenian     | Yes   | Yes
ALB  | Shqip       | Albanian      | Yes   | Yes
MKD  | Македонски  | Macedonian    | Yes   | Yes
UKR  | Українська  | Ukrainian     | Yes   | Yes
KAZ  | Қазақ       | Kazakh        | Yes   | Yes
AZE  | Azərbaycan  | Azerbaijani   | Yes   | No
GEO  | ქართული     | Georgian      | Yes   | No
ARM  | Հայերեն     | Armenian      | Yes   | No
UZB  | O‘zbek      | Uzbek         | Yes   | No
MON  | Монгол Улс  | Mongolian     | Yes   | No
KOR  | 한국어        | Korean        | Yes   | Yes


**CENTRAL ASIA**

Central Asia

Code | Native Name | English Name  | Menu? | Keyboard?
---- | ----------- | ------------- | ----- | ---------
ENG  | English     | English       | Yes   | Yes
FIN  | Suomi       | Finnish       | Yes   | Yes
FRA  | Français    | French        | Yes   | Yes
DEU  | Deutsch     | German        | Yes   | Yes
GRE  | Ελληνικά    | Greek         | Yes   | Yes
HUN  | Magyar      | Hungarian     | Yes   | Yes
ITA  | Italiano    | Italian       | Yes   | Yes
NOR  | Norsk       | Norwegian     | Yes   | Yes
POL  | Polski      | Polish        | Yes   | Yes
POR  | Português   | Portuguese    | Yes   | Yes
ROM  | Română      | Romanian      | Yes   | Yes
RUS  | Русский     | Russian       | Yes   | Yes
SER  | Srpski      | Serbian       | Yes   | Yes
SLK  | Slovenčina  | Slovak        | Yes   | Yes
SPA  | Español     | Spanish       | Yes   | Yes
SWE  | Svenska     | Swedish       | Yes   | Yes
BUL  | Български   | Bulgarian     | Yes   | Yes
CRO  | Hrvatski    | Croatian      | Yes   | Yes
CZE  | Čeština     | Czech         | Yes   | Yes
DAN  | Dansk       | Danish        | Yes   | Yes
DUT  | Nederlands  | Dutch         | Yes   | Yes
SLV  | Slovenščina | Slovenian     | Yes   | Yes
ALB  | Shqip       | Albanian      | Yes   | Yes
MKD  | Македонски  | Macedonian    | Yes   | Yes
UKR  | Українська  | Ukrainian     | Yes   | Yes
KAZ  | Қазақ       | Kazakh        | Yes   | Yes
UZB  | O‘zbek      | Uzbek         | Yes   | No
MON  | Монгол Улс  | Mongolian     | Yes   | No



#### Middle East & Africa

**IRAN**

Iran

Code | Native Name | English Name   | Menu? | Keyboard?
---- | ----------- | -------------- | ----- | ---------
ENG  | English     | English        | Yes   | Yes
PER  | فارسی       | Persian        | Yes   | Yes
ARA  | العربية     | Arabic         | Yes   | Yes
SOR  | سۆرانی      | Sorani          | Yes   | No
KUR  | Kurmancî    | Kurdish        | Yes   | No
URD  | اردو        | Urdu           | Yes   | Yes


**ISRAEL**

Israel

Code | Native Name | English Name | Menu? | Keyboard?
---- | ----------- | ------------ | ----- | ---------
ENG  | English     | English      | Yes   | Yes
FRA  | Français    | French       | Yes   | Yes
ARA  | العربية     | Arabic       | Yes   | Yes
HEB  | עברית       | Hebrew       | Yes   | Yes
RUS  | Русский     | Russian      | Yes   | Yes
TUR  | Türkçe      | Turkish      | Yes   | Yes
DEU  | Deutsch     | German       | Yes   | Yes
SPA  | Español     | Spanish      | Yes   | Yes


**AFRICA**

Southern Africa

Code | Native Name | English Name | Menu? | Keyboard?
---- | ----------- | ------------ | ----- | ---------
ENG  | English     | English      | Yes   | Yes
FRA  | Français    | French       | Yes   | Yes
POR  | Português   | Portuguese   | Yes   | Yes
ARA  | العربية     | Arabic       | Yes   | Yes
YOR  | Yorùbá      | Yoruba       | Yes   | Yes
IGB  | Asusu Igbo  | Igbo         | Yes   | Yes
HAU  | Hausa       | Hausa        | Yes   | Yes
AFR  | Afrikaans   | Afrikaans    | Yes   | Yes
ZUL  | IsiZulu     | Zulu         | Yes   | Yes
XHO  | IsiXhosa    | Xhosa        | Yes   | Yes
SWA  | Kiswahili   | Swahili      | Yes   | Yes
AMH  | አማርኛ       | Amharic      | Yes   | Yes


**N_AFRICA**

Northern Africa

Code | Native Name | English Name | Menu? | Keyboard?
---- | ----------- | ------------ | ----- | ---------
ENG  | English     | English      | Yes   | Yes
FRA  | Français    | French       | Yes   | Yes
ARA  | العربية     | Arabic       | Yes   | Yes
HEB  | עברית       | Hebrew       | Yes   | Yes
RUS  | Русский     | Russian      | Yes   | Yes
TUR  | Türkçe      | Turkish      | Yes   | Yes
DEU  | Deutsch     | German       | Yes   | Yes
SPA  | Español     | Spanish      | Yes   | Yes


**TURKEY**

Türkiye/Turkey

Code | Native Name | English Name | Menu? | Keyboard?
---- | ----------- | ------------ | ----- | ---------
ENG  | English     | English      | Yes   | Yes
FRA  | Français    | French       | Yes   | Yes
RUS  | Русский     | Russian      | Yes   | Yes
TUR  | Türkçe      | Turkish      | Yes   | Yes
ARA  | العربية     | Arabic       | Yes   | Yes
SPA  | Español     | Spanish      | Yes   | Yes
KOR  | 한국어        | Korean       | Yes   | Yes


**MIDDLE ASIA**

Middle East

Code | Native Name | English Name   | Menu? | Keyboard?
---- | ----------- | -------------- | ----- | ---------
ENG  | English     | English        | Yes   | Yes
FRA  | Français    | French         | Yes   | Yes
ARA  | العربية     | Arabic         | Yes   | Yes
URD  | اردو        | Urdu           | Yes   | Yes
SOR  | سۆرانی      | Sorani         | Yes   | No
KUR  | Kurmancî    | Kurdish        | Yes   | No
KOR  | 한국어        | Korean         | Yes   | Yes
PER  | فارسی       | Persian        | Yes   | Yes
RUS  | Русский     | Russian        | Yes   | Yes
HIN  | हिंदी         | Hindi          | Yes   | Yes



#### Southwest Asia

**WEST ASIA**

India and Southwest Asia

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
HIN  | हिंदी           | Hindi             | Yes   | Yes
TAM  | தமிழ்          | Tamil             | Yes   | Yes
BEN  | বাংলা          | Bangla            | Yes   | No
TEL  | తెలుగు         | Telugu            | Yes   | No
MAR  | मराठी          | Marathi           | Yes   | No
KOK  | कोंकणी         | Konkani           | Yes   | No
GUJ  | ગુજરાતી         | Gujarati          | Yes   | No
KAN  | ಕನ್ನಡ          | Kannada           | Yes   | No
MAL  | മലയാളം        | Malayalam         | Yes   | No
ORI  | ଓଡ଼ିଆ          | Odia              | Yes   | No
PAN  | ਪੰਜਾਬੀ          | Punjabi           | Yes   | No
ASM  | অসমীয়া        | Assamese          | Yes   | No
MAI  | मैथिली         | Maithili          | Yes   | No
SAN  | ᱥᱟᱱᱛᱟᱲᱤ      | Santali           | Yes   | No
KAS  | कॉशुर          | Kashmiri          | Yes   | No
NEP  | नेपाली          | Nepali            | Yes   | No
SIN  | सिन्धी          | Sindhi            | Yes   | No
MAN  | মণিপুরী         | Manipuri          | Yes   | No
SKR  | संस्कृतम्         | Sanskrit          | Yes   | No
BHI  | भिलोडी          | Bhilodi           | Yes   | No
TUL  | ತುಳು           | Tulu              | Yes   | No
URD  | اردو          | Urdu              | Yes   | Yes



#### Asia Pacific

**EAST ASIA**

South Korea, China mainland, Taiwan, Cambodia, Indonesia, Malaysia, Myanmar, the Philippines, Thailand, and Vietnam

Code | Native Name   | English Name | Menu? | Keyboard?
---- | ------------- | ------------ | ----- | ---------
ENG  | English       | English      | Yes   | Yes
THA  | ไทย           | Thai         | Yes   | Yes
CAM  | ខ្មែរ            | Khmer        | Yes   | Yes
CHI  | 简体中文        | Chinese      | Yes   | Yes
MYA  | မြန်မာ          | Burmese      | Yes   | Yes
DEU  | Deutsch       | German       | Yes   | Yes
RUS  | Русский       | Russian      | Yes   | Yes
FRA  | Français      | French       | Yes   | Yes
SPA  | Español       | Spanish      | Yes   | Yes
ITA  | Italiano      | Italian      | Yes   | Yes
POR  | Português     | Portuguese   | Yes   | Yes
MAY  | Bahasa Melayu | Malay        | Yes   | Yes
VIE  | Tiếng Việt    | Vietnamese   | Yes   | Yes
IND  | Indonesia     | Indonesian   | Yes   | Yes
TPE  | 國語           | Taiwanese    | Yes   | Yes
TAM  | தமிழ்          | Tamil        | Yes   | Yes
KOR  | 한국어         | Korean       | Yes   | Yes
HIN  | हिंदी           | Hindi        | Yes   | Yes


**MALAYSIA**

Malaysia and China mainland

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
CHI  | 简体中文        | Chinese           | Yes   | Yes
MAY  | Bahasa Melayu | Malay             | Yes   | Yes


**PHILIPPINE**

Philippines, Indonesia, China mainland, South Korea, and Vietnam

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
IND  | Indonesia     | Indonesia         | Yes   | Yes
VIE  | Tiếng Việt    | Vietnamese        | Yes   | Yes
CHI  | 简体中文        | Chinese           | Yes   | Yes
FIL  | Tagalog       | Filipino          | Yes   | No
KOR  | 한국어          | Korean            | Yes   | Yes


**AUSTRALIA**

Australia and New Zealand

Code | Native Name   | English Name | Menu? | Keyboard?
---- | ------------- | ------------ | ----- | ---------
ENG  | English       | English      | Yes   | Yes
CHI  | 简体中文        | Chinese      | Yes   | Yes
KOR  | 한국어          | Korean       | Yes   | Yes
FRA  | Français      | French       | Yes   | Yes
ITA  | Italiano      | Italian      | Yes   | Yes
DEU  | Deutsch       | German       | Yes   | Yes
SPA  | Español       | Spanish      | Yes   | Yes
MAY  | Bahasa Melayu | Malay        | Yes   | Yes
MAO  | Maōri         | Vietnamese   | Yes   | Yes


**MYANMAR**

Myanmar, Cambodia, and Thailand

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
THA  | ไทย           | Thai              | Yes   | Yes
MYA  | မြန်မာ          | Burmese           | Yes   | Yes
CAM  | ខ្មែរ            | Khmer             | Yes   | Yes
CHI  | 简体中文        | Chinese           | Yes   | Yes



#### China

**TAIWAN**

Taiwan

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
TPE  | 國語           | Taiwanese         | Yes   | Yes


**CHINA**

China mainland

Code | Native Name   | English Name      | Menu? | Keyboard?
---- | ------------- | ----------------- | ----- | ---------
ENG  | English       | English           | Yes   | Yes
CHI  | 简体中文        | Chinese           | Yes   | Yes


**HONGKONG**

Hong Kong, Macao, and China mainland

Code | Native Name   | English Name        | Menu? | Keyboard?
---- | ------------- | ------------------- | ----- | ---------
ENG  | English       | English             | Yes   | Yes
HKG  | 繁體中文         | Cantonese          | Yes   | Yes
CHI  | 简体中文        | Chinese             | Yes   | Yes



#### Japan

**JAPAN**

Japan

Code    | Native Name | English Name      | Menu? | Keyboard?
------- | ----------- | ----------------- | ----- | ---------
ENG_US  | English     | English           | Yes   | Yes
JPN     | 日本語        | Japanese          | Yes   | Yes



## Appendix

### Local Set

#### Americas

| Code      | Country/Region |
| --------- | -------------- |
| US        | United States  |
| SD_CANADA | Canada         |
| SD_MEXICO | Mexico         |


### All Languages

The Tizen OS has support for many languages. A "???" indicator means that the language is not used in any of the regions where Samsung Tizen products are sold.

| Code   | Native Name             | English Name                    |
| ------ | ----------------------- | ------------------------------- |
| KOR    | 한국어                    | Korean                          |
| ENG_US | English (US)            | English (US)                    |
| SPA_US | Español (Latinoamérica) | Spanish (Latin America)         |
| FRA_US | Français (Canada)       | French (Canada)                 |
| POR_US | Português (Brasil)      | Portuguese (Brazil)             |
| BUL    | Български               | Bulgarian                       |
| CRO    | Hrvatski                | Croatian                        |
| CZE    | Čeština                 | Czech                           |
| DAN    | Dansk                   | Danish                          |
| DUT    | Nederlands              | Dutch                           |
| ENG    | English (UK)            | English (UK)                    |
| FIN    | Suomi                   | Finnish                         |
| FRA    | Français (France)       | French (France)                 |
| DEU    | Deutsch                 | German                          |
| GRE    | Ελληνικά                | Greek                           |
| HUN    | Magyar                  | Hungarian                       |
| ITA    | Italiano                | Italian                         |
| NOR    | Norsk                   | Norwegian                       |
| POL    | Polski                  | Polish                          |
| POR    | Português (Portugal)    | Portuguese (Portugal)           |
| ROM    | Română                  | Romanian                        |
| RUS    | Русский                 | Russian                         |
| SER    | Srpski                  | Serbian                         |
| SLK    | Slovenčina              | Slovak                          |
| SPA    | Español (España)        | Spanish (Spain)                 |
| SWE    | Svenska                 | Swedish                         |
| TUR    | Türkçe                  | Turkish                         |
| CHI    | 简体中文                 | Chinese                         |
| HKG    | 繁體中文                  | Cantonese                       |
| TPE    | 國語                     | Taiwanese                       |
| JPN    | 日本語                   | Japanese                        |
| MAO    | Māori                   | Maori                           |
| CMN    | ???                     | ???                             |
| YUE    | ???                     | ???                             |
| HIN    | हिंदी                     | Hindi                           |
| EST    | Eesti                   | Estonian                        |
| LAT    | Latviešu                | Latvian                         |
| LTU    | Lietuvių                | Lithuanian                      |
| ARA    | العربية                 | Arabic                          |
| PER    | فارسی                   | Persian                         |
| QAA    | ???                     | ???                             |
| AD     | ???                     | ???                             |
| CAT    | ???                     | ???                             |
| VAL    | ???                     | ???                             |
| THA    | ไทย                     | Thai                            |
| HEB    | עברית                   | Hebrew                          |
| IND    | Indonesia               | Indonesian                      |
| VIE    | Tiếng Việt              | Vietnamese                      |
| URD    | اردو                    | Urdu                            |
| AFR    | Afrikaans               | Afrikaans                       |
| ZUL    | IsiZulu                 | Zulu                            |
| XHO    | IsiXhosa                | Xhosa                           |
| YOR    | Yorùbá                  | Yoruba                          |
| IGB    | Asusu Igbo              | Igbo                            |
| HAU    | Hausa                   | Hausa                           |
| SWA    | Kiswahili               | Swahili                         |
| AMH    | አማርኛ                   | Amharic                         |
| TAM    | தமிழ்                    | Tamil                           |
| IRA    | ???                     | ???                             |
| FIL    | Tagalog                 | Filipino/Tagalog                |
| LIT    | ???                     | ???                             |
| LAV    | ???                     | ???                             |
| SLV    | Slovenščina             | Slovenian                       |
| ALB    | Shqip                   | Albanian                        |
| UKR    | Українська              | Ukrainian                       |
| KAZ    | Қазақ                   | Kazakh                          |
| MKD    | Македонски              | Macedonian                      |
| MAY    | Bahasa Melayu           | Malay                           |
| WEL    | ???                     | ???                             |
| GLA    | ???                     | ???                             |
| IRI    | ???                     | ???                             |
| OTHER  | ???                     | ???                             |
| AKA    | ???                     | ???                             |
| TWI    | ???                     | ???                             |
| EWE    | ???                     | ???                             |
| GAA    | ???                     | ???                             |
| NZI    | ???                     | ???                             |
| NBL    | ???                     | ???                             |
| NSO    | ???                     | ???                             |
| SOT    | ???                     | ???                             |
| SSW    | ???                     | ???                             |
| TSO    | ???                     | ???                             |
| TSN    | ???                     | ???                             |
| VEN    | ???                     | ???                             |
| UZB    | O‘zbek                  | Uzbek                           |
| AZE    | Azərbaycan              | Azerbaijani                     |
| MON    | Монгол Улс              | Mongolian                       |
| BOS    | Bosanski                | Bosnian                         |
| BEN    | বাংলা                    | Bangla                          |
| TEL    | తెలుగు                   | Telugu                          |
| MAR    | मराठी                     | Marathi                         |
| KOK    | कोंकणी                    | Konkani                         |
| GUJ    | ગુજરાતી                    | Gujarati                        |
| KAN    | ಕನ್ನಡ                     | Kannada                         |
| MAL    | മലയാളം                  | Malayalam                       |
| ORI    | ଓଡ଼ିଆ                     | Odia                            |
| PAN    | ਪੰਜਾਬੀ                     | Punjabi                         |
| ASM    | অসমীয়া                   | Assamese                        |
| MYA    | မြန်မာ                    | Burmese                         |
| CAM    | ខ្មែរ                      | Khmer                           |
| SOR    | سۆرانی                  | Sorani                          |
| KUR    | Kurmancî                | Kurmanji                        |
| MAI    | मैथिली                    | Maithili                        |
| SAN    | ᱥᱟᱱᱛᱟᱲᱤ                 | Santali                         |
| KAS    | कॉशुर                     | Kashmiri                        |
| NEP    | नेपाली                    | Nepali                          |
| SIN    | सिन्धी                    | Sindhi                          |
| MAN    | মণিপুরী                   | Manipuri                        |
| SKR    | संस्कृतम्                   | Sanskrit                        |
| BHI    | भिलोडी                   | Bhilodi                         |
| TUL    | ತುಳು                    | Tulu                            |
| GEO    | ქართული                 | Georgian                        |
| ARM    | Հայերեն                 | Armenian                        |





## License

GPL-2.0
