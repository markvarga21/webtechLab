# 9. gyakorlat (11.12)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

# SCSS

https://sass-lang.com/guide

- mi is az az SCSS és a SaSS?
  - igazábol a SaSS egy kiterjesztés, amit a SCSS használ (Sassy CSS), de a kettőt gyakran összekeverik, és a SaSS-t SCSS-nek hívják
  - a SaSS egy **CSS kiterjesztés**, amely lehetővé teszi a CSS kód egyszerűbb és gyorsabb írását
- SCSS direktívák (_at-szabályok_): `@use`, `@forward`, `@mixin`, `@include`, `@extend`
- `$name`: változók használata (pl. színek)
- CSS kód generálása SCSS kódból:
  - `sass --watch style.scss style.css` (node szükséges hozzá)
  - Live Sass Compiler VSCode-ban
- `@use "sass:color";`: a color modul importálása
- CSS kiválasztók egymásba ágyazása SCSS-ben:
  - `&`: a szülő kiválasztóra utal, tehát olyan, mintha egyből utánna írtuk volna (akkor szokás alkalmazni, ha nem a _whitespace_ kombinátort szeretnénk használni)
  - egyébként pedig a következőképpen lehet értelmezni (_whitespace kombinátor_):
    - ```
        .parent {
            .child {
            ...
            }
        }
      ```
    - ```
        .parent .child {...}
      ```

## Hogwarts folytatás (JS + extra feladatok)

**JavaScript megjegyzések**:

- `==` vs `===`: a bal oldali operátor kevésbé szigorú, mint a jobb oldali. Például: `1 == '1'` igaz, de `1 === '1'` hamis
  - vagyis, amennyire lehet, mindig használjuk a `===` operátort (és ennek megfelelően az ezt használó további operátorokat is)
- `customValidity`: egy HTML5-ben bevezetett tulajdonság, amely lehetővé teszi, hogy a fejlesztő saját validációs üzeneteket adjon meg a form elemeihez
- `Math.floor(Math.random() * houses.length);`: mivel a `Math.random()` függvény 0 és 1 közötti valós értéket ad vissza, a `Math.floor()` függvénnyel lefelé kerekítjük, majd a házak számával szorozzuk, hogy egy véletlenszerű indexet kapjunk a 0 és a házak száma között
- `form.house.dispatchEvent(new Event("change"));`: egy `change` eseményt idéz elő, hogy működőképes maradjon a háttérszín változás

## Diagonal sudoku

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/sass/diagonal-sudoku/feladat.html

**CSS megjegyzések**:

- `%valami { ... }`: egy _placeholder_ létrehozása, amelyet a `@extend` direktívával lehet használni
  - **placeholder**: olyan, mint egy osztály, de nem jelenik meg a CSS-ben, csak akkor, ha egy másik osztály kiterjeszti (pl. `@extend %valami`)
  - tulajdonképpen CSS "tulajdonság-csoportokat" tudunk ezzel _copy-paste szerűen_ használni
- `@use "sudoku"`: a `sudoku.scss` fájl importálása
- változókra hivatkozás: `#{$name}` (lásd a sztring interpolációt)
  - **sass string interpoláció**: egy olyan technika, amely lehetővé teszi SASS Script kifejezések használatát pl. CSS kódban, ahol pl. string-ként van rájuk szükség (s nem pedig magára a változóként)
- `@for $i from 1 through 9 { ... }`: egy ciklus, amely 1-től 9-ig megy végig

## Colors

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/sass/colors/feladat.html

**CSS megjegyzések**:

- `@use "sass:color";`: a color modul importálása
  - a `color` modul segítségével lehetőségünk van a színekkel kapcsolatos műveletek végrehajtására (pl. színárnyalatok, színkontrasztok, stb.)

Példa a whitespace karaktertől eltérő kiválasztók egymásba ágyazására SCSS-ben:

```scss
  div.columns {
      ...
      & > div {
          ...
      }
      & > div::before {
          ...
      }
  }
```

A következő CSS kódot generálja:

```css
div.columns > div {
  ...;
}
div.columns > div::before {
  ...;
}
```

Tehát, a `&` karakterrel a szülő kiválasztóra tudunk hivatkozni.

- változók használata: `$name`
- függvény paraméterek megadása:
  - `someLibrary.someFunction($param1: value1, $param2: value2);`, vagy ha nem ragaszkodunk a paraméterek nevéhez, akkor elegendő csak a paraméterek értékeit megadni: `someLibrary.someFunction(value1, value2);`

## Color transition

https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/sass/color-transition/feladat.html

**CSS megjegyzések**:

- **SCSS mixinek**: tekinthetőek egyfajta függvényeknek (bár ez nem helyes terminológia, de a működésük hasonló), amelyeket a `@mixin` direktívával hozhatunk létre, és a `@include` direktívával hívhatunk meg
