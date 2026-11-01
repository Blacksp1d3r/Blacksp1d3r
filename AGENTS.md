## Projectoverstijgende eigenaarsregel — code die je kunt leren lezen (2026-11-01)

**Vanaf nu voor alle nieuwe en substantieel aangepaste code:** elk menselijk onderhouden bronbestand heeft een duidelijke titel, doel en korte uitleg van de werking, aanroepers/afhankelijkheden en belangrijke risico's; belangrijke functies en complexe blokken verklaren invoer, uitvoer en *waarom*. Schrijf begrijpelijk Nederlands waar mogelijk, verklaar vaktermen kort, houd commentaar waarheidsgetrouw en compact. Vereenvoudig en orden code als tests bewijzen dat functionaliteit, beveiliging, API's, servicebindings en rollback gelijk blijven. **Geen massale legacy-herschrijving of automatische serververwijdering.** Back-ups, uploads, laatste installateurs, actieve releases en herstelpunten blijven beschermd; onbekend = behouden. Respecteer bestaande projectclaims en CI. Volledige projectoverstijgende roadmap: [CODE_CLARITY_SERVER_CLEANUP_ROADMAP.md](CODE_CLARITY_SERVER_CLEANUP_ROADMAP.md). Deze aanvulling vervangt geen bestaande veiligheids- en toolblokkeringsregels.

# AGENTS.md — werkafspraken bij technische toolblokkades

## Eigenaarsregel — directe operatoruitvoering (2026-10-31)

Deze afspraak geldt voor alle huidige en toekomstige chats en agents in dit project. De canonieke standaard is `/Standards/MASTER_AI_ENGINEERING_SESSION_HANDOFF_PROTOCOL.md` v1.7, §0 en §0.1.

Als een geautoriseerde, op zichzelf toegestane taak door een technische ChatGPT-/OpenAI-/connectorblokkade faalt: leg de originele geredigeerde fout vast als `TOOL_BLOCK_V1`, controleer of de actie niet alsnog (gedeeltelijk) gelukt is, en geef **direct** een volledig, uitvoerbaar commando of script waarmee de eigenaar de actie via zijn bestaande geautoriseerde terminal zelf kan uitvoeren. Vermeld doelserver, gebruiker, terminal, voorwaarden, eventuele wijzigingsimpact, verwachte uitvoer, herstelmaatregelen en readback. Wacht daarna uitsluitend op de echte operatoruitvoer; hervat vanaf het bewezen resultaat en vermijd herhaalde analyses of overdrachten. Een aangereikt commando is geen bewijs van uitvoering.

Dit is geen toestemming om een inhoudelijk verboden veiligheidsactie te omzeilen, toegang uit te breiden of nieuwe tunnels/privilegeroutes te creëren. Vereiste beveiligings-, herstel- en goedkeuringsgrenzen blijven gelden.
