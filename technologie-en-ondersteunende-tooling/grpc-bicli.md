---
description: >-
  Een GRPC client is een krachtige command-line tool waarmee je metadata in
  records in bulk kan aanpassen via API. De bicli client wordt gebruikt om in
  bulk records in Biblio aan te passen.
---

# GRPC "bicli"

## Voor wie

### Medewerkers in de Universiteitsbibliotheek Gent

Bicli bestaat in eerste instantie voor het technisch bibliotheekpersoneel dat records verwerkt, analyseert en bewerkt voor Biblio. Ontwikkelaars, analisten, reviewers en curatoren zijn de eerste doelgroep.

### Externe leesrechten

In latere fase kunnen partners en stakeholders die inzichten willen in de Biblio records gebruik maken van leesrechten die onze GRPC tooling kan aanbieden.&#x20;

## Voordelen

### **Record- en metadata-beheer**

* **Records zoeken, ophalen en bekijken**: eenvoudig filteren via JQ (JSON L) en zoeken via full text om records te vinden
* **Bewerken**: records openen en bewerken (manueel of met een scriptje).
* **Updaten**: veranderingen opslaan (doorsturen als JSON-L)\

* **Verwijderen** van records in bulk via JSON
* **Importeren** van records in bulk\

* **Verplaatsen** van records naar andere contributors
* **Koppelen** (en ontkoppelen) van files aan records

### **Geautomatiseerd kwaliteitsbeheer**

* **Clean-up** commando's uitvoeren op records (vb. Lege keywords, departementen koppelen aan contributors zonder affiliatie)
* **Valideren van records**: ontdekken welke velden fout zijn
* **Versiegeschiedenis** van records bekijken, verschillende versies vergelijken

## Vooruitgang

Bicli is in opbouw. De eerste mogelijkheden zijn uitgewerkt door en voor ontwikkelaars. Er is een testserver beschikbaar.

Acties te vinden in onze GitHub.
