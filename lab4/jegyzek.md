# XML stilizálása CSS-sel folytatás

## Book

- XML doksi bemutatása és vizsgálata
- kész oldal bemutatása és vizsgálata
- DTD készítése
- számlálók, számláló stílusok, counter-increment, counter-reset stb.
- `:hover` pszeudo-osztály bemutatása és illusztrálása
- super align -> a baseline feletti részre húzza be
- `'+'`: szomszéd testvér kombinátor
  - pl. `div + p {}`: a div-ek utáni első p elementeket fogja stilizálni, a div-vel egy szinten

---

## Movies

- XML doksi bemutatása és vizsgálata
- kész oldal bemutatása és vizsgálata
- DTD készítése
  - attribútumok használata a DTD-ben (pl. `#REQUIRED`) -> a `#REQUIRED` azt jelenti, hogy az adott attribútum kötelező a megadott elemhez (pl. `<movie>`-hoz)
  - `NMTOKEN` (name token) -> tartalmazhat szöveget, számot vagy a következő karaktereket: `':'`, `'_'`, `'-'`, `'.'`, de szóköz nem lehet benne
- `list-style-type: disc;` -> a listaelemeket körökkel jelöli, egyéb lehetséges értékek a `square` és a `circle`
- `lang` attribútum használata XML-ben -> a `lang` attribútummal megadható, hogy az adott elem milyen nyelven van megadva (pl. `<movie lang="en">`), így a böngészők tudják, hogy milyen nyelven kell megjeleníteni az adott elem tartalmát
  - példa bemutatása
- `attr()` -> XML-beli attribútom értékének behivatkozása CSS-ben

---

## Album

- XML doksi bemutatása és vizsgálata
- kész oldal bemutatása és vizsgálata
- DTD készítése
- egy táblázat az egész dokumentum
- `fit-content` és `-moz-fit-content` bemutatása
  - azért van szükség a `moz` előtagra, mivel manapság már szinte minden modern böngésző támogatja a `fit-content` használatát, kivéve a firefox
- `margin: auto;` -> a böngésző számítja ki a margin-t
- a `display: inline-block;` és a sima `display: inline;` között az a különbség, hogy előbbi lehetővé teszi az adott elem magasságának és szélességének a módosítását/beállítását
- Unicode karakterek CSS-en belüli használata/beszúrása a `\nnnn`, ahol `nnnn` a négy számjegy hosszúságú decimális szám
- `:nth-child`: adott elemnek minden `n`-edik elemét válassza ki
  - az `odd` nyilván a páratlanokat, az `even` pedig a párosakat (az `odd` és az `even` előre definiáltak, ezért lehet őket nevüktől fogva használni CSS-be beágyazva)

---

## Directory

- XML doksi bemutatása és vizsgálata
- kész oldal bemutatása és vizsgálata
- DTD készítése
- `<!ENTITY % name.attr "name CDATA #REQUIRED">`
  - ennek köszönhetően a `%name.attr` változót használva be tudjuk hivatkozni a `name` attribútumot a DTD-ben
  - olyan mint egy placeholder
- a `:root` pszeudo-osztály a dokumentum gyökérelemét jelöli
- a `directory:empty` azokat `directory` elemeket jelöli, amik üresek tehát nincsen záró `</directory>` tagjük
- a `file[size="1"]` azokat a `file` elemeket jelöli, amiknek a `size` attribútuma `1`
