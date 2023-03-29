---
description: >-
  Onze GRPC client is een krachtige command-line tool om in bulk records in
  Biblio aan te passen.
---

# GRPC

## Voordelen

### **Record- en metadata-beheer**

* **Records zoeken + ophalen**: eenvoudig filteren via JQ (JSON L) en zoeken via full text om records te vinden
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

****

Huidige status

* De web-app werkt voor Biblio "Bicli"
* De GRPC server werkt voor de client
  * Aparte binary, aparte naam&#x20;
* Test server beschikbaar
