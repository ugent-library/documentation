---
description: Hoe een BibTeX file omvormen tot iets dat Biblio (waarschijnlijk) begrijpt.
---

# Help, deze BibTeX file doet het niet

{% hint style="info" %}
BibTex is een formaat dat erg vrij geïnterpreteerd kan worden door verschillende software programma's. Dat zorgt ervoor dat Biblio niet altijd begrijpt wat er in de files staat die van verschillende plekken kan komen zoals andere universiteiten.
{% endhint %}

## Kies je bron goed

Biblio en Scopus begrijpen elkaar. Wanneer het kan, exporteer files van scopus om in Biblio te stoppen.

{% embed url="https://www.scopus.com/search/form.uri?display=basic#basic" %}

## Laat je files opkuisen

**Gebruik BibTeX Tidy** om de files op te kuisen voor files die niet in Scopus zitten en Biblio niet begrijpt.

1.  Open de file die je hebt gekregen in een text editor.

    _Notepad (Windows) of TextEdit (Mac). Vraag het ontwikkelteam om meer informatie als je je weg niet vindt._
2.  Kopieer de informatie en plak ze in BibTeX Tidy:\
    [https://flamingtempura.github.io/bibtex-tidy/index.html?opt=%7B%22modify%22%3Atrue%2C%22curly%22%3Atrue%2C%22numeric%22%3Atrue%2C%22months%22%3Afalse%2C%22space%22%3A2%2C%22tab%22%3Atrue%2C%22align%22%3A13%2C%22duplicates%22%3A%5B%22key%22%5D%2C%22stripEnclosingBraces%22%3Afalse%2C%22dropAllCaps%22%3Afalse%2C%22escape%22%3Afalse%2C%22sortFields%22%3A%5B%22title%22%2C%22shorttitle%22%2C%22author%22%2C%22year%22%2C%22month%22%2C%22day%22%2C%22journal%22%2C%22booktitle%22%2C%22location%22%2C%22on%22%2C%22publisher%22%2C%22address%22%2C%22series%22%2C%22volume%22%2C%22number%22%2C%22pages%22%2C%22doi%22%2C%22isbn%22%2C%22issn%22%2C%22url%22%2C%22urldate%22%2C%22copyright%22%2C%22category%22%2C%22note%22%2C%22metadata%22%5D%2C%22stripComments%22%3Afalse%2C%22trailingCommas%22%3Afalse%2C%22encodeUrls%22%3Afalse%2C%22tidyComments%22%3Atrue%2C%22removeEmptyFields%22%3Afalse%2C%22removeDuplicateFields%22%3Afalse%2C%22lowercase%22%3Atrue%2C%22backup%22%3Atrue%7D](https://flamingtempura.github.io/bibtex-tidy/index.html?opt=%7B%22modify%22%3Atrue%2C%22curly%22%3Atrue%2C%22numeric%22%3Atrue%2C%22months%22%3Afalse%2C%22space%22%3A2%2C%22tab%22%3Atrue%2C%22align%22%3A13%2C%22duplicates%22%3A%5B%22key%22%5D%2C%22stripEnclosingBraces%22%3Afalse%2C%22dropAllCaps%22%3Afalse%2C%22escape%22%3Afalse%2C%22sortFields%22%3A%5B%22title%22%2C%22shorttitle%22%2C%22author%22%2C%22year%22%2C%22month%22%2C%22day%22%2C%22journal%22%2C%22booktitle%22%2C%22location%22%2C%22on%22%2C%22publisher%22%2C%22address%22%2C%22series%22%2C%22volume%22%2C%22number%22%2C%22pages%22%2C%22doi%22%2C%22isbn%22%2C%22issn%22%2C%22url%22%2C%22urldate%22%2C%22copyright%22%2C%22category%22%2C%22note%22%2C%22metadata%22%5D%2C%22stripComments%22%3Afalse%2C%22trailingCommas%22%3Afalse%2C%22encodeUrls%22%3Afalse%2C%22tidyComments%22%3Atrue%2C%22removeEmptyFields%22%3Afalse%2C%22removeDuplicateFields%22%3Afalse%2C%22lowercase%22%3Atrue%2C%22backup%22%3Atrue%7D)\
    \


    <figure><img src="../../../.gitbook/assets/Screenshot 2023-12-18 at 12.00.16.png" alt=""><figcaption></figcaption></figure>
3.  Klik op "Tidy" onderaan rechts\


    <figure><img src="../../../.gitbook/assets/Screenshot 2023-12-18 at 12.00.47.png" alt=""><figcaption></figcaption></figure>
4.  Kopieer de opgekuiste informatie\


    <figure><img src="../../../.gitbook/assets/Screenshot 2023-12-18 at 11.53.10.png" alt=""><figcaption><p>Zoek het kopieer knopje aan de rechterkant van je scherm, links van de menubalk.</p></figcaption></figure>
5. Plak deze in je text editor.
6. Sla op met de extensie .bib&#x20;
7.  Laad op in Biblio\
    [https://backoffice.biblio.ugent.be/publication/add?method=bibtex](https://backoffice.biblio.ugent.be/publication/add?method=bibtex)\
    of test eerst eens op de test omgeving:\
    [https://backoffice.bibliotest.ugent.be/publication/add?method=bibtex](https://backoffice.bibliotest.ugent.be/publication/add?method=bibtex)

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-12-18 at 11.59.13.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Lukt het nog steeds niet?**\
Neem contact op met het ontwikkelteam met zo veel mogelijk informatie om te kijken of we je verder kunnen helpen.
{% endhint %}

