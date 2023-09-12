# Licenties \[EN]

## Publication licenses

We use [Creative Commons](https://creativecommons.org/about/cclicenses/) licenses for publications.

### Capturing the license in the Biblio back office

Each document type you add to a publication asks for a license:

![](<../../../../.gitbook/assets/Screenshot 2023-09-12 at 17.17.46.png>)![](<../../../../.gitbook/assets/Screenshot 2023-09-12 at 17.18.05.png>)



**Which license does the publication get?**\
When adding multiple documents, the **full text** with the "**most open**" license is chosen as the license for the publication.

### Sharing the license in the Biblio front office

Find the license in the right column. The full license is displayed here.\
Example: [https://biblio.ugent.be/publication/8772899](https://biblio.ugent.be/publication/8772899)

![](<../../../../.gitbook/assets/Screenshot 2023-09-12 at 17.22.30.png>)

### Exchange in the OAI protocol

_Example in_ [_https://biblio.ugent.be/oai?verb=GetRecord\&identifier=01HA4JEMJZH1GV7RGVQAR7SRNQ\&metadataPrefix=mods\_36_](https://biblio.ugent.be/oai?verb=GetRecord\&identifier=01HA4JEMJZH1GV7RGVQAR7SRNQ\&metadataPrefix=mods\_36)

You can find the license in the `<accessCondition>` field.

* Creative Commons Public Domain Dedication\
  (CC0 1.0)
* Creative Commons Attribution 4.0 International Public License\
  (CC-BY 4.0)
* Creative Commons Attribution-ShareAlike 4.0 International Public License\
  (CC BY-SA 4.0)
* Creative Commons Attribution-NonCommercial 4.0 International Public License\
  (CC BY-NC 4.0)
* Creative Commons Attribution-NoDerivatives 4.0 International Public License\
  (CC BY-ND 4.0)
* Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License\
  (CC BY-NC-SA 4.0)
* Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License\
  (CC BY-NC-ND 4.0)

```
<accessCondition lang="eng" type="useAndReproduction">
    Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License (CC BY-NC-ND 4.0)
</accessCondition>
```

## Dataset licenses

We exchange dataset licenses in an [`SPDX`](https://spdx.org/licenses/) format, to conform with the licenses exchanged with the Flemish government.

You can find the license in the `<dcterms:license>` field.

* `CC0-1.0`
* `CC-BY-4.0`
* `CC-BY-SA-4.0`
* `CC-BY-NC-4.0`&#x20;
* `CC-BY-ND-4.0`
* `CC-BY-NC-SA-4.0`
* `CC-BY-NC-ND-4.0`

Example in [https://biblio.ugent.be/oai?verb=GetRecord\&identifier=01GP3RYHDBD42WS0C8Z5DY3CGN\&metadataPrefix=mods\_36](https://biblio.ugent.be/oai?verb=GetRecord\&identifier=01GP3RYHDBD42WS0C8Z5DY3CGN\&metadataPrefix=mods\_36)

```
<location>
    <holdingExternal>
        <dcterms:simpledc xmlns:dcterms="http://purl.org/dc/terms/">
            <dcterms:accessRights>info:eu-repo/semantics/embargoedAccess</dcterms:accessRights>
            <dcterms:license>CC-BY-4.0</dcterms:license>
            <dcterms:format>application/pdf</dcterms:format>
        </dcterms:simpledc>
    </holdingExternal>
</location>
```

## License mappings

### General

| Back-office                                                                                                                                                                                                                    | Front-office (OAI protocol)                                                                                        | Location                            | Info                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Empty selection`                                                                                                                                                                                                              | **No license (in copyright)**                                                                                      | 📃Publications                      | <p><em>Reason: in the past this one has been used to indicate "other license" as well.</em><br><br><em>Datasets does not allow for an empty selection.</em></p> |
| **No license (in copyright)**                                                                                                                                                                                                  | **No license (in copyright)**                                                                                      | 📃Publications                      | _Reason: both old license options meant "there is no license, no reuse"_                                                                                        |
| **I don’t know the status of the copyright for this publication**                                                                                                                                                              | **Information pending**                                                                                            | 📃Publications                      | /                                                                                                                                                               |
| <p>Publications:<br><strong>The license is not in this list</strong><br><br>Datasets:<br><strong>The license is not in this list +</strong> the value that has been entered in the <strong>"other license"</strong> field.</p> | **A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.** | <p>📃Publications<br>🔢Datasets</p> | _In the future, FRIS would like to receive the "other license" field for datasets. This is currently not the case. See further notes._                          |
| CC license option\*                                                                                                                                                                                                            | _Shows the chosen license e.g. Creative Commons Attribution 4.0 International Public License (CC-BY 4.0)\*_        | <p>📃Publications<br>🔢Datasets</p> | _FRIS use the SPDX ID standard. Translations are made somewhere (GISMO? FRIS); we might have to adapt in the future so we can follow the standard._             |

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

#### Data flows: dataset SPDX

For the option "the license is not in this list, there is an "other license" field available for datasets. At this point, the value is not replaced in the front-office. But that would come in handy in the future for FRIS. Need to discuss this with GISMO before we take action here.\
\
We had a discussion with FRIS in the past. They asked us to use the SPDX "ID" field: like so https://github.com/spdx/license-list-data/blob/main/json/licenses.json#L1021

Current code for the "other license" field:

{% embed url="https://github.ugent.be/Universiteitsbibliotheek/biblio/blob/master/views/full.tt#L109" %}

Future dataflows for SPDX values in "other license" field:

* We show&#x20;

#### Examples of dataflows

**Empty selection / No license (in copyright) / No license (in copyright)**

* Publication
  * empty selection
    *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8644564](https://backoffice.bibliotest.ugent.be/publication/8644564)

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.12.47.png" alt=""><figcaption></figcaption></figure>
    * Biblio front-office test record [https://bibliotest.ugent.be/publication/8644564](https://bibliotest.ugent.be/publication/8644564)\
      ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.13.31.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644564\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644564\&metadataPrefix=mods\_36)

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.08.08.png" alt=""><figcaption></figcaption></figure>
  * no license selected
    *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8644924](https://backoffice.bibliotest.ugent.be/publication/8644924?redirect-url=%2Fpublication%3Fq%3D%26sort%3Ddate-updated-desc\&show=files)

        <div align="left">

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.12.26.png" alt=""><figcaption></figcaption></figure>

        </div>
    * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8644924](https://bibliotest.ugent.be/publication/8644924)\
      ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.12.06.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644924\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8644924\&metadataPrefix=mods\_36)

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 16.42.37.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Not possible, you cannot leave this field open in the back-office.

**I don’t know the status of the copyright for this publication / Information pending.**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8646481](https://backoffice.bibliotest.ugent.be/publication/8646481)\


      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.14.27.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8646481](https://bibliotest.ugent.be/publication/8646481)\
    ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.15.10.png>)\

  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8646481\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8646481\&metadataPrefix=mods\_36)

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.15.39.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Not possible, you cannot leave this field open in the back-office.

**The license is not in this list / A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8689255](https://backoffice.bibliotest.ugent.be/publication/8689255)

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.13.16.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8689255](https://bibliotest.ugent.be/publication/8689255)\
    ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.13.42.png>)
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8689255\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8689255\&metadataPrefix=mods\_36)

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 16.43.16.png" alt=""><figcaption></figcaption></figure>
* Dataset
  * Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/dataset/01GM39A1V9G3F374YAE88M0D4V](https://backoffice.bibliotest.ugent.be/dataset/01GM39A1V9G3F374YAE88M0D4V)\
    ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.32.06.png>)
    * Biblio front-office test record: [https://bibliotest.ugent.be/publication/01GM39A1V9G3F374YAE88M0D4V](https://bibliotest.ugent.be/publication/01GM39A1V9G3F374YAE88M0D4V)\
      ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.33.24.png>)
    *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=01GM39A1V9G3F374YAE88M0D4V\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=01GM39A1V9G3F374YAE88M0D4V\&metadataPrefix=mods\_36)\
        \
        `<accessCondition type="useAndReproduction">`

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-19 om 17.32.48.png" alt=""><figcaption></figcaption></figure>

        `<cdterms:license>`

        <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 14.20.31.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For datasets, the specific "other license" does not flow through at this point. In the future, this would be handy data for FRIS to base their licenses on.
{% endhint %}

**CC license options**

* Publication
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/publication/8703190?redirect-url=%2Fpublication\&show=description](https://backoffice.bibliotest.ugent.be/publication/8703190?redirect-url=%2Fpublication\&show=description)

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.20.00.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8703190](https://bibliotest.ugent.be/publication/8703190)\
    ![](<../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.22.06.png>)
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8703190\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8703190\&metadataPrefix=mods\_36)\


      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.23.05.png" alt=""><figcaption></figcaption></figure>
* Dataset
  *   Biblio back-office test record: [https://backoffice.bibliotest.ugent.be/dataset/8759641](https://backoffice.bibliotest.ugent.be/dataset/8759641)

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.26.19.png" alt=""><figcaption></figcaption></figure>
  * Biblio front-office test record: [https://bibliotest.ugent.be/publication/8759641](https://bibliotest.ugent.be/publication/8759641)\
    <img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.50.10.png" alt="" data-size="original">
  *   MODS 36 for GISMO and FRIS in OAI: [https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8759641\&metadataPrefix=mods\_36](https://bibliotest.ugent.be/oai?verb=GetRecord\&identifier=8759641\&metadataPrefix=mods\_36)\
      \
      `<accessCondition type="useAndReproduction">`

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 09.50.44.png" alt=""><figcaption></figcaption></figure>

      `<dcterms:license>`

      <figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 14.23.14.png" alt=""><figcaption></figcaption></figure>

### Screenshots

#### Biblio back office

<img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.43.png" alt="" data-size="original"> Publications options

<img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.22.png" alt="" data-size="original"> Datasets options



## GISMO Mappings

### Publications

Current mappings, they will change starting from 23/01/2023

{% file src="../../../../.gitbook/assets/Publicatie_copyright-2.xlsx" %}

<figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 16.53.28 (1).png" alt=""><figcaption></figcaption></figure>

Changes needed:

* Replace / merge
  * From
    * /be.ugent.biblio/publicatie/copyright/personal
    * /be.ugent.biblio/publicatie/copyright/publisher
  * To
    * **/be.ugent.biblio/publicatie/copyright/nolicense**
    * **No license (in copyright)**
* Replace copy
  * From
    * /be.ugent.biblio/publicatie/copyright/unknown
    * I don't know the status of the copyright for this publication
  * To
    * /be.ugent.biblio/publicatie/copyright/unknown
    * **Information pending**
* Add
  * **/be.ugent.biblio/publicatie/licentie/licensenotlisted**
  * **A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.**

### Datasets

Current mappings, they will change starting from 23/01/2023

{% file src="../../../../.gitbook/assets/Dataset_licentie-2.xlsx" %}

<figure><img src="../../../../.gitbook/assets/Scherm­afbeelding 2023-01-20 om 10.11.02.png" alt=""><figcaption></figcaption></figure>

Optional

* Remove
  * /be.ugent.biblio/dataset/licentie/nolicense
  * /be.ugent.biblio/dataset/licentie/pending
* Replace copy
  * From
    * /be.ugent.biblio/dataset/licentie/other
    * The license is not listed here
  * To
    * **/be.ugent.biblio/dataset/licentie/licensenotlisted**
    * **A specific license has been chosen by the rights holder. Get in touch with the rights holder for reuse rights.**
    * _Context: In the future FRIS would like to see the content filled out manually in the free text field "other license". So they know what will be chosen. However, it would be the SPDX "ID" field: https://github.com/spdx/license-list-data/blob/main/json/licenses.json#L1021_
