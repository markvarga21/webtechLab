# 3. gyakorlat (09.24)

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
  - általános: pl. `*`
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
  - pszeudo elementek (`'::pszeudoElemNeve'`): elemek bizonyos részeinek stilizálásához
    - pl. adott element első betűjének (`::first-letter`) vagy sorának (`::first-line`) stilizálása vagy tartalom beszúrása egy elem elé (`::before`) vagy után (`::after`) anélkül, hogy magát az elemet módosítanánk
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
- **Betűtípusok importálása**:
  - pl. `@import url('https://fonts.googleapis.com/css?family=Roboto');`
  - a fenti példában a Roboto betűtípust importáljuk, melyet a következőképpen tudunk használni a dokumentumunkban: `font-family: 'Roboto', sans-serif;`
    - amennyiben az egész dokumentumban ezt a betűtípust szeretnénk használni, akkor a `body` elemre kell alkalmazni a fenti tulajdonságot
  - egy adott oldalon használt betűtípusokat meg tudjuk tekinteni a böngészőkbeli DevTools segítségével (lásd [ezt](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/edit_fonts/) a linket pl. Firefox-ban)

**Feladatmegoldás**: stilizáljuk a [demó képnek](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/album/album.png) megfelelően az XML dokumentumunkat (`album.xml`)!

## Megjegyzések

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

## Hamlet szöveg átültetése XML-be, majd validálása DTD-vel és végül stilizálása CSS-sel

1. Oldjuk meg a következő linken lévő feladatot: [https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/play/](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/play/)

**Megjegyzések a CSS-sel kapcsolatosan**:

- a `*` kiválasztó az összes elemet kiválasztja (általános kiválasztó)
- `font-variant: small-caps`: kisbetűs szöveg nagybetűs megjelenítése, a kisbetűk nagybetűként jelennek meg (a kis és nagy betűk közötti **méretkülönbség változatlan**)
- `text-transform`: szöveg átalakítása
  - pl. `uppercase`: nagybetűsre alakítja a szöveget
  - pl. `lowercase`: kisbetűsre alakítja a szöveget
  - pl. `capitalize`: minden szó kezdőbetűjét nagybetűsre alakítja

## XML dokumentum validálása DTD-vel, valamint stilizálása CSS-sel

2. Oldjuk meg a következő linken lévő feladatot: [https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/book/](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/book/)

**Megjegyzések a CSS-sel kapcsolatban**:

- betűtípusok betöltése: `@import url('https://fonts.googleapis.com/css?family=Roboto');`
  - használata: pl. `font-family: 'Roboto', Times, serif;`
    - ebben az esetben, egy prioritás sorrendet adunk meg a betűtípusoknak: először a Roboto-t próbálja meg használni, ha nem találja a böngésző, akkor a Times-t, végül a serif-et
  - méretek: pl. `font-size: 1.5em;` vagy `font-size: 1.5rem;` vagy `font-size: 1.5px;` vagy `font-size: 1.5pt;` vagy `font-size: large` (ekkor a böngészőben beállított `large`-nak megfelelő méretet kapjuk, ami lehet különböző böngészőkben eltérő)
- a háttérszínt többféle képpen is be tudjuk állítani:
  - pl. `background-color: rgba(0, 0, 0, 0.5);`: az utolsó érték az átlátszóságot állítja be (0-1 közötti érték) vagy
  - `background-color: hsla(120, 100%, 50%, 0.3);`: az utolsó érték az átlátszóságot állítja be (0-1 közötti érték) vagy
  - ezeknek az átlátszóság nélküli változatai is léteznek: pl. `rgb(0, 0, 0)` és `hsl(0%, 0%, 0%)`
  - `background-color: red`: a háttérszín vörös lesz (szöveges formában)
  - `background-color: #ff0000`: a háttérszín vörös lesz (hexadecimális formában)
- `rem` vs. `em`: a `rem` a gyökér elem betűméretére vonatkozik, míg az `em` az aktuális elem betűméretére
