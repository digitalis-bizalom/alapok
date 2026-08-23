# Bizonyítékok

Ez a könyvtár a `digitalis-bizalom/alapok` követelményeihez kapcsolódó **bizonyítékok, bizonyítékrekordok és ellenőrzési eredmények** helye.

A cél nem dokumentumgyűjtemény létrehozása, hanem annak láthatóvá tétele, hogy egy követelmény teljesülését **miből lehet ténylegesen megállapítani**.

```text
követelmény
-> bizonyíték
-> mérce
-> teszt
-> értékelés
```

A részletes fogalmi szabályokat a `00-modszertan/kovetelmeny-bizonyitek-teszt.md` rögzíti.

## 1. Mi számít bizonyítéknak?

Bizonyíték ebben a módszertanban minden olyan ellenőrizhető adat, artifact, megfigyelés vagy dokumentált eredmény lehet, amely egy konkrét követelmény teljesülését alátámaszthatja vagy cáfolhatja.

A `bizonyíték` itt nem matematikai értelemben vett bizonyítást vagy végleges igazolást jelent. A szó az angol *evidence* megfelelője: olyan ellenőrizhető anyagot, amelyet a mércével és a teszttel együtt értékelünk.

```text
bizonyíték
!= bizonyítás
!= következtetés
```

Például:

- teszt- vagy gyakorlatjegyzőkönyv;
- helyreállítási eredmény;
- mérési adat;
- audit trail;
- konfigurációs állapot;
- reprodukálható build vagy restore artifact;
- szerződéses exit mechanizmus;
- jogosultsági vagy delegációs record;
- incidensből származó ellenőrzött adat;
- kriptográfiailag ellenőrizhető provenance;
- megfelelő jogosultsággal végzett zárt audit eredménye.

```text
bizonyíték
!= forrás
!= szabályzati állítás
!= önigazolás
```

A `FORRÁS` egy állítás vagy követelmény eredetét, szakmai indokát vagy provenance-ét dokumentálja.

A `BIZONYÍTÉK` ezzel szemben azt mutatja meg, hogy egy konkrét rendszer, folyamat vagy képesség esetében mi figyelhető meg vagy ellenőrizhető.

## 2. Mi nem elég önmagában?

Önmagában általában nem tekinthető elegendő bizonyítéknak:

- hogy egy követelmény szerepel egy szabályzatban;
- hogy egy rendszer rendelkezik tanúsítvánnyal;
- hogy a beszállító vagy üzemeltető megfelelőséget állít;
- hogy egy recovery terv létezik;
- hogy egy kontroll technikailag konfigurálva van;
- hogy egy dashboard zöld állapotot mutat.

```text
documented capability
!= demonstrated capability
```

A szükséges bizonyítékot mindig a vizsgált követelmény és annak kockázata határozza meg.

## 3. Bizonyítékrekord

Ha egy bizonyíték külön fájlként kerül a repositoryba, célszerű legalább az alábbi adatokat rögzíteni:

```text
ID
RELATED REQUIREMENT
BIZONYÍTÉK TÍPUSA
SCOPE
DATE / PERIOD
SOURCE SYSTEM / ACTOR
COLLECTION METHOD
RESULT
INTEGRITY / PROVENANCE
LIMITATIONS
ACCESS / DISCLOSURE STATUS
RELATED TEST
STATUS
```

A rekord formája az adott bizonyítéktípustól függhet.

Nem cél, hogy minden bizonyíték ugyanabba a merev sablonba kerüljön; a cél az, hogy a releváns eredet, hatókör, integritás és korlát rekonstruálható legyen.

## 4. Bizonyíték és mérce

A bizonyíték önmagában nem mondja meg, hogy egy követelmény teljesül.

```text
bizonyíték
!= következtetés
```

Az bizonyítékot mindig a követelményhez tartozó `MÉRCE` alapján kell értékelni.

Példa:

```text
BIZONYÍTÉK:
    helyreállítási gyakorlat tényleges ideje

MÉRCE:
    tényleges helyreállítási idő <= deklarált RTO
```

Ha nincs legitim mérce, ezt nyitott szakmai kérdésként kell kezelni.

## 5. Bizonyíték és teszt

A `TESZT` az a dokumentált eljárás, amely az bizonyítékot előállítja vagy a követelmény teljesülését vizsgálja.

```text
TEST PROCEDURE
    -> előállítja / vizsgálja a bizonyítékot
    -> a bizonyítékot a mérce alapján értékeljük
    -> result is compared with failure condition
```

A teszt és a bizonyíték külön rekord lehet.

Egy ismételhető tesztből több időpontban több bizonyítékrekord származhat.

## 6. Pozitív és negatív bizonyíték

Az `evidence/` könyvtár nem csak a teljesülést alátámasztó anyagok helye.

Fontos lehet:

- ellenpélda;
- sikertelen teszt;
- recovery failure;
- nem reprodukálható eredmény;
- hiányzó dependency;
- ellentmondó audit;
- mérési bizonytalanság;
- ellenbizonyíték.

```text
bizonyítéktár
!= sikerek archívuma
```

A negatív bizonyíték különösen értékes lehet a követelmény, mérce vagy teszt javításához.

## 7. Független ellenőrizhetőség

Ahol lehetséges, a kritikus követelmény teljesülését ne kizárólag az a szereplő igazolja, aki:

- a rendszert tervezi;
- a rendszert szállítja;
- a rendszert üzemelteti;
- vagy a megfelelésért közvetlenül felel.

```text
self-assertion
!= independent verification
```

A független ellenőrzés formája lehet például:

- más szervezeti szereplő;
- külső auditor;
- reprodukálható teszt;
- nyilvánosan ellenőrizhető artifact;
- több független bizonyítékcsatorna;
- megfelelő jogosultságú zárt review.

## 8. Időbeliség

A bizonyíték időhöz kötött.

Egy korábbi sikeres teszt nem bizonyít korlátlan ideig fennálló megfelelést.

Ezért ahol releváns, rögzíteni kell:

- a bizonyíték keletkezési idejét;
- az érintett rendszer vagy konfiguráció verzióját;
- az érvényességi időszakot;
- azóta történt lényegi változásokat.

```text
was true
!= is still true
```

## 9. Reprodukálhatóság

Ahol lehetséges, a bizonyíték gyűjtésének vagy a tesztnek reprodukálhatónak kell lennie.

Ez nem jelenti azt, hogy minden tesztnek nyilvánosan reprodukálhatónak kell lennie.

A cél:

- a lépések dokumentálhatók legyenek;
- az inputok és feltételek ismertek legyenek;
- az eredmény ne csak egyetlen személy emlékezetére vagy állítására támaszkodjon.

## 10. Titkosság és disclosure

A public `evidence/` könyvtár nem jelenti azt, hogy minden bizonyíték nyilvános lehet.

Különösen érzékeny lehet:

- kritikus infrastruktúra függőségi térképe;
- recovery priority;
- fallback mechanizmus;
- hozzáférési és jogosultsági részlet;
- fizikai vagy területi sérülékenység;
- security architecture;
- incidens részletes technikai adata.

```text
public methodology
!= automatikusan nyilvános bizonyíték
```

Egy bizonyítékrekord lehet például:

```text
PUBLIC
REDACTED
SUMMARY ONLY
RESTRICTED
NOT FOR PUBLICATION
```

A nyilvános repositoryba csak olyan bizonyíték kerülhet, amelynek publikációs és security kockázata elfogadható.

## 11. Redakció és összefoglaló bizonyíték

Ha a teljes bizonyíték nem publikálható, lehetséges:

- aggregált eredmény;
- redaktált record;
- független audit összefoglaló;
- cryptographic proof;
- ellenőrzött pass/fail eredmény;
- olyan metadata, amely nem tárja fel a veszélyes részleteket.

A redakció nem használható arra, hogy a követelmény ellenőrizhetősége teljesen eltűnjön.

```text
restricted detail
+
documented verification path
```

## 12. A bizonyíték provenance-e

A fontos bizonyítéknál meg kell őrizni, amennyire releváns:

- ki vagy mi hozta létre;
- milyen rendszerből származik;
- milyen módszerrel gyűjtötték;
- változott-e azóta;
- hogyan ellenőrizhető az integritása;
- milyen transzformáció történt rajta.

A provenance célja, hogy később is rekonstruálható legyen:

> Mi alapján vontuk le ezt a következtetést?

## 13. Kapcsolat a diagnózisokkal

A jelenlegi magyar állapotokra, konkrét intézményekre, beszállítókra vagy rendszerekre vonatkozó diagnózisok is bizonyítékot igényelhetnek.

Ezek azonban ne keveredjenek automatikusan a normatív követelményekkel.

```text
diagnosis
!= requirement
```

A diagnózisból származó bizonyíték felhasználható prioritás, kockázat vagy gap igazolására, de nem teszi önmagában univerzálissá az adott követelményt.

## 14. Kapcsolat az implementation candidates réteggel

Egy implementation candidate értékelésénél a bizonyíték feladata annak megmutatása, hogy a candidate ténylegesen hogyan teljesít egy már definiált követelményt.

```text
requirement
-> test
-> bizonyíték
-> candidate evaluation
```

Nem fordítva:

```text
candidate
-> szelektált bizonyíték
-> candidate-specific requirement
```

## 15. Bizonyítékstátusz

Egy bizonyítékrekord státusza lehet például:

```text
DRAFT
    még hiányos vagy ellenőrizetlen

COLLECTED
    a bizonyíték rendelkezésre áll, de még nincs teljesen értékelve

VERIFIED
    eredete és integritása megfelelően ellenőrzött

SUPERSEDED
    újabb bizonyíték váltotta fel

DISPUTED
    lényeges ellenbizonyíték vagy értelmezési vita van

RESTRICTED
    létezik és releváns, de nem publikálható teljes terjedelemben
```

A státusz nem azonos a kapcsolódó követelmény teljesülési eredményével.

```text
bizonyítékstátusz
!= teljesülési eredmény
```

## 16. Minimális szabály

Ha egy követelményhez nincs megfelelő bizonyíték, ezt láthatóan kell kezelni.

```text
nincs bizonyíték
!= teljesült
```

A bizonyíték hiánya nem minden esetben bizonyítja a követelmény megsértését, de nem kezelhető úgy, mintha a teljesülés igazolt lenne.

## 17. Könyvtárszerkezet

A könyvtár később bizonyítéktípus vagy domain szerint bővíthető, de csak akkor érdemes új alkönyvtárat létrehozni, ha tényleges tartalom kerül bele.

Például később:

```text
evidence/
    README.md
    recovery/
    dependency-exit/
    authority/
    interoperability/
```

A cél nem előre felépített üres taxonomy, hanem használat közben kialakuló, indokolt struktúra.
