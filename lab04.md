# 4. gyakorlat (10.01)

**Készítette**: Varga József Márk, Dr. Jeszenszky Péter tananyaga alapján.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/markvarga21/)

[www.markvarga.com](https://www.markvarga.com)

---

## 1. feladat

Ábrázoljuk a _The Hound of the Baskervilles_ című könyv egy részletét DTD és XML segítségével, amely egy esztétikus kimenetet ad a böngészőben. Kövessük a következő leírást: [https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/book/feladat.html](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/book/feladat.html)

**Megjegyzések a CSS stíluslaphoz**:

- betűtípusok betöltése: pl. `@import url("https://fonts.googleapis.com/css2?family=EB+Garamond");`
  - majd ennek használata: pl. `font-family: 'EB Garamond', Times, serif;`
- számlálókból többet is tudunk definiálni **szóközzel** elválasztva őket egymástól (pl. `counter-reset: chapter section;`)
- `vertical-align: super`: a szöveges konténer felső részére igazítja a tartalmat
- a különböző pszeudo elemeket és osztályokat láncolni is tudjuk egymás után
  - pl. `footnote:hover::before`, amely a `footnote` osztályú elemekre húzva az egérmutatót a `before` pszeudo elemet formázza

---

## 2. feladat

Készítsünk egy menürendszert illusztráló DTD-, illetőleg XML fájlt a következő leírást követve: [https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/menu/feladat.html](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/menu/feladat.html)

---

## 3. feladat

Készítsünk egy, a filmeket ábrázoló DTD és XML állományt a következő leírást követve: [https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/movies/feladat.html](https://arato.inf.unideb.hu/jeszenszky.peter/webtech/lab/xml/movies/feladat.html)

**Megjegyzések a CSS stíluslappal kapcsolatban**:

- listaszerű megjelenítés: `display: list-item` és `list-style-type: disc;`, mely a listaelemeket kör alakú pontokkal jelöli
  - számos egyéb érték is használható a `list-style-type` tulajdonságnál, pl. `square`, `circle` stb.
- `:lang(en)`: az angol nyelvű elemekre vonatkozik
- attribútumbeli érték behivatkozása/elérése a CSS-ben: `attr(id)`, amely elkéri az `id` attribútum értékét
- `:is(...)` ennek segítségével több különböző elemet is kiválaszthatunk és kezelhetünk egyszerre;
  - pl. `movie:is([mpa-rating=R], [mpa-rating=NC-17]) > :is(title, year)`: a `movie` elemek közül azokat választja ki, amelyeknek az `mpa-rating` attribútuma `R` vagy `NC-17`, és ezeknek a gyerekelemeként a `title` és `year` elemeket formázza

**DTD megjegyzések**:

- `NMTOKEN`: az attribútumnak érvényes XML névnek kell lennie, vagyis
  - **tartalmazhat**: betűket, számokat, alulvonást, kötőjelet, pontot, kettőspontot, de
  - **nem tartalmazhat**: pl. szóközt
  - lásd ezt a [linket](https://www.liquid-technologies.com/Reference/Glossary/DTD_Datatypes_NMTOKEN.html)
