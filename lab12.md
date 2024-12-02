# 12. gyakorlat (12.03)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

## Bootstrap

A Bootstrap keretrendszer segítségével, előre elkészített, **reszponzív** komponenseket tudunk használni (táblázatok, gombok, form elemek stb.) a kliens oldali fejlesztés során, ami rendkívül meg tudják gyorsítani a fejlesztési folyamatot.

https://getbootstrap.com/

A bootstrap elemek használatához elegendő csupán a megfelelő class neveket hozzá tűzni az elemeinkhez, és a Bootstrap-et behivatkozni a HTML fájlunkba.

Bootstrap keretrendszer behivatkozása:

```html
<head>
  ...
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
    rel="stylesheet"
  />
</head>
```

Példa elsődleges stílusú gombra:

```html
<button class="btn btn-primary">Elsődleges gomb</button>
```

## Tailwind CSS

A Bootstrap alternatívájaként lehet használni a Tailwind CSS stilizálási keretrendszert is, amely lehetővé teszi a komponensek testreszabását. Maga a Tailwind CSS nem tartalmaz előre elkészített komponenseket, csak a stílusokat, amelyeket a HTML elemekhez hozzá kell rendelni, ugyan úgy osztályok formájában (pl. a `bg-blue-500` osztály egy háttérszín beállítására szolgál, amely 500-as skálájú kék színre állítja a háttérszínt). A Tailwind is tartalmaz számos elvonatkoztatott mértékegységet, pl. a `mb-1` osztály egy `0.25rem` magasságú margót állít be az elem aljára. A továbbiakért lásd a dokumentációt: https://tailwindcss.com/

Amennyiben futtató környezet nélkül szeretnénk használni a Tailwind CSS-t, akkor használjuk a következő útmutatót:

https://tailwindcss.com/docs/installation/play-cdn

Normál esetben a Tailwind-et az `npm` csomagkezelő rendszerrel kellene használni, azonban a fenti linken található CDN segítségével a Tailwind-et egy egyszerű HTML fájlban is használhatjuk.

## WebStorm IDE

A kliens oldali fejlesztéshez, a Visual Studio Code alternatívájaként használhatjuk a JetBrains termékét, a Webstorm-ot is. Mindkét IDE-nek megvannak az előnyei és hátrányai, azonban a Webstorm egy kicsit több funkciót tartalmaz a kliens oldali fejlesztéshez, mint a Visual Studio Code, viszont több erőforrást is igényel.

https://www.jetbrains.com/webstorm/

**Megjegyzés**: hallgatói jogviszony esetén a JetBrains Ultimate termékcsomagjai ingyenesen használhatóak, lásd a következő linket: https://www.jetbrains.com/shop/eform/students

## React JS

A React JS egy JavaScript keretrendszer, amely segítségével könnyedén tudunk dinamikus weboldalakat készíteni. A React JS egy komponens alapú keretrendszer, amelynek segítségével a kódunkat kisebb részekre tudjuk szétválasztani, és ezáltal könnyebben karbantarthatóvá válik. A React JS egy modern keretrendszer, amely a JSX (JavaScript XML) szintaxist használja, amely lehetővé teszi a HTML elemek és a JavaScript kód egyidejű használatát.

A fő koncepció a React esetében az **SPA** (_Single Page Application_) fejlesztése lenne, amikor is a különböző oldalakat egyetlen HTML fájlban tartjuk, és a különböző komponensek megjelenítését cseréljük ki a különböző oldalak között.

https://react.dev/

## Hogwarts Bootstrap

- Hogwarts form stilizálása Bootstrap segítségével
- link a feladathoz: https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/hogwarts-form-bootstrap/

## Countries Bootstrap

- az elkészített fájlok stilizálása a Bootstrap keretrendszer használatával
  - `countries1.html`, `countries2.html`, `countries3.html`, ...
- link a feladathoz: https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/html/countries-bootstrap/

**Megjegyzések**:

- a `getJSON()` függvény segítségével adatokat tudunk betölteni egy adott URL-ről, amelyet JSON formátumban kapunk meg
  - ehhez hasonló a `fetch()` függvény is, amely a modern böngészőkben elérhető,
  - vagy ha használunk valamilyen kliens oldali keretrendszert (ReactJS, Angular stb.), ahol rendelkezésünkre áll a NodeJS környezet, akkor a `axios` modult is használhatjuk
- az `each()` függvény segítségével tudunk egy adott tömb elemein végigiterálni (lásd a for-each ciklust)
