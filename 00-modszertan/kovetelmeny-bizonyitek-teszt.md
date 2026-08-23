# Követelmény, bizonyíték, mérce és teszt

Ez a dokumentum az `Alapok` alapvető ellenőrzési grammatikáját definiálja.

```text
ÁLLÍTÁS
-> KÖVETELMÉNY
-> BIZONYÍTÉK
-> MÉRCE
-> TESZT
-> FAILURE CONDITION
```

A lánc célja, hogy egy szakmai elvből olyan követelmény legyen, amelynek teljesülése nem pusztán kijelenthető, hanem érdemben vizsgálható.

## 1. Miért kell a lánc?

Az olyan szavak, mint:

- biztonságos;
- reziliens;
- szuverén;
- helyreállítható;
- interoperábilis;
- auditálható;
- jövőálló

önmagukban nem tesznek egy rendszert ellenőrizhetővé.

Egy állítás akkor válik az `Alapok` részévé megfelelő erősséggel, ha legalább elvileg végigvezethető rajta a következő kérdéssor:

```text
Mit állítunk?
Mit kell ezért a rendszernek vagy az intézménynek tudnia?
Mi számít ennek bizonyítékának?
Milyen szabály vagy küszöb alapján értékeljük?
Hogyan vizsgáljuk meg?
Mi az a körülmény, amelynél kimondjuk, hogy nem teljesül?
```

## 2. A public minimum schema

Egy követelmény alapértelmezett nyilvános rekordja:

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

A mezők nem egymás szinonimái. A szétválasztásuk a módszer része.

## 3. ID

Az `ID` a követelmény stabil azonosítója.

Feladata:

- pontos hivatkozás;
- változások követése;
- kapcsolatok rögzítése;
- tesztek és bizonyítékok visszakötése.

Az ID lehetőleg ne hordozzon több jelentést, mint amennyi a stabil azonosításhoz szükséges.

Egy követelmény szerkesztési változása önmagában ne kényszerítsen tömeges újraszámozást.

```text
ID
!= verziószám
```

A dokumentum és a követelmény változását a Git-history és szükség esetén külön publikált verzió kezeli.

## 4. ÁLLÍTÁS

Az `ÁLLÍTÁS` röviden és emberileg olvashatóan megfogalmazza, mit tartunk szükségesnek vagy igaznak az adott témában.

Példa szerkezet:

> Egy kritikus képesség helyreállíthatósága nem feltételezhető; azt megfelelő bizonyítékkal alá kell támasztani.

Az állítás lehet magasabb szintű, mint a hozzá tartozó operatív követelmény.

```text
ÁLLÍTÁS
    = szakmai jelentés

KÖVETELMÉNY
    = ellenőrizhető kötelező feltétel
```

Egy Manifesto-állítás több Alapok-állításhoz vagy több követelményhez is vezethet.

## 5. KÖVETELMÉNY

A `KÖVETELMÉNY` azt mondja meg, minek kell teljesülnie.

Jó követelmény:

- egyértelmű tárgyra és határra vonatkozik;
- amennyire lehet, implementation-neutral;
- nem pusztán cél- vagy értékmegjelölés;
- elvileg cáfolható;
- elvileg bizonyítékhoz és teszthez köthető;
- kritikus funkciónál szükség szerint kezeli a normál, degradált és helyreállítási működést is.

Gyenge:

> A rendszer legyen reziliens.

Erősebb:

> A kijelölt kritikus funkcióhoz dokumentált helyreállítási célok, szükséges függőségek és rendszeresen végrehajtott helyreállítási teszt tartozzon.

A pontos követelménynek nem kell előírnia, milyen konkrét termékkel vagy architektúrával kell ezt elérni.

```text
required capability
!= preferred implementation
```

Ha egy konkrét implementáció mégis része a követelménynek, annak oka legyen explicit.

## 6. BIZONYÍTÉK

A `BIZONYÍTÉK` azt írja le, milyen megfigyelhető, visszakereshető vagy ellenőrizhető anyag támaszthatja alá vagy cáfolhatja a követelmény teljesülését.

A `bizonyíték` itt az angol *evidence* megfelelője. Nem matematikai értelemben vett bizonyítást és nem önmagában végleges következtetést jelent.

```text
bizonyíték
!= bizonyítás
!= következtetés
```

Bizonyíték lehet például:

- konfiguráció vagy géppel olvasható állapot;
- teszt- vagy gyakorlatjegyzőkönyv;
- helyreállítási log;
- mérési eredmény;
- incidensadat;
- audit trail;
- kriptográfiailag ellenőrizhető provenance;
- szerződés vagy kilépési mechanizmus dokumentuma;
- jogosultsági vagy delegation record;
- reprodukálható build vagy restore artifact;
- fizikai készlet vagy kapacitás ellenőrzött nyilvántartása;
- megfelelő jogosultsággal elvégzett zárt audit eredménye.

Az bizonyíték önmagában még nem mondja meg, hogy a követelmény teljesül. Ehhez kell a mérce.

```text
bizonyíték
!= következtetés
```

### 6.1 Bizonyíték és forrás

A két mező szerepe különbözik:

```text
FORRÁS
    = honnan ered vagy mivel indokolható az állítás/követelmény

BIZONYÍTÉK
    = mit vizsgálunk a konkrét teljesülés megállapításához
```

Egy szabvány, tanulmány vagy jogszabály lehet fontos forrás, de önmagában nem bizonyítja, hogy egy konkrét rendszer megfelelően működik.

## 7. MÉRCE

A `MÉRCE` azt a döntési szabályt írja le, amely alapján a bizonyítékot értékeljük.

A mérce lehet:

- numerikus küszöb;
- időkorlát;
- arány;
- maximális veszteség;
- bináris feltétel;
- kategorikus minősítés;
- invariáns;
- dokumentált döntési szabály.

Példák:

```text
helyreállítási idő <= deklarált RTO

adatveszteség <= deklarált RPO

minden kritikus függőséghez van kijelölt és kipróbált exit path

a hivatalos aktus provenance-e a kijelölt trust chain alapján ellenőrizhető
```

A mérce legyen elég pontos ahhoz, hogy ugyanazt a bizonyítékot két független reviewer lehetőleg ugyanúgy értékelje.

```text
mérce
!= általános kívánalom
```

Ha még nincs legitim küszöb, ezt nem szabad tetszőleges számmal pótolni. A hiányzó vagy nyitott threshold maga is látható státuszú szakmai kérdés.

## 8. TESZT

A `TESZT` az a dokumentált eljárás, amely a bizonyítékot előállítja vagy a követelmény teljesülését megvizsgálja.

Egy jó tesztből legalább a következők rekonstruálhatók:

1. mit vizsgálunk;
2. milyen előfeltételek mellett;
3. milyen lépésekkel;
4. milyen megfigyeléseket rögzítünk;
5. milyen mércét alkalmazunk;
6. mi az elfogadható eredmény;
7. mi számít failure-nek.

Teszt lehet például:

- restore exercise;
- failover vagy degraded-mode exercise;
- tabletop exercise;
- jogosultság- és delegation-review;
- backupból izolált helyreállítás;
- beszállítói exit rehearsal;
- interoperabilitási próba;
- offline/manual fallback próba;
- kulcs- vagy trust-anchor csere;
- disaster-recovery gyakorlat;
- dokumentált inspection vagy audit.

A dokumentum puszta megléte nem mindig teszt. Ahol a követelmény tényleges működési képességre vonatkozik, ott lehetőleg működés közbeni vagy gyakorlatban reprodukálható bizonyíték szükséges.

```text
documented plan
!= demonstrated capability
```

A tesztet a vizsgált rendszer kritikusságához, kockázatához és jogszerű működéséhez kell igazítani. Éles rendszer veszélyeztetése nem módszertani követelmény.

## 9. FAILURE CONDITION

A `FAILURE CONDITION` azt mondja meg, mikor tekintjük a követelményt nem teljesültnek.

Nem elég:

> A teszt sikertelen.

A failure condition lehetőleg megnevezi a szakmailag releváns hibát.

Például:

- a kritikus funkció nem állítható helyre a deklarált határon belül;
- a helyreállított állapot integritása nem bizonyítható;
- egy kritikus külső függőség kiesése működésképtelenséget okoz, és nincs működő alternatíva;
- az arra jogosult hivatalos aktus eredete vagy érvényessége nem különböztethető meg megbízhatóan a hamisítottól;
- a kijelölt fallback létezik dokumentumban, de gyakorlatban nem hajtható végre;
- az ellenőrzés kizárólag ugyanazon szereplő saját állítására támaszkodik, akinek a teljesülést bizonyítania kell.

```text
failure condition
    = explicit falsification boundary
```

A failure condition teszi világossá, hogy a követelmény nem pusztán aspiráció.

## 10. FORRÁS

A `FORRÁS` a követelmény vagy állítás provenance-ét rögzíti.

Ide tartozhat:

- elsődleges jogi vagy szabályozási forrás;
- szabvány;
- hivatalos technikai dokumentáció;
- tudományos vagy szakmai publikáció;
- auditált tapasztalat;
- korábbi, azonosítható szakmai munka;
- a projektben dokumentált eredeti normatív javaslat.

A forrásnál fontos lehet:

- pontos cím vagy azonosító;
- szerző vagy kibocsátó;
- dátum vagy verzió;
- releváns rész;
- hozzáférési hely;
- időbeli érvényesség.

A forrás használata ne legyen tekintélyérv:

```text
jó forrás
!= automatikusan jó követelmény
```

A requirementet továbbra is a saját szakmai tartalma, koherenciája és ellenőrizhetősége alapján kell értékelni.

## 11. STATUS

A `STATUS` a követelményrekord érettségét vagy repositorybeli helyzetét jelzi.

```text
STATUS
!= egy vizsgált rendszer compliance eredménye
```

A státusz szókészlete a repository fejlődésével pontosítható. Minimális közös olvasatként használható például:

```text
DRAFT
    a rekord még változhat vagy hiányos

REVIEW
    érdemi review-ra előkészített

ACCEPTED
    a repository jelenlegi közös követelménye

OPEN / NOT YET COVERED
    szükséges terület vagy kötelezettség azonosítva,
    de a követelmény még nincs megfelelően kidolgozva

DEPRECATED
    korábbi követelmény, amelyet újabb rekord váltott fel
    vagy amelyet kifejezetten visszavontunk
```

Ha egy konkrét rendszer teszteredményét rögzítjük, annak külön eredmény- vagy bizonyítékrekordban kell megjelennie.

## 12. Hiányos rekordok

Korai hozzájárulásnál megengedett, hogy egy rekord még ne legyen teljes.

Ilyenkor:

- a `STATUS` legyen ennek megfelelő;
- a hiányzó mező legyen explicit `TBD`, `OPEN` vagy más egyértelmű jelölés;
- ne állítsuk, hogy a követelmény bizonyított vagy lezárt;
- a hiányzó bizonyíték, mérce vagy teszt legyen látható szakmai adósság.

```text
unknown
!= satisfied
```

## 13. Független ellenőrizhetőség

Ahol lehetséges, a teljesülést ne kizárólag az a szereplő igazolja, aki a rendszert tervezi, üzemelteti vagy szállítja.

```text
self-assertion
!= independent verification
```

A független ellenőrizhetőség jelenthet:

- más szervezeti szereplőt;
- külső auditort;
- reprodukálható tesztet;
- nyilvánosan ellenőrizhető artifactot;
- több, egymástól független bizonyítékcsatornát;
- vagy megfelelő jogosultságú zárt review-t.

A függetlenség formája a követelmény kockázatához és a legitim secrecy-korlátokhoz igazodjon.

## 14. Normál, degradált és helyreállítási mód

Nem minden követelménynél szükséges külön üzemmódokat megadni.

Kritikus state function vagy sovereign capability esetében azonban az értékelés nem állhat meg a normál működésnél.

Szükség szerint külön vizsgálandó:

```text
NORMAL MODE
DEGRADED MODE
EMERGENCY SUBSTITUTION
RECOVERY PRIORITY
RECOVERY / RECONSTRUCTION
```

A részletes coverage-szabályokat a `state-function-completeness.md` tartalmazza.

## 15. Kapcsolat az implementation candidates réteggel

Egy implementation candidate-et ugyanebből az irányból vizsgálunk:

```text
követelmény
-> teszt
-> candidate
```

nem pedig fordítva:

```text
candidate
-> hozzá igazított követelmény
```

Egy candidate előnye, újdonsága vagy résztvevői kapcsolata nem csökkentheti a bizonyítási terhet.

Több eltérő candidate ugyanazt a követelményt különböző módon is teljesítheti.

## 16. Rövid minta

Az alábbi csak a mezők kapcsolatát illusztrálja; nem önálló elfogadott követelmény.

```text
ID
EXAMPLE-RECOVERY-001

ÁLLÍTÁS
Egy kritikus funkció helyreállíthatóságát bizonyítani kell.

KÖVETELMÉNY
A funkcióhoz legyen deklarált helyreállítási cél, azonosított
függőségi kör és rendszeresen végrehajtható helyreállítási teszt.

BIZONYÍTÉK
A legutóbbi helyreállítási gyakorlat reprodukálható eredményei,
logjai és integritás-ellenőrzése.

MÉRCE
A deklarált helyreállítási és adatvesztési célok teljesülnek,
és a helyreállított állapot integritása ellenőrizhető.

TESZT
Izolált környezetben végrehajtott helyreállítás a dokumentált
forrásokból és függőségekkel, az eredmények rögzítésével.

FAILURE CONDITION
A funkció nem állítható helyre a deklarált feltételek szerint,
az integritás nem bizonyítható, vagy a teszt csak nem dokumentált
külső segítséggel hajtható végre.

FORRÁS
A követelményhez tartozó dokumentált szakmai provenance és releváns
külső források.

STATUS
DRAFT
```

A példa szándékosan nem ír elő konkrét technológiát és nem talál ki univerzális RTO/RPO értéket. A legitim mérce a funkció kritikusságától, jogi és működési környezetétől függ.
