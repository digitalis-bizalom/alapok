# Implementation candidates

Ez a könyvtár a `digitalis-bizalom/alapok` követelményeihez kapcsolódó **lehetséges megvalósítási megoldások, architektúrák, technológiák, működési modellek és intézményi mechanizmusok** vizsgálati helye.

A könyvtár célja nem egy preferált technológiai stack kijelölése, hanem annak lehetővé tétele, hogy különböző megoldásokat ugyanazon követelmények alapján lehessen összehasonlítani.

```text
követelmény
    ->
lehetséges megvalósítások
    ->
teszt
    ->
bizonyíték
    ->
értékelés
```

A legfontosabb szabály:

```text
implementation candidate
!= requirement
```

## 1. Mi számít implementation candidate-nek?

Implementation candidate lehet például:

- technológia;
- protokoll;
- szoftver;
- platform;
- architektúra;
- adatkezelési modell;
- hálózati modell;
- azonosítási vagy jogosultsági megoldás;
- cryptographic mechanism;
- recovery mechanism;
- deployment model;
- beszerzési vagy működtetési modell;
- intézményi mechanizmus;
- governance-megoldás;
- szabvány;
- nyílt forrású komponens;
- kereskedelmi termék;
- saját fejlesztés;
- ezek kombinációja.

A könyvtár tehát nem kizárólag informatikai technológiákról szól.

```text
implementation
can be
technical
organizational
institutional
procedural
or mixed
```

## 2. Inclusion != endorsement

Egy candidate felvétele ebbe a könyvtárba nem jelenti, hogy a projekt:

- ajánlja;
- támogatja;
- hitelesíti;
- beszerzésre javasolja;
- biztonságosnak minősíti;
- vagy referenciaimplementációnak tekinti.

```text
included for evaluation
!= endorsed
!= certified
!= recommended
```

A candidate azért kerülhet ide, mert érdemes megvizsgálni.

Negatív vagy bizonytalan értékelésű candidate is maradhat dokumentálva, ha abból szakmai tanulság származik.

## 3. Követelményből indulunk

Candidate-et mindig már azonosított követelményhez vagy követelménycsoporthoz viszonyítunk.

Nem helyes irány:

```text
van egy technológiánk
    ->
keressünk hozzá problémát
    ->
írjunk hozzá követelményt
```

A kívánt irány:

```text
van egy követelmény
    ->
milyen megoldások teljesíthetik?
    ->
milyen feltételek mellett?
    ->
hogyan tesztelhető?
```

Egy candidate új követelményre is rámutathat. Ilyenkor azonban a követelményt külön kell megfogalmazni és önállóan indokolni.

```text
candidate reveals missing requirement
    ->
requirement is evaluated independently
```

## 4. Candidate record

Egy candidate külön fájlban történő értékelésénél célszerű legalább az alábbi mezőket használni:

```text
ID
NÉV
TÍPUS
CÉLZOTT KÖVETELMÉNYEK
RÖVID LEÍRÁS
FELTÉTELEZÉSEK
VÁRHATÓ ELŐNYÖK
FÜGGŐSÉGEK
FAILURE MODES
RENDSZERSZINTŰ HATÁSOK / INTERAKCIÓK
KOMPLEXITÁS / MŰKÖDTETHETŐSÉG
EXIT / REPLACEABILITY
TESZTELHETŐSÉG
BIZONYÍTÉK
KORLÁTOK
ÉRETTSÉG
ÉRDEKELTSÉGI NYILATKOZAT
FORRÁS
STATUS
```

Nem minden candidate igényel minden mezőhöz azonos mélységű leírást.

A record célja az összehasonlíthatóság és a rejtett feltételezések láthatóvá tétele.

## 5. Célzott követelmények

A candidate-et lehetőség szerint konkrét `Alapok`-követelményekhez kell kötni.

Például:

```text
CÉLZOTT KÖVETELMÉNYEK:
    <stabil public requirement-ID>
    <stabil public requirement-ID>
```

Csak ténylegesen publikált követelmény azonosítója használható hivatkozási pontként. Tervezett domain-, taxonómia- vagy belső munkasorszám ne váljon e README használatával implicit nyilvános stabil ID-vé.

Ez lehetővé teszi, hogy ugyanarra a requirementre több candidate is összehasonlítható legyen.

```text
one requirement
    -> many candidates

one candidate
    -> may address many requirements
```

## 6. Feltételezések

Minden megoldás feltételez valamit a környezetéről.

Például:

- stabil hálózati kapcsolat;
- rendelkezésre álló cloud provider;
- speciális hardver;
- központi trust anchor;
- helyi szakértelem;
- folyamatos internetelérés;
- bizonyos jogszabályi környezet;
- magas felhasználói penetráció;
- kompatibilis legacy rendszer;
- külső partner együttműködése.

A feltételezéseket explicit módon kell kezelni.

```text
hidden assumption
=
hidden dependency
```

## 7. Függőségek

A candidate vizsgálatának része:

- technológiai dependency;
- vendor dependency;
- licensing dependency;
- jurisdictional dependency;
- cloud dependency;
- hardware dependency;
- knowledge dependency;
- operational dependency;
- standards dependency;
- cryptographic dependency;
- organizational dependency.

A jó candidate nem feltétlenül dependency-free.

A kérdés:

> A függőség ismert, kezelhető, tesztelhető és szükség esetén elhagyható-e?

## 8. Exit és helyettesíthetőség

Kritikus állami funkciót támogató candidate-nél különösen fontos:

```text
adoptability
!=
exittability
```

Vizsgálandó lehet:

- exportálható-e az adat;
- rekonstruálható-e a schema és semantics;
- tovább működtethető-e a vendor nélkül;
- van-e dokumentált migration path;
- van-e alternatív implementáció;
- újraépíthető-e a runtime environment;
- átadható-e a működtetési tudás;
- mi történik licenc- vagy szolgáltatásmegszűnéskor.

## 9. Failure modes

A candidate értékelése nem korlátozódhat a kívánt működésre.

Kérdések:

- hogyan hibásodhat meg;
- milyen common-mode failure-t hoz létre;
- mekkora a blast radius;
- hogyan viselkedik részleges kiesésnél;
- milyen támadási felületet nyit;
- milyen új governance-kockázatot hoz létre;
- milyen hibát nehéz észlelni;
- milyen többkomponensű vagy common-mode failure alakulhat ki;
- előállhat-e veszélyes rendszerállapot úgy, hogy az egyes komponensek önmagukban a specifikáció szerint működnek;
- milyen latent degradation maradhat sokáig észrevétlen;
- milyen hiányzó, késő vagy félrevezető feedback akadályozhatja a hiba felismerését;
- támaszkodik-e a működés ismétlődő workaroundra, kézi kompenzációra vagy rendkívüli emberi beavatkozásra;
- milyen új failure pathway-t hozhat létre maga a candidate bevezetése vagy későbbi módosítása;
- hogyan áll helyre.

```text
feature list
!= resilience analysis

component correctness
+
formal compliance
!=
system-level safe operation

absence of overt incident
!=
absence of dangerous failure trajectories
```

## 10. Rendszerszintű biztonság és interakciók

Kritikus állami funkciót támogató candidate-et nem elég komponensenként értékelni.

Vizsgálandó, hogy a candidate:

- milyen rendszerhatárt feltételez;
- milyen más komponensekkel, intézményekkel és emberi szereplőkkel lép kölcsönhatásba;
- milyen visszacsatolásból állapítható meg, hogy a kívánt működési állapot fennáll;
- milyen állapotot vagy átmenetet kell megelőzni, észlelni vagy korrigálni;
- hogyan viselkedik latent degradation mellett;
- hogyan teszi láthatóvá a near miss, repeated workaround, manual recovery vagy más weak signal jelenségeket;
- hogyan változtatja a common-mode failure és blast-radius kockázatát;
- hogyan változtatja meg a már meglévő recovery- és fallback-logikát.

Egy system-safety módszer — például STAMP/STPA vagy más megfelelő elemzési keret — használható candidate-értékeléshez, de a projekt nem ír elő egyetlen ilyen módszert kötelező megoldásként.

```text
useful analysis method
!=
mandatory implementation architecture

engineering control / feedback
!=
constitutional control / public authority

engineering safety constraint
!=
legal or normative authority for a constraint
```

Ha a jelenlegi működés emberi szakértelemre vagy adaptív beavatkozásra támaszkodik, ezt dependencyként és működési képességként láthatóvá kell tenni.

```text
automation
!=
proof that previously human adaptive safety functions
have become unnecessary

recognizing human adaptive capacity
!=
requiring permanent human-in-the-loop architecture
```

## 11. Tesztelhetőség

Előnyben részesítendő az a candidate, amelynek releváns állításai:

- mérhetők;
- reprodukálhatók;
- összehasonlíthatók;
- megfelelően auditálhatók;
- tesztkörnyezetben vagy pilotban kipróbálhatók.

A candidate saját marketingállítása nem helyettesíti a tesztet.

```text
vendor claim
!= demonstrated capability
```

A candidate-ről gyűjtött bizonyítékok helye szükség szerint a `bizonyitekok/` könyvtár lehet.

## 12. Bizonyíték

Candidate-ről állított konkrét tulajdonságot lehetőség szerint bizonyíték támasszon alá.

Például:

```text
ÁLLÍTÁS:
    a rendszer hálózati leválasztás mellett is képes a kritikus helyi funkcióra

TESZT:
    kontrollált network partition

BIZONYÍTÉK:
    teszteredmény + napló + helyreállítási record
```

A source és a bizonyíték itt is különbözik.

```text
FORRÁS:
    honnan származik a candidate leírása vagy állítása

BIZONYÍTÉK:
    miből állapítható meg, hogy az állítás ténylegesen igaz az értékelt változatra
```

## 13. Candidate maturity

Az érettséget nem célszerű egyetlen marketingkategóriával leírni.

Hasznos szempontok lehetnek:

- elméleti javaslat;
- proof of concept;
- demonstrátor;
- pilot;
- korlátozott production;
- széles production;
- hosszú távú működési tapasztalat;
- több független implementáció;
- ismert migration history;
- ismert failure history.

```text
new
!= bad

mature
!= automatically suitable
```

A kritikus állami használhatóságot mindig a konkrét requirement és kockázati környezet alapján kell értékelni.

## 14. Leapfrog és komponensújdonság

Egy radikálisan jobb rendszerarchitektúra nem követel radikálisan új alkatrészeket.

```text
LEAPFROG AT SYSTEM LEVEL
!=
NOVELTY AT COMPONENT LEVEL
```

Lehetséges jó kombináció:

```text
new institutional / service architecture
+
proven components
```

Ugyanakkor új technológia sem zárható ki pusztán újdonsága miatt.

A kérdés:

- milyen problémát old meg;
- milyen új failure mode-ot hoz;
- mennyire tesztelhető;
- mennyire helyettesíthető;
- milyen bizonyíték áll rendelkezésre.

## 15. Komplexitás és működtethetőség költsége

Az implementation candidate által bevezetett új komplexitás önálló költség és kockázati koordináta.

```text
additional complexity
must earn its place
```

Nem az a cél, hogy minden új vagy összetett megoldást kizárjunk. A kérdés az, hogy az új komplexitás milyen requirementet szolgál, és teljes életciklusa alatt kezelhető-e.

Minimum vizsgálati kérdések:

- mely requirement indokolja az új komplexitást;
- milyen új expertise szükséges hozzá;
- hogyan dokumentálható;
- hogyan adható át másik üzemeltetőnek;
- milyen új couplingot, failure surface-t vagy közös hibadomént hoz létre;
- milyen observabilityt igényel;
- milyen új monitoring- és incident-response terhet okoz;
- hogyan változtatja a recovery és fallback terhét;
- milyen konfigurációs vagy verziófüggőséget hoz létre;
- hogyan távolítható el vagy helyettesíthető;
- egyszerűbb candidate ugyanazt a requirementet megfelelően teljesítené-e.

```text
system-level leapfrog
!=
component novelty

novel technology
!=
rejected by default

boring technology
!=
safe by default
```

A komplexitás értékelése ne szereplők feltételezett motivációjáról szóljon.

```text
complexity critique
!=
claim about developer / vendor motive
```

A candidate-et a requirement, a működtethetőség, a failure modes, a teszt és a bizonyíték alapján kell értékelni.

## 16. Open source

```text
open source
!= secure
!= maintainable
!= sovereign
```

Az open source ugyanakkor előnyt adhat:

- inspectability;
- buildability;
- reproducibility;
- forkability;
- supplier exit;
- hosszú távú archiválhatóság

szempontjából.

Ezeket külön kell vizsgálni.

## 17. Hazai megoldás és szuverenitás

```text
hazai vendor
!= szuverén képesség

külföldi vendor
!= automatikus szuverenitásvesztés
```

A releváns kérdések:

- kontroll;
- tudás;
- működtethetőség;
- helyettesíthetőség;
- joghatóság;
- recovery;
- migration;
- hosszú távú evolúció.

## 18. Centralizált és elosztott megoldások

A könyvtár nem privilegizál automatikusan sem centralizált, sem elosztott architektúrát.

```text
centralized
!= inherently bad

distributed
!= inherently resilient
```

Vizsgálandó:

- failure domain;
- consistency;
- partition behavior;
- authority model;
- coordination cost;
- recovery;
- attack surface;
- observability;
- operational complexity.

## 19. AI és automatizált megoldások

AI-alapú candidate esetén külön kezelendő:

```text
capability
!= authority
```

Vizsgálandó lehet:

- milyen szerepet tölt be az AI;
- advisor vagy döntéshozó;
- milyen source-ra támaszkodik;
- hogyan kezelhető hallucination vagy model failure;
- milyen jogosultságot kap;
- hogyan auditálható;
- milyen személyes vagy érzékeny adathoz fér hozzá;
- milyen fallback van;
- hogyan működik AI nélkül;
- milyen támadó AI-képességet feltételez a security model.

## 20. Adat- és profilalapú candidate-ek

Személyre szabás vagy life-situation alapú szolgáltatás nem igazolja automatikusan a teljes profil központosítását.

```text
personalization
!= unlimited profiling
```

Vizsgálandó:

- mely adat szükséges;
- milyen jogalappal;
- milyen ideig;
- hol dolgozzuk fel;
- lehet-e lokális vagy szelektív kiértékelés;
- milyen adatot kell ténylegesen felfedni;
- milyen linkage szükséges;
- milyen visszaélési kockázat keletkezik.

## 21. Candidate és jogszerű közhatalom

Egy technológia egyszerűsítheti a szolgáltatást, de nem homályosíthatja el:

- ki jár el;
- milyen hivatalban;
- milyen hatáskörrel;
- milyen jogalapon;
- milyen official act keletkezett.

```text
seamless implementation
!= blurred lawful authority

technical control mechanism
!= public authority

engineering safety constraint
!= legal / constitutional constraint
```

Ha a candidate saját `control`, `controller`, `constraint`, `authority` vagy hasonló fogalmat használ, az értékelésben egyértelművé kell tenni, hogy technikai, szervezeti vagy közhatalmi értelemről van-e szó.

## 22. Candidate és state-function completeness

Egy candidate attól még nem megfelelő, hogy jól old meg egy izolált technikai problémát.

A state-function completeness alapján szükség szerint vizsgálni kell:

- normál működést;
- degradált működést;
- emergency substitutiont;
- recovery priorityt;
- authority continuityt;
- data/semantic continuityt;
- fizikai-területi dependencyt;
- külső/joghatósági dependencyt;
- secrecy/verifiabilityt;
- non-digital fallbacket;
- reconciliationt;
- official communicationt.

Nem minden candidate-re releváns minden dimenzió.

Ahol releváns, a candidate-et külön is vizsgálni kell abból a szempontból, hogy:

- nominálisan normál működés mellett kialakulhat-e latent degradation;
- több kisebb hiba vagy félreértett interakció együtt létrehozhat-e súlyos failure-t;
- megfelelő feedbackből felismerhető-e a veszélyes állapot;
- a near miss, repeated workaround és manual recovery láthatóvá válik-e;
- a candidate bevezetése vagy frissítése milyen új failure pathway-t hozhat létre.

A `N/A` azonban indoklandó legyen, ne automatikus.

## 23. Összehasonlítás

Ha több candidate ugyanazt a követelményt célozza, célszerű azonos koordináták szerint összehasonlítani őket.

Például:

```text
REQUIREMENT
CANDIDATE A
CANDIDATE B
CANDIDATE C

security
resilience
system-level interactions
latent degradation / observability
dependency
exit
recovery
complexity / operability cost
adaptive operational dependencies
verification
maturity
cost assumptions
legal / jurisdictional constraints
```

Nem szükséges minden szempontot egyetlen pontszámmá aggregálni.

```text
comparison
!= ranking
```

A trade-off-ok láthatósága gyakran fontosabb, mint egy összesített score.

## 24. Érdekeltségi nyilatkozat

Ha egy candidate-et olyan személy vagy szervezet javasol, aki:

- fejlesztője;
- tulajdonosa;
- befektetője;
- beszállítója;
- alkalmazottja;
- tanácsadója;
- vagy más lényeges érdekeltséggel rendelkezik,

ezt láthatóan jelezni kell.

```text
contribution
!= disqualification

undisclosed material interest
=
governance problem
```

A disclosure célja nem a candidate kizárása, hanem az értékelési helyzet átláthatósága.

## 25. Résztvevői megoldások

A projekt résztvevőjének saját:

- cége;
- platformja;
- terméke;
- open-source projektje;
- architektúrája;
- módszertana

ugyanúgy candidate lehet, mint külső megoldás.

De:

```text
participant
!= privileged candidate

participant's product
!= reference implementation
```

A candidate ugyanazon követelmények, tesztek és disclosure-szabályok szerint értékelendő.

## 26. Reference implementation

A projekt jelenleg nem jelöl ki hivatalos reference implementationt.

Ha valamikor mégis szükség lenne ilyenre, annak külön governance-döntést, nyilvános kritériumokat és anti-capture guardokat kell kapnia.

```text
good example
!= official reference implementation
```

## 27. Candidate státusz

Lehetséges státuszok:

```text
PROPOSED
    értékelésre felvetett candidate

UNDER REVIEW
    aktív vizsgálat alatt

TESTED
    legalább egy releváns teszt megtörtént

PARTIALLY SUPPORTED
    bizonyos állításait megfelelő bizonyíték támogatja

INSUFFICIENT EVIDENCE
    az értékeléshez nincs elég bizonyíték

CONDITIONAL
    csak meghatározott feltételek mellett megfelelő

NOT SUITABLE
    az adott requirementhez dokumentált okból nem megfelelő

SUPERSEDED
    újabb candidate vagy változat váltotta fel

ARCHIVED
    történeti vagy tanulsági okból megőrzött
```

A státusz mindig meghatározott scope-ra vonatkozik.

```text
NOT SUITABLE for requirement X
!= universally bad technology
```

## 28. Verzió és értékelési hatókör

Egy termék vagy technológia változik.

Ezért a candidate recordnak lehetőség szerint azonosítható változatra kell vonatkoznia:

- verzió;
- commit;
- release;
- configuration;
- deployment model;
- evaluation date.

```text
product name
!= stable evaluated object
```

## 29. Publication és security boundary

Candidate-analysis is tartalmazhat érzékeny információt:

- exploit detail;
- kritikus dependency;
- recovery weakness;
- deployment topology;
- privilege structure;
- physical vulnerability.

Ezért:

```text
public candidate method
!= automatically public full candidate assessment
```

A public repositoryba csak olyan részlet kerülhet, amelynek publication- és security-kockázata elfogadható.

## 30. Reklám és advocacy

A könyvtár nem termékkatalógus és nem marketingfelület.

Kerülendő:

- sales copy;
- ellenőrizetlen teljesítményállítás;
- partnerlista mint minőségi bizonyíték;
- puszta brand comparison;
- befektetési vagy politikai advocacy;
- versenytársak bizonyíték nélküli minősítése.

A candidate leírása lehet pozitív, de a pozitív állításnak ugyanúgy vizsgálhatónak kell lennie.

## 31. Kapcsolat a `bizonyitekok/` könyvtárral

A két könyvtár szerepe eltér:

```text
implementation-candidates/
    mit vizsgálunk mint lehetséges megoldást

bizonyitekok/
    miből állapítjuk meg, hogyan teljesít
```

Egy candidate record hivatkozhat több bizonyítékrekordra.

Egy bizonyítékrekord több candidate vagy requirement értékelésében is releváns lehet.

## 32. Kapcsolat a Manifestóval

A Manifesto technológia-semleges szakmai minimum.

Ezért candidate-ek neve, termék vagy konkrét stack csak kivételes esetben és külön indoklással kerülhet Manifesto-szintre.

```text
Manifesto
    = what must be true

Alapok
    = how it becomes testable

Implementation candidates
    = possible ways to achieve it
```

## 33. Könyvtárszerkezet

A könyvtár csak tényleges tartalommal bővüljön.

Például később:

```text
implementation-candidates/
    README.md
    local-first/
    identity/
    recovery/
    interoperability/
    ai-advisors/
```

Nem szükséges előre teljes candidate-taxonomyt létrehozni.

```text
real candidate
    -> justified file / directory

no candidate
    -> no empty structure
```

## 34. Minimális elfogadási kérdések

Egy candidate első komoly értékelése előtt legalább ezekre legyen válasz:

1. Mely requirementet célozza?
2. Milyen feltételezések mellett működik?
3. Milyen dependencyt hoz létre?
4. Milyen rendszerszintű interakciókat és common-mode failure lehetőségeket hoz létre vagy módosít?
5. Mi történik hibánál, részleges kiesésnél vagy latent degradation mellett?
6. Miből észlelhető, hogy a rendszer eltért a kívánt állapottól?
7. Támaszkodik-e ismétlődő workaroundra, kézi kompenzációra vagy különleges emberi szakértelemre?
8. Milyen új komplexitást vezet be, és mely requirement indokolja ezt?
9. Hogyan áll helyre?
10. Hogyan hagyható el vagy cserélhető?
11. Hogyan tesztelhető?
12. Milyen bizonyíték áll rendelkezésre?
13. Milyen érettségi szinten van?
14. Van-e lényeges résztvevői vagy kereskedelmi érdekeltség?
15. Van-e security vagy publication kockázata az értékelésnek?
16. Ha a candidate technikai `control` vagy `constraint` fogalmat használ, világos-e, hogy ez nem közhatalmi felhatalmazás?
17. Mely állítások maradnak még bizonyítatlanok?

Ha ezek közül több alapvető kérdésre nincs válasz, a candidate ettől még dokumentálható, de nem kezelhető megalapozott megoldási ajánlásként.
