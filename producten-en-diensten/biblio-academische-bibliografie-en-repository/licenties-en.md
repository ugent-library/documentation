# Licenties \[EN]

## License mappings

| Back-office                                                                                                                                                                                                                                                          | Front-office (same as OAI -> GISMO -> FRIS)                                                                                                                                                                                                                                                  | Location                            | Info                                                                                                                                                | Old back-office                                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Empty selection`                                                                                                                                                                                                                                                    | **No license (in copyright)**                                                                                                                                                                                                                                                                | <p>📃Publications<br>🔢Datasets</p> | _Reason: in the past this one has been used to indicate "other license" as well_                                                                    | `Empty selection`                                                                                                                                                                                                                        |
| **No license (in copyright)**                                                                                                                                                                                                                                        | **No license (in copyright)**                                                                                                                                                                                                                                                                | 📃Publications                      | _Reason: both old license options meant "there is no license, no reuse"_                                                                            | <p><strong>I have retained and own the full copyright for this publication</strong><br><br><strong>I have transferred the copyright for this publication to the publisher</strong> <br><br><code>The above options are merged</code></p> |
| **I don’t know the status of the copyright for this publication**                                                                                                                                                                                                    | **Information pending.**                                                                                                                                                                                                                                                                     | 📃Publications                      | /                                                                                                                                                   | I don't know the status of the copyright for this publication                                                                                                                                                                            |
| <p>Publications:<br><strong>The license is not in this list</strong><br><strong></strong><br><strong></strong>Publications:<br><strong>The license is not in this list +</strong> the value that has been entered in the <strong>"other license"</strong> field.</p> | <p>Publications:<br><strong>A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.</strong><br><strong></strong><br><strong></strong>Datasets:<br><strong>The value that has been entered in the "other license" field.</strong></p> | <p>📃Publications<br>🔢Datasets</p> | /                                                                                                                                                   | `Not an option in the old back-office`                                                                                                                                                                                                   |
| CC license option\*                                                                                                                                                                                                                                                  | _Shows the chosen license e.g. Creative Commons Attribution 4.0 International Public License (CC-BY 4.0)\*_                                                                                                                                                                                  | <p>📃Publications<br>🔢Datasets</p> | _FRIS use the SPDX ID standard. Translations are made somewhere (GISMO? FRIS); we might have to adapt in the future so we can follow the standard._ | CC license option\*                                                                                                                                                                                                                      |

### CC License options\*

* Creative Commons Public Domain Dedication (CC0 1.0)\
  SPDX: `CC0-1.0`
* Creative Commons Attribution 4.0 International Public License (CC-BY 4.0)\
  SPDX: `CC-BY-4.0`
* Creative Commons Attribution-ShareAlike 4.0 International Public License (CC BY-SA 4.0)\
  SPDX: `CC-BY-SA-4.0`
* Creative Commons Attribution-NonCommercial 4.0 International Public License (CC BY-NC 4.0)\
  SPDX: `CC-BY-NC-4.0`&#x20;
* Creative Commons Attribution-NoDerivatives 4.0 International Public License (CC BY-ND 4.0) \
  SPDX: `CC-BY-ND-4.0`
* Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License (CC BY-NC-SA 4.0)\
  SPDX: `CC-BY-NC-SA-4.0`
* Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License (CC BY-NC-ND 4.0)\
  SPDX: `CC-BY-NC-ND-4.0`

### Data flows

Licenses selected in the back office flow through to the front-office, and third parties make use of our aoi protocols.

What that looks like is defined here for the front-office:

{% embed url="https://github.com/ugent-library/biblio-backoffice/blob/dev/internal/app/handlers/frontoffice/handler.go" %}

For the option "the license is not in this list, there is an "other license" field available for datasets. At this point, the value is not replaced in the front-office (see case further on), but that would come in handy in the future. Need to discuss this with GISMO before we take action here.

{% embed url="https://github.ugent.be/Universiteitsbibliotheek/biblio/blob/master/views/full.tt#L109" %}

#### Examples of dataflows

**Empty selection / No license (in copyright) / No license (in copyright)**

* Publication
  * empty selection
    *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8644564](https://backoffice.bibliotest.ugent.be/publication/8644564)

        <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.12.47.png" alt=""><figcaption></figcaption></figure>
    * Biblio front-office test record [https://bibliotest.ugent.be/publication/8644564](https://bibliotest.ugent.be/publication/8644564)\
      ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.13.31.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644564\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644564\&metadataPrefix=mods\_36)

        <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.08.08.png" alt=""><figcaption></figcaption></figure>
  * no license selected
    *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8644924](https://backoffice.bibliotest.ugent.be/publication/8644924?redirect-url=%2Fpublication%3Fq%3D%26sort%3Ddate-updated-desc\&show=files)

        <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.12.26.png" alt=""><figcaption></figcaption></figure>
    * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8644924](https://bibliotest.ugent.be/publication/8644924)\
      ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.12.06.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644924\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644924\&metadataPrefix=mods\_36)

        <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 16.42.37.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Not possible, you cannot leave this field open in the back-office.

**I don’t know the status of the copyright for this publication / Information pending.**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8646481](https://backoffice.bibliotest.ugent.be/publication/8646481)\


      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.14.27.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8646481](https://bibliotest.ugent.be/publication/8646481)\
    ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.15.10.png>)\

  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8646481\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8646481\&metadataPrefix=mods\_36)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.15.39.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Not possible, you cannot leave this field open in the back-office.

**The license is not in this list / A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8689255](https://backoffice.bibliotest.ugent.be/publication/8689255)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.13.16.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8689255](https://bibliotest.ugent.be/publication/8689255)\
    ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.13.42.png>)
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8689255\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8689255\&metadataPrefix=mods\_36)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 16.43.16.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/dataset/01GM39A1V9G3F374YAE88M0D4V](https://backoffice.bibliotest.ugent.be/dataset/01GM39A1V9G3F374YAE88M0D4V)\
    ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.32.06.png>)
    * Biblio front-office test record: [https://bibliotest.ugent.be/publication/01GM39A1V9G3F374YAE88M0D4V](https://bibliotest.ugent.be/publication/01GM39A1V9G3F374YAE88M0D4V)\
      ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.33.24.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=01GM39A1V9G3F374YAE88M0D4V\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=01GM39A1V9G3F374YAE88M0D4V\&metadataPrefix=mods\_36)

        <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.32.48.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For datasets, the specific "other license" does not flow through at this point. In the future, this would be handy data for FRIS to base their licenses on.
{% endhint %}

**CC license options**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8703190?redirect-url=%2Fpublication\&show=description](https://backoffice.bibliotest.ugent.be/publication/8703190?redirect-url=%2Fpublication\&show=description)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.20.00.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8703190](https://bibliotest.ugent.be/publication/8703190)\
    ![](<../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.22.06.png>)
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8703190\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8703190\&metadataPrefix=mods\_36)\


      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.23.05.png" alt=""><figcaption></figcaption></figure>
* Dataset
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/dataset/8759641](https://backoffice.bibliotest.ugent.be/dataset/8759641)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.26.19.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8759641](https://bibliotest.ugent.be/publication/8759641)\
    <img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.50.10.png" alt="" data-size="original">
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8759641\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8759641\&metadataPrefix=mods\_36)

      <figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.50.44.png" alt=""><figcaption></figcaption></figure>

### Screenshots

#### Biblio back office

<img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.43.png" alt="" data-size="original"> Publications options

<img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.22.png" alt="" data-size="original"> Datasets options



## GISMO Mappings

### Publications

Current mappings, they will change starting from 19/01/2023

{% file src="../../.gitbook/assets/Publicatie_copyright-2.xlsx" %}

### Datasets

Current mappings, they will change starting from 19/01/2023

{% file src="../../.gitbook/assets/Dataset_licentie-2.xlsx" %}

## Old Biblio

<figure><img src="../../.gitbook/assets/licenses-publications.png" alt=""><figcaption><p>Publications: adapted</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/licenses-datasets.png" alt=""><figcaption><p>Datasets: completely replaced</p></figcaption></figure>
