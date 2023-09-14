# Haladó `curl` kérések

## Űrlap adatok küldése

- űrlapok általános bemutatása
  - ha nem titkos az elküldeni kívánt információ, akkor mehetnek csak simán query parameterként
  - egyébként ha bejelentkezésről, vagy hasonlóról van szó, akkor inkább a body-ban szokás elküldeni az ilyen információkat

### `GET` kérések

```
curl --insecure https://blackwells.co.uk/bookshop/search?keyword=sherlock+holmes\&pubDateFrom=2022\&pubDateTo=2023 -o search.html -v
```

- a `-k` kapcsoló jelzésével a curl egy insecure kérést fog küldeni, mivel máskeppen nem tudunk kérést küldeni, mivel TLS secured az oldal (`https`)
- escaping character, de idézőjelekkel megint ki lehet játszani
- query parameterek
- össze lehet hasonlítani a `search.html` fájlt az aktuális oldallal

```
curl --insecure --get https://blackwells.co.uk/bookshop/search -d keyword=sherlock+holmes -d pubDateFrom=2022 -d pubDateTo=2023 -o search.html -v
```

- ugyan az mint a fenti, csak explicit `-d` kapcsolókkal, query parameterek küldéséhez
- azért van szükség a `--get` kapcsolóra, mivel nélküle, a `-d` kapcsolót hasznalva, a `curl` egy `POST` kérést küldene

---

```
curl --insecure --get https://validator.w3.org/check --data-urlencode "uri=https://www.w3.org/" --data-urlencode "charset=(detect automatically)" -d doctype=Inline -d group=0 -o output.html -v
```

- mivel nem minden esetben küldünk engedélyezett karaktereket egy URI-ban, ezert URL encodingra van szükseg
  - pl. `%20` a szóköz stb. (a továbbiakban lásd: https://www.w3schools.com/tags/ref_urlencode.ASP)
- mint látható az idézőjel elhagyható ha nincs benne illegális karakter (lásd a `doctype=Inline`)

### `POST` kérések

```
curl --insecure https://www.base64encode.org/ --http1.1 -d input=Hello,\ World! -d charset=UTF-8 -d separator=LF -o output.html --trace-ascii trace.txt -s
```

- query paraméterként átadott szöveg encodolása

---

```
curl -k https://www.w3.org/ -o index.html -s
```

- a `-k` ugyanazt éri el mint a `--insecure` parancssori kapcsoló

```
curl --insecure https://validator.w3.org/check -F uploaded_file=@index.html --form-string "charset=(detect automatically)" -F doctype=Inline -F group=0 -o output.html --trace-ascii trace.txt -s
```

- ellenőrzi a feltöltött HTML oldalt a HTML követelményeknek megfelelően
  - ki lehet próbálni invalid HTML dokumentumra is
- `-F`: form adatok küldéséhez
- `@`: fájlok behivatkozásához

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

- időjárás adatok lekérésére (visually appealing)

## HTML oldalak validálása URI használatával és üzenet visszakérese XML formátumban

- több formátum is támogatva van, mint pl. a `html` vagy a `json`

```
curl --insecure --get https://validator.w3.org/nu/ --data-urlencode doc=https://whatwg.org/ -d out=xml -v
```

- valid oldal esetén természetesen nem kapunk vissza semmilyen hibát

```
curl --insecure --get https://validator.w3.org/nu/ --data-urlencode doc=https://www.nasa.gov/ -d out=xml -v
```

- mint látható, ez egy invalid oldal, a hibákat `xml` formátumban kapjuk vissza amit akár le is menthetünk a `-o out.xml` kapcsoló használatával
- online beautiful XML viewer: https://codebeautify.org/xmlviewer

## HTML fájlok validálása

```
curl https://whatwg.org/ -o whatwg.html -s
```

- HTML oldal letöltése

```
curl -k https://validator.w3.org/nu/?out=xml --data-binary @whatwg.html -H "Content-type: text/html; charset=utf-8" -v
```

- oldal validálása

## Fájlmegosztás

```
echo "Hello World!" > hello.txt
cat hello.txt
```

- fájl elkészítése

```
curl -F f:1=@hello.txt http://ix.io
```

- fájl behivatkozása a `@` karaktert használva és ezután feltöltése az http://ix.io oldalra

```
curl -F f:1="Hi there simple text!" http://ix.io
```

- egyszerű szöveges tartalom küldése

```
echo "Hello, World!" | curl --insecure --upload-file . https://transfer.sh/hello.txt -H Max-Downloads:1 -H Max-Days:1 -v -o downloadLink.txt
```

## Sütik

```
curl -k https://www.youtube.com/ -c cookies.txt
```

- oldal sütieinek mentése egy kimeneti fájlba

```
curl https://www.youtube.com/watch?v=pTBjHjRhx_Y -b cookies.txt
```

- oldal megnyitása a `cookies.txt` fájlban definiált sütikkel

---

# Érdekes API-k

- PokeAPI, Kanye, SpaceX, Nasa, stb.
