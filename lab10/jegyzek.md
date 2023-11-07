# 10. gyakorlat (11.07)

## Hogwarts extra

- ...

---

## Colors

- mi is az az SCSS és a SaSS?
  - igazábol a SaSS egy kiterjesztés, amit a SCSS használ (Sassy CSS), de a kettőt gyakran összekeverik, és a SaSS-t SCSS-nek hívják
  - a SaSS egy **CSS kiterjesztés**, amely lehetővé teszi a CSS kód egyszerűbb és gyorsabb írását
- SCSS direktívák (_at-szabályok_): `@import`, `@use`, `@forward`, `@mixin`, `@include`, `@extend`
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

---

## Color transition

- `@mixin`: újrafelhasználható kódrészletek létrehozása (többé kevésbé függvények, de ez nem a legjobb hasonlat)
- `@include`: a mixin-ek használata
- `for` ciklusok használata: pl. `@for $i from 1 through 10 {...}`
- `${i}` vs. `#{$i}`: a `#`-t használjuk, ha a változó értékét szeretnénk használni, nem magát a változót
  - tehát, a SASS interpoláció egy olyan technika, amely lehetővé teszi SASS Script kifejezések használatát pl. CSS kódban, ahol pl. string-ként van rájuk szükség

---

## Sudoku diagonal

- HTML kód megírása Emett rövidítések segítségével
- alap CSS/SCSS kód/stíluslap megírása
- diagonális stíluslap megírása
- placeholder kiválasztók használata: `%`-al kezdődnek, és nem jelennek meg a CSS kimenetben
  - `@extend`: a placeholder kiválasztók használata
  - `@extend` vs. `@mixin` + `@include`: https://medium.com/stories-from-the-keen/when-to-use-extends-vs-mixins-in-sass-b09d55abd53
