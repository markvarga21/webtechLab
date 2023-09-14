# A curl használata

## Telepítés

- Linux:

  ```
  sudo apt-get install curl
  ```

- Windows: <https://curl.se/windows/>

- Telepítés a [Miniconda](https://docs.conda.io/en/latest/miniconda.html) révén (Linux, macOS, Windows):
  ```
  conda install curl
  ```

## Rendelkezésre állás ellenőrzése

```
curl
curl --version
curl -V
```

## Segítség

Rendelkezésre álló parancssori opciók megjelenítése:

```
curl --help
curl -h
```

Kézikönyv megjelenítése:

```
curl --manual
curl -M
man curl
```

Dokumentáció: <https://curl.se/docs/>

## Alapvető használat

Webhely: <https://ip-api.com/>

---

Kapcsolók nélküli használat (_konzolra írja a kimenetet_)

```
curl http://ip-api.com/json
```

---

A lekérdezés eredményének mentése.

```
curl http://ip-api.com/json -O
```

Kapcsoló magyarázat:

- `-O`: kimenet átírányítása fájlba, melynek neve megegyezik a végpont nevével

---

A lekérdezés eredményének mentése és végbemenő némítása.

```
curl http://ip-api.com/json -O -s
```

Kapcsoló magyarázat:

- `-O`: kimenet átírányítása fájlba, melynek neve megegyezik a végpont nevével
- `-s`: néma üzemmód (nincs kimenete a parancsnak a konzolra)

---

A lekérdezés eredményének mentése az `ip-api.json` fájlba és végbemenő műveletek némítása.

```
curl http://ip-api.com/json -o ip-api.json -s
```

Kapcsoló magyarázat:

- `-o`: kimenet átírányítása a megadott fájlba
- `-s`: néma üzemmód (nincs kimenete a parancsnak a konzolra)

---

A lekérdezés eredményének mentése az `ip-api.json` fájlba és végbemenő műveletek kiíratása a konzolra.

```
curl http://ip-api.com/json -o ip-api.json -v -s
```

Kapcsoló magyarázat:

- `-o`: kimenet átírányítása a megadott fájlba
- `-v`: "beszédes" (_verbose_) mód bekapcsolása (a végbemenő műveletek ki lesznek iratva a konzolra)

---

A lekérdezés eredményének mentése az `ip-api.json` fájlba és végbemenő műveletek némítása.
Visszatéríti a kapott válaszban használt fejlécmezőket.

```
curl http://ip-api.com/json -o ip-api.json --dump-header ip-api.txt -s
```

Kapcsoló magyarázat:

- `-o`: kimenet átírányítása a megadott fájlba
- `-s`: néma üzemmód (nincs kimenete a parancsnak a konzolra)
- `---dump-header`: a válasz fejlécmezőinek átírányítása a megadott fájlba

---

A lekérdezés eredményének mentése az `ip-api.json` fájlba.
Kimenő és bejővő adatok kiiratása a konzolra (_stdout_).

```
curl http://ip-api.com/json -o ip-api.json --trace - | less
```

Kapcsoló magyarázat:

- `-o`: kimenet átírányítása a megadott fájlba
- `--trace`: kimenő és bejővő adatok átirányítása a megadott fájlba
  - `-`: ez esetben a standard kimenetre írja ezen adatokat

---

A lekérdezés eredményének mentése az `ip-api.json` fájlba.
Kimenő és bejővő adatok kiiratása a konzolra (_stdout_).

```
curl http://ip-api.com/json -o ip-api.json --trace-ascii - | less
```

Kapcsoló magyarázat:

- `-o`: kimenet átírányítása a megadott fájlba
- `--trace-ascii`: kimenő és bejővő adatok átirányítása a megadott fájlba, viszont ez esetben csak az ASCII részét téríti vissza
  - `-`: ez esetben a standard kimenetre írja ezen adatokat

---

## Átirányítás

### Példa (1)

Webhely: <http://www.w3.org/>

```
curl http://w3.org -v
```

Kérés átirányítása/mentése a megadott fájlba.

```
curl http://w3.org -v --location -o w3.html
curl http://w3.org -v -L -o w3.html
```

Kapcsoló magyarázat:

- `-v`: "beszédes" (_verbose_) mód bekapcsolása (a végbemenő műveletek ki lesznek iratva a konzolra)
- `--location`: ha a kért oldal át lett helyezve egy másik helyre (`3XX` státusz kód), akkor megismétli a kérést az új helyen lévő erőforráson
- `-o`: kimenet átírányítása a megadott fájlba

Továbbá, a fenti két parancs egyenlő, mivel a `--location` és a `-L` kapcsolók ugyan azt a célt szolgálják.

### Példa (2)

URL rövidítő szolgáltatás: <https://is.gd/>

```
curl -s https://is.gd/create.php?format=simple\&url=https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP > shorturl.txt
cat shorturl.txt
cat shorturl.txt | xargs curl -Is | grep -i ^Location
```

Kapcsoló magyarázat:

- `-s`: néma üzemmód (nincs kimenete a parancsnak a konzolra)
- `-I`: csak fejlécmezők lekérése

## Tartalomegyeztetés

### Ugyanaz a tartalom több különböző nyelven

Webhely: <http://www.gnu.org/>

```
curl http://www.gnu.org/ -v -H Accept-Language:de -o gnu.de.html
curl http://www.gnu.org/ -v -H Accept-Language:fr -o gnu.fr.html
```

Kapcsoló magyarázat:

- `-v`: "beszédes" (_verbose_) mód bekapcsolása (a végbemenő műveletek ki lesznek iratva a konzolra)

* `-H`: fejlécmezők beállításához

- `-o`: kimenet átírányítása a megadott fájlba

### Átirányítás webhely mobil verziójára

Webhely: <https://hvg.hu/>

```
curl https://hvg.hu/ --http1.1 -v --user-agent "Mozilla/5.0 (iPhone; CPU iPhone OS 14_7_1 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.1.2 Mobile/15E148 Safari/604.1"
```

Lásd: <https://www.whatismybrowser.com/guides/the-latest-user-agent/>

Kapcsoló magyarázat:

- `--http1.1`: HTTP verziószám megadásához
- `--user-agent`: felhasználói ágens megadásához

### Ugyanaz a tartalom több különböző formátumban

Lásd: <https://www.dbpedia.org/>

```
curl https://dbpedia.org/resource/Grumpy_Cat -v
curl https://dbpedia.org/resource/Grumpy_Cat -v -H Accept:text/html
curl https://dbpedia.org/resource/Grumpy_Cat -v -H Accept:text/html -L -o Grumpy_Cat.html
curl https://dbpedia.org/resource/Grumpy_Cat -v -H Accept:application/json
curl https://dbpedia.org/resource/Grumpy_Cat -v -H Accept:application/json -L -O
```

## Minták

### Példa (1)

Lásd: <https://www.gnu.org/licenses/>

Ugyanazon erőforrás több változatának egyszerre való kérése. (`.html`, `.md` és `.txt` formátumokban). Az utolsó példánál külön mappába lesznek irányítva e kimenetek.

```
curl https://www.gnu.org/licenses/gpl-3.0.\{html,md,txt\} -O
curl "https://www.gnu.org/licenses/gpl-3.0.{html,md,txt}" -O
curl "https://www.gnu.org/licenses/gpl-3.0.{html,md,txt}" -O -v
curl "https://www.gnu.org/licenses/gpl-3.0.{html,md,txt}" --create-dirs -o "licenses/gpl-3.0.#1"
```

### Példa (2)

Lásd: <https://en.wikisource.org/wiki/The_Hound_of_the_Baskervilles_(Newnes,_1902)>

Ugyanazon webhelynek több aloldalának letöltése. Ki lehet próbálni megnyitni a HTML oldalt. Utóbbi alkönyvtárakba szedi a kapott válaszokat.

```
curl https://en.wikisource.org/wiki/The_Hound_of_the_Baskervilles_\(Newnes,_1902\)/Chapter_[1-15] -O
curl https://en.wikisource.org/wiki/The_Hound_of_the_Baskervilles_\(Newnes,_1902\)/Chapter_[1-15] --create-dirs -o "The_Hound_of_the_Baskervilles/Chapter_#1.html"
```

## Több kérés

Több kérés egyszerre indítása.

```
curl https://www.gnu.org/licenses/gpl-3.0.txt -O https://www.apache.org/licenses/LICENSE-2.0.txt -O
curl -H Accept:application/json https://dbpedia.org/resource/Hungary https://dbpedia.org/resource/Budapest -v
```

Csak a fejlécmezők elkérése (`--head`)

```
curl --head https://dbpedia.org/resource/Hungary https://dbpedia.org/resource/Budapest
```

Jelzi a curl-nek, hogy egy különböző folyamot, műveletet biztosítson/használjon a következő cím lekéréséhez. Változatos paraméterek megadásához használatos. (`--next`)

```
curl -H Accept:application/json https://dbpedia.org/resource/Hungary --next -H Accept:application/rdf+xml https://dbpedia.org/resource/Budapest -v
```

## Megszakított átvitel folytatása

Lásd: <https://download.bbbike.org/osm/bbbike/Budapest/>

Szakítsuk meg az átvitelt a <kbd>CTRL</kbd> + <kbd>C</kbd> megnyomásával:

```
curl https://download.bbbike.org/osm/bbbike/Budapest/Budapest.osm.gz -O
```

Az átvitel folytatása:

```
curl https://download.bbbike.org/osm/bbbike/Budapest/Budapest.osm.gz -O -C -
```

Kapcsoló magyarázat:

- `-C -`: a curl automatikusan megtalálja mit kell folytatnia és folytatja is azt

## Tartományra vonatkozó kérések

Lásd: <https://www.gnu.org/licenses/gpl-3.0.txt>

Az első 100 bájt: (-r maga a range vagy --range)

```
curl https://www.gnu.org/licenses/gpl-3.0.txt -r 0-99
curl https://www.gnu.org/licenses/gpl-3.0.txt -r 0-99 -v
```

Az utolsó 100 bájt:

```
curl https://www.gnu.org/licenses/gpl-3.0.txt -r -100
curl https://www.gnu.org/licenses/gpl-3.0.txt -r -100 -v
```

Az első és utolsó 100 bájt:

```
curl https://www.gnu.org/licenses/gpl-3.0.txt -r 0-99,-100
curl https://www.gnu.org/licenses/gpl-3.0.txt -r 0-99,-100 -v
```

## Feltételes kérések

Lásd: <https://earthquake.usgs.gov/earthquakes/feed/v1.0/csv.php>

```
curl https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.csv -O --http1.1 -v
curl https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.csv -O --http1.1 -z all_hour.csv -v
sleep 60; curl https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.csv -O --http1.1 -z all_hour.csv -v
```

Kapcsoló információk:

- `-z`: elkér egy fájlt, amely módosítva volt a megadott időtartam óta. Ha nincs semmi megadva, a fájl módosítási dátumat veszi alapul.
