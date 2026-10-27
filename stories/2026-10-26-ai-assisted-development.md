# 656 GitHub-pullrequests op één dag — bouwen aan AI-ondersteunde softwareontwikkeling

*27 oktober 2026 · Een praktijkexperiment, geen afgewerkt product*

Op **26 oktober 2026 (UTC)** werden er in de GitHub-repositories onder **Blacksp1d3r** **656 pull requests aangemaakt**. Daarvan werden **557 PR's zowel aangemaakt als gemerged op diezelfde dag**. Over de volledige dag waren er **561 merges**, inclusief PR's die eerder waren aangemaakt.

Dat is een opvallend resultaat, maar het belangrijkste verhaal gaat niet over het aantal PR's.

## Wat ik probeer te bouwen

Met **AIfordable** en **Runner-Fabric** experimenteer ik met een infrastructuur waarin één ontwikkelaar AI-agents, eigen rekenkracht, testprocessen en ontwikkeltaken kan coördineren.

De ambitie: een ontwikkelketen waarin taken steeds zelfstandiger worden uitgevoerd, resultaten controleerbaar zijn en het werk op andere onafhankelijke taken kan doorgaan wanneer één onderdeel vastloopt.

**De volledige autonome ontwikkelketen is nog niet af of bewezen.** Er zijn menselijke tussenkomsten, CI-wachtrijen en technische beperkingen. Dat hoort bij de huidige stand van het experiment.

## De les: niet elke controle mag een blokkade worden

Een belangrijke uitdaging blijkt de balans tussen **doorontwikkeling en veiligheid**.

Extra beveiligingswerk, documentatie, herhaalde controles of telkens nieuwe back-ups kunnen onbedoeld de hoofdontwikkeling vertragen. Daarom werk ik aan een meer proportionele aanpak:

1. **De noodzakelijke basis eerst.** Authenticatie, bescherming van secrets en gevoelige gegevens, essentiële tests en bescherming tegen kritieke of onomkeerbare fouten horen bij de minimale voorwaarden.
2. **Daarna blijft functionele ontwikkeling vooruitgaan.** Niet-kritieke bevindingen worden geregistreerd en ingepland, in plaats van automatisch alle voortgang te stoppen.
3. **Verdieping volgt gefaseerd.** Extra beveiliging, observability, optimalisatie en verdere automatisering krijgen een plek op de roadmap. Kritieke risico's worden onmiddellijk aangepakt.
4. **Een blokkade op één taak is geen blokkade voor het hele systeem.** Als CI of een afhankelijkheid wacht, kan een andere onafhankelijke taak verdergaan.

Het doel is niet om veiligheidsmaatregelen over te slaan, maar om ze **risicogericht, toetsbaar en proportioneel** in te zetten.

## Waarom deze cijfers interessant zijn — en wat ze níét aantonen

De PR-telling laat zien dat in deze ontwikkelomgeving op één dag veel wijzigingen konden worden voorbereid en verwerkt. Maar **meer PR's betekenen niet automatisch betere software**. Voor een sterkere evaluatie zijn ook tests, regressies, doorlooptijd, herstelwerk, aantoonbaar correct uitgevoerde taken en succesvolle deployments belangrijk.

De volgende stap is daarom niet alleen méér produceren, maar bewijzen dat de ontwikkelketen **betrouwbaar en met minder menselijke tussenkomst** kan functioneren.

## Bewijs en meetmethode

- [Dated evidence and methodology](../evidence/2026-10-26/README.md)
- [Machine-readable aggregate counts](../evidence/2026-10-26/counts.json)

De tellingen zijn uitgevoerd met de **GitHub Search API**, op basis van de **UTC-datum 26 oktober 2026**.

**Transparantie:** de cijfers omvatten ook private repositories. Bezoekers zonder toegangsrechten kunnen daarom het volledige totaal niet zelfstandig herhalen. Dit is geen geverifieerd wereldrecord en geen onafhankelijke kwaliteitsmeting.

---

## English summary

**656 pull requests were opened across repositories owned by Blacksp1d3r on 26 October 2026 (UTC); 557 were both opened and merged that day.**

This is part of an ongoing experiment with **AI-assisted software development**, combining coding agents, self-hosted compute resources and automated testing. The long-term goal is to make development workflows more autonomous without allowing non-critical reviews or administrative work to block all progress.

The system is **still under development**: some steps require human intervention, and CI queues and technical limitations remain. The principle is **minimum necessary safeguards first, continuous functional development next, and deeper hardening through planned follow-up work**, while addressing critical risks immediately.

These PR counts demonstrate activity, **not independently validated code quality, full autonomy or a world record**. The totals include private repositories, so public visitors cannot reproduce every result. [Evidence and methodology](../evidence/2026-10-26/README.md).
