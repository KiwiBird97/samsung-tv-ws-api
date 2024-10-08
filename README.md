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

## Usage

### Basic

```python
import sys
import os
import logging
import wakeonlan

sys.path.append('../')

from samsungtvws import SamsungTVWS

# Increase debug level
logging.basicConfig(level=logging.INFO)

# Normal constructor
tv = SamsungTVWS('192.168.xxx.xxx')

# Autosave token to file
token_file = os.path.dirname(os.path.realpath(__file__)) + '/tv-token.txt'
tv = SamsungTVWS(host='192.168.xxx.xxx', port=8002, token_file=token_file)

# Toggle power
tv.shortcuts().power()

# Power On
wakeonlan.send_magic_packet('CC:6E:A4:xx:xx:xx')

# Open web in browser
tv.open_browser('https://duckduckgo.com/')

# View installed apps
apps = tv.app_list()
logging.info(apps)

# Open app (Spotify)
tv.run_app('3201606009684')

# Get app status (Spotify)
app = tv.rest_app_status('3201606009684')
logging.info(app)

# Open app (Spotify)
app = tv.rest_app_run('3201606009684')
logging.info(app)

# Close app (Spotify)
app = tv.rest_app_close('3201606009684')
logging.info(app)

# Install from official store (Spotify)
app = tv.rest_app_install('3201606009684')
logging.info(app)

# Get device info (device name, model, supported features..)
info = tv.rest_device_info()
logging.info(info)

```

### Art Mode

TVs that support art mode (such as The Frame) can be controlled as follows:

```python
import sys
import logging

sys.path.append('../')

from samsungtvws import SamsungTVWS

# Increase debug level
logging.basicConfig(level=logging.INFO)

# Normal constructor
tv = SamsungTVWS('192.168.xxx.xxx')

# Is art mode supported?
info = tv.art().supported()
logging.info(info)

# List the art available on the device
info = tv.art().available()
logging.info(info)

# Retrieve information about the currently selected art
info = tv.art().get_current()
logging.info(info)

# Retrieve a thumbnail for a specific piece of art. Returns a JPEG.
thumbnail = tv.art().get_thumbnail('SAM-F0206')

# Set a piece of art
tv.art().select_image('SAM-F0206')

# Set a piece of art, but don't immediately show it if not in art mode
tv.art().select_image('SAM-F0201', show=False)

# Determine whether the TV is currently in art mode
info = tv.art().get_artmode()
logging.info(info)

# Switch art mode on or off
tv.art().set_artmode(True)
tv.art().set_artmode(False)

# Upload a picture
file = open('test.png', 'rb')
data = file.read()
tv.art().upload(data)

# If uploading a JPEG
tv.art().upload(data, file_type='JPEG')

# To set the matte to modern and apricot color
tv.art().upload(data, matte='modern_apricot')

# Delete an uploaded item
tv.art().delete('MY-F0020')

# Delete multiple uploaded items
tv.art().delete_list(['MY-F0020', 'MY-F0021'])

# List available photo filters
info = tv.art().get_photo_filter_list()
logging.info(info)

# Apply a filter to a specific piece of art
tv.art().set_photo_filter('SAM-F0206', 'ink')
```

### Async

Examples are available in the examples folder: `async_remote.py`, `async_rest.py`

### Encrypted API

Examples are available in the examples folder: `encrypted_authenticator.py`, `encrypted_remote.py`

## Supported TVs

List of support TV models. https://developer.samsung.com/smarttv/develop/extension-libraries/smart-view-sdk/supported-device/supported-tvs.html

```
2017 : M5500 and above
2016 : K4300, K5300 and above
2015 : J5500 and above (except J6203)
2014 : H4500, H5500 and above (except H6003/H6103/H6153/H6201/H6203)
Supported TV models may vary by region.
```

For complete list https://developer.samsung.com/smarttv/develop/specifications/tv-model-groups.html


## MRT Option

### Language Set

There are 25 different language sets.

#### Korea

**KOREA (2)**

South Korea
* **Menu and Keyboard:** KOR, ENG_US


#### Americas

**US**

USA, Canada, Mexico, Brazil, North America, Latin America & Caribbean, Europe, and South Korea
* **Menu (28):** ENG_US, SPA_US, FRA_US, EST, FIN, DEU, GRE, HUN, ITA, LAT, LTU, NOR, POL, POR, ROM, SER, SLK, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, BOS, KOR
* **Keyboard (27):** ENG_US, SPA_US, FRA_US, EST, FIN, DEU, GRE, HUN, ITA, LAT, LTU, NOR, POL, POR, ROM, SER, SLK, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, KOR

**CANADA (3)**
* **Menu and Keyboard:** ENG_US, SPA_US, FRA_US

**S_AMERICA (3)**

Mexico, Brazil, and South America
* **Menu and Keyboard:** ENG_US, SPA_US, POR_US


#### Europe

**EU**

Europe and South Korea
* **Menu (28):** ENG, EST, FIN, FRA, DEU, GRE, HUN, ITA, LAT, LTU, NOR, POL, POR, ROM, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, BOS, KOR
* **Keyboard (27):** ENG, EST, FIN, FRA, DEU, GRE, HUN, ITA, LAT, LTU, NOR, POL, POR, ROM, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, KOR


#### CIS

**CIS (26)**
* **Menu and Keyboard:** ENG, FIN, FRA, DEU, GRE, HUN, ITA, NOR, POL, POR, ROM, RUS, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, UKR, KAZ

**CAUCASUS**

CIS, Central Asia, and South Korea
* **Menu (32):** ENG, FIN, FRA, DEU, GRE, HUN, ITA, NOR, POL, POR, ROM, RUS, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, UKR, KAZ, AZE, GEO, ARM, UZB, MON, KOR
* **Keyboard (27):** ENG, FIN, FRA, DEU, GRE, HUN, ITA, NOR, POL, POR, ROM, RUS, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, UKR, KAZ, KOR

**CENTRAL ASIA**
* **Menu (28):** ENG, FIN, FRA, DEU, GRE, HUN, ITA, NOR, POL, POR, ROM, RUS, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, UKR, KAZ, UZB, MON
* **Keyboard (26):** ENG, FIN, FRA, DEU, GRE, HUN, ITA, NOR, POL, POR, ROM, RUS, SER, SLK, SPA, SWE, BUL, CRO, CZE, DAN, DUT, SLV, ALB, MKD, UKR, KAZ


#### India

**WEST ASIA**

India, Nepal, and Bangladesh
* **Menu (23):** ENG, HIN, TAM, BEN, TEL, MAR, KOK, GUJ, KAN, MAL, ORI, PAN, ASM, MAI, SAN, KAS, NEP, SIN, MAN, SKR, BHI, TUL, URD
* **Keyboard (4):** ENG, HIN, TAM, URD


#### Asia Pacific

**EAST ASIA (18)**

South Korea, China mainland, Taiwan, Macau, Cambodia, Indonesia, Malaysia, Myanmar, and Philippines
* **Menu and Keyboard:** ENG, THA, CAM, CHI, MYA, DEU, RUS, FRA, SPA, ITA, POR, MAY, VIE, IND, TPE, TAM, KOR, HIN

**MALAYSIA (3)**

Malaysia and China mainland
* **Menu and Keyboard:** ENG, CHI, MAY

**PHILIPPINE**

Philippines, Indonesia, China mainland, South Korea, and Vietnam
* **Menu (6):** ENG, IND, VIE, CHI, FIL, KOR
* **Keyboard (5):** ENG, IND, VIE, CHI, KOR

**AUSTRALIA (9)**

Australia, New Zealand, Malaysia, and China mainland
* **Menu and Keyboard:** ENG, CHI, KOR, FRA, ITA, DEU, SPA, MAY, MAO

**MYANMAR (5)**

Myanmar, Cambodia, Thailand, and China mainland
* **Menu and Keyboard:** ENG, THA, MYA, CAM, CHI


#### China

**TAIWAN (2)**
* **Menu and Keyboard:** ENG, TPE

**CHINA (2)**
* **Menu and Keyboard:** ENG, CHI

**HONGKONG (3)**

Hong Kong and China mainland
* **Menu and Keyboard:** ENG, HKG, CHI


#### Japan

**JAPAN (2)**
* **Menu and Keyboard:** ENG_US, JPN


## Appendix

### Language Codes

| Code   | Native Name             | English Name                    |
| ------ | ----------------------- | ------------------------------- |
| AFR    | Afrikaans               | Afrikaans                       |
| IGB    | Asusu Igbo              | Igbo                            |
| AZE    | Azərbaycan              | Azerbaijani                     |
| MAY    | Bahasa Melayu           | Malay                           |
| BOS    | Bosanski                | Bosnian                         |
| CZE    | Čeština                 | Czech                           |
| DAN    | Dansk                   | Danish                          |
| DEU    | Deutsch                 | German                          |
| EST    | Eesti                   | Estonian                        |
| ENG    | English (UK)            | English (UK)                    |
| ENG_US | English (US)            | English (US)                    |
| SPA    | Español (España)        | Spanish (Spain)                 |
| SPA_US | Español (Latinoamérica) | Spanish (Latin America)         |
| FRA_US | Français (Canada)       | French (Canada)                 |
| FRA    | Français (France)       | French (France)                 |
| HAU    | Hausa                   | Hausa                           |
| CRO    | Hrvatski                | Croatian                        |
| IND    | Indonesia               | Indonesian                      |
| XHO    | IsiXhosa                | Xhosa                           |
| ZUL    | IsiZulu                 | Zulu                            |
| ITA    | Italiano                | Italian                         |
| SWA    | Kiswahili               | Swahili                         |
| KUR    | Kurmancî                | Kurmanji                        |
| LAT    | Latviešu                | Latvian                         |
| LTU    | Lietuvių                | Lithuanian                      |
| HUN    | Magyar                  | Hungarian                       |
| MAO    | Māori                   | Maori                           |
| DUT    | Nederlands              | Dutch                           |
| NOR    | Norsk                   | Norwegian                       |
| UZB    | O‘zbek                  | Uzbek                           |
| POL    | Polski                  | Polish                          |
| POR_US | Português (Brasil)      | Portuguese (Brazil)             |
| POR    | Português (Portugal)    | Portuguese (Portugal)           |
| ROM    | Română                  | Romanian                        |
| ALB    | Shqip                   | Albanian                        |
| SLK    | Slovenčina              | Slovak                          |
| SLV    | Slovenščina             | Slovenian                       |
| SER    | Srpski                  | Serbian                         |
| FIN    | Suomi                   | Finnish                         |
| SWE    | Svenska                 | Swedish                         |
| FIL    | Tagalog                 | Filipino/Tagalog                |
| VIE    | Tiếng Việt              | Vietnamese                      |
| TUR    | Türkçe                  | Turkish                         |
| YOR    | Yorùbá                  | Yoruba                          |
| GRE    | Ελληνικά                | Greek                           |
| BUL    | Български               | Bulgarian                       |
| KAZ    | Қазақ                   | Kazakh                          |
| MKD    | Македонски              | Macedonian                      |
| MON    | Монгол Улс              | Mongolian                       |
| RUS    | Русский                 | Russian                         |
| UKR    | Українська              | Russian                         |
| GEO    | ქართული                 | Georgian                        |
| ARM    | Հայերեն                 | Armenian                        |
| HEB    | עברית                   | Hebrew                          |
| URD    | اردو                    | Urdu                            |
| ARA    | العربية                 | Arabic                          |
| PER    | فارسی                   | Persian                         |
| SOR    | سۆرانی                  | Sorani Kurdish                  |
| AMH    | አማርኛ                   | Amharic                         |
| KAS    | कॉशुर                    | Kashmiri                        |
| KOK    | कोंकणी                   | Konkani                         |
| NEP    | नेपाली                    | Nepali                          |
| BHI    | भीली                     | Bhili                           |
| MAR    | मराठी                     | Marathi                         |
| MAI    | मैथिली                    | Maithili                        |
| SKR    | संस्कृतम्                   | Sanskrit                        |
| SIN    | सिन्धी                    | Sindhi                          |
| HIN    | हिंदी                     | Hindi                           |
| ASM    | অসমীয়া                  | Assamese                        |
| BEN    | বাংলা                    | Bangla                          |
| MAN    | মণিপুরী                   | Manipuri                        |
| PAN    | ਪੰਜਾਬੀ                    | Punjabi                         |
| GUJ    | ગુજરાતી                   | Gujarati                        |
| ORI    | ଓଡ଼ିଆ                    | Odia                            |
| TAM    | தமிழ்                    | Tamil                           |
| TEL    | తెలుగు                   | Telugu                          |
| KAN    | ಕನ್ನಡ                    | Kannada                         |
| TUL    | ತುಳು                    | Tulu                            |
| MAL    | മലയാളം                 | Malayalam                       |
| THA    | ไทย                    | Thai                            |
| MYA    | မြန်မာ                   | Burmese                         |
| CAM    | ខ្មែរ                     | Khmer                           |
| SAN    | ᱞᱟᱝᱠᱠᱭᱦ                | Santali                         |
| KOR    | 한국어                   | Korean                          |
| TPE    | 國語                    | Traditional Chinese (Taiwan)    |
| JPN    | 日本語                   | Japanese                        |
| CHI    | 简体中文                 | Simplified Chinese              |
| HKG    | 繁體中文                  | Traditional Chinese (Hong Kong) |





## License

LGPL-3.0
