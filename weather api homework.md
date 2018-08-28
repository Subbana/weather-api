
# weatherPy

### 3 trend


```python
# Import dependencies
import openweathermapy as ow
from citipy import citipy
import pandas as pd
import numpy as np
import requests
import json
from random import uniform
import matplotlib.pyplot as plt

# import api_key from config file
from config import api_key
```


```python
# collect information about weather from 1500 cities
city_location = []
coordinates = []
for i in range (1500):
    random = uniform(-90,90), uniform(-180,180)
    coordinates.append(random)
for lat_long in coordinates:
    lat, long = lat_long
    city_location.append(citipy.nearest_city(lat, long))
```


```python
# get name of cities
cities = []
for city in city_location:
    name = city.city_name
    cities.append(name)
city_unique = set(cities)
```


```python
# Save config information.# Save  
url = "http://api.openweathermap.org/data/2.5/weather?"
units = "imperial"

# Build partial query URL
query_url = f"{url}appid={api_key}&units={units}&q="
for printed_url in city_unique: 
    print(f"{query_url}{printed_url}")
```

    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=senmonorom
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rusape
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=boromo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=acapulco
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yamachiche
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=margate
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=murray bridge
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=torbay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=shelopugino
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint-georges
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lokosovo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=oranjemund
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kokkola
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ibra
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=znamenskoye
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=klaksvik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=skagastrond
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=southbridge
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san lazaro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=olafsvik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=brae
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tibagi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=roros
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=norman wells
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=domoni
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pandan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mahibadhoo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=harper
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=balabac
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cotonou
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=encheng
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=northam
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port macquarie
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mogilno
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bol
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=shelburne
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=louisbourg
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=marienburg
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=plouzane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vostok
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tabou
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=souillac
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=banda aceh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dutlwe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nouakchott
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yumen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=labuhan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=luangwa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tautira
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nova odesa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sioux lookout
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=touros
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ferrol
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=zhigansk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=itarema
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kuusamo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=helong
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=havelock
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sri aman
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cabedelo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=abha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=jiancheng
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gondanglegi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=zyryanka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=miraflores
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=razdolnaya
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tilichiki
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hirado
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=maloshuyka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kindu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yerbogachen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cape town
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=khowst
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=fulda
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kapuskasing
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ruatoria
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kajaani
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=almaznyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=egvekinot
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sisimiut
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=solovetskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=esmeraldas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sokoni
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=umzimvubu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=namatanai
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bari
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=borujerd
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bad urach
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=haibowan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=thurso
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cururupu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lemesos
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=waingapu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hami
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=placido de castro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=taketa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=amparafaravola
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=houma
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tasiilaq
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=marcona
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kushmurun
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gharb
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=coquimbo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=quelimane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=chokurdakh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=digby
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=banos
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=poum
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kandrian
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bredasdorp
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=teya
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=townsville
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dikson
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=natal
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mozhga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bonthe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=trairi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ulaanbaatar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=boende
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aitape
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=umm durman
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=moses lake
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=den helder
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ponnani
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mauganj
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tura
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=naze
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sao filipe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kultuk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lazaro cardenas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=grindavik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nikolskoye-na-cheremshane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=soria
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lakes entrance
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=huaibei
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yellowknife
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=carutapera
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=maceio
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=puerto escondido
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vaini
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hofn
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bekhteyevka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tuatapere
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saldanha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nanortalik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=necochea
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=puerto narino
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aktau
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lubbock
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gus-zheleznyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=palana
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=urbino
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mocuba
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dolores
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=iacu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tsentralnyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=elko
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wukari
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=isangel
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=russell
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint-philippe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=clyde river
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tsihombe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kofarnihon
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bloomfield
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=anchorage
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=oriximina
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gilgil
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=trat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yarada
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=albany
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ararat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nishihara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bengkulu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=chumikan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=fairbanks
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=biltine
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=labuan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=snyder
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tiarei
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lebu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hermanus
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=artigas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=amderma
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dingle
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=panguna
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hilo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=talnakh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vila velha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ilulissat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=anadyr
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=skjervoy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mys shmidta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mandalgovi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=arona
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=richards bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=superior
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kapit
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rudbar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mount gambier
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=leh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sola
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint george
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=baherden
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=samalaeulu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=barentsburg
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=khatanga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lolua
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=fortuna
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=halalo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=stornoway
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=marzuq
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lumphat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=keti bandar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dauphin
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=prabumulih
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gigmoto
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=orodara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bestobe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=luderitz
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dongsheng
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=haines junction
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rumoi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=soyo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=utete
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mrirt
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ipixuna
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=quanzhou
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=henties bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tiksi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=warqla
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=huilong
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pevek
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=calvia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wana
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pedro carbo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=chuy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=taiping
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=khingansk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=batagay-alyta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nhulunbuy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bredy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wloszczowa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tumannyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san manuel chaparron
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hirara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=constantine
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=shirokiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=burnie
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=half moon bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=qaanaaq
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=beisfjord
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bin qirdan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=albacete
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint-pierre
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=baghmara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hithadhoo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yanam
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aripuana
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=zhetysay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hualmay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint-joseph
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lagoa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ulladulla
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nome
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=grand river south east
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=khandyga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kristianstad
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=alta floresta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=punta arenas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=faanui
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=straumen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=qaqortoq
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=beloha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=damietta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=neiafu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=japura
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=samusu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=riacho de santana
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=verkh-usugli
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nuuk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=srandakan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=jiuquan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port elizabeth
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cayenne
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=panjakent
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dandong
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sfantu gheorghe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=suntar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=two rivers
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pisco
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=uray
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=misratah
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tsienyane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sao joao da barra
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bilibino
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dwarka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mana
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=barrow
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kavieng
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mikkeli
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint anthony
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=comodoro rivadavia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=senador jose porfirio
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=broome
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=totolapa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=taolanaro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lucapa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=deputatskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=artyk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=duz
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cockburn town
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=urozhaynoye
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=plettenberg bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=champerico
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ribeira grande
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kalmunai
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gamba
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=codrington
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=avarua
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=jibuti
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=busselton
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=esso
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tinskoy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=malakal
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ambon
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=killybegs
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ilinsko-podomskoye
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=karamea
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mochudi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ghanzi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bismarck
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aberdeen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=provideniya
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dickinson
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mayma
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=palabuhanratu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mar del plata
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saskylakh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cidreira
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=oxapampa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=casino
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san quintin
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saint-denis
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=svetlyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=urumqi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sitka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tabuk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=siimusti
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mareeba
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=iqaluit
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mantua
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=el alto
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kodiak
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vestmanna
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ivangorod
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port hardy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=youhao
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aykhal
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ahuimanu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=requena
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=berdigestyakh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=urucara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=carnarvon
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=castro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=belushya guba
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mataura
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=antalaha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mount isa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=carcassonne
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=caravelas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=anloga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=okhotsk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sinjah
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rosarito
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=samarai
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=esil
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port alfred
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bathsheba
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=atasu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=longyearbyen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lhokseumawe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=coihaique
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=do rud
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port keats
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hobyo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mahebourg
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=popondetta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kirakira
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yabelo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=visnes
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=martapura
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=fort saint john
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pitimbu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=luebo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vila franca do campo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=petropavlovsk-kamchatskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mayo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=komsomolets
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ancud
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=costinesti
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=molchanovo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cedar city
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=thompson
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sarkand
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ondorhaan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=shingu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=muli
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=atuona
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=puerto del rosario
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kahului
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lorengau
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sept-iles
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ligayan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ushuaia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sergeyevka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=awbari
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bowen
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=inhambane
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port hawkesbury
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=new norfolk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=port-gentil
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wisconsin rapids
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bayir
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=constitucion
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=salamanca
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hasaki
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=adrar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=padang
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sungai besar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dekoa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=voznesenye
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=campbell river
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=upernavik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hobart
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=fukuma
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kamaishi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yar-sale
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lasa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gzhatsk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kruisfontein
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hue
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bur gabo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=muisne
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=airai
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pottsville
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bonavista
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tual
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sterling
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=husavik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nikolskoye
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aklavik
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hihifo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bastia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kemijarvi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=karratha
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hammerfest
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ranfurly
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pozzallo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=asau
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=garden city
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aguilas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mao
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bafra
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rawson
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=celestun
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=magam
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=la tuque
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kudahuvadhoo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=viedma
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=seguela
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nioro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=flinders
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bluff
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=antu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=paoua
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kiruna
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=qazvin
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=antofagasta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tambul
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nemuro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=geraldton
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mehamn
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=blanquefort
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=attawapiskat
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san patricio
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=great falls
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=loiza
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ouesso
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=honningsvag
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=emirdag
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=boca do acre
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=zuwarah
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=esperance
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=east london
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=georgetown
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kedougou
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mbandaka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=taltal
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mount darwin
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=igrim
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lompoc
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=komsomolskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=west bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tezu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=batemans bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=zapolyarnyy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vardo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ballater
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lipari
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=andenes
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hearst
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=leiyang
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=altay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ngukurr
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bongandanga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ahipara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=benguela
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san ciro de acosta
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=puerto ayora
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=leningradskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bashtanka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=puerto colombia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ust-omchug
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=maues
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=maridi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=chiria
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=saryshagan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=stryn
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=rikitea
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=belaya gora
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=yaring
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=toliary
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bambous virieux
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=cherskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=verkhnevilyuysk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wewak
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=san policarpo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=lusambo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=batagay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=jaguariaiva
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=huanuni
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=satara
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ituni
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kapaa
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=daru
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=nalut
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mirabad
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sabalgarh
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sao felix do xingu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=harbour breton
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=pangnirtung
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kaitangata
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=guerrero negro
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bridlington
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gezing
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kwekwe
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=beni
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bacuit
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=inyonga
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=salinas
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=najran
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=del rio
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=merauke
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=inirida
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tutoia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=gao
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hamilton
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hudiksvall
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=menongue
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=srednekolymsk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=butaritari
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ugoofaaru
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=mumford
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=dongli
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=carahue
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=srivardhan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=butembo
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hit
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=maragogi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=shaoyang
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hervey bay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=jamestown
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=buala
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ponta do sol
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sinnamary
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=sorvag
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=ngunguru
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=achisay
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aksarka
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=wahran
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=hambantota
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=salinopolis
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=kavaratti
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=tazovskiy
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=iberia
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=bethel
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=aswan
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=alofi
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=vaitupu
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=katsuura
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=victoria
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=meru
    http://api.openweathermap.org/data/2.5/weather?appid=c990d19da8b95bb4cd3d357bcebfc5d0&units=imperial&q=udachnyy
    


```python
city_temp = []
lat = []
lon = []
date = []
clouds = []
wind =[]
name = []
country = []
humidity =[]
for city in city_unique:
    try:
        print(f"Now collect {city} city infomation")
        response = requests.get(query_url + city).json()
        lat.append(response['coord']['lat'])
        city_temp.append(response['main']['temp_max'])
        lon.append(response['coord']['lon'])
        date.append(response['dt'])
        clouds.append(response['clouds']['all']) 
        wind.append(response['wind']['speed'])
        name.append(response['name'])
        country.append(response['sys']['country'])
        humidity.append(response['main']['humidity'])
    except: 
        print("Didn't find any info")
```

    Now collect senmonorom city infomation
    Didn't find any info
    Now collect rusape city infomation
    Now collect boromo city infomation
    Now collect acapulco city infomation
    Now collect yamachiche city infomation
    Now collect margate city infomation
    Now collect murray bridge city infomation
    Now collect torbay city infomation
    Now collect shelopugino city infomation
    Now collect saint-georges city infomation
    Now collect lokosovo city infomation
    Now collect oranjemund city infomation
    Now collect kokkola city infomation
    Now collect nizhneyansk city infomation
    Didn't find any info
    Now collect ibra city infomation
    Now collect znamenskoye city infomation
    Now collect klaksvik city infomation
    Now collect skagastrond city infomation
    Didn't find any info
    Now collect southbridge city infomation
    Now collect san lazaro city infomation
    Now collect olafsvik city infomation
    Didn't find any info
    Now collect brae city infomation
    Now collect tibagi city infomation
    Now collect roros city infomation
    Now collect norman wells city infomation
    Now collect domoni city infomation
    Didn't find any info
    Now collect pandan city infomation
    Now collect mahibadhoo city infomation
    Now collect harper city infomation
    Now collect balabac city infomation
    Now collect cotonou city infomation
    Now collect encheng city infomation
    Now collect northam city infomation
    Now collect port macquarie city infomation
    Now collect mogilno city infomation
    Now collect bol city infomation
    Now collect shelburne city infomation
    Now collect louisbourg city infomation
    Didn't find any info
    Now collect illoqqortoormiut city infomation
    Didn't find any info
    Now collect marienburg city infomation
    Now collect plouzane city infomation
    Now collect vostok city infomation
    Now collect tabou city infomation
    Now collect souillac city infomation
    Now collect cabo san lucas city infomation
    Now collect banda aceh city infomation
    Now collect dutlwe city infomation
    Now collect nouakchott city infomation
    Now collect yumen city infomation
    Now collect labuhan city infomation
    Now collect luangwa city infomation
    Now collect tautira city infomation
    Now collect nova odesa city infomation
    Now collect sioux lookout city infomation
    Now collect touros city infomation
    Now collect ferrol city infomation
    Now collect zhigansk city infomation
    Now collect itarema city infomation
    Now collect kuusamo city infomation
    Now collect helong city infomation
    Now collect havelock city infomation
    Now collect sri aman city infomation
    Now collect cabedelo city infomation
    Now collect abha city infomation
    Now collect jiancheng city infomation
    Now collect gondanglegi city infomation
    Now collect zyryanka city infomation
    Now collect miraflores city infomation
    Now collect razdolnaya city infomation
    Now collect tilichiki city infomation
    Now collect hirado city infomation
    Now collect maloshuyka city infomation
    Didn't find any info
    Now collect kindu city infomation
    Now collect yerbogachen city infomation
    Now collect cape town city infomation
    Now collect khowst city infomation
    Didn't find any info
    Now collect fulda city infomation
    Now collect kapuskasing city infomation
    Now collect ruatoria city infomation
    Didn't find any info
    Now collect kajaani city infomation
    Now collect almaznyy city infomation
    Now collect egvekinot city infomation
    Now collect sisimiut city infomation
    Now collect solovetskiy city infomation
    Didn't find any info
    Now collect esmeraldas city infomation
    Now collect sokoni city infomation
    Now collect umzimvubu city infomation
    Didn't find any info
    Now collect namatanai city infomation
    Now collect bari city infomation
    Didn't find any info
    Now collect borujerd city infomation
    Now collect bad urach city infomation
    Now collect sentyabrskiy city infomation
    Didn't find any info
    Now collect haibowan city infomation
    Didn't find any info
    Now collect thurso city infomation
    Now collect cururupu city infomation
    Now collect lemesos city infomation
    Didn't find any info
    Now collect waingapu city infomation
    Now collect hami city infomation
    Now collect placido de castro city infomation
    Now collect taketa city infomation
    Now collect amparafaravola city infomation
    Now collect houma city infomation
    Now collect tasiilaq city infomation
    Now collect marcona city infomation
    Didn't find any info
    Now collect kushmurun city infomation
    Didn't find any info
    Now collect gharb city infomation
    Didn't find any info
    Now collect coquimbo city infomation
    Now collect los llanos de aridane city infomation
    Now collect tuktoyaktuk city infomation
    Now collect quelimane city infomation
    Now collect chokurdakh city infomation
    Now collect digby city infomation
    Now collect banos city infomation
    Now collect poum city infomation
    Now collect kandrian city infomation
    Now collect bredasdorp city infomation
    Now collect teya city infomation
    Now collect townsville city infomation
    Now collect dikson city infomation
    Now collect natal city infomation
    Now collect mozhga city infomation
    Now collect bonthe city infomation
    Now collect trairi city infomation
    Now collect ulaanbaatar city infomation
    Now collect boende city infomation
    Now collect aitape city infomation
    Now collect umm durman city infomation
    Didn't find any info
    Now collect moses lake city infomation
    Now collect den helder city infomation
    Now collect ponnani city infomation
    Now collect mauganj city infomation
    Now collect tura city infomation
    Now collect naze city infomation
    Now collect gat city infomation
    Now collect sao filipe city infomation
    Now collect kultuk city infomation
    Now collect lazaro cardenas city infomation
    Now collect grindavik city infomation
    Now collect nikolskoye-na-cheremshane city infomation
    Didn't find any info
    Now collect soria city infomation
    Now collect lakes entrance city infomation
    Now collect huaibei city infomation
    Now collect yellowknife city infomation
    Now collect carutapera city infomation
    Now collect maceio city infomation
    Now collect puerto escondido city infomation
    Now collect vaini city infomation
    Now collect hofn city infomation
    Now collect bekhteyevka city infomation
    Now collect tuatapere city infomation
    Now collect saldanha city infomation
    Now collect nanortalik city infomation
    Now collect necochea city infomation
    Now collect puerto narino city infomation
    Now collect aktau city infomation
    Now collect lubbock city infomation
    Now collect gus-zheleznyy city infomation
    Now collect palana city infomation
    Now collect urbino city infomation
    Now collect mocuba city infomation
    Now collect dolores city infomation
    Now collect arraial do cabo city infomation
    Now collect iacu city infomation
    Now collect tsentralnyy city infomation
    Didn't find any info
    Now collect elko city infomation
    Now collect wukari city infomation
    Now collect isangel city infomation
    Now collect russell city infomation
    Now collect saint-philippe city infomation
    Now collect clyde river city infomation
    Now collect tsihombe city infomation
    Didn't find any info
    Now collect kofarnihon city infomation
    Didn't find any info
    Now collect bloomfield city infomation
    Now collect anchorage city infomation
    Now collect oriximina city infomation
    Now collect gilgil city infomation
    Didn't find any info
    Now collect trat city infomation
    Now collect yarada city infomation
    Now collect albany city infomation
    Now collect ararat city infomation
    Now collect nishihara city infomation
    Now collect bengkulu city infomation
    Didn't find any info
    Now collect chumikan city infomation
    Now collect fairbanks city infomation
    Now collect biltine city infomation
    Now collect labuan city infomation
    Now collect snyder city infomation
    Now collect tiarei city infomation
    Now collect lebu city infomation
    Now collect hermanus city infomation
    Now collect artigas city infomation
    Now collect amderma city infomation
    Didn't find any info
    Now collect dingle city infomation
    Now collect panguna city infomation
    Now collect hilo city infomation
    Now collect talnakh city infomation
    Now collect vila velha city infomation
    Now collect ilulissat city infomation
    Now collect anadyr city infomation
    Now collect skjervoy city infomation
    Now collect mys shmidta city infomation
    Didn't find any info
    Now collect mandalgovi city infomation
    Now collect arona city infomation
    Now collect richards bay city infomation
    Now collect superior city infomation
    Now collect kapit city infomation
    Now collect rudbar city infomation
    Didn't find any info
    Now collect mount gambier city infomation
    Now collect leh city infomation
    Now collect sola city infomation
    Now collect saint george city infomation
    Now collect baherden city infomation
    Now collect samalaeulu city infomation
    Didn't find any info
    Now collect barentsburg city infomation
    Didn't find any info
    Now collect khatanga city infomation
    Now collect lolua city infomation
    Didn't find any info
    Now collect fortuna city infomation
    Now collect halalo city infomation
    Didn't find any info
    Now collect stornoway city infomation
    Didn't find any info
    Now collect marzuq city infomation
    Now collect lumphat city infomation
    Now collect keti bandar city infomation
    Now collect dauphin city infomation
    Now collect prabumulih city infomation
    Now collect gigmoto city infomation
    Now collect orodara city infomation
    Now collect bestobe city infomation
    Now collect luderitz city infomation
    Now collect dongsheng city infomation
    Now collect haines junction city infomation
    Now collect rumoi city infomation
    Now collect soyo city infomation
    Now collect utete city infomation
    Now collect mrirt city infomation
    Didn't find any info
    Now collect ipixuna city infomation
    Now collect quanzhou city infomation
    Now collect henties bay city infomation
    Now collect tiksi city infomation
    Now collect warqla city infomation
    Didn't find any info
    Now collect huilong city infomation
    Now collect pevek city infomation
    Now collect calvia city infomation
    Now collect wana city infomation
    Now collect pedro carbo city infomation
    Now collect chuy city infomation
    Now collect taiping city infomation
    Now collect khingansk city infomation
    Now collect batagay-alyta city infomation
    Now collect nhulunbuy city infomation
    Now collect bredy city infomation
    Now collect wloszczowa city infomation
    Now collect tumannyy city infomation
    Didn't find any info
    Now collect san manuel chaparron city infomation
    Now collect hirara city infomation
    Now collect constantine city infomation
    Now collect shirokiy city infomation
    Now collect burnie city infomation
    Now collect half moon bay city infomation
    Now collect qaanaaq city infomation
    Now collect beisfjord city infomation
    Now collect bin qirdan city infomation
    Now collect albacete city infomation
    Now collect saint-pierre city infomation
    Now collect baghmara city infomation
    Now collect hithadhoo city infomation
    Now collect yanam city infomation
    Now collect aripuana city infomation
    Now collect zhetysay city infomation
    Now collect hualmay city infomation
    Now collect saint-joseph city infomation
    Now collect lagoa city infomation
    Now collect ulladulla city infomation
    Now collect nome city infomation
    Now collect grand river south east city infomation
    Didn't find any info
    Now collect khandyga city infomation
    Now collect kristianstad city infomation
    Now collect alta floresta city infomation
    Now collect punta arenas city infomation
    Now collect faanui city infomation
    Now collect straumen city infomation
    Now collect qaqortoq city infomation
    Now collect beloha city infomation
    Now collect damietta city infomation
    Now collect neiafu city infomation
    Now collect japura city infomation
    Now collect samusu city infomation
    Didn't find any info
    Now collect riacho de santana city infomation
    Now collect verkh-usugli city infomation
    Now collect nuuk city infomation
    Now collect srandakan city infomation
    Now collect jiuquan city infomation
    Now collect port elizabeth city infomation
    Now collect cayenne city infomation
    Now collect panjakent city infomation
    Now collect dandong city infomation
    Now collect sfantu gheorghe city infomation
    Now collect suntar city infomation
    Now collect two rivers city infomation
    Now collect pisco city infomation
    Now collect uray city infomation
    Now collect misratah city infomation
    Now collect tsienyane city infomation
    Didn't find any info
    Now collect sao joao da barra city infomation
    Now collect bilibino city infomation
    Now collect dwarka city infomation
    Now collect mana city infomation
    Now collect barrow city infomation
    Now collect kavieng city infomation
    Now collect mikkeli city infomation
    Now collect saint anthony city infomation
    Now collect comodoro rivadavia city infomation
    Now collect senador jose porfirio city infomation
    Now collect broome city infomation
    Now collect totolapa city infomation
    Now collect taolanaro city infomation
    Didn't find any info
    Now collect lucapa city infomation
    Now collect deputatskiy city infomation
    Now collect artyk city infomation
    Didn't find any info
    Now collect duz city infomation
    Didn't find any info
    Now collect cockburn town city infomation
    Now collect urozhaynoye city infomation
    Now collect plettenberg bay city infomation
    Now collect champerico city infomation
    Now collect ribeira grande city infomation
    Now collect kalmunai city infomation
    Now collect gamba city infomation
    Now collect codrington city infomation
    Now collect avarua city infomation
    Now collect jibuti city infomation
    Didn't find any info
    Now collect busselton city infomation
    Now collect esso city infomation
    Now collect tinskoy city infomation
    Now collect malakal city infomation
    Didn't find any info
    Now collect ambon city infomation
    Now collect killybegs city infomation
    Now collect ilinsko-podomskoye city infomation
    Didn't find any info
    Now collect karamea city infomation
    Didn't find any info
    Now collect mochudi city infomation
    Now collect ghanzi city infomation
    Now collect bismarck city infomation
    Now collect aberdeen city infomation
    Now collect provideniya city infomation
    Now collect dickinson city infomation
    Now collect mayma city infomation
    Now collect palabuhanratu city infomation
    Didn't find any info
    Now collect mar del plata city infomation
    Now collect saskylakh city infomation
    Now collect cidreira city infomation
    Now collect oxapampa city infomation
    Now collect casino city infomation
    Now collect san quintin city infomation
    Now collect saint-denis city infomation
    Now collect svetlyy city infomation
    Didn't find any info
    Now collect urumqi city infomation
    Didn't find any info
    Now collect sitka city infomation
    Now collect tabuk city infomation
    Now collect siimusti city infomation
    Now collect mareeba city infomation
    Now collect iqaluit city infomation
    Now collect mantua city infomation
    Now collect el alto city infomation
    Now collect kodiak city infomation
    Now collect vestmanna city infomation
    Now collect ivangorod city infomation
    Now collect port hardy city infomation
    Now collect youhao city infomation
    Now collect aykhal city infomation
    Now collect ahuimanu city infomation
    Now collect requena city infomation
    Now collect berdigestyakh city infomation
    Now collect urucara city infomation
    Now collect carnarvon city infomation
    Now collect castro city infomation
    Now collect belushya guba city infomation
    Didn't find any info
    Now collect mataura city infomation
    Now collect antalaha city infomation
    Now collect mount isa city infomation
    Now collect carcassonne city infomation
    Now collect caravelas city infomation
    Now collect anloga city infomation
    Now collect okhotsk city infomation
    Now collect sinjah city infomation
    Didn't find any info
    Now collect rosarito city infomation
    Now collect samarai city infomation
    Now collect esil city infomation
    Now collect port alfred city infomation
    Now collect bathsheba city infomation
    Now collect atasu city infomation
    Now collect longyearbyen city infomation
    Now collect lhokseumawe city infomation
    Now collect coihaique city infomation
    Now collect do rud city infomation
    Didn't find any info
    Now collect port keats city infomation
    Now collect hobyo city infomation
    Now collect mahebourg city infomation
    Now collect popondetta city infomation
    Now collect kirakira city infomation
    Now collect yabelo city infomation
    Now collect visnes city infomation
    Now collect martapura city infomation
    Now collect fort saint john city infomation
    Didn't find any info
    Now collect pitimbu city infomation
    Now collect luebo city infomation
    Now collect vila franca do campo city infomation
    Now collect petropavlovsk-kamchatskiy city infomation
    Now collect mayo city infomation
    Now collect komsomolets city infomation
    Now collect ancud city infomation
    Now collect costinesti city infomation
    Now collect molchanovo city infomation
    Now collect cedar city city infomation
    Now collect thompson city infomation
    Now collect sarkand city infomation
    Now collect ondorhaan city infomation
    Didn't find any info
    Now collect shingu city infomation
    Now collect muli city infomation
    Now collect atuona city infomation
    Now collect puerto del rosario city infomation
    Now collect kahului city infomation
    Now collect lorengau city infomation
    Now collect sept-iles city infomation
    Now collect ligayan city infomation
    Now collect ushuaia city infomation
    Now collect sergeyevka city infomation
    Now collect awbari city infomation
    Now collect bowen city infomation
    Now collect inhambane city infomation
    Now collect port hawkesbury city infomation
    Now collect new norfolk city infomation
    Now collect port-gentil city infomation
    Now collect wisconsin rapids city infomation
    Now collect bayir city infomation
    Now collect constitucion city infomation
    Now collect salamanca city infomation
    Now collect hasaki city infomation
    Now collect adrar city infomation
    Now collect padang city infomation
    Now collect sungai besar city infomation
    Now collect dekoa city infomation
    Didn't find any info
    Now collect voznesenye city infomation
    Now collect campbell river city infomation
    Now collect upernavik city infomation
    Now collect hobart city infomation
    Now collect fukuma city infomation
    Now collect kamaishi city infomation
    Now collect yar-sale city infomation
    Now collect lasa city infomation
    Now collect gzhatsk city infomation
    Didn't find any info
    Now collect kruisfontein city infomation
    Now collect hue city infomation
    Now collect bur gabo city infomation
    Didn't find any info
    Now collect muisne city infomation
    Now collect airai city infomation
    Now collect pottsville city infomation
    Now collect bonavista city infomation
    Now collect tual city infomation
    Now collect sterling city infomation
    Now collect husavik city infomation
    Now collect nikolskoye city infomation
    Now collect aklavik city infomation
    Now collect hihifo city infomation
    Didn't find any info
    Now collect bastia city infomation
    Now collect kemijarvi city infomation
    Didn't find any info
    Now collect karratha city infomation
    Now collect hammerfest city infomation
    Now collect ranfurly city infomation
    Now collect pozzallo city infomation
    Now collect asau city infomation
    Didn't find any info
    Now collect garden city city infomation
    Now collect aguilas city infomation
    Now collect mao city infomation
    Now collect bafra city infomation
    Didn't find any info
    Now collect rawson city infomation
    Now collect celestun city infomation
    Now collect magam city infomation
    Now collect la tuque city infomation
    Now collect kudahuvadhoo city infomation
    Now collect viedma city infomation
    Now collect seguela city infomation
    Now collect nioro city infomation
    Now collect vestmannaeyjar city infomation
    Now collect flinders city infomation
    Now collect bluff city infomation
    Now collect antu city infomation
    Now collect paoua city infomation
    Now collect kiruna city infomation
    Now collect qazvin city infomation
    Now collect antofagasta city infomation
    Now collect tambul city infomation
    Didn't find any info
    Now collect nemuro city infomation
    Now collect geraldton city infomation
    Now collect mehamn city infomation
    Now collect blanquefort city infomation
    Now collect attawapiskat city infomation
    Didn't find any info
    Now collect san patricio city infomation
    Now collect great falls city infomation
    Now collect loiza city infomation
    Now collect ouesso city infomation
    Now collect honningsvag city infomation
    Now collect emirdag city infomation
    Now collect boca do acre city infomation
    Now collect zuwarah city infomation
    Now collect esperance city infomation
    Now collect east london city infomation
    Now collect georgetown city infomation
    Now collect kedougou city infomation
    Now collect mbandaka city infomation
    Now collect taltal city infomation
    Now collect ostrovnoy city infomation
    Now collect mount darwin city infomation
    Now collect igrim city infomation
    Now collect lompoc city infomation
    Now collect komsomolskiy city infomation
    Now collect west bay city infomation
    Now collect tezu city infomation
    Now collect batemans bay city infomation
    Now collect zapolyarnyy city infomation
    Now collect vardo city infomation
    Now collect ballater city infomation
    Now collect lipari city infomation
    Now collect andenes city infomation
    Didn't find any info
    Now collect hearst city infomation
    Now collect leiyang city infomation
    Now collect altay city infomation
    Now collect ngukurr city infomation
    Didn't find any info
    Now collect bongandanga city infomation
    Now collect ahipara city infomation
    Now collect benguela city infomation
    Now collect san ciro de acosta city infomation
    Now collect puerto ayora city infomation
    Now collect leningradskiy city infomation
    Now collect bashtanka city infomation
    Now collect puerto colombia city infomation
    Now collect ust-omchug city infomation
    Now collect maues city infomation
    Now collect maridi city infomation
    Didn't find any info
    Now collect chiria city infomation
    Now collect saryshagan city infomation
    Didn't find any info
    Now collect stryn city infomation
    Now collect rikitea city infomation
    Now collect belaya gora city infomation
    Now collect yaring city infomation
    Now collect toliary city infomation
    Didn't find any info
    Now collect bambous virieux city infomation
    Now collect cherskiy city infomation
    Now collect verkhnevilyuysk city infomation
    Now collect wewak city infomation
    Now collect san policarpo city infomation
    Now collect lusambo city infomation
    Now collect batagay city infomation
    Now collect jaguariaiva city infomation
    Now collect huanuni city infomation
    Now collect satara city infomation
    Now collect ituni city infomation
    Didn't find any info
    Now collect kapaa city infomation
    Now collect daru city infomation
    Now collect nalut city infomation
    Now collect mirabad city infomation
    Now collect sabalgarh city infomation
    Now collect sao felix do xingu city infomation
    Now collect harbour breton city infomation
    Now collect pangnirtung city infomation
    Now collect kaitangata city infomation
    Now collect guerrero negro city infomation
    Now collect bridlington city infomation
    Now collect gezing city infomation
    Now collect kwekwe city infomation
    Now collect beni city infomation
    Now collect bacuit city infomation
    Didn't find any info
    Now collect inyonga city infomation
    Now collect salinas city infomation
    Now collect najran city infomation
    Now collect del rio city infomation
    Now collect merauke city infomation
    Now collect inirida city infomation
    Now collect tutoia city infomation
    Now collect gao city infomation
    Now collect hamilton city infomation
    Now collect hudiksvall city infomation
    Now collect menongue city infomation
    Now collect srednekolymsk city infomation
    Now collect butaritari city infomation
    Now collect ugoofaaru city infomation
    Now collect mumford city infomation
    Now collect dongli city infomation
    Now collect carahue city infomation
    Now collect srivardhan city infomation
    Now collect butembo city infomation
    Now collect hit city infomation
    Now collect maragogi city infomation
    Now collect shaoyang city infomation
    Now collect hervey bay city infomation
    Now collect jamestown city infomation
    Now collect buala city infomation
    Now collect ponta do sol city infomation
    Now collect sinnamary city infomation
    Now collect sorvag city infomation
    Didn't find any info
    Now collect ngunguru city infomation
    Now collect achisay city infomation
    Didn't find any info
    Now collect aksarka city infomation
    Now collect wahran city infomation
    Didn't find any info
    Now collect hambantota city infomation
    Now collect salinopolis city infomation
    Now collect severo-kurilsk city infomation
    Now collect kavaratti city infomation
    Now collect tazovskiy city infomation
    Now collect iberia city infomation
    Now collect bethel city infomation
    Now collect aswan city infomation
    Now collect alofi city infomation
    Now collect vaitupu city infomation
    Didn't find any info
    Now collect katsuura city infomation
    Now collect victoria city infomation
    Now collect meru city infomation
    Now collect udachnyy city infomation
    


```python
# create data frame
weather_dic = {
    "City": name,
    "Latitude":lat,
    "Longitude": lon,
    "date":date,
    "Max Temperature": city_temp,
    "Cloudiness":clouds,
    "Windspeed":wind,
    "Humidity":humidity
}
weather_df = pd.DataFrame(weather_dic)
weather_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>date</th>
      <th>Max Temperature</th>
      <th>Cloudiness</th>
      <th>Windspeed</th>
      <th>Humidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Rusape</td>
      <td>-18.53</td>
      <td>32.12</td>
      <td>1535430482</td>
      <td>46.66</td>
      <td>0</td>
      <td>2.59</td>
      <td>93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Boromo</td>
      <td>11.74</td>
      <td>-2.93</td>
      <td>1535430482</td>
      <td>74.02</td>
      <td>0</td>
      <td>5.17</td>
      <td>88</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Acapulco</td>
      <td>16.86</td>
      <td>-99.88</td>
      <td>1535428140</td>
      <td>75.20</td>
      <td>90</td>
      <td>11.41</td>
      <td>94</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Yamachiche</td>
      <td>46.28</td>
      <td>-72.83</td>
      <td>1535430482</td>
      <td>70.69</td>
      <td>92</td>
      <td>12.44</td>
      <td>91</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Margate</td>
      <td>-43.03</td>
      <td>147.26</td>
      <td>1535428800</td>
      <td>50.00</td>
      <td>40</td>
      <td>17.22</td>
      <td>87</td>
    </tr>
  </tbody>
</table>
</div>




```python
#saving Datafile to a CSV
weather_df.to_csv("Weather_DataFrame.csv", index=False, header=True)
```


```python
# at least 500 cities
print(len(city_unique))
```

    615
    


```python
# Latitude vs temperature plot
# create the plot by seaborn
import seaborn 
seaborn.lmplot(x='Latitude', y='Max Temperature',data=weather_df, fit_reg=False, markers='o',
            scatter_kws={'edgecolors':'black',
                           'color': 'blue'},
            size=6,
            aspect=2)

# title and labels
plt.title("City Latitude vs. Max Temperature 8/27/2017", fontsize=20)
plt.xlabel("Latitude", fontsize=15)
plt.ylabel("Max Temperature (F)", fontsize=15)
# ticks size
plt.xticks(fontsize=15)
plt.yticks(fontsize=15)
# set x and y limits
plt.xlim(weather_df['Latitude'].min()-10,weather_df['Latitude'].max()+10)
plt.ylim(weather_df['Max Temperature'].min()-10, weather_df['Max Temperature'].max() +10)
plt.savefig("latitude vs max temperature.png")
plt.show()
```


![png](output_10_0.png)



```python
# Latitude vs humidity plot
seaborn.lmplot(x='Latitude', y='Humidity',data=weather_df, fit_reg=False, markers='o',
            scatter_kws={'edgecolors':'black',
                           'color': 'blue'},
            size=6,
            aspect=2)

# title and labels
plt.title("City Latitude vs. Humidity 8/27/2017", fontsize=20)
plt.xlabel("Latitude", fontsize=15)
plt.ylabel("Humidity(%)", fontsize=15)
# ticks size
plt.xticks(fontsize=15)
plt.yticks(fontsize=15)
# set x and y limits
plt.xlim(weather_df['Latitude'].min()-10,weather_df['Latitude'].max()+10)
plt.ylim(weather_df['Humidity'].min()-10, weather_df['Humidity'].max() +10)
plt.savefig("latitude vs humidity.png")
plt.show()
```


![png](output_11_0.png)



```python
# Latitude vs wind speed plot
seaborn.lmplot(x='Latitude', y='Windspeed',data=weather_df, fit_reg=False, markers='o',
            scatter_kws={'edgecolors':'black',
                           'color': 'blue'},
            size=6,
            aspect=2)

# title and labels
plt.title("City Latitude vs. Windspeed 8/27/2017", fontsize=20)
plt.xlabel("Latitude", fontsize=15)
plt.ylabel("Windspeed()", fontsize=15)
# ticks size
plt.xticks(fontsize=15)
plt.yticks(fontsize=15)
# set x and y limits
plt.xlim(weather_df['Latitude'].min()-10,weather_df['Latitude'].max()+10)
plt.ylim(weather_df['Windspeed'].min()-10, weather_df['Windspeed'].max() +10)
plt.savefig("latitude vs Windspeed.png")
plt.show()
```


![png](output_12_0.png)



```python
# Latitude vs wind plot
seaborn.lmplot(x='Latitude', y='Cloudiness',data=weather_df, fit_reg=False, markers='o',
            scatter_kws={'edgecolors':'black',
                           'color': 'blue'},
            size=6,
            aspect=2)

# title and labels
plt.title("City Latitude vs. Humidity 8/27/2017", fontsize=20)
plt.xlabel("Latitude", fontsize=15)
plt.ylabel("Cloudiness(%)", fontsize=15)
# ticks size
plt.xticks(fontsize=15)
plt.yticks(fontsize=15)
# set x and y limits
plt.xlim(weather_df['Latitude'].min()-10,weather_df['Latitude'].max()+10)
plt.ylim(weather_df['Cloudiness'].min()-10, weather_df['Cloudiness'].max() +10)
plt.savefig("latitude vs Cloudiness.png")
plt.show()
```
