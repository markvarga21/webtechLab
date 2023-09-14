# Halado ```curl``` keresek 
## Urlap adatok kuldese
- urlapok altalanos bemutatasa
    - ha nem titkos az elkuldeni kivant informacio, akkor mehetnek csak siman query parameterkent
    - egyebkent ha bejelentkezesrol, vagy hasonlorol van szo, akkor inkabb body-ban szokas kuldeni az ilyen informaciokat
### GET keresek
```
curl --insecure https://blackwells.co.uk/bookshop/search?keyword=sherlock+holmes\&pubDateFrom=2022\&pubDateTo=2023 -o search.html -v
```
- a ```-k``` kapcsolo jelzesevel a curl egy insecure kerest fog kuldeni, mivel maskeppen nem tudunk kerest kuldeni, mivel TLS secured az oldal (https)
- escaping character, de idezojelekkel megint ki lehet jatszani
- query parameterek
- ossze lehet hasonlitani a ```search.html``` fajlt az aktualis oldallal
```
curl --insecure --get https://blackwells.co.uk/bookshop/search -d keyword=sherlock+holmes -d pubDateFrom=2022 -d pubDateTo=2023 -o search.html -v
```
- ugyan az mint a fenti, csak explicit ```-d``` kapcsolokkal, query parameterek kuldesehez
- azert van szukseg a ```--get``` kapcsolora, mivel nelkule, a ```-d``` kapcsolot hasznalva, a ```curl``` egy ```POST``` kerest kuldene

---

```
curl --insecure --get https://validator.w3.org/check --data-urlencode "uri=https://www.w3.org/" --data-urlencode "charset=(detect automatically)" -d doctype=Inline -d group=0 -o output.html -v
```
- mivel nem minden esetben kuldunk engedelyezett karaktereket egy URI-ban, ezert URL encodingra van szukseg
    - pl. ```%20``` a szokoz stb.
- mint lathato az idezojel elhagyhato ha nincs benne illegalis karakter (lasd a ```doctype=Inline```)

### POST keresek
```
curl --insecure https://www.base64encode.org/ --http1.1 -d input=Hello,\ World! -d charset=UTF-8 -d separator=LF -o output.html --trace-ascii trace.txt -s
```
- query parameterkent atadott szoveg encodolasa
---
```
curl -k https://www.w3.org/ -o index.html -s
```
- a ```-k``` ugyanazt eri el mint a ```--insecure``` parancssori kapcsolo

```
curl --insecure https://validator.w3.org/check -F uploaded_file=@index.html --form-string "charset=(detect automatically)" -F doctype=Inline -F group=0 -o output.html --trace-ascii trace.txt -s
```
- ellenorzi a feltoltott HTML oldalt a HTML kovetelmenyeknek megfeleloen
    - ki lehet probalni invalid HTML dokumentumra is
- ```-F```: form adatok kuldesehez
- ```@```: fajlok behivatkozasahoz

## Web API-k hasznalata
```
curl http://wttr.in
curl http://wttr.in/:help
curl http://wttr.in/London
curl http://wttr.in/New+York
curl http://wttr.in/~Tower+Bridge
curl http://wttr.in/~Mount+Everest
curl http://wttr.in/ -H Accept-Language:en
curl http://wttr.in/ -H Accept-Language:de
curl http://wttr.in?lang=hu
curl http://wttr.in?lang=en
curl http://wttr.in?lang=de
curl http://hu.wttr.in
curl http://de.wttr.in
curl http://wttr.in/?format=1
curl http://wttr.in/?format=2
curl http://wttr.in/?format=3
curl http://wttr.in/?format=4
curl http://wttr.in/Budapest?format=v2
curl http://v2.wttr.in/Budapest
curl http://wttr.in/Moon
```
- idojaras adatok lekeresere (visually appealing)

## HTML oldalak validalasa URI hasznalataval es uzenet visszakerese XML formatumban
- tobb formatum is tamogatva van, mint pl. a HTML vagy a JSON
```
curl --insecure --get https://validator.w3.org/nu/ --data-urlencode doc=https://whatwg.org/ -d out=xml -v
```
- valid oldal eseten termeszetesen nem kapunk vissza semmilyen hibat

```
curl --insecure --get https://validator.w3.org/nu/ --data-urlencode doc=https://www.nasa.gov/ -d out=xml -v
```
- mint lathato, ez egy invalid oldal, a hibakat XML formatumban kapjuk vissza amit akar le is menthetunk a ```-o out.xml``` kapcsolo hasznalataval
- beautiful XML viewer: https://codebeautify.org/xmlviewer
## HTML fajlok validalasa
```
curl https://whatwg.org/ -o whatwg.html -s
```
- HTML oldal letoltese

```
curl -k https://validator.w3.org/nu/?out=xml --data-binary @whatwg.html -H "Content-type: text/html; charset=utf-8" -v
```
- oldal validalasa

## Fajlmegosztas
```
echo "Hello World!" > hello.txt
cat hello.txt
```
- fajl elkeszitese

```
curl -F f:1=@hello.txt http://ix.io
```
- fajl bahivatkozasa a ```@``` karaktert hasznalva es ezutan feltoltese az ix.io oldalra
```
curl -F f:1="Hi there simple text!" http://ix.io
```
- egyszeru szoveges tartalom kuldese
```
echo "Hello, World!" | curl --insecure --upload-file . https://transfer.sh/hello.txt -H Max-Downloads:1 -H Max-Days:1 -v -o downloadLink.txt
```

## Sutik

```
curl -k https://www.youtube.com/ -c cookies.txt
```
- oldal sutieinek mentese egy kimeneti fajlba

```
curl https://www.youtube.com/watch?v=pTBjHjRhx_Y -b cookies.txt
```
- oldal megnyitasa a ```cookies.txt``` fajlban definialt sutikkel


---

# Postman

1. Postmanrol altalanosan
2. Interfesz bemutatasa
3. GET keresek kuldese
    - paramterek nelkul
    - query parameterekkel
    - konfiguralt fejlecmezokkel
4. Valtozok bemutatasa
5. POST keresek kuldese
    - fajlokkal
6. Authorization?
7. Collection es keresek mentese
8. API dokumentacio keszitese es publikalasa
    - mi is az az API?
9. History

# Httpie

- par parancs kiprobalasa a Gist oldalrol

# Chrome dev tools

- ha marad ido chrome dev tools-t bemutatni, azon belul is a ```Network``` tabot. Ha nem marad, akkor maradhat a HTML+CSS gyakorlatra.

# Erdekessegek

- APIk: PokeAPI, Kanye, SpaceX, Nasa, stb.