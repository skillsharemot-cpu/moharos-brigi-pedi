# Moharos Brigi - Pedikűr | Weboldal és Rendszer Vázlat

A megosztott dokumentumok (Weblap felépítése, Chat-Widget Logika, Brief) aprólékos feldolgozása alapján az alábbi részletes struktúra rajzolódik ki. A weboldal nemcsak információs és bemutatkozó felület, hanem a GoHighLevel (GHL) rendszerének köszönhetően egy komoly automata előszűrő és foglalási automatizmus is egyben.

## 1. Weboldal Felépítése és Design Elemei

### A) Header (Fejléc)
*   **Logó:** Moharos Brigi - Pedikűr
*   **Menüpontok:** Szolgáltatások | Galéria | Házirend | Kapcsolat
*   **Kiemelt CTA Gomb:** `[IDŐPONTOT FOGLALOK]` (figyelemfelkeltő színnel)

### B) Hero Section (Nyitóképernyő - Az első benyomás)
*   **Vizuális elem:** Egy professzionális, magas minőségű kép Brigiről munka közben, vagy egy esztétikus közeli fotó egy ápolt lábról.
*   **Főcím:** "Professzionális gondoskodás a lábaidnak – Moharos Brigi Pedikűr"
*   **Alcím:** "Szakértelem, precizitás és megújulás egy nyugodt, tiszta környezetben. Fedezd fel a fájdalommentes és esztétikus lábápolás élményét! Szikés, gépi és Callux kezelések a lábaid egészségéért."
*   **Gomb:** `[IDŐPONTOT FOGLALOK]`

### C) Bemutatkozás / Értékajánlat
*   **Címsor:** "Miért bízd rám a lábaid egészségét?"
*   **Szövegezés:** Hangsúly a szakmai felkészültségen és a prevención (a pedikűr egészségügyi fontosságán). Cél, hogy a vendég könnyű léptekkel, egy tiszta és rendezett környezetből távozzon.

### D) Szolgáltatások (Kártyás elrendezés)
Három fő pillér vizuális, lapos tagolása:
1.  **Esztétikai és Gépi Pedikűr:** Frissítő, szépítő kezelés, megelőzéshez.
2.  **Szakpedikűr (Szikés technika):** Bőrkeményedések, repedt sarkak és makacs problémák professzionális, biztonságos kezelése.
3.  **Problémás területek kezelése:** Benőtt köröm, tyúkszem fájdalommentes és szakszerű eltávolítása. 

### E) A "Bizalom és Rend" szekció (Házirend kivonat)
*A naptár (foglalási modul) elé építve figyelemfelhívó arany kerettel és pasztell hátterrel.*
*   **Címsor:** "Vigyázzunk egymás idejére!"
*   **Tartalom:**
    *   Pontos érkezés (10-15 perc késés már kezelési idő rövidülést vonhat maga után).
    *   24 órás lemondási és módosítási szabályzat.
    *   Egészségügyi felelősségvállalás (betegen vagy fertőző lábbal módosítás szükséges).

### F) Vélemények (Testimonials)
*   Valós elégedettségi visszajelzések a Google-ről vagy a Facebook oldalról.

### G) Lábléc (Footer)
*   **Elérhetőségek:** Cím, Telefon, Email.
*   **Linkek:** Adatkezelési tájékoztató, Házirend teljes szövege (A kapott `Házirend.pdf` belinkelése/megjelenítése).

---

## 2. Foglalási Folyamat és Chat-Widget "Szűrő" Logika (GHL)

A weboldal kulcsfontosságú eleme az integrált kérdőív (Survey), amely mind a widgetből, mind az időpontfoglaló gombokból indulhat. Célja a kliens állapotának felmérése és a megfelelő szolgáltatás előkészítése.

### I. Fázis: Állapotfelmérő Kérdőív (Survey)
1.  **Alapadatok:** Név, Telefonszám, Mikor volt utoljára pedikűrön.
2.  **Kezelés Típusa & Fájdalom:**
    *   Keresett szolgáltatás (Esztétikai / Szakpedikűr / Problémás).
    *   Szabadszöveges fájdalomleírás.
3.  **Egészségügyi és Biztonsági check (Azonnali elágazások):**
    *   *Problémás láb (vadhús, súlyosabb benövés stb.):* A vendég felkérése egy fotó feltöltésére a területről (GHL File Upload) -> Brigi előre látja a helyzetet.
    *   *Cukorbetegség / Keringési zavar:* "Figyelmeztetés: Szikés kezelést csak fokozott óvatossággal végzek. Kérlek, jelezd a helyszínen!"
    *   *Fertőző betegség (gomba, rosszindulatú szemölcs, nyílt seb):* A rendszer megszakítja az utat a naptár felé -> Várólista üzenet: *"Orvosi szakvéleményre lehet szükség, Brigi hamarosan visszahív egyeztetni."*
4.  **Házirend Elfogadása:** Kötelező checkbox a naptár elérése előtt.

### II. Fázis: Naptár (Booking)
Csak a "tiszta", automatikusan kezelhető esetek jutnak el az időpontválasztásig, a többiekkel Brigi manuálisan veszi fel a kapcsolatot.

### III. Fázis: Automatizált Visszaigazolás & Címkézés
*   Az ügyfél azonnali SMS-t kap a foglalás idejével, a címmel, és a 24 órás lemondási emlékeztetővel.
*   Brigi egy belső applikációs értesítést (vagy e-mailt) kap arról, hogy kicsoda és milyen problémával (GHL "Tag"-ek pl: `Cukorbeteg`, `Problémás`, `Új vendég`) foglalt időpontot.

### IV. Fázis: Emlékeztetők és "No-Show" büntetés
*   **T-24 órás Emlékeztető:** SMS üzenet holnapi időpontról; utolsó esély visszamondani díjmentesen.
*   **T+1 órás Follow-up:** Kezelés után üzenet + értékelés kérése (Google Review Link).
*   **Problémakezelés:**
    *   *Késés esetén:* Gombnyomásra indítható SMS Brigitte részéről ("Kérlek hívj, 15 perc felett nem tudlak fogadni").
    *   *No-Show (Nem jött el a vendég):* Brigi rárakja az "Előlegköteles" / "Tiltólista" taget.
    *   *Következmény:* Ha a vendég legközelebb újra foglalni próbál, kap egy figyelmeztetést: "Korábbi meg nem jelenésed miatt az időpontot csak 50% bankkártyás előleg (Stripe) befizetésével rögzíthetjük".
