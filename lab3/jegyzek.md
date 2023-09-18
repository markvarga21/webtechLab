## XML (eXtensible Markup Language)

- általános célú jelölőnyelv
  - mi is az a jelölőnyelv?
- adatcsere formátumként használatos
  - JSON rövid bemutatása
- XML elementek validálása (lásd DTD)
- címkék bemutatása
- HTML vs. XML

## DTD (Document Type Definition)

- XMl dokumentumok validálásához
- element típusok:
  - `<!ELEMENT element-name EMPTY>`
  - `<!ELEMENT element-name (#PCDATA)>`
  - `<!ELEMENT element-name ANY>`
  - `<!ELEMENT element-name (child1, child2, ...)>`
- előfordulási számok:
  - `'|'`: vagy ez vagy az
  - `'*'`: nulla vagy több (akármennyi)
  - `'+'`: egy vagy több
  - `'?'`: nulla vagy egy
- attribútumok:
  - `<!ATTLIST element-name attribute-name attribute-type attribute-value>`
  - típusok: `CDATA`, `ID`, `(en1|en2)` (enum)
  - érték: `value`, `#REQUIRED`, `#IMPLIED` (megadása opcionális), `#FIXED`

## CSS (Cascading StyleSheet)

Egy stíluslap nyelv strukturált dokumentumok stilizálására (pl. XML, HTML).

Jellemzők:

- dobozmodell bemutatása:
  - `tartalom < padding < border < margin`
- értékpárokból áll
  - pl. a `display: block;` blokkosítva jeleníti meg az adott elemet, vagyis az elem **új sorban kezdődik** és a böngésző **teljes szélességét kitölti**
- **CSS megjegyzések**: `<!-- ... -->` karakterlánc használatával
- **CSS kiválasztók**: általános-, osztály-, azonosító-, típus kiválasztó (p), attribútum-, pszeudo kiválasztó
- **CSS kombinátorok**
  - _`whitespace`_: leszármazott kombinátor
    - pl. `div > p {}`: a div-en belüli összes p-t kiválassza mélységi szinttől függetlenül
  - `'>'`: gyermek kombinátor
    - pl. `div > p {}`: a div-en belüli összes p-t kiválassza ami közvetlenül a div után jön mélységét tekintve
  - `'+'`: szomszéd testvér kombinátor
    - pl. `div + p {}`: a div-ek utáni első p elementeket fogja stilizálni, a div-vel egy szinten
  - `'~'`: általános testvér kombinátor
    - pl. `div > p {}`: ugyan az mint a szomszéd testvér kombinátor, de ez stilizálja a div utáni összes p elementet, ugyanazon szinten
- **CSS pszeudo**
  - pszeudo osztályok (`':'`): speciális állapotok kezelésére és definiálására
    - pl. `:hover`
  - pszeudo elementek (`'::'`): elemek bizonyos részeinek stilizálásához
    - pl. adott element első betűjének vagy sorának stilizálása vagy tartalom beszúrása egy elem elé vagy után
- **CSS mértékegységek**
  - **abszolút-**: rögzített értékek
    - pl. `px`, `mm`, stb.
  - **relatív-**: relatívan változik egy másik méretbeli propertyhez
    - pl. `%`, `rem`, `em` (relatív a betűtípus méretéhez képest, pl. `2em` = 2-szer az aktuális betűtípus mérete)
- **CSS számlálók**
  - ...
- **Egyebek**:
  - `vertical-align: super;` a baseline fölé helyezi az adott elemet

## Kiegészítések

- ajánlatos a kurzus előadásának a Moodle kurzusában fellelhető VS Code kiterjesztéses dokumentumát áttanulmányozni, hiszen hasznos kiegészítőket tartalmaz a félévi munkához
- hasznos oldalak:
  - https://www.w3schools.com/
  - https://developer.mozilla.org/en-US/
