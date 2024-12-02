# 6. gyakorlat (10.15)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

## Előszó

- a HTML, úgy mint az XML egy jelölő nyelv, amelyet a weboldalak struktúrájának leírására használunk
  - annyi a különbség, hogy még az XML esetében tetszőleges elemeket használhattunk, HTML-ben előre definiált címkekészlet van (+ előre definiált attribútumok, a `data-*` attribútumokat kivéve)
- a HTML egy szabványosított nyelv, amelyet a W3C (World Wide Web Consortium) fejlesztett ki

**HTML felépítése**

- `<!DOCTYPE html>`: a dokumentum típusának deklarációja
- `<html>` címke: a dokumentum gyökéreleme
- `<head>` címke: a dokumentum fejléce
  - ide kerülnek a metaadatok, a stíluslapok és a JavaScriptek (mely lehet külső vagy beágyazott)
- `<body>` címke: a dokumentum tartalma
  - ide kerülnek a látható elemek, mint a szöveg, képek, táblázatok, űrlapok, stb.
- számos egyéb elem van, melyek egy részére, majd a gyakorlatok során térünk ki

**JavaScript**

- **nem összekeverendő a Java programozási nyelvvel**
- a JavaScript egy szkriptnyelv, amelyet a weboldalak interaktivitásának növelésére használunk
- esetünkben látni fogunk majd példát egy régebbi megoldásra, mely jquery-t használ, valamint egy újabb megoldásra, mely a modern JavaScript szabványokat követi (vanilla JavaScript)
  - ahhoz, hogy jquery-t tudjunk használni, be kell linkelni a jquery fájlt a HTML dokumentumba (pl. `<script src="https://www.w3schools.com/jquery/jquery_get_started.asp"></script>`)
- típus nélküli nyelv, tehát nem kell deklarálni a változók típusát
  - a változók típusa futási időben derül ki
  - amennyiben szeretnénk a típusokat szigorúbban kezelni, használhatunk TypeScriptet, ami egy szigorúan típusos JavaScript kiterjesztés
- felhasználási lehetőségei:
  - **kliens oldalon**: pl. a React vagy Angular keretrendszerek
  - **szerver oldalon**: pl. a Node.js

## Megjegyzések

**Emmet rövidítések**

- [https://docs.emmet.io/cheat-sheet/](https://docs.emmet.io/cheat-sheet/)
  - a fejlesztést nagyban megkönnyíti, ha ismerjük ezeket a rövidítéseket
  - pl. a `table.chessboard>thead>tr>th*10^^tbody>tr*8>th{$@-}+td*8+th{$@-}^^tfoot>tr>th*10` rövidítés egy sakktáblát hoz létre - `>`: gyermekelemet hoz létre - `^`: egy szinttel visszalép - `+`: testvérelemet hoz létre - `table.chessboard`: egy táblázatot hoz létre, melynek osztályneve `chessboard` - `thead>tr>th*10`: a táblázat fejlécében egy sor található, melynek 10 db fejléc cellája van - `th{$@-}`: a fejléc cellák tartalma a soron belül az aktuális cella sorszámától függ (azért kerül a `<th>` elem tartalmába, mivel használva van a `{}` jelölés)

**Unicode karakterek beszúrása**

- HTML címkék tartalmába:
  - pl. `<td>&#x265c;</td>`: egy fekete bástya karaktert szúr be a táblázat cellájába
- CSS segítségével:
  - pl. `valami::before { content: "\265C"; }`: egy fekete bástya karaktert szúr be a `valami` elem elé
- vegyük észre, hogy a karakterek beszúrása minimálisan eltér a két esetben

**CSS**

- `border-collapse: collapse`: a táblázat celláinak határvonalait összevonja
- `margin: 1em auto;`:
  - fent és lent 1em margót ad a szövegnek
  - jobbra és balra automatikusan igazítja a szöveget a böngésző (esetünkben középre az adott konténerben)
- `!important`: minden megelőző stílus felülírására szolgál
  - **kerülendő a használata**, mivel nehezen karbantartható kódot eredményez
- `@import "chessboard1.css";`: egy külső stíluslapot importál a dokumentumba
  - a stíluslapot a dokumentum elején kell importálni, mivel a CSS fájlok sorrendje számít

**JavaScript**

JavaScript fájlokat beilleszthetünk a HTML dokumentum fejlécébe vagy a testébe

- a fejlécbe való beillesztés esetén a fájl betöltése a dokumentum betöltése előtt megtörténik (így érdemes okosan megválasztanunk az elhelyezését)

Jquery használata:

- `$('table.chessboard td')`: a jQuery segítségével a `table.chessboard` osztályú táblázat celláit (`<td>...</td>`) kiválasztjuk
- `.on('mouseenter', function () { ... })`: a jQuery segítségével az egér belépésekor egy eseményt hozunk létre
- `$(this)`: a jQuery segítségével az aktuális elemre hivatkozunk

Vanilla JavaScript használata:

- `document.querySelectorAll('table.chessboard td')`: a `table.chessboard` osztályú táblázat celláit kiválasztjuk a DOM (_Document Object Model_) segítségével (ezt jelöli a `document`)
