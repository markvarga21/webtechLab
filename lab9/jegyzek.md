## 9. gyakorlat

### Kártyás feladat
- **HTML oldal**:
  - `<span>` elemek: általános célú, semleges elem (nem befolyásolja a szöveg megjelenését)
  - `data-customName`: saját attribútum, a `data-` előtaggal kezdődő attribútumokat a böngésző nem kezeli, így a fejlesztők saját célra használhatják
  - `<br>`: új sorba törés
- **CSS stíluslap flexbox nélkül**:
  - `transform: rotate(45deg)`: forgatás 45 fokkal
    - további megadási módok: `rotateX()`, `rotateY()`, `rotateZ()`
    - mértékegységei: `deg`, `rad`, `turn`
- **CSS stíluslap flexbox használatával**:
  - CSS tulajdonságok/szabályok importálása egy másik CSS fájlba: `@import url("fajlnev.css");`
  - mi is az a flexbox?
    - reszponzivitás (képernyőmérethez igazodó elrendezés) növelésére használatos
  - `display: flex`: flexbox bekapcsolása
  - hasznos oldalak:
    - https://css-tricks.com/snippets/css/a-guide-to-flexbox/
    - https://flexbox.help/

---

### Color bars feladat
- **HTML oldal**:
  - relatív CSS mértékegység: `vh` (viewport height) vagyis a képernyő magasságának százaléka
    - pl. ha a képernyő magassága 30cm akkor az `1vh` 0.3cm lesz
- **CSS stíluslap**:
  - ID kiválasztók használata: `#id`
  
---

### Color bars float
- **HTML oldal**: ...
- **CSS stíluslap**:
  - `float: left`: balra igazítás
    - esetünkben a színek sorrendjének manipulálására használjuk, vagyis rendes megadási sorrendben (balról) adja vissza a színeket
    - ennek értéke lehet:
      - `left`: balra igazítás
      - `right`: jobbra igazítás
      - `none` (alapértelmezett): ahogy meg voltak adva
      - `inherit`: szülőtől öröklődik

---

### Color bars flexbox
- **HTML oldal**: ...
- **CSS stíluslap**:
  - `flex: 1`: a flexbox elemek egyenlően osztoznak a rendelkezésre álló helyen
    - ennek értéke lehet:
      - `0`: nem osztozik a rendelkezésre álló helyen
      - `1`: egyenlően osztozik a rendelkezésre álló helyen
      - `auto`: a tartalomnak megfelelően osztozik a rendelkezésre álló helyen
    - ez a tulajdonság a `flex-grow`, `flex-shrink` és `flex-basis` tulajdonságokat rövidített formában tartalmazza
      - `flex-grow`: megadja, hogy az elem mennyit fog növekedni az ugyanabban a tárolóban lévő többi flex elemhez képest 
      - `flex-shrink`: megadja, hogy az elem mennyit fog csökkenni az ugyanabban a tárolóban lévő többi flex elemhez képest
      - `flex-basis`: megadja, hogy az elem alapértelmezett mérete mennyi legyen

---

### Hogwarts form továbbfejlesztése
- utolsó pont karakter levédése az email cím megadásánál
- színek hozzáadása az `<option>` elemekhez
- jelszó mező hozzáadása
- fotó mező hozzáaadása
- dinamikus színváltás JavaScript segítségével