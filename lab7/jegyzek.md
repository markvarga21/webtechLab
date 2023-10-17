# 7. gyakorlat

- HTML mint jelölőnyelv
  - HTML vs. XML
- HTML dokumentum felépítése
  - HTML dokumentumok szerkezete (`<html>`, `<head>`, `<body>`, stb.)
  - HTML dokumentumok elemei
  - HTML dokumentumok attribútumai
    - fontosabb attribútumok: `id` (hivatkozása `#idName`, pl. linkekben - `<a href="#idName">`) és `class` (hivatkozása `.className`, pl. CSS-ben)
  - általánosan haznált HTML konténerek: pl. a `<div>` és `<span>` elemek, utóbbi inline elem (pl. szövegbe ágyazható) és nem rendelkezik semmilyen formázással
- **Emett rövidítések használata**:
  - pl `table>thead>tr>th*10^^tbody>tr*8>th+td{$@-}*8+th^^tfoot>tr>th*10`
    - `+`: konkatenáció
    - `>`: gyermek
    - `^`: szülő
    - `^^`: szülő szülője
    - `*`: ismétlés
    - `$`: számláló
    - `{}`: tartalom

---

## Hamlet

- az eddigiekben használt és látott Hamlet-es példa átültetése HTML-be és annak stilizálása CSS-sel
- linkek használata

---

## Chessboard 1

- statikus figura behivatkozások alkalmazása
- Unicode karakterek behivatkozása HTML-be, pl. `&#9812;`

---

## Chessboard 2

- dinamikus figura behivatkozások alkalmazása attribútumok használatával
- Unicode karakterek behivatkozása CSS-be, pl. `\2654`
- egy előre megírt CSS stíluslap behivatkozása egy másik CSS fájlba:
  - `@import "chessboard1.css";`

---

## Chessboard 2 + JavaScript

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
