# Projectoverstijgende roadmap — Server-Aware AI Code Cleaner & uitlegbare code
**Versie:** 1.0 · **Datum:** 2026-11-01 · **Eigenaar:** Blacksp1d3r · **Status:** norm voor nieuwe code vanaf opname in de repository; serveronderzoek en opschoning alleen na afzonderlijke kwalificatie.

## 0. Missie
Iedere repository bevat begrijpelijke, logisch geordende, onderhoudbare code. De projecteigenaar leert programmeren door elk bestand te openen en in normale taal te kunnen lezen: **wat is dit, waarom bestaat het, hoe werkt het en waar wordt het gebruikt?** De AI mag vereenvoudigen, duplicatie en omwegen wegnemen, logische mappen en namen voorstellen, code documenteren, afhankelijkheden in kaart brengen en bewezen overbodige serverartefacten veilig opruimen. **Geen functionaliteitsverlies, geen automatische destructieve serveractie, geen extra platform.**

Dit is een **cross-project norm**, geen nieuw centraal controlepaneel of tweede task/issue/inventory-databank. De bestaande `AGENTS.md`, projectroadmaps, source-of-truth, CI, issueclaims, bevoegdheden, geheimenregels en rollback blijven leidend voor project-specifieke details. `computer-cleaner` heeft een andere bestaande missie (persoonlijke Windows-diskcatalogus); deze roadmap verruimt zijn persoonlijke-scanmachtigingen niet.

## 1. Onmiddellijk verplicht voor nieuwe of substantieel gewijzigde code (Q0)
Vanaf merge van de lokale `AGENTS.md`-verwijzing in een repository:
1. **Bestandskop** bij elk *nieuw* menselijk onderhouden bronbestand (Python, JS/TS, shell, HTML, CSS, SQL, configuratie waar commentaar is toegestaan): **titel/bestandsnaam, doel in gewone taal, werking in 2–5 zinnen of stappen, belangrijkste invoer/uitvoer, wie het aanroept of waar het start, belangrijke afhankelijkheden en neveneffecten/risico's**. Vermeld 'onbekend' in plaats van afhankelijkheden te verzinnen. Voeg niets toe vóór verplichte shebang, encoding, XML-declaratie, `'use strict'`, licentie, of syntactisch vereiste directive; respecteer parser/formatter.
2. **Belangrijke functies, klassen en niet-evidente blokken** krijgen een docstring/compacte toelichting: wat, waarom, argumenten, resultaat, relevante fouten/neveneffecten en eventuele veiligheidsgrens. Leg complexe beslissingen uit; herhaal niet elke code-instructie. Gebruik duidelijke, consistente namen, kleine functies en logische modulegrenzen.
3. **Taal voor lerende eigenaar:** uitleg bij voorkeur in begrijpelijk Nederlands; API-contracten/extern gebruikte symbolen en vastliggende Engelstalige conventies blijven intact. Eerste gebruik van jargon kort verklaren, voorbeeld indien behulpzaam; geen misleidende zekerheid. Een codebestand moet zonder extra AI-chat al leerbaar zijn.
4. **Bij substantieel aangepaste bestaande bestanden:** actualiseer minimaal hun bestandskop en de gewijzigde logica. **Geen massale commentaar-only rewrite** van werkende legacy code om de regel op dag één te halen. Op termijn geleidelijke, afzonderlijke backfill.
5. **Automatische bestanden uitgezonderd:** generated code, bundels, lockfiles, minified code, binary/media, vendored dependencies, vertalingsdata en syntactisch commentaar-onmogelijke formaten. Documenteer functie in de eigenaarbron of nabije README. Geheimen, persoonlijke paden, IP's, private infrastructuur en credentials nooit in commentaar/PR plaatsen.
6. **PR-acceptatie meteen:** reviewer/agent bevestigt kop, relevante functieuitleg, codehelderheid, tests en geen gedragsbreuk. Waar passend formatter/lint met lokale bestaande tool; geen globale strengere CI-gate vóór baseline en testbewijs. Geen permanente verplichte extra AI-review of wachttijd.

### Voorbeeld Python
```python
"""Schijfruimtecontrole.

Doel: lees hoeveel vrije ruimte op een bestaand bestandssysteem beschikbaar is.
Gebruik: monitoring roept `vrije_ruimte_gb(pad)` aan; er worden geen bestanden gewijzigd.
Afhankelijkheid: standaardbibliotheek `shutil`.
"""

import shutil

def vrije_ruimte_gb(pad: str) -> float:
    """Geef vrije gigabytes terug; een ongeldig pad geeft een OS-fout."""
    return shutil.disk_usage(pad).free / (1024 ** 3)
```
De kop is *niet* bedoeld als bureaucratisch sjabloon: pas lengte aan modulecomplexiteit aan en documenteer echte werking. Functionele waarheid gaat boven fraaie commentaar.

## 2. Werkregels: vereenvoudigen zonder omwegen of regressies
- Zoek echte duplicatie, redundante wrappers, onnodige indirecties, dode vertakkingen en onduidelijke namen; maak de kleinste gecontroleerde patch die dezelfde functie behoudt.
- **Bewijslast vóór verwijderen/verplaatsen:** code search + runtime aanroepketen + import-/config-/systemd-/cron-/timer-/CLI-/installer-/webhook-/CI-/deployment-/rollback-referenties; dynamische imports, reflectie en configuratie worden expliciet onderzocht. Alleen 'niet gevonden met grep' is geen bewijs.
- Vastliggende externe API's, databankschema's, routes, CLI's, URL's, servicepaden, securitychecks, lease/fencing, auth en compatibiliteit alleen wijzigen via bestaande projectmigratiegates. Een omweg kan bewust een veiligheidsgrens zijn.
- Kleine PR's per logisch component, relevante unit- en integratietests, negatieve regressietests, documentatie en traceerbare voor/na-vergelijking. Bij onzekerheid voorlopig behouden; geen herformatteer-PR tegelijk met semantische refactor.
- Geen onnodige afhankelijkheden, betaalde producten, nieuw modelplatform, nieuwe service, relay of controller. Hergebruik Runner-MCP, Runner-Fabric, Claude/Qwen waar bevoegd en bewezen.

## 3. Serverbewuste inventaris en bescherming
De AI analyseert **eerst read-only** per expliciet geautoriseerde originele host/UID:
- huidige services/user-units, actuele processen, poorten, `ExecStart`, importeerbare werkelijke code/wheel, crontabs, systemd timers, runners, pipelines, scripts, runtime/log/config en afhankelijkheden;
- bestaande centrale AIfordable infrastructuurregistry/topology, eigenaar, daadwerkelijke bronrevisie, release-slots, symlinks en relevante monitoring, zonder tweede authority;
- installaties, downloads, staging, uploadhistoriek, operator-scripts, data, herstelpunten en back-ups; categoriseer op **feitelijke functie en herkomst** in plaats van naam, leeftijd of mtime.

**Bescherm altijd:** back-ups en herstelkopieën, actieve en laatst werkende rollbackrelease, installatie- en geüploade bronartefacten die voor herstel/forensiek nodig kunnen zijn, databases en journal/WAL, logs die nodig zijn voor audit, uploads en gebruikersbestanden, private tokens/omgeving, symlinks met onzekere bestemming, migratiebestanden en onduidelijke eigenaar. Geen automatische delete/move/rename/permission-change hierop. Bewaar bestaande bewaartermijnen en wettelijk/auditplichtige gegevens.

**Classificatie per kandidaat:** `ACTIVE`, `DEPENDENCY`, `ROLLBACK_REQUIRED`, `BACKUP_OR_UPLOAD`, `USER_DATA`, `FORENSIC_OR_AUDIT`, `POSSIBLY_UNUSED`, `VERIFIED_UNUSED`, `UNKNOWN`. Elke classificatie vermeldt bewijsbron, tijd/generatie, juiste machine/UID, verwijzingen, gevolgen, herstelwijze en wie het heeft goedgekeurd. `UNKNOWN` = **houden**. De agent mag geen absolute zekerheid claimen uit louter statische code-analyse.

**Toegang:** ruim genoeg voor *geautoriseerde* inspectie op de originele server, maar **niet één permanent onbeperkt rootaccount**. Read-only inventaris via bestaande rechten; specifieke afgeschermde inspecties op eigenaarssessie; pas voor een afzonderlijk goedgekeurde verandering tijdelijke minimale schrijfrechten. Nooit generieke root, privématerialen naar modellen sturen of toolbeveiliging omzeilen.

## 4. Verwijderproces (standaard uitgeschakeld)
1. **Rapport, niet wissen:** toon exacte kandidaten en reden, impact en herstelplan. Werk in de bestaande issue/handover; geen parallelle cleanup-database.
2. **Onafhankelijke dependencycontrole:** geen live proces, startup, call-site, installer, CI, backup, rollback, audit of klant-/gebruikersdata nodig. Verifieer oorspronkelijke UID/host, symlink/mount/device, versheid en hashes waar gepast.
3. **Herstelbare quarantaine** uitsluitend voor vrijgegeven tijdelijke artefacten op hetzelfde toegestane bestandssysteem, met manifest en TTL die uitdrukkelijk is goedgekeurd; nooit automatisch voor back-ups/uploads/laatste installateurs. Snapshot/backup op zichzelf is geen verwijdertoestemming.
4. **Bewijs van normaal draaien:** functionele tests, restart/boot- en monitorgedrag (waar relevant), geen dubbele scheduler, gecontroleerde readback, echte rollbackproef.
5. **Definitieve verwijdering** pas na expliciet project-/hostgericht besluit en passende retentie. Onzeker/onbereikbaar/geen herstel -> `WAIT`, niets wijzigen.
6. Geen recursive wildcard cleanup, geen `rm -rf`-advies als generieke uitvoeringsroute; staging of gemergde bron != gedeployde code. Niet alle servers tegelijk.

## 5. Volledige roadmap en meetbare acceptatie
| Fase | Prioriteit | Werk | Bewijs / definitie gereed |
| --- | --- | --- | --- |
| **Q0 — Nu** | P0 (nieuwe code) | Deze norm in root `AGENTS.md` per actief project; nieuwe/gewijzigde bron onmiddellijk uitleggen en helder indelen | Rootregel via PR gemerged; nieuwe bestanden met accurate kop en relevante functiedocs; geen bestaande code- of servermutatie vereist |
| **Q1 — Normen en voorbeeldbank** | P1 | 1 lichte commentaarconventie per taal: Python docstring; JS/TS JSDoc; shell na shebang; SQL `--`; CSS/HTML veilige kop; configs in README waar geen comments | Syntax/lint/build op voorbeeldbestanden PASS; didactisch leesbaar voor beginnende eigenaar; uitzonderingslijst getest |
| **Q2 — Source-kaart** | P1 | Repositories, bestaande docs, entrypoints, callgraph, importgraph, hergebruik/dupliceer-kandidaten; benoem ieder onderdeel | Per repo componentkaart in bestaande docs/handover en brongebonden referenties; geen secrets, geen verzonnen dependencies |
| **Q3 — Server-runtime-kaart** | P1 na bevoegdheid | Read-only exacte host/proces/service/cron/systemd → bronconfig/slots → deployment en recovery | Echte hostidentiteit, processen, starters, dependents, bewijsversheid en beschermde artefacten; onduidelijk = UNKNOWN |
| **Q4 — Linter/checker op gewijzigde code** | P1 | Reeds beschikbare Ruff/Biome/ESLint/testtools hergebruiken; commentaarcheck op *nieuwe/gewijzigde* onderhouden bron, uitzonderingen expliciet | CI checkt uitsluitend nieuwe scope zonder legacy massafail; faux-file/false-positive en syntax negative tests |
| **Q5 — Veilige refactor** | P2 | Per klein component duplicatie, onnodige omwegen en layout verbeteren; uitleg actualiseren | Behaviortests, imports/CLI/API/security/rollback contract behouden, gericht PR, groene CI; rollback van patch mogelijk |
| **Q6 — Historische code documenteren** | P2 incrementeel | Bij aanraken oud bestand uitleg aanvullen; per component review van werkelijk gedrag, geen gokken | Dekking per repo aantoonbaar stijgend; semantische comments actueel; geen grote noisy rewrite |
| **Q7 — Opschoonkandidaten rapporteren** | P2 | Serverartefacten classificeren; referenties, back-ups, uploads en installateurs onderscheiden | Read-only, operatorrapport met exacte kandidaten, NONE DELETED; negatieve tests voor beschermde bestanden |
| **Q8 — Canary-quarantaine en herstel** | P3 | Eén aantoonbaar onschuldig, klein niet-productieartefact op goedgekeurde originele host | Exacte toestemming, quarantaine/restore, relevante functionele test PASS, 0 back-ups of uploads aangeraakt |
| **Q9 — Gecontroleerde per-host uitbreiding** | P3 | Eén eigenaar en rol tegelijk, herstel- en monitoringcontroles, expliciet vrijgegeven opruimacties | Nooit auto-delete, geen serviceuitval/dataverlies, audit en recovery; bewijs in bestaande handover |
| **Q10 — Doorlopend onderhoud** | P3 | Na nieuwe release lint/learn/artefactrapport en kleine onderhouds-PR's; latere opruimvensters | Geen extra modelkosten standaard, baseline blijft groen, bestaande projectworkflow leidt, geen duplicaatplatform |

**Fases zijn geen voorwaarde om Q0 te starten.** Legacy-backfill en server-deletions wachten op hun eigen bewijslast; nieuwe code hoeft niet te wachten op F18 of historische sanering. De bestaande F18/SQL eerste echte ACK en de productieprojecten blijven eigenaar van hun P0. Een bronbestand-op-branch voldoet niet aan Q0 op default branch zolang de PR niet gemerged is.

## 6. Uitrol per repository
- Iedere bestaande actieve repository behoudt haar eigen `AGENTS.md` in de root, bestaande roadmap, CI en handover. Plaats daar de **korte bindende Q0-regel** en deze canonieke link; overschrijf nooit eerdere projectbesluiten.
- Rootregel geldt voor nieuwe/aangepaste code direct **na merge**. Werkende legacy-onderdelen worden niet mechanisch herschreven. De veilige standaard geldt voor toekomstige projecten als onderdeel van hun bootstrap.
- Per repo eigen issue/PR of bestaand onderhoudsissue volgens lokale policy; geen massale merge zonder vereiste CI. Voor lopende exclusieve claims en F18-workunits: vermijd dezelfde bestanden in parallel.
- Repos met alleen documentatie: pas Q0 toe zodra er broncode bijkomt. Lege test-repo zonder rootbron blijft buiten automatische uitrol.

## 7. Educatieve gebruikerservaring
Bij het openen van een bronbestand moet zonder chat duidelijk zijn: **(a)** titel en doel, **(b)** wat het bestand start/aanroept, **(c)** welke invoer en uitvoer, **(d)** welke functies of stappen er zijn, **(e)** welke risico's en beveiligingen. Voor ingewikkelde code mag een eenvoudig gebruiksvoorbeeld of schematische ASCII-flow helpen. Niet meer dan nodig; onbekend eerlijk vermelden; moeilijke termen in Nederlands uitleggen. Code en uitleg veranderen samen; een AI mag onjuiste comments nooit als bewijs gebruiken voor runtimegedrag.

## 8. Grenzen en eigenaarschap
- Geen autonome breedmachtige productie-opruimagent, nieuwe privileges, credentialkopieën of extra publieke infrastructuur.
- Geen destructieve opruimtaak op `github-runner`, `aifordable-lab`, `black`, `blacky`, VPS of persoonlijke Windows-schijven op basis van dit document alleen.
- Respecteer A7 zesrol-cron/rollback en #866 cron→systemd fase; bron-/service-/live-release-proof zijn verschillende feiten.
- Geen AI-verzonnen runtimefeiten of impliciete acceptatie van ongeteste schema/API/datawijzigingen.
- Bij conflict wint de specifieke bestaande veiligheidsgrens; registreer conflict in bestaande issue en kies veilig onafhankelijk werk.

## 9. Eenvoudige controlevragen voor elke PR
**Wat doet het bestand? Waarom bestaat deze functie? Waar wordt het aangeroepen? Kan het simpeler zonder andere werking? Welke tests bewijzen dat? Wat gebeurt er bij fouten? Heeft het effect op data, auth, service of herstel? Is uitleg tegelijk bijgewerkt?**
