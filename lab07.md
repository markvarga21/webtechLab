# 7. gyakorlat (10.29)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

## JavaScript

JavaScript fájlokat beilleszthetünk a HTML dokumentum fejlécébe vagy a testébe

- a fejlécbe való beillesztés esetén a fájl betöltése a dokumentum betöltése előtt megtörténik (így érdemes okosan megválasztanunk az elhelyezését)

Jquery használata:

- `$('table.chessboard td')`: a jQuery segítségével a `table.chessboard` osztályú táblázat celláit (`<td>...</td>`) kiválasztjuk
- `.on('mouseenter', function () { ... })`: a jQuery segítségével az egér belépésekor egy eseményt hozunk létre
- `$(this)`: a jQuery segítségével az aktuális elemre hivatkozunk

Vanilla JavaScript használata:

- `document.querySelectorAll('table.chessboard td')`: a `table.chessboard` osztályú táblázat celláit kiválasztjuk a DOM (_Document Object Model_) segítségével (ezt jelöli a `document`)

## Hamlet dráma szövegének átültetése HTML-be, valamint ennek stilizálása

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/hamlet/feladat.html

**HTML megjegyzések**:

- címek hierarchiája és méretbeli különbségei
  - lásd a `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>` elemeket, ahol a `<h1>` a legnagyobb, a `<h6>` pedig a legkisebb (méretbeli) címet jelöli
- a `<hgroup>` a heading-hez kapcsolódó tartalmak csoportosítására szolgál, amely pontosan egy címet (pl. `<h1>`) és egy vagy több al-címet (`<p>`) tartalmaz
  - ezzel növelve a dokumentum szemantikáját
- erőforrásrész azonosítók használata a navigációban
  - pl. `<a href="#act1-scene5">Scene 5</a>`: a `#act1-scene5` azonosítójú elemre ugorjon a böngésző
- általános célú konténer: `<div>`
- unicode karakterek hivatkozása a HTML dokumentumban
  - pl. `&#x2014;`: hosszú kötőjel
- a `<small>` elem a kisebb méretű szövegek megjelenítésére szolgál
- a `<cite>` elem a művek címének megjelenítésére szolgál

**CSS megjegyzések**:

- `float: right`: a jobb oldalra igazítja a szöveget
- `margin-left: -1em`: a bal margót csökkenti 1 egységgel

**JavaScript megjegyzések**:

- HTML-ben van lehetőségünk egyedi nevű attribútumokat létrehozni, viszont minden esetben tartalmazniuk kell a `data-` előtagot
  - pl. `<div data-act="1" data-scene="5">`
- vanilla JS-ben, a `myElement.dataset.act` módon hivatkozhatunk az egyedi nevű attribútumra
  - jQuery-ben pedig a `$(this).data('act')` módon
