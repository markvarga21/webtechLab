# 10. gyakorlat (11.19)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

# Reszponzív webdesign (RWD)

Több féleképpen is el tudunk érni reszpozív webdizájnt, pl. a flexbox-, grid-, multi column elrendezésekkel. Továbbá, a média lekérdezések is rendkívül fontos szerepet játszanak egy reszponzív weboldal kifejlesztése során.

Egy alternatívája az adaptív webdizájn (AWD), amely a különböző eszközökön való megjelenítésre külön-külön elkészített weboldalakat használja. Ilyenek például azon oldalak, ahol a weboldal különböző URL-eken érhető el aszerint, hogy milyen eszközön jelenik meg (pl. `m.domain.com`).

https://medium.com/pxcode/difference-between-awd-rwd-why-you-should-use-rwd-6731ce57cd28

# Media lekérdezések

Lehetővé teszik CSS szabályok csak bizonyos feltételek teljesülése esetén történő alkalmazását. A média lekérdezések a `@media` kulcsszóval kezdődnek, amelyet egy feltétel követ. A feltétel egy vagy több tulajdonság értékétől függően dönthető el, hogy a CSS szabályokat alkalmazni kell-e.

```css
@media screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

A fenti példában a `@media` kulcsszó után a `screen` kulcsszóval megadjuk, hogy a média lekérdezés a képernyőre vonatkozik (egyéb média típusok pl. `printer` és `all`). A `and` kulcsszó után a feltétel következik, amely egy vagy több tulajdonság értékétől függően dönthető el, hogy a CSS szabályokat alkalmazni kell-e. A fenti példában a `max-width: 600px` feltétel azt jelenti, hogy a CSS szabályok akkor fognak alkalmazódni, ha a képernyő szélessége nem haladja meg a 600 pixelt.

Kialakíthatunk olyan média lekérdezéseket is, amelyek több feltételt is tartalmaznak. Például:

```css
@media screen and (min-width: 400px) and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

A fenti példában a CSS szabályok a $[400px, 600px]$ tartományban fognak alkalmazódni.

# Flexbox

https://css-tricks.com/snippets/css/a-guide-to-flexbox/

# Grid

https://css-tricks.com/snippets/css/complete-guide-grid/

## Cards

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/cards/feladat.html

**HTML megjegyzések**:

- a `<br/>` elemek sortörésre használatosak, amennyiben nem szeretnénk flexboxot használni

**CSS megjegyzések**:

```css
... {
  text-orientation: upright;
  writing-mode: vertical-rl;
}
```

A `writing-mode` tulajdonság segítségével lehetőségünk van a szöveg irányát megváltoztatni. A `vertical-rl` értékkel a szöveg függőlegesen, jobbról balra fog megjelenni.

A `text-orientation` tulajdonság segítségével a szöveg orientációját tudjuk megváltoztatni. Az `upright` értékkel a szöveg függőlegesen fog megjelenni.

- azért érdemes `span` elemeket használni, mivel ezek nem rendelkeznek alapértelmezett stílussal, így könnyen formázhatóak (nem `block` elemek)

## Flexbox playground (interaktív flexbox "játszótér")

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/flexbox-playground/feladat.html

**CSS megjegyzések**:

- a `align-self` tulajdonság segítségével egy elemnek lehetősége van arra, hogy felülírja a konténer `align-items` tulajdonságát

**JS megjegyzések**:

- amennyiben CSS tulajdonságokat szeretnénk elérni és módosítani, melyek tartalmaznak kötőjelet, úgy a kötőjelet követő karakternek nagybetűnek kell lennie (pl. `align-items` helyett `alignItems`), lásd `camelCase` konvenció

## Webtech feladat

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
