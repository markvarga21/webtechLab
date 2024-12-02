# 11. gyakorlat (11.26)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

# Grid Layout

A CSS Grid Layout egy két dimenziós elrendezési rendszer, amely segítségével a weboldalakat oszlopokra és sorokra oszthatjuk. A Grid Layout segítségével a weboldalakat könnyen és gyorsan lehet elrendezni, anélkül, hogy a HTML kódját módosítanánk.

https://www.w3schools.com/css/css_grid.asp

# Multi Column Layout

A Multi Column Layout egy olyan elrendezési rendszer, amely segítségével a weboldalakat több oszlopra oszthatjuk.

https://www.w3schools.com/css/css3_multiple_columns.asp

## Kártyás feladat extra (1)

**Megjegyzések**:

- a számításban olvasható `10in + 5em` a következőképpen jön ki: a 4 kártyalap között `3x1 em` hézag van + `2em` margin a széleken, továbbá mivel 4 kártya van, melyek egyenkénti szélessége 2.5inch, ezért a számítás: `10in + 5em`
- a `calc()` függvény segítségével tudjuk kiszámolni ezen értékeket, melyben a `+` és `-` műveletek között **szóközöknek kell lenniük**

## Kártyás feladat extra (2)

**Megjegyzések**:

- `grid-template-columns: repeat(X, Y)`: `X` darab `Y` széles oszlop

```css
@media screen and (min-width: calc(5in + 3em)) {
  .cards {
    grid-template-columns: repeat(2, 2.5in);
  }
}
```

A fenti példában a következőképpen számolódnak a mértékek:

- 2 kártya oszlopot hozunk létre, melyek szélessége 2 x 2.5inch, valamint mivel 2 kártya van egyszerre egy sorban, melyek között `1em` hézag van, a széleken pedig `2em` margin, ezért a számítás: `5in + 3em`
  - ugyan így van a többi méret esetén is

## Kártyás feladat extra (3)

**Megjegyzések**:

- `grid-template-columns: repeat(auto-fit, 2.5in);`: a `repeat()` függvény `auto-fit` értéke azt jelenti, hogy annyi oszlopot hoz létre, amennyi csak belefér a konténerbe, melyek szélessége 2.5inch

## Grid puzzle

**Megjegyzések**:

- `height: 100vh;`: a `vh` egység a viewport magasságát jelenti, így a konténer magassága a teljes képernyő magasságát foglalja el
- `margin: auto`: a `margin` tulajdonság segítségével tudjuk középre igazítani a konténert
- `display: grid;`: a `grid` értékkel a konténer egy rácsos elrendezési rendszerként jelenik meg
- `grid-template-columns: repeat(3, 1fr);`: 3 egyenlő széles oszlopot hoz létre **a konténerben**
  - az `1fr` (_fraction_) érték azt jelenti, hogy az oszlopok egyenlő szélességűek lesznek
  - ha pl. `1fr 2fr 1fr` lenne, akkor az első és harmadik oszlop szélessége egyenlő lenne, a második pedig kétszer akkora lenne, mint a többié
- `grid-template-rows: repeat(5, 1fr)`: 5 egyenlő magas sorokat hoz létre **a konténeren belül**

```css
grid-template-areas:
  "A A A B" /* 1. sor */
  "C C D E" /* 2. sor */
  "F . G E" /* 3. sor */
  "F H H E" /* 4. sor */
  "I J J K" /* 5. sor */;
```

A fenti példában a `grid-template-areas` tulajdonság segítségével tudjuk megadni, hogy melyik elem melyik sorban és oszlopban helyezkedjen el.

A `.` karakterrel jelöljük azokat a területeket, ahol nem szeretnénk elemet elhelyezni.

A külünböző betűvel ellátott elemeket be is kell hivatkozni az általunk elkészített elemekre, pl. a következő módon:

```css
.A {
  grid-area: A;
}
```

A fenti példában a `grid-area` tulajdonság segítségével tudjuk megadni, hogy az adott elem melyik "azonosítójú" területen helyezkedjen el.

# Hogwarts extra extra

**Megjegyzések**:

- háttérkép beállítása: `background-image: url('...');`
- `background-size` lehetséges értékei:
  - https://www.w3schools.com/cssref/css3_pr_background-size.php
- `background-position` lehetséges értékei:
  - https://www.w3schools.com/cssref/pr_background-position.asp
- `-webkit-text-stroke-width`: azért van szükség a `-webkit-` előtagra, mert a `text-stroke` tulajdonság nem támogatott minden böngészőben
  - https://css-tricks.com/adding-stroke-to-web-text/https://www.w3schools.com/cssref/css3_pr_text-stroke.asp
- `background-size: 100% 100%`: a háttérkép mérete a konténer méretéhez igazodik
- `background-size: cover`: a háttérkép mérete a konténer méretéhez igazodik, de a kép arányai nem változnak
- `background-size: contain`: a háttérkép mérete a konténer méretéhez igazodik, de a kép arányai nem változnak, és a kép teljesen látható lesz

```css
form.fancy-form :is(input, select, textarea) {
  cursor: url("https://icons.getbootstrap.com/assets/icons/magic.svg"), default;
}
```

Amennyiben a kurzor egy `input`, `select` vagy `textarea` elem felett van, akkor a kurzor ikonja a megadott SVG fájlra fog váltani. Természetesen, saját kurzor ikont is megadhatunk.
