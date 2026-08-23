# State-function completeness

Ez a dokumentum azt a módszertani kaput definiálja, amellyel ellenőrizzük, hogy az `Alapok` ne csak digitális infrastruktúrákat, biztonsági kontrollokat vagy közigazgatási szolgáltatásokat vizsgáljon, hanem a digitális állam működéséhez szükséges **állami funkciók teljességét** is.

A kiinduló különbség:

```text
ország / társadalom működőképessége
!=
közszolgáltatások működőképessége
!=
az állam mint szuverén közhatalom működőképessége
```

A digitális állam akkor sem tekinthető teljesnek, ha szolgáltatásai kényelmesek és informatikai rendszerei biztonságosak, de egy kritikus helyzetben nem képes jogszerűen és rekonstruálhatóan fenntartani a közhatalmi működést.

## 1. A completeness gate célja

A `state-function completeness` nem újabb követelménydomain, hanem **ellenőrzési kapu**.

Feladata annak vizsgálata, hogy egy követelménykészlet:

- lefedi-e az állam kritikus funkcióit;
- nem redukálja-e az államot digitális szolgáltatóplatformmá;
- kezeli-e a közhatalom folytonosságát;
- kezeli-e a fizikai-területi működés függőségeit;
- kezeli-e a normál, degradált, rendkívüli és helyreállítási működést;
- különbséget tesz-e identitás, jogosultság, hivatal és jogszerű közhatalmi aktus között;
- képes-e kimutatni a jelenlegi követelménykészlet vakfoltjait.

```text
completeness gate
!=
minden állami funkció külön követelményként való felsorolása
```

A gate eredménye lehet az is, hogy egy területet még nem fedünk le megfelelően.

A jelen dokumentumnak nem célja az állam vagy az állami funkciók általános és végleges elméleti definíciója. A `state function` itt feladathoz kötött auditfogalom: annyi elméleti megkülönböztetést vezetünk be, amennyi a megbízható digitális állam követelményeinek vakfoltmentes vizsgálatához szükséges.

```text
audit coordinate
!= complete theory of the state
```

## 2. Az állami funkció mint vizsgálati egység

Ebben a módszertanban `state function` olyan közfeladat, közhatalmi vagy szuverén képesség, amelynek elvesztése az állam jogszerű működését, területi kontrollját, társadalmi alapfunkcióit vagy az állampolgárok jogállását érdemben veszélyeztetné.

A state function lehet:

- közvetlen közhatalmi funkció;
- szuverén döntési képesség;
- kritikus adminisztratív képesség;
- olyan háttérfunkció, amely nélkül jogszerű közhatalmi működés nem tartható fenn;
- olyan szolgáltatás, amelynek kiesése más állami funkciók működését teszi lehetetlenné.

A kategória nem azonos a minisztériumok, hatóságok vagy szervezeti egységek aktuális listájával.

```text
state function
!= organization chart
```

Az állami funkciókat lehetőleg a szükséges képesség felől kell leírni, nem a jelenlegi intézményi elhelyezkedésük felől.

## 3. A szuverén közhatalmi réteg

A completeness gate külön ellenőrzi, hogy a rendszer képes-e fenntartani a jogszerű közhatalom működését.

A következő fogalmak nem vonhatók össze:

```text
identity
!= authentication
!= authorization
!= public office
!= lawful public authority
!= valid official act
```

Egy személy vagy gépi ágens sikeres azonosítása önmagában nem bizonyítja:

- hogy közhivatalt tölt be;
- hogy az adott ügyben hatáskörrel rendelkezik;
- hogy a hatáskör gyakorlásának feltételei fennállnak;
- hogy a döntés jogszerű;
- hogy a kibocsátott aktus hiteles és érvényes;
- hogy az aktus később rekonstruálható.

A digitális állami infrastruktúrának ezért nemcsak identitás- és hozzáférés-kezelést, hanem szükség szerint a **hivatal, hatáskör, delegáció, döntési provenance és hivatalos aktus** ellenőrizhetőségét is támogatnia kell.

## 4. Állami funkciók lefedettségi mátrixa

A completeness audit során minden azonosított kritikus state functionhöz legalább a következő dimenziókat kell megvizsgálni.

```text
STATE FUNCTION

1. NORMAL MODE
2. DEGRADED MODE
3. EMERGENCY SUBSTITUTION
4. RECOVERY PRIORITY
5. AUTHORITY CONTINUITY
6. DATA / SEMANTIC CONTINUITY
7. PHYSICAL-TERRITORIAL DEPENDENCIES
8. EXTERNAL / JURISDICTIONAL DEPENDENCIES
9. SECRECY / VERIFIABILITY
10. NON-DIGITAL FALLBACK
11. RECONCILIATION
12. OFFICIAL COMMUNICATION
```

Nem minden dimenzió ugyanolyan erős minden funkciónál. A `N/A` azonban legyen indokolt, ne hallgatólagos.

### 4.1. Normál működés

A `NORMAL MODE` azt írja le, hogyan működik a state function rendes körülmények között.

Vizsgálható többek között:

- mely szereplők jogosultak eljárni;
- milyen rendszerek és adatok szükségesek;
- milyen külső és belső függőségek vannak;
- milyen idő- és minőségi követelmények érvényesek;
- hogyan bizonyítható a döntések vagy aktusok eredete és érvényessége.

A normál működés leírása önmagában nem teljesíti a completeness gate-et.

### 4.2. Degradált működés

A `DEGRADED MODE` azt vizsgálja, hogy a funkció milyen csökkentett szolgáltatási vagy információs szinten maradhat működőképes.

Példák:

- központi szolgáltatás kiesése;
- hálózati kapcsolat korlátozottsága;
- részleges adat-hozzáférés;
- külső szolgáltató elérhetetlensége;
- kapacitáshiány;
- bizonyos automatizmusok kiesése.

A cél nem feltétlenül a teljes normál szolgáltatás fenntartása, hanem a funkció **minimum jogszerű és biztonságos működésének** megőrzése.

```text
degraded operation
!= normal operation at lower performance only
```

Lehetséges, hogy degradált módban más eljárás, más szerepkör vagy más prioritás szükséges.

### 4.3. Emergency substitution

Az `EMERGENCY SUBSTITUTION` azt vizsgálja, hogy rendkívüli helyzetben:

- ki helyettesíthet kit;
- milyen jogalapon;
- milyen időbeli és tárgyi korláttal;
- hogyan dokumentáljuk az eltérést;
- hogyan akadályozzuk meg, hogy az ideiglenes jogkör tartóssá váljon;
- hogyan térünk vissza a normál működéshez.

```text
emergency authority
!= permanent authority
```

A rendkívüli működés csak akkor tekinthető teljesnek, ha a visszatérés és az utólagos ellenőrzés mechanizmusa is megvan.

### 4.4. Recovery priority

Nem minden állami funkció állítható helyre egyszerre.

A completeness gate ezért megköveteli a helyreállítási prioritás explicit kezelését.

Vizsgálandó:

- mi az a minimum viable sovereign operation, amelyet először helyre kell állítani;
- mely funkciók függenek egymástól;
- milyen sorrendben kell adatot, identitást, kommunikációt, jogosultságot és fizikai infrastruktúrát helyreállítani;
- mely funkciók időérzékenyek;
- mely funkciók elvesztése okoz visszafordíthatatlan vagy aránytalan kárt.

```text
recovery
!= systems restored in arbitrary order
```

A prioritás indoklása része a state-function coverage-nek.

### 4.5. Continuity of sovereign authority

A digitális működés kiesése nem szakíthatja meg automatikusan a jogszerű közhatalmi folytonosságot.

Vizsgálandó:

- hogyan bizonyítható, hogy ki jogosult eljárni;
- hogyan marad rekonstruálható a hatáskör és delegáció;
- hogyan állapítható meg egy hivatalos aktus érvényessége;
- mi történik kulcs-, identitás- vagy trust-anchor kompromittálódásakor;
- hogyan áll helyre a hiteles döntési lánc;
- hogyan kezelhető vezető, hivatal vagy szervezet átmeneti kiesése.

A cél:

```text
authenticity and validity of official acts
must not depend on an irreplaceable operator
```

Ez nem követeli meg, hogy minden döntés decentralizált legyen. A követelmény a hitelesség, jogszerűség és rekonstruálhatóság folytonossága.

### 4.6. Data and semantic continuity

Az állami funkció működéséhez nemcsak adatokra, hanem azok értelmére is szükség lehet.

Vizsgálandó:

- az adatok hozzáférhetősége;
- integritása;
- eredete;
- időbelisége;
- sémája és jelentése;
- a szükséges végrehajtási környezet;
- hosszú távú visszaolvashatósága;
- migrálhatósága;
- rekonstruálhatósága.

```text
data retained
!= state function reconstructable
```

A szuverenitás időbeli dimenziója ezért magában foglalhatja a szemantikai, környezeti és kriptográfiai folytonosságot is.

### 4.7. Physical-territorial continuity

A digitális állam fizikai állam marad.

A completeness gate ezért vizsgálja a digitális funkciók fizikai és területi feltételeit is:

- energia;
- telekommunikáció;
- fizikai hozzáférés;
- adatközpont vagy más infrastruktúra;
- eszköz- és alkatrészellátás;
- területi jelenlét;
- helyi személyzet;
- logisztika;
- kritikus dokumentumok vagy tárgyi eszközök;
- határ- vagy terület-specifikus működés.

```text
digital continuity
!= physical continuity automatically
```

Ahol a funkció területi jelenlétet igényel, annak kiesése önálló failure mode.

### 4.8. External and jurisdictional dependencies

A state function nem tekinthető teljesen kontrolláltnak pusztán azért, mert technikailag működik.

Vizsgálandó:

- külföldi joghatóság;
- exportkontroll;
- szankciós kitettség;
- szolgáltatásmegtagadás;
- külföldi cloud vagy platformfüggőség;
- licenc vagy kulcs elérhetősége;
- külső identitás- vagy trust-szolgáltató;
- külső szakértelem;
- kritikus alkatrész vagy frissítés;
- határon átnyúló adat- vagy hálózati függőség.

A kérdés nem az, hogy minden külső függőség megszüntethető-e, hanem:

```text
dependency known?
dependency bounded?
dependency replaceable?
failure survivable?
```

### 4.9. Legitimate secrecy and verifiability

Egy államnak lehetnek jogszerűen titkos vagy korlátozott információi.

Ezért:

```text
verifiability
!= universal public disclosure
```

A completeness gate azt vizsgálja, hogy korlátozott nyilvánosság mellett is létezzen megfelelő ellenőrzési út:

- jogosult auditor;
- elkülönített oversight;
- reprodukálható zárt teszt;
- ellenőrizhető provenance;
- dokumentált kivétel;
- megfelelő hozzáférési és naplózási mechanizmus.

A titkosság önmagában nem lehet az ellenőrizhetetlenség indoka.

### 4.10. Non-digital fallback

Bizonyos state functionöknél szükség lehet nem digitális vagy kevésbé digitális helyettesítő működésre.

Ez lehet például:

- papíralapú eljárás;
- helyi offline nyilvántartás;
- manuális hitelesítés;
- alternatív kommunikáció;
- helyben működő minimális rendszer.

A fallback megléte azonban önmagában nem elég.

Vizsgálandó:

- valóban végrehajtható-e;
- megfelelően jogszerű-e;
- kik jogosultak használni;
- hogyan kerülnek vissza az eredmények a normál rendszerbe;
- milyen konfliktusokat okozhat párhuzamos működés.

### 4.11. Reconciliation

A helyettesítő, offline vagy degradált működés után az állapotokat össze kell tudni egyeztetni.

A `RECONCILIATION` azt vizsgálja:

- melyik adat vagy aktus elsődleges;
- hogyan kezeljük a konfliktusokat;
- hogyan bizonyítjuk az időrendet;
- hogyan kerülhető el a duplikáció;
- hogyan kezeljük az utólag érvénytelennek bizonyuló aktust;
- hogyan dokumentáljuk az eltéréseket.

```text
fallback completed
!= normal state restored
```

A visszatérés külön state-function capability.

### 4.12. Authentic official communication

A szuverén állami működés része, hogy az állam hitelesen tudjon kommunikálni.

Vizsgálandó:

- hogyan ismerhető fel egy hivatalos közlés;
- hogyan igazolható annak kibocsátója;
- hogyan kezelhető kompromittált kommunikációs csatorna;
- van-e alternatív hivatalos csatorna;
- hogyan kommunikálható rendkívüli helyzetben a jogosultság, döntés vagy utasítás;
- hogyan különböztethető meg a hamisított állami kommunikáció a valóditól.

A hiteles kommunikáció nem azonos a puszta platform-hozzáféréssel.

```text
message delivered
!= official communication authenticated
```

## 5. Minimum viable sovereign operation

Súlyos válságban a teljes digitális állam nem feltétlenül tartható fenn.

A completeness gate ezért megköveteli annak meghatározását, hogy mi az a **minimum viable sovereign operation**, amely alatt az állam már nem képes alapvető szuverén és közhatalmi funkcióit jogszerűen fenntartani.

Ez a minimum nem univerzális fix lista. Az elemzésnek azonban explicit módon választ kell adnia legalább arra, hogy:

- mely funkciók elengedhetetlenek;
- milyen minimális információ szükséges hozzájuk;
- milyen fizikai jelenlét szükséges;
- milyen jogosultsági és döntési lánc szükséges;
- milyen kommunikáció szükséges;
- milyen függőségek nélkülözhetetlenek;
- mennyi ideig tartható fenn a minimum állapot.

## 6. State-function coverage record

Egy állami funkció completeness-auditja legalább az alábbi formában dokumentálható:

```text
STATE FUNCTION
<név>

PURPOSE
<mit kell az államnak képesnek lennie megtenni>

SOVEREIGN / PUBLIC-AUTHORITY RELEVANCE
<miért konstitutív vagy kritikus>

NORMAL MODE
<normál működés>

DEGRADED MODE
<csökkentett működés>

EMERGENCY SUBSTITUTION
<helyettesítés, jogalap, korlátok>

RECOVERY PRIORITY
<helyreállítási sorrend és időérzékenység>

AUTHORITY CONTINUITY
<hivatal, hatáskör, delegáció, official act>

DATA / SEMANTIC CONTINUITY
<adat, jelentés, provenance, környezet>

PHYSICAL-TERRITORIAL DEPENDENCIES
<fizikai és területi feltételek>

EXTERNAL / JURISDICTIONAL DEPENDENCIES
<külső kitettségek>

SECRECY / VERIFIABILITY
<ellenőrzési út>

NON-DIGITAL FALLBACK
<ha releváns>

RECONCILIATION
<visszatérés és konfliktuskezelés>

OFFICIAL COMMUNICATION
<hiteles kommunikáció>

COVERAGE STATUS
<COVERED / PARTIAL / OPEN / N/A>

OPEN GAPS
<azonosított hiányok>
```

Ez a record nem feltétlenül public requirement file. Lehet módszertani audit-artefaktum, amelyből később konkrét követelmények származnak.

Egy konkrét állami funkcióra kitöltött coverage record olyan információkat tartalmazhat, amelyekből kritikus függőségek, recovery priorityk, fallback-mechanizmusok, területi vagy infrastruktúra-kitettségek következtethetők ki. Ezért:

```text
public methodology
!= automatically public audit result
```

Konkrét coverage record nyilvánosságra hozatala külön publication- és security-review tárgya. A nyilvános változat szükség esetén aggregált, részleges vagy redaktált lehet, miközben a releváns ellenőrzési út továbbra is dokumentált marad.

## 7. Coverage státusz

Javasolt minimális státuszok:

```text
COVERED
    a releváns dimenziókat megfelelő követelmények fedik

PARTIAL
    van érdemi lefedettség, de ismert hiány maradt

OPEN
    a funkció vagy dimenzió releváns, de még nincs megfelelően lefedve

N/A
    az adott dimenzió szakmailag nem releváns; indoklás szükséges
```

A `COVERED` nem jelenti azt, hogy egy konkrét állami rendszer teljesíti a követelményeket.

```text
coverage status
!= compliance result
```

## 8. A completeness audit kimenete

A completeness audit eredménye nem egyetlen százalék vagy pontszám.

Elsődleges kimenete:

- lefedett state functionök;
- részlegesen lefedett state functionök;
- nyitott funkciók;
- nyitott dimenziók;
- ismeretlen függőségek;
- olyan területek, ahol nincs legitim mérce vagy teszt;
- olyan state functionök, amelyekhez új `Alapok` követelmény szükséges.

A cél a vakfoltok láthatóvá tétele.

```text
unknown
!= covered
```

## 9. Kapcsolat az élethelyzet- és szolgáltatási nézettel

A state-function completeness az állam oldaláról vizsgálja a teljességet.

Ettől különbözik az állampolgár vagy vállalkozás oldaláról vizsgált szolgáltatási, élethelyzet- vagy ügyteljesség.

```text
state-function view
!=
life-situation / service view
```

A két nézet várhatóan egymást kiegészítő ellenőrzési perspektíva, de a jelen dokumentum nem rögzíti közöttük a részletes fogalmi vagy szerkezeti megfeleltetést.

A jelen dokumentum csak a state-function oldali completeness gate-et definiálja.

Az élethelyzet- és szolgáltatási teljesség részletes módszertana külön dokumentumban kezelhető, ha ehhez megfelelő elsődleges forrás- és módszertani alap rendelkezésre áll.

## 10. Kapcsolat a követelmény–bizonyíték–teszt módszerrel

A completeness gate azt mondja meg, **mit nem szabad elfelejteni**.

A `kovetelmeny-bizonyitek-teszt.md` azt mondja meg, **hogyan kell egy már azonosított követelményt ellenőrizhetővé tenni**.

```text
state-function completeness
    -> coverage / blind-spot detection

követelmény-bizonyíték-teszt
    -> operationalization / verification
```

Egy azonosított coverage gapből ezért tipikusan egy vagy több új követelmény származik.

## 11. Kapcsolat a Manifestóval

A completeness gate nem követeli meg, hogy minden state function külön Manifesto-pontként jelenjen meg.

A Manifesto rövid szakmai minimum marad.

A gate azt ellenőrzi, hogy a rövid állítások és az `Alapok` együtt ne hagyjanak el olyan konstitutív állami képességet, amely nélkül a „megbízható digitális állam” fogalma félrevezetően szűk lenne.

```text
short manifesto
+
complete enough supporting requirements
```

A completeness audit ezért a Manifesto publikálása előtt is használható kontrollként.

## 12. Módszertani korlát

Ez a dokumentum nem állítja, hogy a state functionök teljes és végleges taxonómiája már rendelkezésre áll.

A módszer célja éppen az, hogy a taxonómiát és a coverage-et később is javíthatóvá tegye.

Új:

- állami funkció;
- failure mode;
- területi vagy fizikai függőség;
- joghatósági kitettség;
- rendkívüli működési tapasztalat;
- élethelyzet- vagy szolgáltatási kapcsolat

indokolhatja a coverage-modell módosítását.

A completeness ezért nem egyszeri minősítés, hanem ismételhető audit.
