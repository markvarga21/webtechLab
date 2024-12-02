# 8. gyakorlat (11.05)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

## Hogwarts feladat

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/hogwarts-form/

**HTML megjegyzések**:

- a `fieldset` elem egy űrlapban egy csoportot jelöl, amelynek egy keretet ad
  - a `legend` elemmel lehet címet adni a `fieldset`-nek
- általában mindegyik `input`-hoz tartozik egy `label` elem, amely a beviteli mező mellett jelenik meg
  - a `for` attribútum segítségével a `label` elem `id` attribútumára lehet hivatkozni
  - a `label` elembe általában a beviteli mezőt követő szöveget szokás tenni
- számos bemeneti típust lehet megadni, úgy mint:
  - text, number, email, password, checkbox, radio, date, time, file, color, range, submit, reset, button
- a `textarea` elemmel többsoros szövegbeviteli mezőt lehet létrehozni

**CSS megjegyzések**:

- `label:has(+ :is(input, select, textarea)[required])`: a `label` elemek közül azokra, amelyeknek a következő elemük egy `input`, `select` vagy `textarea` elem, amelynek a `required` attribútuma van megadva, azokra vonatkozik a stílus

## Hogwarts extra feladat

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/hogwarts-form/

**CSS megjegyzések**:

- `form.fancy-form :is(input[type=radio], input[type=radio] + label)`: a `.fancy-form` osztályú `form` elemen belül az `input` elemek közül azokra, amelyeknek a típusa `radio`, valamint azokra a `label` elemekre vonatkozik, amelyek az `input` elemek után következnek
- flex display tulajdonság: _lásd a későbbi gyakorlatokban_

**JavaScript megjegyzések**:

- form-beli elemek eléréséhez, pl. a `dateOfBirth` azonosítójú input elemre így tudunk hivatkozni: `document.getElementById('myFormId').dateOfBirth`
  - ekkor nyilván nem tartalmazhat szóköz karaktert az azonosító
- customValidity: amennyiben a bemeneti mezőben megadott adat nem érvényes, akkor megadhatunk egy tetszőleges szöveget, amely a bemeneti mező alatt jelenik meg
  - pl. `document.getElementById('myFormId').myInput.setCustomValidity('Az év nem lehet negatív szám!')`
- események:
  - `(on)input`: minden alkalommal, amikor a felhasználó beír valamit a bemeneti mezőbe
  - `(on)change`: minden alkalommal, amikor a felhasználó megváltoztatja a bemeneti mező értékét

## Webtech feladat (extra, otthonra)

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/web-technologies/feladat.html

**HTML megjegyzések**:

- listák használata
  - `<ul>`: felsorolás (_unordered list_)
  - `<ol>`: számozott felsorolás (_ordered list_)
  - `<li>`: listaelem (_list item_)
- a `<pre>` elem a formázott szövegek megjelenítésére szolgál
  - pl. kódok, szövegek, stb.
  - nincs szöveg tördelés, a szöveg pontosan úgy jelenik meg, ahogy meg van adva
  - nem szerepelhet benne semmilyen HTML-ben használt elem, karakter stb.
    - ezeket a `<`, `>`, `&` karaktereket pl. unicode karakterként kell megadni (pl. `&lt;`, `&gt;`, `&amp;`)

**CSS megjegyzések**:

- `ul:is(.toc, .specs) a:hover`: a `ul` elemek közül a `.toc` és `.specs` osztályú elemekben lévő `a` elemekre húzva az egeret, azokra a stílusokra vonatkozik, amelyeket a `:hover` pszeudo-osztály definiál
- a linkeknek számos állapotuk lehet, úgy mint: `:link`, `:visited`, `:hover`, `:active`
  - ezeket a stílusokat a következő sorrendben érdemes definiálni: `:link`, `:visited`, `:hover`, `:active`
