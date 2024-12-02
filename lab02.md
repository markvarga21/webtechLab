# 2. gyakorlat (09.17)

## Visual Studio Code kiterjesztések

[Link az ajánlásokhoz](https://gist.github.com/jeszy75/2e1ebba7b1836692ef6b3478f92c4e68)

Számunkra a következők lesznek fontosak:

- `markdown all in one`
- `markdown preview enhanced`
- `markdown pdf`
- `marp for vs code`
- `live preview`
- `xml` és `xml tools`
- `css peek`
- `color highlight`

Pár egyéb, hasznos kiterjesztés:

- `auto close tag` és `auto rename tag`
- `indent-rainbow`
- `live sass compiler`
- `prettier`
- `tailwind css intellisense` és `tailwind fold`
- `github copilot`

## Markdown

Készítsünk egy markdown dokumentumot, majd próbáljuk ki az alábbiakban említett megjegyzéseket!

Megjegyzések:

- [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/)
- Próbáljuk ki a `markdown all in one` és a `markdown preview enhanced` kiterjesztéseket, illetve ezután exportáljuk is ki a dokumentumot a `ctrl+shift+p` paranccsal (pl. PDF-be a `markdown pdf` kiterjesztéssel, vagy HTML-be a `markdown all in one` kiterjesztéssel)
- Alternatíva a markdown különböző formátumokba való exportálására: [pandoc](https://pandoc.org/)
  - pl. `pandoc input.md -o output.pdf` vagy `pandoc input.md -o output.html`
- A Github alapértelmezetten támogatja a markdown formátumot, lásd az órai jegyzékeinket nyers formátumban, vagy a következő dokumentumot (amely teljes mértékeben kihasználja a Github Flavor Markdown nyújtotta lehetőségeket):
  - [link](https://gist.github.com/jeszy75/0353997f8db8332f61a777602d252b07)
- [Markdown Marp](https://marp.app/): prezentációk készítéséhez
- [Mardown Mermaid](https://gist.github.com/jeszy75/f5f09955da5621856654cb801799315d) diagramok beágyazásához
- Bizonyos esetekben HTML elemeket is használhatunk a Markdown-ban, pl. egy könyvjegyzék készítéséhez
- Egyéb jelölőnyelvek a Markdown-hoz hasonlóan: `LaTeX`

## XML (eXtensible Markup Language)

- általános célú jelölőnyelv
  - mi is az a jelölőnyelv: szöveges annotálására használt számítógépes nyelv
- adatcsere formátumként használatos
  - mint pl. a JSON-t
- XML elementek validálása (lásd DTD)
- HTML vs. XML

**Feladatmegoldás**: készítsük el az [album.txt](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/album/album.txt)-nek megfelelő XML fájlt!

## DTD (Document Type Definition)

- XML dokumentumok validálásához
- elem típusok:
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

**Feladatmegoldáss**: készítsünk egy validációs DTD állományt az előző XML fájlunkhoz!

## CSS (Cascading StyleSheet)

Egy stíluslap nyelv strukturált dokumentumok stilizálására (pl. XML, HTML).

Jellemzők:

- dobozmodell bemutatása:
  - `tartalom < padding < border < margin`
- kulcs-érték párokból áll
  - pl. a `background-color: blue;`
- **CSS szintaxis**:

```css
kiválasztó1 <kombinátor > kiválasztó2,
... {
  kulcs: érték;
  ...;
}
```

- **CSS megjegyzések**: `<!-- ... -->` karakterlánc használatával
- **CSS kiválasztók**:
  - általános
  - osztály: pl. `.valami`, `elem.valami` vagy `[class="valami"]`
  - azonosító: pl. `#valami`, `elem#valami` vagy `[id="valami"]`
  - típus kiválasztó pl. `p`
  - attribútum: pl. `[attr]`, `[attr="value"]` vagy `[attr~="value"]`
  - pszeudo kiválasztó: pszeudo osztályok és pszeudo elemek (lásd a lentiekben)
- **CSS [kombinátorok](https://www.w3schools.com/css/css_combinators.asp)**
  - _`whitespace`_: leszármazott kombinátor
    - pl. `div > p {}`: a div-en belüli összes p-t kiválassza mélységi szinttől függetlenül
  - `'>'`: gyermek kombinátor
    - pl. `div > p {}`: a div-en belüli összes p-t kiválassza ami közvetlenül a div után jön mélységét tekintve
  - `'+'`: szomszéd testvér kombinátor
    - pl. `div + p {}`: a div-ek utáni első p elementeket fogja stilizálni, a div-vel egy szinten
  - `'~'`: általános testvér kombinátor
    - pl. `div ~ p {}`: ugyan az mint a szomszéd testvér kombinátor, de ez stilizálja a div utáni összes p elementet, ugyanazon szinten
- **CSS pszeudo**
  - pszeudo osztályok (`':pszeudoOsztalyNev'`): speciális állapotok kezelésére és definiálására
    - pl. `:hover`
  - pszeudo elementek (`'::pszeudoElemNev'`): elemek bizonyos részeinek stilizálásához
    - pl. adott element első betűjének vagy sorának stilizálása vagy tartalom beszúrása egy elem elé (`::before`) vagy után (`::after`) anélkül, hogy magát az elemet módosítanánk
- **CSS mértékegységek**
  - **abszolút**: rögzített értékek
    - pl. `px`, `mm`, stb.
  - **relatív**: relatívan változik egy másik méretbeli propertyhez
    - pl. `%`, `rem`, `em` (relatív a betűtípus méretéhez képest, pl. `2em` = 2-szer az aktuális betűtípus mérete)
- **CSS számlálók**
  - `counter-reset`: számláló kezdeti értéke
    - ezt mindig az adott elem előtt kell megadni ahol a számlálót használni szeretnénk (pl. a szülő vagy a legkülsőbb body elemben)
  - `counter-increment`: számláló növelése
  - `content: counter(szamlalo);`: a számláló értékének megjelenítése

**Feladatmegoldás**: stilizáljuk a [demó képnek](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/album/album.png) megfelelően az XML dokumentumunkat!

## Megjegyzések:

- `display` tulajdonságok:
  - `block`: minden ilyen elem új sorban kezdődik és a teljes szélességet elfoglalja
  - `inline`: az elemek egymás mellett jelennek meg
  - `inline-block`: az elemek egymás mellett jelennek meg, de a blokk elemek tulajdonságait is megkapják
  - `table`: táblázatot hoz létre
  - `table-cell`: cellát hoz létre
  - `table-row`: sort hoz létre
    - a fenti három tulajdonság a táblázatoknál használatos, de inkább az XML esetében, hiszen a HTML-ben rendelkezésre állnak a táblázat elemek (lásd `<table>`, `<tbody>`, `<thead>`, `<tr>`, `<td>`)
- Unicode karakterek használata decimális formában CSS-ben: `\2013` (a hosszú `–` karakter)
- `box-shadow`: doboz árnyékolás
  - pl. `box-shadow: 10px 15px 5px #000000;`, ami a következőt jelenti: `10px` jobbra, `15px` lefelé, `5px` árnyékolás és `#000000` szín
