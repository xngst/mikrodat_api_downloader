# mikrodat api downloader

Ez a kód a mikrodat API-n keresztül adatokat gyűjt, feldolgozza azokat, majd egy SQLite adatbázisba menti. Az API által biztosított információk alapján fájlokat is letölt, PDF-ből szöveges formátumba konvertálja őket, és a megfelelő könyvtárakban tárolja. A kód részletes logokat készít, hogy könnyebb legyen a hibák diagnosztizálása és a működés nyomon követése.

---

## Funkciók és Célok

### 1. **Adatok Tárolása Az Adatbázisban**
A kód 3 adatbázis-táblát hoz létre és kezel:
- **`ujbuda_meghivo_mappa` (db_folder):** A mappák metaadatait tárolja, például a dátumot, üléstípust és helyszínt.
- **`ujbuda_napirendi` (db_napirendi):** A napirendi pontok adatait tartalmazza, beleértve a napirendi pont nevét, az előterjesztőt és a hivatkozásokat.
- **`ujbuda_file_det` (db_file_detail):** A napirendi pontokhoz tartozó dokumentumok adatait tartalmazza  
A tábla sémák megtalálhatóak lentebb.

### 2. **Mappaadatok Feldolgozása**
- Az API segítségével lekéri a mappák UUID-jait és metaadatait.
- Kiegészíti a meglévő mappaadatokat az adatbázisban.

### 3. **Napirendi Pontok Lekérése**
- A mappák típusától függően meghatározza a megfelelő API URL-t.
- Lekéri a napirendi pontokat, hozzáadja azokat az adatbázis ujbuda_napirendi táblájához.

### 4. **Fájlok Letöltése és Konvertálása**
- Letölti a napirendi pontokhoz kapcsolódó PDF fájlokat.
- Hozzáadja az ujbuda_file_det táblához a dokumentumok metaadatait. 
- A letöltött PDF dokumentumokat szöveges formátumba konvertálja, és letükrözve az eredeti mappastruktúrát menti.    
