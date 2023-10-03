# 5. gyakorlat jegyzék

- directory XML feladat
  - XML vázolása
  - DTD elkészítése
  - CSS bemutatása és magyarázata

---

## JSON (JavaScript Object Notation)

- mi is az a JSON?
- JSON vs. XML
- JSON szintaxisa
  - kulcs-érték párokból áll
    - kulcs típusai
    - érték típusai: `null`, `true`, `false`, `number`, `string`, `object`, `array`
- JSON használata: https://gist.github.com/jeszy75/90e1fff9bcc35f7cfeb8123b4a31399a
  - JSON adatok küldése szövegesen: `echo '{"message": "Hello, World!"}' | http https://httpbin.org/post -v`
  - JSON adatok küldése kulcs-érték párok használatával: `http https://httpbin.org/post name="Tim Berners-Lee" email=cos@timbl.com url=https://www.w3.org/People/Berners-Lee/ -v`
  - beépített típusok használata a kérés küldésekor (lásd a `kulcs:=érték`): `http https://httpbin.org/post title="The Big Bang Theory" year:=2007 seasons:=12 ended:=true genres:='["comedy", "romance"]' -v`
  - JSON-be ágyazott JSON objektum küldése és használata: `http https://httpbin.org/post title="The Big Bang Theory" year:=2007 cast:='{"Leonard Hofstadter": "Johnny Galecki", "Sheldon Cooper": "Jim Parsons", "Penny": "Kaley Cuoco", "Howard Wolowitz": "Simon Helberg", "Raj Koothrappali": "Kunal Nayyar", "Bernadette Rostenkowski": "Melissa Rauch", "Amy Farrah Fowler": "Mayim Bialik"}' -v`
- JSON schema bemutatása
  - JSON objektumok validálására használatos
  - hasonló az XML fájloknál használt DTD-hez, annyi külünbséggel, hogy ez JSON objektumok/fájlok validálásához használatos
  - ez is kulcs-értékekből áll, és használ egy alap sémát: http://json-schema.org/draft-07/schema
- Frankfurter feladat
- Nationalize feladat
- további érdekes API-k
