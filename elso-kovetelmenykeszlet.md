# Alapok — első kis tényleges követelménykészlet

Ez a dokumentum az `Alapok` első, kis méretű tényleges követelménykészlete.

Nem a megbízható digitális állam tíz „legfontosabb” követelményét próbálja kijelölni, és nem fagyaszt be teljes taxonómiát. A cél az, hogy különböző természetű követelményeken próbára tegyük a közös módszertant, és ezekkel visszateszteljük a Manifesztó állításait.

A jelenlegi készlet kétirányú visszateszt eredménye:

```text
Manifesztó
    ->
első tényleges követelmények
    ->
operacionalizálási problémák
    ->
Manifesztó pontosítása
    ->
követelmények újrapontosítása
```

A készlet szándékosan keresztmetszeti:

- alkotmányos kiindulópontból meghatározott társadalmi és állami funkció;
- bizonyíték és független ellenőrizhetőség;
- kritikus függőség;
- helyreállítás;
- degradált működés;
- közhatalmi folytonosság;
- élethelyzet / szolgáltatási nézőpont;
- támadói képességfeltételezések;
- szakmai kockázatjelzés és döntési felelősség;
- időbeli fenntarthatóság, migráció, kivezetés és archiválhatóság.

Az azonosítók stabil, jelentésszegény public ID-k:

```text
R-0001
R-0002
...
```

Az ID nem domain-sorszám és nem verziószám. Nem rögzíti a későbbi teljes követelményrendszer szerkezetét.

A rekordok a közös minimum sémát követik:

```text
ID
ÁLLÍTÁS
KÖVETELMÉNY
BIZONYÍTÉK
MÉRCE
TESZT
FAILURE CONDITION
FORRÁS
STATUS
```

A `FORRÁS` a követelmény szakmai eredetét vagy indokát jelzi. A `BIZONYÍTÉK` ezzel szemben azt mutatja meg, miből lehet egy konkrét rendszerben megállapítani, hogy a követelmény teljesül-e.

A forrás feltüntetése önmagában nem jelenti, hogy a forrás szerzője e követelmény szerzője, támogatója vagy jóváhagyója.

A nyilvános követelmény- és bizonyítékmódszertan nem jelenti azt, hogy a konkrét kitöltött audit-, teszt-, függőség-, recovery-, authority- vagy security-recordoknak nyilvánosnak kell lenniük. A konkrét bizonyítékok külön biztonsági és publikációs felülvizsgálat tárgyai. Titok, kulcs, sérülékenységi adat vagy más operatívan érzékeny információ nem kerül nyilvános repositoryba pusztán azért, mert valamely követelmény bizonyítékot kér.

---

# R-0001 — A kritikus funkció és kiesésének következménye legyen ismert

## ID

`R-0001`

## ÁLLÍTÁS

Nem az informatikai rendszer önmagában kritikus, hanem az a társadalmi vagy állami működés, amely rajta keresztül valósul meg vagy rá támaszkodik.

Az állami funkciókat nem pusztán a meglévő informatikai és intézményi felosztásból kell visszaolvasni. A vizsgálat tágabb alkotmányos kiindulópontja az állam működőképessége mellett az emberek, szervezetek és közöttük fennálló jogszerű kapcsolatok működőképességét is figyelembe veszi.

Egy rendszer kritikussága ezért csak a támogatott funkció, annak alkotmányos, jogi vagy közérdekű szerepe és kiesésének következménye felől értelmezhető.

## KÖVETELMÉNY

Minden, a vizsgált hatókörben kritikusnak minősített digitális rendszerhez vagy szolgáltatáshoz legyen dokumentáltan hozzárendelve:

1. az általa támogatott társadalmi vagy állami funkció;
2. a funkció alkotmányos, jogi vagy közérdekű indoka olyan részletességgel, amelyből látható, miért kell a funkciót fenn- vagy működésben tartani;
3. a funkció felelőse;
4. a funkció kiesésének vagy hibás működésének lényeges következményei;
5. a funkció minimálisan fenntartandó működési szintje, ahol ez értelmezhető;
6. a lényeges technikai, szervezeti, fizikai és külső függőségek;
7. a helyreállítási prioritás;
8. legalább a kritikusabb esetekben annak vizsgálata, hogy nemcsak egyedi komponenshiba, hanem rendszerinterakció, hiányzó visszajelzés vagy több hiba együttállása is vezethet-e súlyos veszteséghez.

A kritikusfunkció-jegyzék ne legyen pusztán a meglévő szervezeti vagy informatikai leltár átnevezése: legyen visszavezethető arra a tágabb működési célra, amelyet az intézmény vagy rendszer szolgál.

A követelmény nem ír elő konkrét kockázatelemzési vagy system-safety módszert.

## BIZONYÍTÉK

Releváns bizonyíték lehet például:

- jóváhagyott kritikusfunkció-jegyzék;
- alkotmányos, jogi vagy közérdekű cél–funkció megfeleltetés;
- rendszer–funkció megfeleltetés;
- következmény- vagy hatáselemzés;
- függőségi térkép;
- működési módokat és helyreállítási prioritást rögzítő dokumentum;
- gyakorlat vagy incidens során igazolt dependency;
- near miss vagy más rendszer-szintű failure evidence;
- megfelelő jogosultságú zárt audit eredménye.

## MÉRCE

A követelmény teljesül, ha a vizsgált hatókörben:

- minden kritikusnak minősített rendszer vagy szolgáltatás visszaköthető legalább egy konkrét társadalmi vagy állami funkcióhoz;
- a funkció indoka nem merül ki abban, hogy azt a jelenlegi intézményi struktúra vagy informatikai rendszer már tartalmazza;
- minden ilyen funkcióhoz meg van határozva legalább a felelős, a súlyos kiesési következmény és a fő függőségek;
- nincs olyan kritikus funkció, amelynek helyreállítási prioritása meghatározatlan;
- a magas következményű funkciók elemzése nem korlátozódik kizárólag egyedi komponenshibákra, ha ismert rendszerinterakciós vagy összetett hibakockázat áll fenn.

A konkrét kritikussági küszöböt az adott hatókörben külön kell meghatározni.

## TESZT

Válasszunk ki reprezentatív mintát a kritikus rendszerekből, és minden elemnél vezessük végig mindkét irányt:

```text
alkotmányos / jogi / közérdekű cél
    ->
társadalmi vagy állami funkció
    ->
felelős
    ->
rendszer / szolgáltatás
    ->
fő függőségek
```

és:

```text
rendszer / szolgáltatás
    ->
támogatott funkció
    ->
súlyos kiesési következmény
    ->
minimális működés
    ->
helyreállítási prioritás
```

Legalább egy magas következményű funkciónál külön vizsgáljuk meg egy összetett vagy interakciós failure scenario kezelését.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- kritikus rendszerhez nem rendelhető világosan társadalmi vagy állami funkció;
- a kritikusság indoka csak az, hogy „fontos IT-rendszer” vagy „ezt a jelenlegi szervezet így végzi”;
- a funkció mögötti alkotmányos, jogi vagy közérdekű cél nem rekonstruálható;
- nincs megnevezett felelős;
- a kiesés következménye nincs meghatározva;
- kritikus függőség érdemben ismeretlen;
- a helyreállítási prioritás nincs meghatározva;
- súlyos rendszerkockázatnál az elemzés bizonyíthatóan csak egyedi komponenshibákat vesz figyelembe.

## FORRÁS

- `00-modszertan/state-function-completeness.md`
- *A digitális bizalom 12 pontja* — a funkció elsődlegessége és a tágabb alkotmányos kiindulópont.
- Frész Ferenc: *A biztonságos magyar digitális állam manifestója* — a védendő tárgy az állami működés.
- Richard I. Cook: *How Complex Systems Fail* — interacting failures, latent degradation.
- Nancy G. Leveson: *Engineering a Safer World* — system-level loss/hazard and interaction perspective.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0002 — Kritikus működési állítást ne lehessen pusztán önigazolással bizonyítani

## ID

`R-0002`

## ÁLLÍTÁS

A megbízhatóság bizonyított képesség.

Egy kritikus rendszer vagy képesség nem tekinthető megfelelőnek pusztán azért, mert annak üzemeltetője, szállítója vagy felelőse ezt állítja.

Kritikus állításnál az ellenőrizhetőséghez érdemi független ellenőrzési út is tartozik. A függetlenség nem jelent szükségképpen nyilvánosságot vagy külső szervezetet, de az ellenőrzés eredménye nem függhet kizárólag ugyanannak az érdekelt szereplőnek az önállításától, amelynek megfelelését vizsgáljuk.

## KÖVETELMÉNY

Minden kritikus működési követelményhez legyen meghatározva:

1. milyen bizonyíték alkalmas a teljesülés vizsgálatára;
2. milyen mérce alapján értékeljük;
3. milyen teszt vagy ellenőrzési eljárás hozza létre vagy vizsgálja ezt a bizonyítékot;
4. ki vagy mi képes az eredményt ellenőrizni;
5. milyen érdemi független ellenőrzési út áll rendelkezésre.

Ha a bizonyítékot a megfelelésben közvetlenül érdekelt szereplő — például a szállító vagy üzemeltető — állítja elő, a független ellenőrzési útnak képesnek kell lennie legalább a releváns adat, teszt, számítás, konfiguráció, provenance vagy eredmény érdemi vizsgálatára.

A független ellenőrzés nem jelent szükségképpen nyilvánosságot, és nem követel minden esetben külső auditcéget. Jelentheti például szervezetileg elkülönült ellenőrzést, függetlenül újrafuttatható tesztet vagy más, az eredeti önállítástól érdemben különálló evidence-channelt.

## BIZONYÍTÉK

Releváns lehet például:

- reprodukálható teszt;
- gyakorlatjegyzőkönyv;
- mérési adat és annak provenance-e;
- konfigurációs vagy géppel olvasható állapot;
- audit trail;
- külső vagy szervezetileg független audit;
- függetlenül újrafuttatott teszt vagy számítás;
- több érdemben független evidence-channel;
- megfelelő jogosultsággal végzett zárt ellenőrzés;
- redaktált vagy aggregált public eredmény, ha a részletek nem publikálhatók.

## MÉRCE

A követelmény teljesül, ha minden vizsgált kritikus követelményhez:

- azonosítható bizonyíték;
- értékelési mérce;
- teszt vagy ellenőrzési eljárás;
- dokumentált ellenőrzési felelősség;
- és érdemi független ellenőrzési út

tartozik.

Kritikus működési állításnál az érdekelt szereplő puszta önnyilatkozata nem lehet az egyetlen bizonyíték.

Ha nincs érdemi független ellenőrzési út, a kritikus állítás e követelmény szerint nem tekinthető bizonyított képességnek.

## TESZT

Válasszunk ki több különböző típusú kritikus követelményt, és próbáljuk meg az eredeti megfelelésért közvetlenül felelős szereplőtől érdemben független nézőpontból rekonstruálni:

```text
mit állítunk?
    ->
milyen bizonyíték támasztja alá?
    ->
hogyan keletkezett?
    ->
mi a mérce?
    ->
mi volt a teszt?
    ->
ki ellenőrizte?
    ->
mi az a független út, amelyen az eredmény érdemben ellenőrizhető?
```

A teszt akkor erős, ha az ellenőrző fél nem kénytelen a megfelelésért közvetlenül felelős szereplő puszta állítását elfogadni.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- nincs meghatározva releváns bizonyíték;
- nincs mérce vagy teszt;
- a bizonyíték eredete nem rekonstruálható;
- kritikus állítás kizárólag szállítói vagy üzemeltetői önnyilatkozáson alapul;
- a teszteredmény érdemben nem reprodukálható vagy ellenőrizhető;
- a titkosságra hivatkozás miatt ténylegesen nincs semmilyen független ellenőrzési út;
- az „független ellenőrzés nem lehetséges” állítás önmagában felmentésként szolgál a kritikus állítás bizonyítása alól.

## FORRÁS

- `00-modszertan/kovetelmeny-bizonyitek-teszt.md`
- `bizonyitekok/README.md`
- *A digitális bizalom 12 pontja* — a megbízhatóság mint bizonyított képesség és az önigazolás korlátja.
- Frész Ferenc: compliance és tényleges biztonság megkülönböztetése; valós mérés és gyakorlat.
- A projekt módszertani alapelve: `self-assertion != independent verification`.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0003 — Kritikus függőség esetén legyen kilépési vagy túlélési út

## ID

`R-0003`

## ÁLLÍTÁS

Egy kritikus állami funkció működőképessége nem függhet észrevétlenül olyan külső szereplőtől, technológiától vagy tudástól, amelynek kiesésekor nincs működőképes válasz.

A szuverenitás itt nem autarkiát, hanem ismert és kezelhető függőséget jelent. Szövetségi vagy európai interoperabilitás és külső együttműködés összeegyeztethető ezzel; a követelmény azt zárja ki, hogy egyetlen külső szereplő rendelkezésre állása vagy döntése szükségképpen megszüntesse a kritikus funkció minimális működését.

## KÖVETELMÉNY

Minden azonosított kritikus függőséghez legyen dokumentálva:

1. a függőség tárgya és felelőse;
2. a technikai, szerződéses, joghatósági, tudás- vagy más releváns kitettség;
3. mi történik a függőség részleges vagy teljes kiesésekor;
4. milyen ideig és milyen szinten tartható fenn az érintett funkció;
5. létezik-e helyettesítés, migráció, saját továbbműködtetés vagy más legitim exit;
6. ha a teljes exit nem reális, milyen kipróbált túlélési mód tartja fenn legalább a jóváhagyott minimális kritikus funkciót;
7. milyen maradványkockázat marad a választott exit vagy túlélési út mellett, és ki jogosult azt elfogadni;
8. hogyan bizonyítható, hogy az exit vagy túlélési út nem csak papíron létezik.

A maradványkockázat elfogadása nem helyettesíti a minimális kritikus funkcióhoz szükséges túlélési út meglétét.

A követelmény nem írja elő, hogy a függőség hazai vagy külföldi legyen, és nem követel minden esetben saját fejlesztést.

## BIZONYÍTÉK

Releváns lehet például:

- dependency inventory;
- szerződéses kilépési feltételek;
- adat- és konfigurációexport eredménye;
- migration runbook;
- alternatív szállító vagy implementáció alkalmassági vizsgálata;
- reprodukálható build vagy runtime artifact;
- átadott működtetési dokumentáció;
- kritikus szakértelem nyilvántartása;
- exit- vagy service-denial gyakorlat eredménye;
- zárt joghatósági vagy supply-chain review.

## MÉRCE

A követelmény teljesül, ha minden vizsgált kritikus függőséghez:

- ismert owner;
- dokumentált failure consequence;
- és legalább egy tesztelhető exit, replacement vagy survivable-failure út

tartozik.

Ha a teljes kiváltás ésszerűen nem lehetséges, a túlélési útnak a kritikus funkció előre jóváhagyott minimális működését fenn kell tartania a meghatározott időtartamban.

Egyetlen külső szereplő kiesése vagy döntése nem teheti a minimális kritikus funkció megszűnését strukturálisan szükségszerűvé.

## TESZT

Legalább egy reprezentatív kritikus függőségnél hajtsunk végre technikai vagy asztali gyakorlatot, amelyben a függőség megszűnik, nem elérhető, vagy a külső szereplő olyan döntést hoz, amely a normál együttműködést megszakítja.

Vizsgáljuk:

- a szolgáltatás vagy termék elérhetetlenségét;
- adat és konfiguráció kinyerhetőségét;
- licenc- vagy kulcsfüggőséget;
- szükséges szakértelmet;
- migrációs vagy helyettesítési időt;
- a minimális állami funkció fenntarthatóságát;
- a normál együttműködés helyreállításának vagy más megoldásra átvitelének útját.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- kritikus függőség nincs azonosítva vagy nincs felelőse;
- a szolgáltató vagy termék megszűnése kontrollálatlanul megszünteti a minimálisan fenntartandó kritikus funkciót;
- a releváns adat, schema, konfiguráció vagy működtetési tudás nem vihető tovább;
- az exit kizárólag szerződéses állítás, gyakorlati bizonyíték nélkül;
- a funkció egyetlen külső szereplő kiesése vagy döntése miatt szükségképpen működésképtelenné válik;
- a teljes kiesés kockázatának puszta elfogadása helyettesíti az exit vagy survivable-failure képességet.

## FORRÁS

- `00-modszertan/state-function-completeness.md`
- *A digitális bizalom 12 pontja* — kritikus függőség, interoperabilitás és tényleges kilépési/túlélési út.
- Frész Ferenc: supplier independence / exit.
- Nagymajtényi Gábor: data/process/infrastructure sovereignty; partner nélküli működtethetőség.
- A projekt controlling distinctionje: `interoperability != dependency`.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0004 — A helyreállíthatóságot gyakorlatban kell bizonyítani

## ID

`R-0004`

## ÁLLÍTÁS

Helyreállítási terv még nem helyreállítási képesség.

Kritikus funkciónál a recovery akkor tekinthető valós képességnek, ha a szükséges állapot, adat, környezet, jogosultság és függőség ténylegesen helyreállítható, és ezt megfelelő próbával igazoltuk.

A válság túlélése önmagában nem elég: a rendkívüli vagy degradált működésből a normál, jogszerű állapotba való rendezett visszatérés is a helyreállítás része.

## KÖVETELMÉNY

Minden kijelölt kritikus funkcióhoz legyen:

1. meghatározott helyreállítási cél és prioritás;
2. azonosított recovery object — szükség szerint adat, metadata, schema, semantics, szoftver, konfiguráció, runtime, kulcs, trust material, authority record és fizikai dependency;
3. dokumentált helyreállítási eljárás;
4. megfelelő időközönként és lényeges változás után ténylegesen végrehajtott helyreállítási teszt;
5. olyan ellenőrzés, amely a helyreállított állapot integritását és használhatóságát is vizsgálja;
6. ahol fallback vagy párhuzamos működés keletkezhet, rendezett reconciliation eljárás;
7. ahol a rendkívüli működés eltérő jogosultsági, közhatalmi vagy működési szabályokat aktivál, explicit visszatérési feltétel és út a normál, jogszerű állapothoz;
8. magas következményű funkciónál szükség szerint összetett vagy több függőséget érintő recovery scenario.

## BIZONYÍTÉK

Releváns lehet például:

- restore/DR gyakorlatjegyzőkönyv;
- tényleges helyreállítási idő;
- visszaállított rendszer vagy környezet;
- integrity check;
- authoritative-record ellenőrzés;
- kulcs- és trust-chain visszaállítás;
- reconciliation eredmény;
- rendkívüli jogosultságok megszüntetésének vagy visszavonásának recordja;
- post-exercise gap list;
- ismételt teszt javítás után;
- zárt gyakorlat független összefoglalója.

## MÉRCE

A követelmény teljesül, ha:

- az elfogadott recovery célokhoz tényleges teszteredmény tartozik;
- a tesztelt helyreállítás a kijelölt funkció szempontjából használható állapotot eredményez;
- az eredmény megfelel az adott funkcióhoz jóváhagyott idő-, adatvesztési és integritási követelményeknek;
- a fallback, párhuzamos vagy rendkívüli működés után a normál, jogszerű állapotba való visszatérés rendezett és ellenőrizhető;
- a teszt óta nem történt olyan lényeges változás, amely a bizonyítékot érdemben érvényteleníti, vagy ha történt, újratesztelés történt.

A konkrét RTO/RPO vagy más küszöb nem univerzális: azt a funkció következményei alapján kell meghatározni.

## TESZT

Válasszunk ki egy reprezentatív kritikus funkciót, és hajtsunk végre end-to-end recovery gyakorlatot olyan környezetben, amely a valós függőségeket érdemben reprezentálja.

A teszt ne érjen véget a technikai „service started” állapotnál. Ellenőrizze:

```text
adat
+
jelentés
+
jogosultság
+
függőségek
+
hivatalos működőképesség
+
szükség esetén reconciliation
+
visszatérés a normál, jogszerű állapotba
```

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- csak dokumentált recovery terv létezik tényleges gyakorlat nélkül;
- a teszt nem állítja helyre a funkció számára szükséges teljes állapotot;
- a helyreállítás a jóváhagyott küszöbön kívül marad;
- a helyreállított adat vagy jogosultsági állapot integritása nem igazolható;
- a recovery olyan külső függőségre támaszkodik, amely a vizsgált failure scenarióban maga sem elérhető;
- a fallbackből vagy rendkívüli működésből a normál, jogszerű működésbe való visszatérés nem rendezhető;
- a rendkívüli jogosultság vagy működési mód a kiváltó helyzet megszűnése után kontroll nélkül aktív maradhat.

## FORRÁS

- `00-modszertan/kovetelmeny-bizonyitek-teszt.md`
- `00-modszertan/state-function-completeness.md`
- *A digitális bizalom 12 pontja* — válság előtti gyakorlat és visszatérés a normál, jogszerű állapotba.
- Frész Ferenc: recoveryt incidens előtt gyakorolni kell.
- Nagymajtényi korábbi szuverenitási/reconstructability vonala.
- Richard I. Cook: recovery és adaptáció a valós komplex rendszer működésében.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0005 — Kritikus funkció részleges kiesésben is ellenőrzötten működjön

## ID

`R-0005`

## ÁLLÍTÁS

A reziliencia nem azonos a normál üzem elérhetőségével.

Kritikus funkciónál előre tudnunk kell, milyen minimális működés marad fenn részleges kiesés, kapcsolatvesztés vagy külső szolgáltatás elvesztése esetén, és azt is észlelnünk kell, ha a rendszer már degradált állapotban működik.

## KÖVETELMÉNY

Ahol a kritikus funkció következményei és függőségei ezt indokolják, legyen meghatározva:

1. a minimálisan fenntartandó szolgáltatási vagy állami funkció;
2. a degradált állapot felismerésének módja;
3. a degradált működésben engedélyezett és tiltott műveletek;
4. a felelősségi és szükség szerint közhatalmi korlátok;
5. a szükséges helyi, offline, manuális vagy alternatív működési mód — ha ilyenre szükség van;
6. az adat- és állapotkezelés szabálya;
7. a normál működésbe való visszatérés és reconciliation módja;
8. a minimális működés gyakorlati tesztje.

A követelmény nem ír elő `local-first`, decentralizált vagy bármely más konkrét architektúrát.

[OPCIONÁLIS — ha a Manifesztó tartós fenyegetettségre vonatkozó tétele megmarad:]

Ha a degradált vagy rendkívüli működés jogi vagy közhatalmi eltéréssel jár, legyen meghatározva annak aktiválási feltétele, jogalapja, szükségességi indoka, felülvizsgálati rendje és megszüntetési feltétele. A tartós fenyegetettség önmagában nem helyettesíti a rendkívüli működés fennmaradásának konkrét igazolását.

## BIZONYÍTÉK

Releváns lehet például:

- degraded-mode leírás;
- minimum-service definition;
- trigger és monitoring konfiguráció;
- offline vagy helyi működés gyakorlatának eredménye;
- external-service-loss teszt;
- manuális fallback record;
- authority/delegation szabály;
- reconnect/reconciliation log;
- near miss vagy incidens, amely latent degradationt tárt fel;
- az opcionális ág esetén rendkívüli működés szükségességi, jogalapi és felülvizsgálati recordja.

## MÉRCE

A követelmény teljesül, ha a releváns kritikus funkciónál:

- a minimális működés explicit;
- a degradált állapot észlelhető;
- a működés nem lépi túl a jóváhagyott jogosultsági vagy működési határt;
- a kijelölt minimális funkció a meghatározott tesztidőszakban fenntartható;
- a normál állapothoz való visszatérés rendezett és ellenőrizhető.

Az opcionális ág akkor teljesül, ha a rendkívüli jogi vagy közhatalmi működés fennmaradása nem automatikus, hanem dokumentált szükségességhez, jogalaphoz és felülvizsgálathoz kötött.

## TESZT

Hozzunk létre olyan gyakorlatot, amelyben egy releváns központi vagy külső függőség nem érhető el.

Például:

```text
network partition
external service denial
central platform unavailable
identity/trust service degraded
regional infrastructure loss
```

A teszt során mérjük:

- mikor észleli a rendszer a degradációt;
- mi marad működőképes;
- milyen manuális vagy alternatív lépések szükségesek;
- megmarad-e a jogszerű döntési határ;
- hogyan történik a visszakapcsolás és reconciliation.

Az opcionális ág tesztjeként, ha rendkívüli jogi vagy közhatalmi mód aktiválódott, vizsgáljuk meg azt is, milyen feltétellel, ki és milyen bizonyíték alapján tartja fenn vagy szünteti meg.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- releváns kritikus funkció egyetlen kieső dependency miatt minden kontrollált fallback nélkül megszűnik;
- a rendszer nem tudja megbízhatóan felismerni saját degradált állapotát;
- degradált módban nem világos, milyen művelet engedélyezett;
- a fallback csak papíron létezik;
- a lokálisan vagy manuálisan keletkezett állapot később nem egyeztethető össze;
- a degraded mode-ban végzett hivatalos aktusok hatásköre vagy érvényessége nem rekonstruálható.

Az opcionális ág nem teljesül, ha a rendkívüli működési mód pusztán a fenyegetettség általános fennmaradására hivatkozva, külön szükségességi és jogalapi felülvizsgálat nélkül állandósulhat.

## FORRÁS

- `00-modszertan/state-function-completeness.md`
- *A digitális bizalom 12 pontja* — degradált működés, visszatérés és az opcionális tartós fenyegetettség / tartós rendkívüli működés elválasztása.
- Richard I. Cook: complex systems operate with latent degradation; human adaptation and graceful cutback.
- Nancy G. Leveson: system-level control/feedback perspective.
- Nagymajtényi Gábor: local/offline survivability mint implementation input; ebből a követelmény csak a bounded independent / degraded operation képességet emeli át.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0006 — Digitális kiesésben is rekonstruálható maradjon a jogszerű közhatalom

## ID

`R-0006`

## ÁLLÍTÁS

Azonosítás, hitelesítés és technikai jogosultság nem azonos a közhatalmi felhatalmazással.

Digitális hiba, támadás vagy helyettesítő működés esetén is rekonstruálható maradjon, ki, milyen hivatalban, milyen jogalappal és milyen korlátok között járhatott el.

Az intelligencia önmagában nem keletkeztet hatáskört. Automatizált vagy mesterségesintelligencia-rendszer döntést előkészíthet és jogszerűen meghatározott műveletet végrehajthat, de a közhatalmi működés mögött végső soron rekonstruálható, jogszerűen meghatározott emberi felhatalmazási és felelősségi láncnak kell állnia.

## KÖVETELMÉNY

Minden olyan kritikus digitális folyamatnál, amely hivatalos döntést, közhatalmi aktust vagy joghatást kiváltó közlést hoz létre, legyen rekonstruálható:

1. az eljáró személy, hivatal és — ahol releváns — technikai rendszer azonosítása;
2. az érintett hivatal vagy szerep;
3. a hatáskör és illetékesség;
4. a delegáció vagy helyettesítés jogalapja;
5. annak időbeli és tárgyi határa;
6. a kibocsátott aktus tartalma és verziója;
7. az aktus időpontja;
8. az authority chain helyreállítása és ellenőrizhetősége;
9. automatizált vagy AI-közreműködés esetén a rendszer pontos szerepe: előkészítés, javaslat, végrehajtás vagy más jogszerűen meghatározott művelet;
10. automatizált vagy AI-közreműködés esetén az a jogszerűen meghatározott emberi felhatalmazási és felelősségi lánc, amelyhez a közhatalmi működés végső soron visszaköthető.

Rendkívüli helyettesítéshez legyen explicit:

- jogalap;
- kezdőfeltétel;
- scope;
- lejárat vagy megszüntetési feltétel;
- audit trail;
- visszatérési út a normál authority chainhez.

## BIZONYÍTÉK

Releváns lehet például:

- office/role registry;
- delegation record;
- jogosultsági és authority mapping;
- official-act audit trail;
- hiteles időbélyeg vagy más megbízható időadat;
- dokumentált emergency substitution;
- expiry/revocation record;
- automatizált vagy AI-rendszer szerepét, verzióját és felhatalmazását rögzítő record;
- modell- vagy rendszeroutput és az azt követő hivatalos aktus provenance-e;
- digitális aláírás vagy más provenance-mechanizmus;
- megfelelő jogosultsággal végzett zárt jogi/technikai audit.

## MÉRCE

A követelmény teljesül, ha reprezentatív hivatalos aktusok esetén utólag egyértelműen rekonstruálható:

```text
ki / mi
+
milyen hivatalban
+
milyen hatáskörrel
+
milyen jogalapon
+
mikor
+
milyen aktust
+
automatizálás / AI esetén milyen szerepben
+
mely emberi felhatalmazási és felelősségi lánc alapján
```

bocsátott ki vagy hozott létre.

Lejárt, visszavont vagy scope-on kívüli delegáció nem eredményezhet érvényes közhatalmi felhatalmazást.

A rendkívüli helyettesítés nem maradhat korlátlanul aktív a kiváltó helyzet megszűnése után.

Automatizált vagy AI-rendszer nem válhat a közhatalmi hatáskör végső, önmagában álló címzettjévé.

## TESZT

1. Válasszunk ki több hivatalos aktust, és rekonstruáljuk teljes authority/provenance láncukat.
2. Szimuláljunk egy kulcsszereplő vagy digitális authority-service kiesését.
3. Aktiváljuk a jogszerű helyettesítési utat.
4. Legalább egy automatizált vagy AI-közreműködésű folyamatnál rekonstruáljuk külön:
   - mit végzett a rendszer;
   - milyen jogszerűen meghatározott szabály vagy felhatalmazás alapján;
   - hol kapcsolódik hozzá emberi döntés, felhatalmazás és felelősség.
5. Ellenőrizzük:
   - ki léphet a kieső szereplő helyére;
   - milyen scope-ban;
   - milyen aktust bocsáthat ki;
   - hogyan kerül ez naplózásra;
   - hogyan szűnik meg a helyettesítés;
   - hogyan áll vissza a normál authority chain.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- technikai belépési jogosultság önmagában közhatalmi felhatalmazást eredményez;
- nem állapítható meg, ki vagy mely hivatal járt el;
- a delegáció jogalapja vagy scope-ja nem rekonstruálható;
- lejárt vagy visszavont authority tovább használható;
- emergency substitution korlátlanul fennmaradhat;
- hivatalos aktus eredete, ideje vagy verziója nem bizonyítható;
- automatizált vagy AI-rendszer szerepe nem rekonstruálható;
- a közhatalmi aktus egy AI- vagy más technikai rendszerhez úgy ér véget, hogy mögötte nincs rekonstruálható, jogszerűen meghatározott emberi felhatalmazási és felelősségi lánc.

## FORRÁS

- `00-modszertan/state-function-completeness.md`
- A projekt controlling distinctionje:
  `identity != authentication != authorization != public office != lawful public authority != valid official act`.
- *A digitális bizalom 12 pontja* — közhatalmi folytonosság és az intelligencia / hatáskör elválasztása.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0007 — Az állammal kapcsolatba kerülő embernek vagy szervezetnek ne az állam szervezeti térképét kelljen ismernie

## ID

`R-0007`

## ÁLLÍTÁS

A szolgáltatási út az állammal kapcsolatba kerülő ember vagy szervezet legitim céljából, joggyakorlásából vagy kötelezettségteljesítéséből induljon ki, ne abból a feltételezésből, hogy ismeri az állam belső szervezeti és hatásköri felosztását.

A user-facing egyszerűség azonban nem moshatja össze a háttérben működő jogszerű hatásköröket.

Ez a követelmény a Manifesztó élethelyzet / szolgáltatási nézőpontjának operacionalizálása. A Manifesztóban ez a nézőpont jelenleg opcionális tétel; ezért ez a rekord egyúttal azt is teszteli, hogy az elv önálló `Alapok`-követelményként indokolható-e akkor is, ha a Manifesztóban nem válik kötelező főszöveggé.

## KÖVETELMÉNY

Egy kijelölt, több állami szereplőt vagy ügyet érintő élethelyzetnél legyen lehetséges:

1. az érintett ember vagy szervezet céljából, joggyakorlásából vagy kötelezettségteljesítéséből kiindulva azonosítani a releváns szolgáltatási utat;
2. a szükséges ügyeket és lépéseket elérni anélkül, hogy előzetesen ismerni kellene a részt vevő szervezetek belső felépítését;
3. a folyamatban egyértelmű státuszt és következő lépést kapni;
4. a háttérben minden hivatalos döntést visszakötni az arra jogosult szervhez, hatáskörhöz és jogalaphoz;
5. csak az adott szolgáltatáshoz vagy szabály alkalmazásához szükséges személyes adatot kérni vagy felhasználni;
6. az intézményi határok közötti átadást úgy kezelni, hogy az ne hozzon létre se jogi bizonytalanságot, se indokolatlan adatösszekapcsolást.

A követelmény nem ír elő központi személyprofilt, egyetlen portált vagy egyetlen technológiai megoldást.

## BIZONYÍTÉK

Releváns lehet például:

- life-situation/service map;
- service–case–task mapping;
- user journey;
- kontrollált felhasználói teszt;
- ügyféloldali keresési és navigációs eredmény;
- process handoff log;
- status/next-step evidence;
- authority és official-act mapping;
- adatmező–cél–jogalap megfeleltetés;
- accessibility/usability vizsgálat.

## MÉRCE

A követelmény teljesül, ha a kijelölt élethelyzet reprezentatív tesztjében:

- az érintett ember vagy szervezet a saját célját, joggyakorlását, kötelezettségét vagy élethelyzetét megfogalmazva megtalálja az indulási pontot;
- a szükséges lépések végigjárhatók úgy, hogy szervezeti ismeret csak ott szükséges, ahol ennek jogi vagy működési oka van;
- a folyamat státusza és következő lépése érthető;
- a háttérben a hatáskör és official-act provenance végig rekonstruálható;
- a személyesadat-használat szükségessége és célja dokumentálható.

A konkrét usability küszöböket az adott szolgáltatási környezetben külön kell rögzíteni.

## TESZT

Válasszunk ki egy valós, több ügyet vagy szervezetet érintő élethelyzetet.

A tesztalanynak csak a saját célját, joggyakorlását vagy kötelezettségét adjuk meg, nem a részt vevő hatóságok listáját.

Vizsgáljuk:

1. megtalálja-e az indulási pontot;
2. felismeri-e, mi a következő lépés;
3. kell-e szervezeti struktúrát előzetesen ismernie;
4. hol szakad meg vagy válik bizonytalanná a folyamat;
5. mely adatokat kérik tőle és miért;
6. a háttérben minden döntéshez rekonstruálható-e a jogszerű authority.

A tesztet lehetőség szerint eltérő hozzáférési és digitális készségű felhasználókkal is ismételjük.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- legitim szolgáltatási út csak a szervezeti felépítés ismeretében található meg;
- intézményi határnál a folyamat az érintett számára indokolatlanul megszakad vagy újrakezdődik;
- nem világos a státusz vagy a következő lépés;
- a user-facing integráció miatt nem rekonstruálható, mely szerv milyen jogalapon járt el;
- a szolgáltatás teljesítéséhez nem szükséges személyes adat megadása válik kötelezővé;
- az integráció indokolatlan, korlátlan profil- vagy adatösszekapcsolást követel.

## FORRÁS

- Nagymajtényi Gábor – Varga Péter: *Élethelyzet tudásbázis kialakítása — „Közigazgatási útvonaltervező”* (2016).
- *Élethelyzet tudásbázis kialakításának módszertana*.
- `00-modszertan/state-function-completeness.md` — lawful authority és life-situation/service nézet elválasztása.
- *A digitális bizalom 12 pontja* — tágabb alkotmányos kiindulópont és opcionális élethelyzet / szolgáltatási nézőpont.
- A projekt controlling distinctionje:
  `life situation != service != case != task`.

## STATUS

`DRAFT — OPTIONAL MANIFESTO BRANCH TEST`

---

# R-0008 — Kritikus biztonsági állítás ne függjön alá nem támasztott támadói képességkorláttól

## ID

`R-0008`

## ÁLLÍTÁS

Egy biztonsági tulajdonság értékelése támaszkodhat explicit threat modelre és támadói feltételezésekre.

Ha azonban egy kritikus biztonsági tulajdonság fennállása attól függ, hogy a támadó valamire nem képes, nem elég ezt hallgatólagosan feltételezni. A releváns képességkorlát maga is a biztonsági állítás egyik előfeltétele, ezért külön alátámasztást igényel.

Ha a szükséges képességkorlát nincs kellően alátámasztva, nem az következik, hogy „nincs biztonsági tulajdonság”, hanem az, hogy az adott tulajdonság fennállása e feltételezés mellett nem tekinthető kellően igazoltnak.

Ez a rekord a Manifesztó jelenleg `[ELDÖNTENDŐ — támadói képességkorlát]` jelöléssel szereplő tételének operacionalizálhatóságát teszteli; önmagában nem dönti el, hogy a tétel a végleges Manifesztó része lesz-e.

## KÖVETELMÉNY

Minden olyan kritikus biztonsági állításnál, amely támadói képességkorlátra támaszkodik, legyen dokumentálva:

1. maga a biztonsági tulajdonság vagy állítás;
2. a releváns threat model;
3. mely támadói képességet, erőforrást, hozzáférést, sebességet, tudást vagy más korlátot feltételezünk;
4. miért szükséges ez a korlát az állítás fennállásához;
5. milyen bizonyíték támasztja alá a korlátot;
6. mi történik, ha a feltételezett korlát nem áll fenn vagy idővel megszűnik;
7. milyen státuszt kap a biztonsági állítás, ha a korlát alátámasztása elégtelen.

A követelmény nem tilt minden támadói modellt és nem követel korlátlan ellenféllel szembeni abszolút biztonságot.

A támadói képességkorlát alátámasztása maga is kritikus állítás. Ezért az alátámasztására szolgáló bizonyíték és ellenőrzési út az `R-0002` független ellenőrzési követelménye alá esik.

## BIZONYÍTÉK

Releváns lehet például:

- explicit threat model;
- támadói feltételezésjegyzék;
- mért vagy ellenőrzött rate/resource bound;
- hozzáférési vagy fizikai korlát bizonyítéka;
- protokoll- vagy rendszeranalízis;
- red-team vagy adversarial test eredménye;
- érzékenységi vizsgálat;
- a feltételezett támadói képesség változását követő felülvizsgálat;
- független security review.

## MÉRCE

A követelmény teljesül, ha minden vizsgált kritikus biztonsági állításnál:

- explicit, hogy támaszkodik-e támadói képességkorlátra;
- ha igen, a korlát azonosítható és érdemben alátámasztott;
- dokumentált, mi történik a korlát túllépésekor;
- a biztonsági állítást nem kezelik bizonyítottként olyan feltételezés mellett, amelynek szükséges korlátja nincs kellően alátámasztva.

## TESZT

Válasszunk ki egy kritikus biztonsági állítást, és végezzünk assumption auditot:

```text
mit állítunk biztonságosnak?
    ->
milyen támadói modell mellett?
    ->
mely képességkorlát szükséges hozzá?
    ->
mi támasztja alá ezt a korlátot?
    ->
mi történik, ha a korlátot növeljük vagy eltávolítjuk?
```

Ahol technikailag és jogszerűen lehetséges, a teszt legalább egy releváns képességkorlátot stresszeljen vagy lépjen túl, és vizsgálja meg, hogyan változik a biztonsági állítás státusza.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- kritikus biztonsági állítás lényeges támadói feltételezése implicit marad;
- a tulajdonság csak azért „biztonságos”, mert a támadót lassabbnak, kevésbé hozzáértőnek vagy kisebb erőforrásúnak feltételezzük, de ennek nincs kellő alátámasztása;
- a szükséges képességkorlát bizonyítéka elavult vagy nem releváns;
- a képességkorlát megszűnése után a biztonsági állítás változatlanul bizonyítottként szerepel;
- nincs vizsgálva, milyen következménye van a feltételezett korlát túllépésének;
- a támadói képességkorlát alátámasztása kizárólag annak a szereplőnek az önállításán alapul, aki a rá épülő kritikus biztonsági állítást teszi.

## FORRÁS

- *A digitális bizalom 12 pontja* — a támadói képességkorlátokra épülő biztonsági állítás döntési pontja.
- A projekt controlling distinctionje:
  `assumed attacker limitation != established security property`.

## STATUS

`DRAFT — DECISION-BRANCH TEST`

---

# R-0009 — Kritikus szakmai kockázatjelzés jusson el a döntés szintjéig

## ID

`R-0009`

## ÁLLÍTÁS

A felelősség nem merül ki abban, hogy incidens után megnevezhető legyen valaki.

Kritikus döntés előtt a releváns szakmai kockázatjelzésnek el kell jutnia arra a döntési szintre, ahol a kockázat vállalásáról, csökkentéséről vagy a működés megváltoztatásáról ténylegesen dönteni lehet.

A döntéshozó eltérhet a szakmai javaslattól, de az eltérés lényegi indoka, a döntés felelőse és a rendelkezésre álló kockázati információ utólag rekonstruálható maradjon.

## KÖVETELMÉNY

Kritikus funkciót érintő jelentős kockázatjelzéshez legyen meghatározva:

1. ki fogadhatja és értékelheti a jelzést;
2. milyen súlyosság vagy bizonytalanság esetén milyen eszkalációs út aktiválódik;
3. mely döntési szintig kell a jelzés lényegi tartalmának eljutnia;
4. hogyan rögzítjük a jelzés technikai vagy szakmai alapját és bizonytalanságát;
5. ki jogosult a kockázatot elfogadni, csökkenteni vagy a javaslattól eltérni;
6. eltérés esetén hogyan marad rekonstruálható a döntés indoka és felelőse;
7. hogyan kerülnek be az ismétlődő near miss-ek, workaroundok, kézi kompenzációk és más gyenge jelzések a kockázati eszkalációba;
8. hogyan ellenőrizzük, hogy idő-, költség-, teljesítmény- vagy szervezeti nyomás ne tudja észrevétlenül megszakítani a releváns kockázati információ útját.

A követelmény nem írja elő, hogy a döntéshozónak minden esetben a szakmai javaslatot kell követnie. Azt írja elő, hogy kritikus eltérés ne legyen információhiányos, láthatatlan vagy felelősség nélküli.

## BIZONYÍTÉK

Releváns lehet például:

- hazard/risk register;
- engineering vagy szakmai dissent record;
- issue/escalation log;
- döntési jegyzőkönyv;
- change-approval record;
- risk acceptance record;
- meeting record vagy döntési memo;
- near-miss és workaround trend;
- az eredeti szakmai jelzés és a vezetői döntés közötti provenance;
- anonim vagy védett jelzési csatorna eredménye, ha ilyen létezik.

## MÉRCE

A követelmény teljesül, ha reprezentatív kritikus kockázatjelzéseknél rekonstruálható:

```text
mi volt a szakmai jelzés?
    ->
milyen bizonyíték / bizonytalanság tartozott hozzá?
    ->
ki kapta meg?
    ->
milyen döntési szintre jutott?
    ->
mi lett a döntés?
    ->
ha eltért a javaslattól, miért?
    ->
ki vállalta a döntést?
```

Súlyos vagy ismétlődő kockázatjelzés nem tűnhet el pusztán azért, mert szervezetileg kényelmetlen, határidőt veszélyeztet vagy ellentmond a korábbi vezetői álláspontnak.

## TESZT

1. Válasszunk ki több múltbeli vagy szimulált kritikus kockázatjelzést.
2. Rekonstruáljuk a jelzés útját a keletkezéstől a döntésig.
3. Egy tabletop gyakorlatban juttassunk be olyan szakmai jelzést, amely költség-, idő- vagy teljesítménycéllal konfliktusba kerül.
4. Ellenőrizzük:
   - eljut-e a megfelelő döntési szintig;
   - megmarad-e a jelzés lényegi tartalma;
   - rögzül-e a bizonytalanság;
   - dokumentált-e a döntés;
   - eltérés esetén megmarad-e az indok és a felelősség.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- jelentős szakmai kockázatjelzésnek nincs meghatározott eszkalációs útja;
- a jelzés a döntési szint előtt szervezeti szűrésben eltűnik vagy lényegileg torzul;
- a döntéshozó nem kapja meg a releváns kockázati információt;
- a szakmai javaslattól való eltérésnek nincs rekonstruálható indoka vagy felelőse;
- ismétlődő near miss, workaround vagy kézi kompenzáció tartósan jelzés nélkül marad;
- korábbi sikeres működés önmagában igazolja egy ismert kockázat további elfogadását.

## FORRÁS

- *A digitális bizalom 12 pontja* — a felelősség legyen valódi, ne csak utólagos.
- Presidential Commission on the Space Shuttle Challenger Accident: *Report to the President*; Richard P. Feynman, Appendix F — *Personal Observations on the Reliability of the Shuttle*.
- U.S. House Committee on Transportation and Infrastructure: *The Design, Development & Certification of the Boeing 737 MAX*.
- A projekt controlling distinctionje:
  `named responsibility != effective risk-information path`.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# R-0010 — Kritikus rendszer az időben is maradjon értelmezhető, migrálható, kivezethető és archiválható

## ID

`R-0010`

## ÁLLÍTÁS

Kritikus adatot nem elég elmenteni, és kritikus rendszert nem elég addig működtetni, amíg a jelenlegi technológia rendelkezésre áll.

Évek vagy évtizedek múlva is értelmezhetőnek kell maradnia, mit jelentett a releváns adat vagy hivatalos record, honnan származott, milyen szabály és környezet mellett jött létre, és milyen döntéshez kapcsolódott.

A technológiai változás miatt a kritikus működés lifecycle-képességéhez a fenntarthatóság mellett a migrálhatóság, szükség esetén a kivezethetőség és az archiválhatóság is hozzátartozik.

## KÖVETELMÉNY

Minden olyan kritikus rendszerhez, amely hosszú távú állami vagy társadalmi funkciót, hivatalos recordot vagy tartós joghatást hordoz, legyen meghatározva:

1. mely adatok, metadata, schema és semantics szükségesek a későbbi értelmezéshez;
2. milyen provenance és időbeli kontextus szükséges annak megállapításához, hogyan és milyen szabály szerint jött létre a record;
3. milyen szoftver-, konfiguráció-, runtime-, kulcs-, trust-material- vagy jogosultsági információ szükséges a későbbi értelmezéshez vagy igazoláshoz;
4. milyen hivatalos döntéshez, hatáskörhöz vagy authority chainhez kell a recordot vissza tudni kötni;
5. hogyan vihető át a kritikus működés vagy record új technológiai környezetbe;
6. hogyan vezethető ki a rendszer anélkül, hogy a szükséges bizonyíthatóság vagy működési folytonosság elveszne;
7. milyen archiválási csomag vagy eljárás őrzi meg a későbbi olvashatósághoz, értelmezéshez és ellenőrzéshez szükséges összefüggéseket;
8. milyen időközönként vagy milyen változás után kell az értelmezhetőséget, migrációt vagy archív visszaállítást ténylegesen kipróbálni.

A követelmény nem ír elő egyetlen fájlformátumot, archiváló technológiát vagy preservation frameworköt.

## BIZONYÍTÉK

Releváns lehet például:

- data dictionary és schema history;
- metadata/provenance record;
- dokumentált semantics;
- konfiguráció- és verziótörténet;
- szoftver- vagy runtime-artifact;
- kulcs- és trust-material preservation eljárás;
- migration plan és végrehajtott migration test;
- decommission plan;
- archive package inventory;
- cold restore / readback teszt;
- régi hivatalos record új környezetben végzett értelmezési és provenance-tesztje.

## MÉRCE

A követelmény teljesül, ha reprezentatív kritikus record vagy rendszer esetén:

- a record jelentése és eredete a meghatározott megőrzési időn belül rekonstruálható;
- a szükséges authority/provenance kapcsolat fennmarad;
- a rendszer vagy record migrációjának útja ismert és tesztelhető;
- a kivezetés nem semmisíti meg a szükséges bizonyíthatóságot;
- az archivált állapotból a kijelölt információ ténylegesen visszaolvasható, értelmezhető és ellenőrizhető;
- a preservation evidence nincs olyan elavult technológiához kötve, amelynek elvesztésekor maga a bizonyíték válna használhatatlanná, hacsak ehhez nincs külön működő fenntartási vagy emulációs út.

## TESZT

Válasszunk ki egy reprezentatív hosszú élettartamú kritikus recordot vagy rendszert, és hajtsunk végre időbeli rekonstrukciós próbát:

```text
archivált adat / record
    ->
schema + semantics
    ->
provenance
    ->
alkalmazott szabály / verzió
    ->
authority / hivatalos döntés
    ->
technikai környezet
    ->
mai vagy alternatív környezetben értelmezhető eredmény
```

Ahol reális, külön hajtsunk végre migrációs vagy cold-readback tesztet olyan környezetben, amely nem támaszkodik automatikusan a jelenlegi éles rendszer minden komponensére.

## FAILURE CONDITION

A követelmény nem teljesül, ha például:

- az adat fizikailag megvan, de jelentése vagy schema-ja később nem rekonstruálható;
- nem állapítható meg, milyen szabály vagy rendszerverzió hozta létre;
- a hivatalos record authority/provenance kapcsolata elveszett;
- migráció csak elméleti terv, teszt nélkül;
- a rendszer kivezetése együtt megszünteti a szükséges bizonyíthatóságot;
- az archívum olyan kulcstól, szoftvertől vagy szolgáltatástól függ, amelynek elvesztésére nincs működő válasz;
- az archivált állapotot a megőrzési időn belül ténylegesen nem lehet visszaolvasni vagy értelmezni.

## FORRÁS

- *A digitális bizalom 12 pontja* — a digitális államnak az időben is működőképesnek kell maradnia.
- Nagymajtényi korábbi szuverenitási / reconstructability és legacy-retention vonala.
- A projekt controlling distinctionje:
  `stored != interpretable != reconstructable != migratable != archivable`.

## STATUS

`DRAFT — FIRST PUBLIC TEST SET`

---

# Keresztellenőrzés

Ez a tíz rekord együtt szándékosan több külön problématípust tesztel.

| ID | Elsődleges kérdés | Rendszerszintű keresztellenőrzés |
| --- | --- | --- |
| `R-0001` | Tudjuk-e, milyen tágabb célból milyen funkciót védünk? | constitutional purpose / interacting failure / hazardous state |
| `R-0002` | Miből tudjuk, hogy teljesül, és ki tudja ezt függetlenül ellenőrizni? | self-assertion != independent verification |
| `R-0003` | Mi történik kritikus függőség elvesztésekor vagy külső döntéskor? | external dependency / common-mode failure / survivable failure |
| `R-0004` | Ténylegesen helyre tudunk-e állni és vissza tudunk-e térni a normál jogszerű állapotba? | compound failure / recovery interaction / return |
| `R-0005` | Mi marad működőképes részleges kiesésben? | latent degradation / feedback / reconciliation / bounded emergency |
| `R-0006` | Megmarad-e a jogszerű közhatalmi lánc technikai és AI-közreműködés mellett is? | authority continuity != technical access != intelligence |
| `R-0007` | Az érintett ember vagy szervezet célja felől működik-e a szolgáltatási út? | seamless service != blurred authority / totalized data |
| `R-0008` | Milyen támadói feltételezéstől függ a biztonsági állítás? | assumed capability bound != established property |
| `R-0009` | Eljut-e a szakmai kockázatjelzés oda, ahol tényleges döntés születik? | risk information / escalation / accountable deviation |
| `R-0010` | Évek múlva is értelmezhető, átvihető és bizonyítható marad-e a kritikus állapot? | lifecycle / provenance / migration / archival reconstructability |

A keresztellenőrzés nem jelent kötelező STAMP/STPA vagy más branded módszertant.

```text
system-level requirement
!=
mandatory analysis framework
```

---

# Első back-test kérdések a Manifesztóhoz

A követelménykészlet átdolgozása után a Manifesztó jelenlegi szövegét legalább a következő kérdésekkel kell visszatesztelni:

1. A tágabb alkotmányos kiindulópontból és a „funkciót védünk” állításból ténylegesen levezethető-e `R-0001` anélkül, hogy a funkciólistát a meglévő intézményi térképből olvasnánk vissza?
2. A „megbízhatóság bizonyított képesség” elég erős alapot ad-e `R-0002` számára, vagy marad-e benne olyan fallback, amely kritikus állításnál puszta önigazolást enged?
3. A rendszerbiztonsági pontból természetesen levezethető-e `R-0008`, és világos-e, hogy alá nem támasztott támadói képességkorlát esetén az állítás igazoltsága, nem maga a „tulajdonság létezése” bukik el?
4. A rendszerbiztonsági pont nem sugallja-e, hogy egyetlen módszertant kell használni?
5. A felelősségi pont elég alapot ad-e `R-0009` számára: eljut-e a szakmai kockázatjelzés a döntés szintjéig, és rekonstruálható-e a javaslattól való eltérés?
6. A kritikus függőségre vonatkozó Manifesztó-szöveg elég tág-e az exit mellett a survivable failure kezelésére is, és világos-e, hogy egyetlen külső szereplő kiesése vagy döntése nem teheti szükségszerűvé a minimális kritikus funkció elvesztését?
7. A 6. pont címe indokolatlanul szűkebb-e a saját törzsszövegénél, amikor csak „kilépési utat” nevez meg, miközben a törzsszöveg túlélési utat is elfogad?
8. A válság/fallback szöveg tartalmazza-e a degraded-state detection, a reconciliation és a normál, jogszerű állapotba való visszatérés lényegét?
9. Ha a tartós fenyegetettségre vonatkozó opcionális tétel megmarad, `R-0005` megfelelően választja-e el a tartós fenyegetést a rendkívüli működés tartós szükségességének külön igazolásától?
10. A közhatalmi pont világosan elválasztja-e a technikai jogosultságot és az intelligenciát a jogszerű authoritytől, és `R-0006` nem tesz-e ennél többet?
11. Az időbeli működőképességre vonatkozó tételből természetesen levezethető-e `R-0010`, különösen az archiválhatóság mint értelmezhető és rekonstruálható lifecycle-képesség?
12. Ha az élethelyzet / szolgáltatási nézőpont a Manifesztóban opcionális marad, `R-0007` továbbra is indokolható-e az `Alapok` önálló requirementjeként a tágabb alkotmányos kiindulópontból?
13. A 12. pont `tényleges kontroll` fogalma operacionalizálható-e úgy, hogy világos legyen, milyen minimális állami képességeket kell megtartani, de ebből ne következzen tulajdonosi, hazai beszállítói vagy általános insourcing-kötelezettség?
14. A Manifesztó vagy e követelmények bármelyike rejtetten konkrét technológiát, szervezeti modellt vagy analysis frameworköt ír-e elő?

---

# Következő lépés

A következő munka továbbra sem a teljes követelményfa kitöltése.

Ez a v0.2.1 a következő szakmai review egyik inputja. A következő menet:

1. az aktuális Manifesztó- és `Alapok`-állapotot, a nyitott döntéseket és a kért külső teszteket rövid `status.md`-ben rögzíteni;
2. a working materialt a kijelölt GitHub-munkafelületen elérhetővé tenni;
3. heterogén szakmai körből kifejezetten falszifikációs review-t kérni: hol mérhetetlen, túl erős, túl gyenge, kijátszható vagy rejtetten implementációt előíró valamely követelmény;
4. legalább 2–3 rekordnál valódi vagy realisztikus teszt-/bizonyítékpéldával dry runt végezni;
5. külön stress-testelni legalább `R-0002`, `R-0008` és `R-0009` bizonyíthatóságát, valamint a 12. pont `tényleges kontroll` fogalmának implementációsemleges operacionalizálhatóságát;
6. a review és a dry run eredményeit visszavezetni az `Alapok` következő változatába;
7. ezután külön Manifesztó-deltaellenőrzést végezni: csak az a találat indokoljon Manifesztó-módosítást, amely nem pusztán követelményszintű részletezés, hanem valódi normatív vagy szerkezeti lyukat tár fel.

```text
current working pair
    ->
status.md
    ->
expert falsification
    ->
2–3 dry runs
    ->
Alapok revision
    ->
Manifesztó delta check
    ->
public-freeze candidate
```
