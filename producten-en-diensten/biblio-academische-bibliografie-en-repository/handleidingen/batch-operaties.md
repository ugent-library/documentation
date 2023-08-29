---
description: 'Batch operaties: records in bulk aanpassen voor BKT bibliotheekmedewerkers'
---

# Batch operaties

## Doel

**Batch update publications** laat je in bulk informatie toevoegen aan records.

<figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 09.31.16 (1).png" alt=""><figcaption><p>Screenshot van test omgeving</p></figcaption></figure>

Je kan meerdere records tegelijk bewerken. Een actie per regel per record, bijvoorbeeld:

/

_Voorlopig enkel beschikbaar voor publicaties. Wanneer een bulk operatie nodig is voor datasets, kunnen we de functionaliteit uitbreiden._

## Algemene principes

De batch operaties zijn opgebouwd uit 3 onderdelen:

1. **Record nummer**\
   `01H25B3813V9YV613A27TVH9SV`\
   `8701504`\

2. **Metadata veld + actie**\
   `keyword.add`\
   vb. vabb\_year, project, keyword, classification, reviewer\_tag\
   \
   `classification.set`\
   vb. set (instellen voor classificatie)\
   vb. add (toevoegen voor project, keywords, reviewer\_tag, vabb\_year)\
   vb. remove (verwijderen keywords, reviewer\_tag)\
   \
   **Tip:** Aan elkaar vast met een punt tussen. Hier mogen geen in spaties staan.\

3. **Waarde voor veld**\
   vb.  `A2` of  `2023`\
   vb.  `dna,"double helix"` (enkel meerdere waarden mogelijk voor keywords)

Je plakt het commando eenvoudig aan elkaar met komma's:

`8701504,project.add,2345`

## Voorbeelden batch operaties

* 8701504,project.add,2345&#x20;
* 8701504,vabb\_year.add,2023&#x20;
* 8701504,classification.set,A2&#x20;
* 8701504,keyword.add,dna,"double helix"&#x20;
* 8701504,keyword.remove,dna&#x20;
* 8701504,reviewer\_tag.add,esci&#x20;
* 8701504,reviewer\_tag.remove,esci
* 8701504,journal\_title.set,"my journal"
* 8701504,journal\_abbreviation.set,"my journal abbreviation"
* 8701504,isbn.add,"0268-1161" 1234,isbn.remove,"0268-1161"
* 8701504,eisbn.add,"0268-1161" 1234,eisbn.remove,"0268-1161"
* 8701504,issn.add,"0268-1161" 1234,issn.remove,"0268-1161"
* 8701504,eissn.add,"0268-1161" 1234,eissn.remove,"0268-1161"

🚨 Niet elke operatie werkt voor elk type publicatie, de velden moeten beschikbaar zijn.

### Projecten toevoegen

8701504,`project.add`,001D04503

### VABB jaar toevoegen

Toevoegen: 8701504,`vabb_year.add`,2023

### Keywords toevoegen en verwijderen

Toevoegen: 8701504,`keyword.add`,dna,"double helix"\
Verwijderen: 8701504,`keyword.remove`,dna

_Je kan meerdere keywords tegelijk toevoegen met een komma. Keywords met een spatie tussen kan je toevoegen door er aanhalingstekens rond te zetten._

Tips:

* Gebruik **aanhalingstekens** om **keywords met spaties** toe te voegen.
* Gebruik **komma's** om **meerdere keywords** toe te voegen aan een record.

### Classificaties instellen

Instellen: 8701504,`classification.set`,A2

### Reviewer tags toevoegen en verwijderen

Toevoegen: 8701504,`reviewer_tag.add`,esci\
Verwijderen: 8701504,`reviewer_tag.remove`,esci

### Journal title toevoegen

Toevoegen: 8701504,`journal_title.set`,"my journal"

### Journal abbreviation toevoegen

Toevoegen: 8701504,`journal_abbreviation.set`,"my journal abbreviation"

### ISBN, eISBN, ISSN, eISSN title toevoegen en verwijderen

#### ISBN

Toevoegen: 8701504,`isbn.add`,"0268-1161"\
Verwijderen: 8701504,`isbn.remove`,"0268-1161"

#### eISBN

Toevoegen: 8701504,`eisbn.add`,"0268-1161"\
Verwijderen: 8701504,`eisbn.remove`,"0268-1161"

#### ISSN

Toevoegen: 8701504,`issn.add`,"0268-1161"\
Verwijderen: 8701504,`issn.remove`,"0268-1161"

#### eISSN

Toevoegen: 8701504,`eissn.add`,"0268-1161"\
Verwijderen: 8701504,`eissn.remove`,"0268-1161"

### _Wat is er nog mogelijk?_

Wanneer je een concrete batch operatie nodig hebt die vaak nodig is, die hier niet beschreven staat, laat zeker weten wat je nodig hebt aan Miet.&#x20;

## Maak het jezelf gemakkelijk

Gebruik deze excel sheet om je operaties mee op te bouwen:

{% file src="../../../.gitbook/assets/batch-operaties-publicaties-voorbeeld.xlsx" %}

1.  **Voeg al je record nummers, metadata velden + acties en waarden toe aan de excel sheet.**\
    Maximum 500 regels.\


    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.37.26.png" alt=""><figcaption></figcaption></figure>
2.  **Kopieer de velden.**\
    Zonder de hoofdingen.\


    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.37.48.png" alt=""><figcaption></figcaption></figure>
3.  **Plak in het "Operations" veld.**\


    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.40.09.png" alt=""><figcaption></figcaption></figure>
4.  Klik op Process\


    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.41.35.png" alt=""><figcaption></figcaption></figure>

    Als er iets niet lukt, zie je dat ook:\


    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.57.29.png" alt=""><figcaption><p>Let op; in je excel kan het nummer van je regel verschillen.</p></figcaption></figure>
5.  Bekijk je resultaat in het record\
    ![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.43.15.png>)\
    ![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.44.23.png>)\
    ![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.43.45.png>)\
    ![](<../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.43.05.png>)

    <figure><img src="../../../.gitbook/assets/Scherm­afbeelding 2023-06-05 om 11.43.39.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Opgelet!**\
Excel begint je regels te tellen vanaf lijn 2.\
De batch operatie begint te tellen vanaf lijn 0.\
\
Als er een fout gesignaleerd wordt met "could not process publication at line 0" betekent dit lijn 2, "could not process publication at line 2" betekent dit lijn 4.
{% endhint %}

{% hint style="success" %}
Probeer de batch operaties zeker eens uit op onze testomgeving: [https://backoffice.bibliotest.ugent.be/publication/batch](https://backoffice.bibliotest.ugent.be/publication/batch) – hier kan je niet stuk maken!
{% endhint %}
