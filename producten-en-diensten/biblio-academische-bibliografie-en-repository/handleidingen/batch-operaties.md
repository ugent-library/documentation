---
description: 'Batch operaties: records in bulk aanpassen voor BKT bibliotheekmedewerkers'
---

# Batch operaties

## Doel

**Batch update publications** laat je in bulk informatie toevoegen aan records.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-06-14 at 15.47.28.png" alt=""><figcaption><p>Screenshot van test omgeving</p></figcaption></figure>

_Voorlopig enkel beschikbaar voor publicaties. Wanneer een bulk operatie nodig is voor datasets, kunnen we de functionaliteit uitbreiden._

## Algemene principes

Met batch operaties kan je meerdere records tegelijk bewerken. Een actie per regel per record.

De batch operaties zijn opgebouwd uit 3 onderdelen:

1. **Record nummer**\
   `01H25B3813V9YV613A27TVH9SV`\
   `8701504`\

2. **Metadata veld + actie**\
   `add_keyword`\
   vb. vabb\_year, project, keyword, classification, reviewer\_tag\
   \
   `set_classification`\
   vb. set (instellen voor classificatie)\
   vb. add (toevoegen voor project, keywords, reviewer\_tag, vabb\_year)\
   vb. remove (verwijderen keywords, reviewer\_tag)\
   \
   **Tip:** Aan elkaar vast met een laag kastlijntje ( \_ ) tussen. Hier mogen geen spaties staan.\

3. **Waarde voor veld**\
   vb.  `A2` of  `2023`\
   vb.  `dna,"double helix"` (enkel meerdere waarden mogelijk voor keywords)

Je plakt het commando eenvoudig aan elkaar met komma's:

`8701504,add_project,2345`

## Voorbeelden batch operaties

* 8701504,add\_project,2345&#x20;
* 8701504,add\_vabb\_year,2023&#x20;
* 8701504,set\_classification,A2&#x20;
* 8701504,add\_keyword,dna,"double helix"&#x20;
* 8701504,remove\_keyword,dna
* 8701504,add\_reviewer\_tag,esci&#x20;
* 8701504,remove\_reviewer\_tag,esci
* 8701504,set\_journal\_title,"my journal"
* 8701504,set\_journal\_abbreviation,"my journal abbreviation"
* 8701504,add\_isbn,"0268-1161"
* 1234,remove\_isbn,"0268-1161"
* 8701504,add\_eisbn,"0268-1161"
* 1234,remove\_eisbn,"0268-1161"
* 8701504,add\_issn,"0268-1161"
* 1234,remove\_issn,"0268-1161"
* 8701504,add\_eissn,"0268-1161"
* 1234,remove\_eissn,"0268-1161"
* 8701504,set\_locked,true
* 8701504,set\_locked,false
* 8701504,set\_status,deleted
* 8701504,set\_status,private
* 8701504,set\_status,public
* 8701504,set\_status,returned



🚨 Niet elke operatie werkt voor elk type publicatie, de velden moeten beschikbaar zijn.

### Projecten toevoegen

8701504,`add_project`,001D04503

### VABB jaar toevoegen

Toevoegen: 8701504,`add_vabb_year`,2023

### Keywords toevoegen en verwijderen

Toevoegen: 8701504,`add_keyword`,dna,"double helix"\
Verwijderen: 8701504,`remove_keyword`,dna

_Je kan meerdere keywords tegelijk toevoegen met een komma. Keywords met een spatie tussen kan je toevoegen door er aanhalingstekens rond te zetten._

Tips:

* Gebruik **aanhalingstekens** om **keywords met spaties** toe te voegen.
* Gebruik **komma's** om **meerdere keywords** toe te voegen aan een record.

### Classificaties instellen

Instellen: 8701504,`set_classification`,A2

### Locking instellen

Instellen: 8701504,`set_locked`,true

Instellen: 8701504,`set_locked`,false

### Reviewer tags toevoegen en verwijderen

Toevoegen: 8701504,`add_reviewer_tag`,esci\
Verwijderen: 8701504,`remove_reviewer_tag`,esci

### Journal title toevoegen

Toevoegen: 8701504,`set_journal_title`,"my journal"

### Journal abbreviation toevoegen

Toevoegen: 8701504,`set_journal_abbreviation`,"my journal abbreviation"

### ISBN, eISBN, ISSN, eISSN title toevoegen en verwijderen

#### ISBN

Toevoegen: 8701504,`add_isbn`,"0268-1161"\
Verwijderen: 8701504,`remove_isbn`,"0268-1161"

#### eISBN

Toevoegen: 8701504,`add_eisbn`,"0268-1161"\
Verwijderen: 8701504,`remove_eisbn`,"0268-1161"

#### ISSN

Toevoegen: 8701504,`add_issn`,"0268-1161"\
Verwijderen: 8701504,`remove_issn`,"0268-1161"

#### eISSN

Toevoegen: 8701504,`add_eissn`,"0268-1161"\
Verwijderen: 8701504,`remove_eissn`,"0268-1161"

### Status van een record aanpassen

_Use it wisely ;-)_

**Set record to public**\
8701504,`set_status`,public\
⚠️ _een onvolledig record kan je niet op public zetten._

**Set record as draft**\
8701504,`set_status`,private

**Withdraw record**\
8701504,`set_status`,returned

**Delete record**\
8701504,`set_status`,deleted

### _Wat is er nog mogelijk?_

Wanneer je een concrete batch operatie nodig hebt die vaak nodig is, die hier niet beschreven staat, laat zeker weten wat je nodig hebt aan Miet.&#x20;

## Maak het jezelf gemakkelijk

Gebruik deze excel sheet om je operaties mee op te bouwen:

{% file src="../../../.gitbook/assets/batch-operaties-publicaties-voorbeeld.xlsx" %}

1.  **Voeg al je record nummers, metadata velden + acties en waarden toe aan de excel sheet.**\
    Maximum 500 regels.\


    <figure><img src="../../../.gitbook/assets/Screenshot 2024-06-14 at 16.37.07.png" alt=""><figcaption></figcaption></figure>
2.  **Kopieer de velden.**\
    Zonder de hoofdingen.\


    <figure><img src="../../../.gitbook/assets/Screenshot 2024-06-14 at 16.37.43.png" alt=""><figcaption></figcaption></figure>
3.  **Plak in het "Operations" veld.**\


    <figure><img src="../../../.gitbook/assets/Screenshot 2024-06-14 at 16.39.01.png" alt=""><figcaption></figcaption></figure>
4.  Klik op Process\
    \
    Je ziet wat er slaagt, en wat er mislukt.\


    <figure><img src="../../../.gitbook/assets/Screenshot 2024-06-14 at 16.39.38.png" alt=""><figcaption></figcaption></figure>
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
