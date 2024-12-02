# 5. gyakorlat (10.08)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

## JSON (JavaScript Object Notation)

- a JSON egy adatcsere formátum, amely az ember által olvasható szöveges formátumot használ az adatok strukturálására. Bár a JSON származik a JavaScript-ből, a JSON adatokat egyéb programozási nyelvekben is használják.
- JSON vs. XML
  - JSON: könnyen olvasható, könnyen írható, könnyen értelmezhető, könnyen generálható, könnyen feldolgozható
  - XML: olvasható, írható, értelmezhető, generálható, feldolgozható, nagyobb rugalmasság
- JSON szintaxis: kulcs-érték párok listája
  - kulcs típusai: string
  - érték típusai: string, szám, objektum, tömb, true, false, null
    ![JSON](https://i.sstatic.net/7zOHB.gif)

**Példák**:

- objektum

```json
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
```

- tömb

```json
{
  "employees": ["John", "Anna", "Peter"]
}
```

- objektum tömb

```json
{
  "employees": [
    {
      "name": "John",
      "age": 30
    },
    {
      "name": "Anna",
      "age": 28
    },
    {
      "name": "Peter",
      "age": 35
    }
  ]
}
```

## JSON formázása

JSON formázása parancssorban:

```bash
python -m json.tool --help
python -m json.tool <file.json>
cat <file.json> | python -m json.tool
curl <url> | python -m json.tool
```

Pédlák:

```bash
curl -s https://api.chucknorris.io/jokes/random
curl -s https://api.chucknorris.io/jokes/random | python -m json.tool
curl -s https://restcountries.com/v3.1/alpha/hu | python -m json.tool
curl -s https://restcountries.com/v3.1/alpha/hu | python -m json.tool --no-ensure-ascii
```

**Megjegyzések**:

- a `--no-ensure-ascii` kapcsolóval a nem ASCII karaktereket is megjeleníti

## HTTPie

- a `curl` parancssori program alternatívája, amely a JSON esetében szép formázást biztosít
- **fontos**: a két program parancsai _nem teljesen kompatibilisek_ egymással
- a `httpie`-nak van egy böngészőben is használható verziója, amely a Postman-re hasonlít
  - https://httpie.io/app

1. Adatok küldése `HTTPie`-val:

```bash
echo '{"message": "Hello, World!"}' | http https://httpbin.org/post -v
```

Megjegyzések:

- a httpbin lehetővé teszi számunkra POST kérések küldését, amelyeket vissza is küld nekünk a válaszban (tulajdonképpen tükörként működik)

2. Adatok lekérése, majd küldése a httpbin API-nak:

```bash
http https://api.chucknorris.io/jokes/random -d
cat random.json | http https://httpbin.org/post -v
```

Megjegyzések:

- a `-d` kapcsolóval le tudjuk tölteni a választ egy fájlba (a fenti esetben a végpont neve.json fájlba)
  - alternatívája: `--download` (`httpie`)
  - ugyan ezt tudjuk elérni a `curl`-al a `-o` kapcsolóval

1. JSON adatok küldése közvetlenül a parancssorból:

```bash
http https://httpbin.org/post name="Tim Berners-Lee" email=cos@timbl.com url=https://www.w3.org/People/Berners-Lee/ -v
```

Megjegyzések:

- a kulcs-érték párokat a `name="Tim Berners-Lee"` módon tudjuk megadni
  - amennyiben nem tartalmaz szóközt a kulcs vagy az érték, akkor a `name=Tim` módon is megadhatjuk
- ha így adjuk meg, akkor minden érték **string** lesz

4. JSON adatok küldése, az érték típusának megtartásával:

```bash
http https://httpbin.org/post title="The Big Bang Theory" year:=2007 seasons:=12 ended:=true -v
```

## API dokumentáció

- egy jól ismert standard a [Swagger](https://swagger.io/) (OpenAPI)
  - lásd a fenti feladatokban használt httpbin.org dokumentációját: [https://httpbin.org/](https://httpbin.org/)
- dokumentációt tudunk például egy Postman collection-ből is generálni
  - lásd a következő példát: [https://documenter.getpostman.com/view/22391147/2s9YC5xXRQ](https://documenter.getpostman.com/view/22391147/2s9YC5xXRQ)

## Haladó HTTP kérések

**GET metódus**

```bash
http http://httpbin.org/get string==bazinga number==42 -v
http http://httpbin.org/get "string==Hello, World!" number==42 -v
```

```bash
http http://httpbin.org/anything title="The Big Bang Theory" year:=2007 seasons:=12 ended:=true genres:='["comedy", "romance"]' -v
http http://httpbin.org/anything title="The Big Bang Theory" year:=2007 seasons:=12 ended:=true genres[]=comedy genres[]=romance -v
http http://httpbin.org/anything title="The Big Bang Theory" year:=2007 seasons:=12 ended:=true genres[1]=romance genres[0]=comedy -v
http http://httpbin.org/anything title="The Big Bang Theory" year:=2007 cast:='{"Leonard Hofstadter": "Johnny Galecki", "Sheldon Cooper": "Jim Parsons", "Penny": "Kaley Cuoco", "Howard Wolowitz": "Simon Helberg", "Raj Koothrappali": "Kunal Nayyar", "Bernadette Rostenkowski": "Melissa Rauch", "Amy Farrah Fowler": "Mayim Bialik"}' -v
http http://httpbin.org/anything title="The Big Bang Theory" year:=2007 cast["Leonard Hofstadter"]="Johnny Galecki" cast["Sheldon Cooper"]="Jim Parsons" cast[Penny]="Kaley Cuoco" cast["Howard Wolowitz"]="Simon Helberg" cast["Raj Koothrappali"]="Kunal Nayyar" cast["Bernadette Rostenkowski"]="Melissa Rauch" cast["Amy Farrah Fowler"]="Mayim Bialik" -v
```

```bash
http "https://blackwells.co.uk/bookshop/search?keyword=sherlock+holmes&pubDateFrom=2022&pubDateTo=2023" -d -o search.html -v
http https://blackwells.co.uk/bookshop/search keyword==sherlock+holmes pubDateFrom==2022 pubDateTo==2023 -d -o search.html -v
```

```bash
http https://validator.nu/ doc==https://www.w3.org/ -d -o output.html -v
```

**POST metódus** különböző médiatípusokkal

```bash
http --form http://httpbin.org/post string=bazinga number=42 -v
http --multipart http://httpbin.org/post string=bazinga number=42 -v
```

Megjegyzések:

- a `form` és `multipart` között az a különbség, hogy a `form` a `Content-Type: application/x-www-form-urlencoded`-et használja, míg a `multipart` a `Content-Type: multipart/form-data`-t

```bash
http -f POST https://www.base64encode.org/ input="Hello, world!" charset=UTF-8 separator=lf -d -o output.html -v
```

```bash
http https://www.w3.org/ -d -o index.html
http -f POST https://validator.nu/ file@index.html -d -o output.html -v
```

**Megjegyzések**:

- tudunk fájlokat is csatolni a POST kéréseinkhez a `file@<filename>` módon
- a `-f` (vagy `--form`) kapcsolóval tudunk form adatokat küldeni
- további példák: https://gist.github.com/jeszy75/47e2a2693aba0170f2d178df2703afb1

**Kérések küldése hitelesítéssel**

```bash
http https://rebrickable.com/api/v3/lego/sets/60386-1/ "Authorization: key <your-key>" -v

http https://rebrickable.com/api/v3/lego/sets/60386-1/minifigs/ "Authorization: key <your-key>" -v

http https://rebrickable.com/api/v3/lego/sets/60386-1/parts/ "Authorization: key <your-key>" -v
```

**Basic authentication**:

```bash
http https://api.github.com/user -v
http https://api.github.com/user -v -a <username>
```

## Filebin API

- a Filebin egy egyszerű fájlmegosztó szolgáltatás, amely lehetővé teszi a fájlok feltöltését és letöltését

**POST**: töltsük fel a "Hello World!" szöveget egy `hello.txt` fájlba

```bash
http POST https://filebin.net/ bin:webtech_gyakorlat_1012 filename:hello.txt --raw "Hello World!" -v
```

**GET**: ellenőrizzük a feltöltött fájlt

```bash
http GET https://filebin.net/webtech_gyakorlat_1012 Accept:application/json -v
```

**GET**: generáljunk QR kódót a bin-hez (ezt próbáljuk ki inkább a böngészőben)

```
https://filebin.net/qr/webtech_gyakorlat_1012
```

**DELETE**: töröljük a feltöltött fájlt

```bash
http DELETE https://filebin.net/webtech_gyakorlat_1012/hello.txt -v
```

Megjegyzések:

- itt érdemes mindenkinek külön bin-be feltölteni a fájlokat, a kellemetlenségek elkerülése végett

## Postman

- a Postman egy API tesztelő és dokumentáló platform
- a Postman segítségével könnyen tudunk HTTP kéréseket küldeni, teszteket futtatni, dokumentációt készíteni

## JSON séma

- a JSON séma egy JSON dokumentum struktúráját írja le
- ez is egy JSON dokumentum, amely JSON dokumentumok validációjára szolgál

1. A `fraunkfurt.json` állományhoz készítsünk egy JSON sémát.
   - https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/json/frankfurter/feladat.html

```
http https://api.frankfurter.app/latest
```

```json
{
  "$schema": "http://json-schema.org/draft-07/schema",
  "title": "Schema for the Frankfurter API",
  "type": "object",
  "properties": {
    "$schema": {
      "type": "string"
    },
    "amount": {
      "type": "number"
    },
    "base": {
      "type": "string",
      "pattern": "^[A-Z]{3}$"
    },
    "date": {
      "type": "string"
    },
    "rates": {
      "type": "object",
      "patternProperties": {
        "^[A-Z]{3}$": {
          "type": "number"
        }
      },
      "additionalProperties": false
    }
  },
  "required": ["amount", "base", "date", "rates"],
  "additionalProperties": false
}
```

1. Készítsünk egyetlen JSON sémát a `name.json` és a `names.json` állományokhoz.

   - https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/json/nationalize/feladat.html

```
curl https://api.nationalize.io/?name=ubul -o name.json
curl "https://api.nationalize.io/?name[]=antal&name[]=suzuki&name[]=ivanov" -o names.json
```

```json
{
  "$schema": "http://json-schema.org/draft-07/schema",
  "definitions": {
    "countryCode": {
      "type": "string",
      "pattern": "^[A-Z]{2}$"
    },
    "probability": {
      "type": "number",
      "minimum": 0,
      "maximum": 1
    },
    "response": {
      "type": "object",
      "properties": {
        "$schema": {
          "type": "string"
        },
        "count": {
          "type": "number"
        },
        "name": {
          "type": "string"
        },
        "country": {
          "type": "array",
          "items": {
            "type": "object",
            "properties": {
              "country_id": {
                "$ref": "#/definitions/countryCode"
              },
              "probability": {
                "$ref": "#/definitions/probability"
              }
            },
            "additionalProperties": false
          }
        }
      },
      "required": ["count", "name", "country"],
      "additionalProperties": false
    },
    "arrayOfResponses": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/response"
      }
    },
    "errorDef": {
      "type": "object",
      "properties": {
        "error": {
          "type": "string"
        }
      },
      "required": ["error"],
      "additionalProperties": false
    }
  },
  "oneOf": [
    {
      "$ref": "#/definitions/response"
    },
    {
      "$ref": "#/definitions/arrayOfResponses"
    },
    {
      "$ref": "#/definitions/errorDef"
    }
  ]
}
```

1. Ellenőrizzük le a sémáinkat, hogy valóban jól vannak-e megírva.

   - https://www.jsonschemavalidator.net/

**Megjegyzések**:

- mint látható, a JSON séma fájlok is egy úgy-nevezett meta-sémát követnek

## Egyéb érdekes API-k

Időjárás adatok lekérése a `wttr.in` API segítségével:

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

Továbbiakért lásd ezt a [linket](https://gist.github.com/jeszy75/6959c60a00fb72f3ad7b1d39cb42d46e).

## Gofile API

A Gofile egy egyszerű fájlmegosztó szolgáltatás, amely lehetővé teszi a fájlok feltöltését és letöltését

1. Nézzük meg, milyen szerverek állnak rendelkezésünkre:

```bash
http 'https://api.gofile.io/servers'
```

2. Töltsünk fel egy fájlt a Gofile szerverre:

```bash
curl -X POST https://store3.gofile.io/contents/uploadfile -F "file=@example.txt" -o file_upload.txt -v
type file_upload.txt | python -m json.tool
```

Amennyiben van tokenünk, akkor a következő módon tudjuk feltölteni a fájlt:

```bash
curl -X POST https://store3.gofile.io/contents/uploadfile -F "file=@example.txt" -H "Authorization: Bearer <token>" -o file_upload_auth.txt -v
type file_upload_auth.txt | python -m json.tool
```

3. Módosítsuk a feltöltött fájl nevét a szerveren `webtech.txt`-re:

```bash
curl -X PUT -H "Authorization: Bearer <token>" "https://api.gofile.io/contents/73de6a75-53e1-49b8-9f72-50f4e0668661/update" -H "Content-Type: application/json" -d "{\"attribute\": \"name\", \"attributeValue\": \"webtech.txt\"}" -v
```

4. Töröljük a fájlt a szerverről:

```bash
curl -X DELETE -H "Authorization: Bearer <token>" "https://api.gofile.io/contents" -H "Content-Type: application/json" -d "{\"contentsId\": \"73de6a75-53e1-49b8-9f72-50f4e0668661\"}" -v
```

**Megjegyzések**:

- sajnos nem tudjuk letölteni a fájlt a parancssorból, mivel ehhez már premium fiókra lenne szükségünk
