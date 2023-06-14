---
description: >-
  Af en toe werken DOI imports niet. Hier vind je wat je kan doen wanneer dit
  gebeurt.
---

# Help, deze DOI werkt niet

## Context

De metadata die binnengetrokken wordt in Biblio via DOI, verloopt via twee diensten: [Crossref](https://www.crossref.org) (publicaties) en [DataCite](http://datacite.org) (datasets). Dat zijn twee betrouwbare bronnen waar we informatie mee kunnen uitwisselen.

Je kan altijd checken of een DOI werkt, door de Crossref of DataCite website te gebruiken:

* Crossref: api.datacite.org/dois/plak-hier-de-DOI
* DataCite: api.crossref.org/works/plak-hier-de-DOI

Wanneer het niet werkt, zijn er twee redenen:

### Reden 1: nog niet actief

Soms duurt het even voor een DOI die via deze diensten komt actief wordt. Je kan dan later nog eens proberen.

#### Oplossing

Even wachten tot de DOI actief is.

### Reden 2: DOI van een onbetrouwbare bron

Buiten Crossref en DataCite zijn er nog bronnen die een DOI aanbieden. Dat zijn bijvoorbeeld onafhankelijke publicatiehuizen. Dat zijn geen betrouwbare bronnen, die andere regels en contracten hanteren om informatie van binnen te trekken. Deze informatieuitwisseling kunnen we niet duurzaam implementeren.

#### Oplossing

Indien de onderzoeksoutput niet terecht kan komen op een DOI die door Crossref of DataCite erkent kan worden, kunnen ze&#x20;

* Importeren via BibTex of WoS indien beschikbaar
* Manueel aanvullen

Voorbeeld DOI die niet werkt:

Van een onafhankelijk publicatiehuis

* 10.2143/TVF.84.3.3291503
* Plak de DOI achter api.crossref.org.works en zie dat de DOI niet werkt: [https://api.crossref.org/works/](https://api.crossref.org/works/10.2143/TVF.84.3.3291503)[10.2143/TVF.84.3.3291503](https://api.crossref.org/works/10.2143/TVF.84.3.3291503)![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-14 om 14.41.53.png>) of![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-14 om 14.42.25.png>)

## Wat gaan we doen in Biblio?

We gaan ervoor zorgen dat we herkennen wanneer de DOI niet herkent wordt door Crossref of DataCite.

### Publicatie voorstel

"This DOI cannot be found in CrossRef, or is not yet active. Please make sure your DOI is recognised by this trusted party. You can also import your publication via an other service like WoS or BibTex or manually add your publication.”

### Dataset voorstel

“This DOI cannot be found in Datacite, or is not yet active. Please make sure your DOI is recognised by this trusted party, or manually add your dataset.”

