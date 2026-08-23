# Módszertan

Ez a könyvtár az `alapok` repository közös módszertani szabályait tartalmazza.

Az `Alapok` célja nem újabb általános elvek felsorolása, hanem olyan nyílt, javítható és verziózott szakmai infrastruktúra létrehozása, amelyben egy állításból ellenőrizhető követelmény lesz.

```text
Manifesto
    = rövid, nyilvánosan vállalható szakmai minimum

Alapok
    = annak operatív jelentése és ellenőrizhetősége
```

A két réteg ezért összetartozik, de nem egymás másolata.

## 1. Alapminta

Az `Alapok` alapvető mérési grammatikája:

```text
állítás
-> követelmény
-> evidencia
-> mérce
-> teszt
-> failure condition
```

A cél az, hogy egy fontos szakmai állításról elvileg meg lehessen mondani:

1. pontosan mit követel;
2. milyen megfigyelhető vagy dokumentálható evidencia releváns hozzá;
3. milyen mérce alapján értékeljük ezt az evidenciát;
4. milyen teszt képes a követelményt érdemben vizsgálni;
5. és milyen körülmény esetén tekintjük a követelményt nem teljesültnek.

```text
jó szándék
!= bizonyított működőképesség

szabályozási megfelelés
!= bizonyított reziliencia

dokumentált képesség
!= kipróbált képesség
```

## 2. A módszertan feladata

A módszertan három külön kérdést választ szét:

```text
MIT követelünk?
HONNAN tudjuk, hogy teljesül?
LEFEDTÜK-E azt, amit egyáltalán vizsgálnunk kell?
```

Az első két kérdés részletes szabályait a `kovetelmeny-evidencia-teszt.md` tartalmazza.

A harmadik kérdéshez tartozik a `state-function-completeness.md`: annak ellenőrzése, hogy a digitális állam vizsgálata ne szűküljön pusztán általános cyber-, adat-, recovery-, beszállítói vagy interoperabilitási kérdésekre, hanem a konstitutív állami funkciók működőképességét is lefedje.

A completeness gate nem azt jelenti, hogy minden állami funkcióból külön Manifesto-pontnak kell keletkeznie. A feladata a vakfoltok láthatóvá tétele.

## 3. Módszertani alapelvek

### 3.1 Követelmény előbb, implementáció utána

```text
követelmény
!= implementáció
```

A követelményt lehetőleg úgy kell megfogalmazni, hogy több különböző technikai vagy intézményi megoldás is versenyezhessen a teljesítéséért.

Egy konkrét termék, architektúra, protokoll vagy szervezeti megoldás csak akkor kerülhet magába a követelménybe, ha éppen annak használata a vizsgált normatív állítás tárgya.

### 3.2 Normatív minimum és diagnózis különválasztása

```text
normatív követelmény
!= aktuális tényállítás
```

A magyar jelenre, konkrét intézményre, beszállítóra, incidensre, költségre vagy rendszerállapotra vonatkozó állítások külön evidenciát igényelnek.

Egy jelenlegi probléma fennállása indokolhat vizsgálatot vagy prioritást, de nem helyettesíti a követelmény általános megfogalmazását.

### 3.3 Forrás és evidencia nem ugyanaz

```text
forrás
!= evidencia
```

A forrás megmutatja egy állítás vagy követelmény eredetét, szakmai alapját vagy provenance-ét.

Az evidencia azt mutatja meg, hogy egy konkrét rendszer, képesség vagy eljárás esetében mi figyelhető meg, mérhető meg vagy ellenőrizhető.

Egy tekintélyes forrás önmagában nem bizonyítja, hogy egy konkrét rendszer teljesíti a követelményt.

### 3.4 Az ellenőrizhetőség nem jelent szükségképpen nyilvánosságot

A követelményeknek ellenőrizhetőknek kell lenniük, de ebből nem következik, hogy minden releváns evidencia korlátozás nélkül nyilvános lehet.

Minősített, biztonságérzékeny vagy más jogszerűen korlátozott információnál az ellenőrizhetőséghez megfelelő jogosultságú, dokumentált ellenőrzési út szükséges.

```text
ellenőrizhetőség
!= teljes nyilvánosság
```

### 3.5 Normál működés önmagában nem elég

Ahol a funkció kritikussága indokolja, a követelménynek a normál működés mellett a degradált, helyettesítő és helyreállítási működésre is ki kell terjednie.

A részletes state-function coverage szabályokat a `state-function-completeness.md` rögzíti.

## 4. Public minimum schema

Az `Alapok` egyedi követelményeinek alapértelmezett nyilvános szerkezete:

```text
ID
ÁLLÍTÁS
KÖVETELMÉNY
EVIDENCIA
MÉRCE
TESZT
FAILURE CONDITION
FORRÁS
STATUS
```

A schema célja nem a bürokratikus teljesség, hanem az, hogy a szakmai állítások ellenőrizhető formában legyenek vitathatók és javíthatók.

Egy korai draft tartalmazhat hiányzó mezőt, de a hiányt láthatóan kell jelölni. Hiányzó teszt vagy evidencia nem tehető úgy láthatatlanná, mintha a követelmény már bizonyított lenne.

A mezők részletes jelentését a `kovetelmeny-evidencia-teszt.md` rögzíti.

## 5. Belső részletesség és nyilvános egyszerűség

Egyes témák elemzéséhez a public schemánál több mezőre lehet szükség, például:

- scope;
- state function / sovereign capability;
- authority / legal basis;
- rationale;
- threat / failure model;
- normal mode;
- degraded mode;
- emergency substitution;
- recovery priority;
- physical dependencies;
- jurisdictional dependencies;
- secrecy / disclosure boundary;
- counterevidence / limits;
- implementation options;
- provenance.

Ezek hasznos elemzési koordináták, de nem cél, hogy minden nyilvános hozzájárulást már az első lépésben egy nehéz, teljes belső sablon kitöltésére kényszerítsünk.

```text
public schema
    = minimális közös ellenőrizhetőségi felület

részletes elemzés
    = szükség szerint bővíthető
```

## 6. Kanonikus helyek

A szakmai követelmény és annak részletes leírása az `alapok` repositoryban él.

A Manifesto rövid állításai a `manifesto` repositoryban élnek.

A governance és a közös hozzájárulási szabályok kanonikus helye a `digitalis-bizalom/.github` repository.

A presentation surface-ek — organization profile vagy későbbi weboldal — ezeket bemutathatják és linkelhetik, de nem hoznak létre külön, eltérő normatív példányt.

## 7. Nyitott módszertan

A módszertan maga is verziózott és javítható.

Új követelmény, ellenpélda vagy teszttapasztalat visszahatással lehet:

- egy mércére;
- egy tesztre;
- egy követelmény megfogalmazására;
- egy domain határára;
- vagy akár egy Manifesto-állítás pontosítására.

A cél nem egy egyszer lezárt checklist, hanem olyan szakmai rendszer, amelyben a követelmények és a bizonyításuk módja nyilvánosan vitatható, tesztelhető és javítható.
