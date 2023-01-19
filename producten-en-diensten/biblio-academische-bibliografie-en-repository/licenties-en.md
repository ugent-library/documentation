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

For the option "the license is not in this list, there is an "other license" field available for datasets. The content of that field will replace that value for datasets here:

{% embed url="https://github.ugent.be/Universiteitsbibliotheek/biblio/blob/master/views/full.tt#L109" %}

### Screenshots

#### Biblio back office

<img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.43.png" alt="" data-size="original"> Publications options

<img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 16.44.22.png" alt="" data-size="original"> Datasets options

#### OAI licenses current screenshots

Will be adapted from 19/01/2023

<figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 17.36.38.png" alt=""><figcaption><p>OAI for CC</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 17.37.02.png" alt=""><figcaption><p>OAI for no license</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 17.39.22.png" alt=""><figcaption></figcaption></figure>

## GISMO Mappings

### Publications

<figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 17.03.05.png" alt=""><figcaption></figcaption></figure>

### Datasets

This is a snippet

<figure><img src="../../.gitbook/assets/Scherm­afbeelding 2023-01-18 om 17.40.29.png" alt=""><figcaption></figcaption></figure>

## Old Biblio

<figure><img src="../../.gitbook/assets/licenses-publications.png" alt=""><figcaption><p>Publications: adapted</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/licenses-datasets.png" alt=""><figcaption><p>Datasets: completely replaced</p></figcaption></figure>
