# 8. gyakorlat
## Javascript és jQuery
- mi is az a JavaScript?
  - a böngészőben futó programnyelv
  - ajánlott weboldal: https://www.w3schools.com/js/
  - használata: frontend (akár React, Angular, Vue.JS, stb.), backend (NodeJS), mobil (React Native)
  - npm csomagkezelő
- Javascript használata HTML-be behivatkozva:
  - `<script src="chessboard2.js"></script>`
  - vagy mindezt be is lehet ágyazni magába a HTML fájlba:
    - `<script>...</script>`
- **jQuery**: a nevéből is látszik, hogy a HTML elemek manipulálását és lekérdezését egyszerűvé tévő JavaScript library
  - használata:
    - pl. az összes `<td>` elem kiválasztása: `$("td")`
  - event handler csatolása az elemekhez: `$("td").click(function() { ... });` vagy `$("td").on("click", function() { ... });`
  - mik is azok az események: pl. `click`, `mouseover`, `mouseout`, `keydown`, `keyup`, `keypress`, stb.
  - JavaScript változók: `var`, `let`, `const`
  - JavaScript objektumok: `var obj = { ... };`
  - JavaScript tömbök: `var arr = [ ... ];`
  - JavaScript függvények: `function f() { ... }`
  - JavaScript függvények paraméterekkel: `function f(x, y) { ... }`
  - arrow function: `var f = (x, y) => { ... }` (lásd React-ban)
  - JavaScript típusok: `number`, `string`, `boolean`, `object`, `undefined`, `null`, `function`
    - stringek különböző megadási módjai
  - azért kell a `-1`, mivel az első oszlop nem igazi sakk-oszlop, hanem a számokat tartalmazó oszlop
- érdekességek: **typescript**


## Hamlet jQuery
- egy számlálót helyezünk el az anchor element-en, és ha rávisszük egy anchor tag-re az egeret, és rajta is tartjuk 3 másodpercig, akkor elnavigálja az oldalt (a window.location változik) az adott href-fel rendelkező section-re (esetünkben)
  - eközben tároljuk a várakozás idejét a timer data attribútumban
  - ha a felhasználó elhagyja az anchor tag-et, akkor nullázzuk az elindított timer-t

## Chessboard jQuery + CSS extra
- bábuk (avagy Unicode karakterek) behivatkozása CSS-be

## Hogwarts FORM
- saját azonosítójú webhook link generálása majd annak beillesztése a HTML dokumentumba
- `<fieldset>`: bekeretezi az benne található elemeket
- `<textarea>`: többsoros szövegbeviteli mező
- a `label:has(+ :is(input, select, textarea)[required])` kiválasztja az összes olyan label-t, amelynek van egy olyan testvére, amely input, select vagy textarea, és amelynek van required attribútuma. A + jel a testvérre utal tehát hogy **közvetlenül utánna** kell hogy következzenek, a :is pedig a felsorolt elemek közül bármelyikre illeszkedik.
- az `input[type=checkbox]:not(:checked)` kiválasztja az összes olyan checkboxot, amely nincs bepipálva
- az `:is(input, select, textarea)` kiválasztja az összes olyan input, select vagy textarea elemet. Ugyan ezt el tudjuk érni a `input, select, textarea` kifejezéssel is, de az előbbi gyorsabb, mivel a böngészőben a :is() kifejezés már be van építve, míg az utóbbi nem.
- a `div:has(button[type=submit])` kiválasztja az összes olyan div-et, amelynek van egy olyan gyermeke, amely button, és amelynek a típusa submit
- az `input[type=email]:invalid` kiválasztja az összes olyan email típusú inputot, amelynek az értéke nem megfelelő (invalid)
- a `:focus` kiválasztja az összes olyan elemet, amelyre éppen rá (bele) van kattintva
- a `name` attribútum lesz felhasználva a form elküldésekor a kulcsokként, a `value` attribútum pedig az értékeként