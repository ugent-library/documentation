# Deledda Handleiding

````markdown
# 1. Purpose

Imaging is web application that is located at domain deledda.ugent.be (from here on called "deledda").
It serves as a dashboard where users can follow, and intervene in
the flow of scanned images from its arrival till it is ingestion
in the digital repository of grep.ugent.be.

# 2. Workflow

## 2.1. Scan

Books and other works are scanned by Geert Roels or Rik Declercq.
They follow these rules:

* a directory is made with the name of the barcode of the scanned item
* for every scanned page a TIFF file is created, and put in that directory
* the name of a TIFF file must conform to the NARA pattern `{barcode}_{year}_{sequence}_MA.tif`:
    * `{barcode}`: barcode that is also given to the directory name
    * `{year}`: four digit year number
    * `{sequence}`: four digit sequence number, starting at `0001`, with padding zero's.
* there must be no missing files, i.e. if there is a file with sequence number `0001` and one with `0003`, there should also be one with `0002`.

This is commonly referred to as the NARA profile.
There are others too, like the TAR profile, but those
are actually never used. In practice only the NARA profile
is used. That is why we assume the NARA profile here everywhere.

These directories are stored in their "personal" incoming directory
in a special network drive, located at `//shares.isilon.ugent.be/scanworkflow/01_ready/{username}`:

On server level these incoming directories are mounted as `/mnt/data01/01_ready/{username}`

e.g. in `/mnt/data01/01_ready/groels` you would find:

```
000000007521/
    000000007521_2021_0001_MA.tif
    000000007521_2021_0002_MA.tif
910000086844/
    910000086844_2022_0001_MA.tif
    910000086844_2022_0002_MA.tif
    910000086844_2022_0003_MA.tif
...
```

In practice only these incoming directories are actually in use at the moment:

- `/mnt/data01/01_ready/groels`: Geert and Rik share the same incoming directory
- `/mnt/data01/01_ready/emiherma`: Emilie Hermans is the quality manager (see below) who
   sometimes delivers files (for why, see below)

## 2.2. Validation of new directories

A server side script (`scripts/scan_check_incoming`) at deledda detects new directories
in users incoming directory

e.g. in Geert's incoming directory `/mnt/data01/01_ready/groels` it sees a new directory `000000007521`,
    with the following contents:

    000000007521_2021_0001_MA.tif
    000000007521_2021_0002_MA.tif
    000000007521_2021_0003_MA.tif
    000000007521_2021_0004_MA.tif

It creates a new record in the database in order to track the lifecycle
of the scan directory. The scan can now be found at https://deledda.ugent.be/scans/000000007521.

Via https://deledda.ugent.be/scans/000000007521.json you can inspect the scan record.

It gives the record status `incoming`, which means that no validation
has been done on the scan directory.

It start validation on the scan directory, following the rules
as explained in 2.1. On succesfull validation, the status of
the record is set to `incoming_ok`. When there are one or more
validation errors, the status is set to `incoming_error`.

Validation of incoming directories only happen
between 08:00 and 19:00

All of your incoming directories (and their validation logs) can be tracked in https://deledda.ugent.be/ready/{uid}

e.g. https://deledda.ugent.be/ready/groels

Click on one of the scan directories, and go to the second tab.
Here you can see a list of all errors.

Notes

- If the barcode exists anywhere else, then validation is refused, and a comment `REEDS AANGELEVERD` is shown. This happens for example when previously someone delivered a scan directory `/mnt/data01/01_ready/groels/012345678`, which was moved to `/mnt/data01/02_processed/012345678`, after which
another `/mnt/data01/01_ready/groels/012345678` appeared. This avoids a situation where a new incoming directory, and its attached metadata, would overwrite existing records that were previously edited by a qa manager.


## 2.3. Validation of updated directories

A server side script (`scripts/scan_check_incoming`) at deledda detects changes to already known directories.

e.g. a file has been added

It updates the status of the record back to `incoming`

It starts a new validation, which may set the status to either

`incoming_ok` or `incoming_error`

Validation of incoming directories only happens
between 08:00 and 19:00

## 2.4. Automatic processing of directories

At 19:10 a nightly job starts the following tasks

- all incoming directories whose record's status is set to `incoming_ok`
  are moved to `/mnt/data01/02_processed` (e.g. `/mnt/data01/02_processed/000000007521`)

- a file `__MANIFEST-MD5.txt` is added to the directory containing a list of all files
  with their MD5 checksum. The purpose of this file is to detect file changes (which 
  should not happen), and to have a list of what was delivered originally by the scanner.

- the status of these accepted records is set to `registered`.

- MARC metadata is added to the record automatically, by searching the barcode in Aleph
  and fetching all matching bibliographical records. Additional filters are used
  here:

  - must be located in `rug01`
  - marc field 540 (license) must be set

  Sometimes multiple records may be found (for convolutes), and sometimes none (when cataloging has not been done yet). All found metadata records
  are added to the scan record, and it is up to the quality manager in a later step
  to delete the irrelevant one, or add the right one; and so keep only one.

  For every MARC record added, there will be set of Dublin Core fields, mapped from that MARC record.
  This will become part of metadata in GREP. All fields are repeatable. These are the mapping rules:

  - `Archive-Id`: read only UUID generated by the system
  - `DC-Title`: `uppercase({SOURCE})-{001}` e.g. `RUG01-012345678`
  - `DC-Identifier`:
    - `{SOURCE}:{001}` e.g. `rug01:012345678`
    - `{Z30$3}` (item callnr).
    - `{Z30$h}` (item description)
    - `{035$a}`, mostly used for external identifiers (e.g. biblio id, OCLC ..)
  - `DC-AccessRights`:
    - `closed` when marc field `856$z` contains `no access`. `closed` means that GREP cannot sent this record to anyone.
    - `ugent` when marc field `856$z` contains `ugent`. `ugent` means that the files should served from within the university network, or with login validation.
    - `open` when marc field `856$z` contains other value. `open` means that the files may be server without restrictions
  - `Z-Preferred-Access-Route`: enumeration with values `adore` or `none`. This value can be changed to `none`. When `none`, the record should never be sent to the image library, even if `DC-AccessRights` says so.
  - `DC-Description`: mapped from marc field `{245}`
  - `DC-DateAccepted`: read only field generated by system, containing current date (formatted as `YYYY-mm-dd`) when the metadata was assigned.
  - `DC-Type`: mapped from marc field `920$a` to a dublin core known value
    - `article` -> `Text` 
    - `audio` -> `Sound` 
    - `book` -> `Text` 
    - `coin` -> `Image` 
    - `cursus` -> `Text` 
    - `database` -> `Dataset` 
    - `digital` -> `Dataset` 
    - `dissertation` -> `Text` 
    - `ebook` -> `Text` 
    - `ephemera` -> `Text` 
    - `film` -> `MovingImage` 
    - `image` -> `Image` 
    - `manuscript` -> `Text` 
    - `map` -> `Image` 
    - `medal` -> `Image` 
    - `microform` -> `Text` 
    - `mixed` -> `Dataset` 
    - `music` -> `Sound` 
    - `newspaper` -> `Text` 
    - `periodical` -> `Text` 
    - `plan` -> `Image` 
    - `poster` -> `Image` 
    - `score` -> `Text` 
    - `videorecording` -> `MovingImage` 
    - `-` -> `Text`
  - `DC-Creator`: mapped from marc fields `100$a` and `700$a`
  - `DC-Subject`: mapped from marc fields `922$a`

- derivative files are created:
    - For every file ending in `_MA.tif`, a jpeg is generated with name ending changed to `_AC.jpg`. The size is reduced to fit a boundary box of 2000x2000, and the quality to 80 percent.
    - A low resolution pdf is generated with name `{barcode}_{year}_0001.pdf`. Each page contains a jpeg file, which is generated from the master tif, with its size reduced to fit a boundary box of 2000x2000, its quality reduced to 60 percent, and sampling rate reduced to `2x2,1x1,1x1`.
    - A high resolution pdf is generated with name `{barcode}_{year}_0002.pdf`. Each page contains a jpeg file, w
hich is generated from the master tif, with its size reduced to fit a boundary box of 2000x2000, and its quality
 reduced to 90 percent.

## 2.5. Quality Control

A quality manager (read: Emilie Hermans) will now do additional checks
on all scan directories that been accepted by the system.

For this he/she goes https://deledda.ugent.be/scans and filters on [status:registered](https://deledda.ugent.be/scans?q=status%3A%22registered%22)

In the list you can see the following:

- the scan identifier (which should be a barcode)

- the number of files, and the total size. This is calculated live

- the owner of the scan directory. This is the user that originally delivered the files

- the status of the scan directory.

- a comment, which is the latest comment that was given through the user interface (see below)

If you click on one of the scan links you'll see the following:

- tab "Bestanden":

    - tab header contains the total number of files for quick lookup
    - lists all files, and its size.
    - show statistics about all found file types in the right corner
    - shows button that should open the scan directory in your file explorer.
      this used to work in Windows environments, but now it is blocked everywhere.
      mostly the quality manager opens the scan directory manually in his/her
      network drive, and inspects its contents.

- tab "Metadata"

    - tab header adds label "missing" or "multiple" if there is not just one metadata record assigned, as it should be.
    - if there is no metadata record assigned, you'll see an empty tab with an input that shows "metadata identifier" in its tooltip. Fill in there the catalog identifier (e.g. rug01:123456789). The input is only accepted when it returns exactly one match, and if the catalog record contains a license in marc field 540.
    - if there are multiple metadata records assigned, you will have to remove the wrong metadata records first
    - this tab is read only in the following situations:
        - background tasks are working on the scan directory. e.g. the generation of the derivatives.
        - the user does not have sufficient rights
        - the status of the scan directory is not one of the following:
            - registered
            - reprocess_scans
            - reprocess_scans_qa_manager
            - reprocess_metadata
            - reprocess_derivatives

    - the metadata that was mapped from MARC to DC, is listed in the sub tab "bag info". Some of these fields can be manually updated. Only these fields are usually changed (for meaning, see above):
        - `Z-Preferred-Access-Route`
        - `DC-AccessRights`

- tab "Wijzig status"

    In the tab "Wijzig status", the status of the scan directory can be changed.
    Some statuses will change the scan directory:

    - `qa_control_ok`:
        - scan is validated by the quality manager, and therefore may be stored in GREP. The upload to GREP happens around 19:10, so until then this status can be reset.

    - `reprocess_scans` ("Terug naar scanner"): temporary status which marks as a flag that the directory will be moved back to the incoming directory of the (original) scanner. Scans with this status are processed by script `bin/scans/reprocess_scans`, which does the following:
        - move scan directory from `/mnt/data01/02_processed/{barcode}` to `/mnt/data01/{user_id}/{barcode}`
        - remove derivative files. In fact only the files listed in `__MANIFEST-MD5.txt`.
        - set status to `incoming`
        - write comment in file `__FIXME.txt`. This way the scanner can read what is wrong. When fixing is done, the scanner is expected to delete this file, after which validation will be restarted (see 2.3).

    -  `reprocess_scans_qa_manager` ("Terug naar qa manager"):  temporary status which marks as a flag that the directory will be moved to the incoming directory of the currently logged in qa manager. Scans with this status are processed by script `bin/scans/reprocess_scans`, which does the following:

        - move scan directory from `/mnt/data01/02_processed/{barcode}` to `/mnt/data01/{user_id}/{barcode}`
        - remove derivative files. In fact only the files listed in `__MANIFEST-MD5.txt`.
        - set status to `incoming`
        - write comment in file `__FIXME.txt`. This way the scanner can read what is wrong. When fixing is done
, the scanner is expected to delete this file, after which validation will be restarted (see 2.3).

    - `reprocess_metadata` ("Terug naar catalografie"):
        - a mail is sent to all catalographers informing that there is something wrong with this item on a metadata level.
        - status should be reset to `registered` by someone when fixed.

    - `reprocess_derivatives` ("Afgeleiden foutief"):
        - the derivative files contain errors and therefore should be regenerated. A background script regenerates them, and resets the status to `registered`. Not that during this processing, all editing to the scan record is blocked (as it is when done for the first time).

    - `problematic` ("Problematisch"):
        - scan is deemed problematic
        - status should be reset to `registered` by someone when fixed.

    - `purge` ("Verwijder"):
        - scan record and its files will be removed. This removal happens around 19:10. So until then one can reset this.

- tab "Status geschiedenis"

  list of status changes in time, and who was responsible for it. When user is "-",
  the status change was caused by a system job.


## 2.6. Upload to digital repository (GREP)

Around 19:10 a script `bin/scans/to_archive` will create a bagit for each
scan with status `qa_control_ok`, and store it in in `/mnt/data01/03_grep/process-in/BAG/{barcode}`.
The DC metadata is stored in the bag-info.txt of the bagit.

That directory is picked up by GREP, validated and inserted.
When validation of the bagit fails, GREP moves it to `/mnt/data01/03_grep/ingest-rejected/{barcode}_{timestamp}`, and adds the necessary in file `verify.txt`

The status is set `archiving`.

During the day, script `bin/scans/check_archive` checks the archive id
in GREP, and if found sets the status to `archived`.

## 2.7. Publication of images

When the scan is archived in GREP, the quality manager can check if the
scan is also uploaded in the image library, and set the status to `published`.

In practice a script `bin/scans/check_published` will check all scans
with status `archived`, and have `DC-AccessRight` `open` or `ugent`
are found in the image library. If yes, the status is set to `done`.

## 2.8. Cleanup of scan directories

A scan directory whose status is set to `done` will be removed
from disk. The record itself remains in the database.

## 3. Redelivery of scan directories

Only one scan directory with the same barcode
can be available in the system. This has a 
few reasons:

- every scan record has the barcode as its identifier (`_id`)
- every scan record stores the path of the current location of the scan directory (`path`)
- storing a record for every scan directory of the same name would
  introduce unwanted complexity. It is better to stop processing
  and alert the users that there are duplicates in the system.

Therefore this situation should be avoided:

```
/mnt/data01/01_ready/groels/012345678
/mnt/data01/02_processed/012345678
```

And this situation should be avoided:

```
/mnt/data01/01_ready/groels/012345678
/mnt/data01/01_ready/njfranck/012345678
```

In both cases the system will choose the path
that was last stored in the scan record with
that barcode. Because a location like `/mnt/data01/02_processed/012345678`
typically follows `/mnt/data01/01_ready/groels/012345678`
that first location always has precedence.

This means that incoming directories with
a barcode that already exists in `/mnt/data01/02_processed`
will only be validated and processed when the
other directories with the same name are removed.

# Appendix: scan record attributes

* `_id`:
  * type: string
  * description: database identifier. Should be item barcode. Older records also have callnumbers like `BHSL-HS-III-0024-000125`, but those should not be used anymore.
* `path`:
  * type: string
  * description: location of scan directory.
* `status`:
  * type: string (enumeration)
  * description: status of scan record
  * possible values:
    * `incoming`: initial status of any new incoming directory. Means that no validation has taken place
    * `incoming_error`: validation of incoming directory has failed. See list of errors in attribute `check_log`
    * `incoming_ok`: validation of incoming directory was successfull. Attribute `check_log` may contain warnings though. Scan directory may now be moved to `/mnt/data01/02_processed`
    * `registered`: scan directory has been moved from the incoming directory to `/mnt/data01/02_processed`. Now the user may not change the scan directory anymore.
    * `reprocess_scans`: qa manager instructs the system to return/move this directory from `/mnt/data01/02_processed/{barcode}` to `/mnt/data01/01_ready/{uid}/{barcode}` where `{uid}` is the uid of the owner. This is used to let the owner fix the files. This is a temporary status, and will be reset to `incoming` once moved.
    * `reprocess_scans_qa_manager`: qa manager instructs the system to move this directory from `/mnt/data01/02_processed/{barcode}` to `/mnt/data01/01_ready/{uid}/{barcode}`, where `{uid}` is the uid of the qa manager. This means that the qa manager wants to the fix the files himself. This is a temporary status, and will be reset to `incoming` once moved.
    * `reprocess_metadata`: with this status the qa manager informs catalographers that the metadata is problematic. A mail is sent to a list of catalographers
    * `reprocess_derivatives`: the qa manager informs the system that the derivative files should be regenerated. This is a temporary status, and after regeneration of the derivative files, the status is reset to `registered`
    * `problematic`: the qa manager flags this scan as problematic
    * `qa_control_ok`: scan directory and its metadata are validated by the qa manager, and may be archived in GREP
    * `archiving`: scan directory has been converted to bagit, and sent to GREP for archival. Job is in progress
    * `archived`: scan has been archived successfully in GREP
    * `archived_ok`: qa manager confirms that scan has been archived successfully in GREP (never used)
    * `archived_error`: qa manager detects that scan has NOT been archived successfully in GREP (never used)
    * `published`: system detects that the scan has been published in the image library (never used)
    * `published_ok`: qa manager confirms that scan has been published in the image library (adore.ugent.be) (never used)
    * `published_error`: qa manager detects that scan has not been published succesfully in the image library
    * `purge`: qa manager instructs the system to completely remove the scan record, its files and all of its log history.
    * `done`: scan workflow is deemed complete. System uses this to remove the scan directory
````
