---
description: 'Batch operaties: records in bulk aanpassen voor BKT bibliotheekmedewerkers'
---

# Batch operaties

## Doel

De batch operations view geeft je de optie om in bulk informatie toe te voegen aan records.

Voorlopig enkel voor publicaties.

<figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 09.31.16 (1).png" alt=""><figcaption><p>Screenshot van test omgeving</p></figcaption></figure>

## Algemene principes

De batch operaties zijn opgebouwd uit 4 onderdelen:

1. **Record nummer**\
   `01H25B3813V9YV613A27TVH9SV`\
   `8701504`
2. **Metadata veld + actie**\
   `keyword.add`\
   vb. vabb\_year, project, keyword, classification, reviewer\_tag\
   \
   `classification.set`\
   vb. set (instellen voor classificatie)\
   vb. add (toevoegen voor project, keywords, reviewer\_tag, vabb\_year)\
   vb. remove (verwijderen voor project, keywords, reviewer\_tag)\

3. **Waarde voor veld**\
   vb.  `A2` of  `2023`\
   vb `dna,"double helix"` (enkel meedere waarden voor keywords)

Je plakt het commando aan elkaar met komma's:

`8701504,project.add,2345`

## Voorbeelden batch operaties

* 8701451,project.add,2345&#x20;
* 8701451,vabb\_year.add,2023&#x20;
* 8701451,classification.set,A2&#x20;
* 8701451,keyword.add,dna,"double helix"&#x20;
* 8701451,keyword.remove,dna&#x20;
* 8701451,reviewer\_tag.add,esci&#x20;
* 8701451,reviewer\_tag.remove,esci

### Projecten toevoegen

8632074,project.add,001D04503

Metadataveld: `project`

Acties: `.add` of `.remove`

### VABB jaar toevoegen

8632074,vabb\_year.add,2023

Metadataveld: `vabb_year`

Acties: `.add` of `.remove`

### Keywords toevoegen en verwijderen

8632074,keyword.add,dna,"double helix"\
8632074,keyword.remove,dna

Metadataveld: `keyword`

Acties: `.add` of `.remove`

Tips:

* Gebruik **aanhalingstekens** om **keywords met spaties** toe te voegen.
* Gebruik **komma's** om **meerdere keywords** toe te voegen aan een record.

### Abstracts en taal toevoegen

_In opbouw_

### Classificaties toevoegen

8632074,classification.set,A2

Metadataveld: `classification`

Acties: `.set`

### Reviewer tags toevoegen en verwijderen

8632074,reviewer\_tag.add,esci\
8632074,reviewer\_tag.remove,esci

Metadataveld: `keyword`

Acties: `.add` of `.remove`

## Maak het jezelf gemakkelijk

Excel

{% hint style="success" %}
Probeer de batch operaties zeker eens uit op onze testomgeving: [https://backoffice.bibliotest.ugent.be/publication/batch](https://backoffice.bibliotest.ugent.be/publication/batch) – hier kan je niet stuk maken!
{% endhint %}
