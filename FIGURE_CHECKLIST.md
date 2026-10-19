# MapInfo figure checklist: three PNGs to create

The DataExtractor guide has been consolidated to **three figure placements,
using three replacement PNGs**. The main form appears once in Running the tool
and is referenced from Introduction and Anatomy. Loading and launching each
appear once in Setting up the tool; Running the tool refers back to launching.

Save the images in `D:\GitHub\DataExtractor-UserGuide` using the exact paths
below. Replace the existing files in place. They currently contain old screenshots
and are placeholders: changing the guide has not updated their image contents.

Use the compiled and tested **DataExtractor v1.7.05**, fictional or anonymised
partners and one consistent example profile. Capture at a readable scale, with
enough resolution for labels and annotations to remain legible at normal HTML
and PDF page width. There are no fixed image dimensions in the guide.

## Required files

| File, relative to the guide folder | Subject | Used in |
| --- | --- | --- |
| `setup/figures/AddToolDialog.png` | Adding and loading the application | Setting up the tool: installation. |
| `setup/figures/DataExtractorToolMenu.png` | Ribbon launch | Setting up the tool: launching; referenced from Running the tool. Despite the existing filename, the replacement should show the ribbon. |
| `execute/figures/DisplayForm.png` | Annotated extraction form with selections | Running the tool: using the form; referenced from Introduction and Anatomy. |

## Capture details

### 1. Adding and loading the application

`setup/figures/AddToolDialog.png`

Use the tool-management controls in the MapInfo version you intend to illustrate.
Show the selected DataExtractor MBX and how it is added and loaded. Include the
automatic-startup setting if it can be shown legibly. If browsing for the MBX
and showing its loaded state require different windows, combine two tightly
cropped captures into this **one PNG**. Short numbered callouts can identify:

1. The add/browse control.
2. The correct compiled MBX.
3. Loading the tool and, where shown, automatic loading at startup.

Use the executable appropriate to that MapInfo version and architecture. Avoid
exposing personal paths. The guide describes classic Tool Manager wording in
text, so separate classic screenshots are not required.

### 2. Launching from the ribbon

`setup/figures/DataExtractorToolMenu.png`

Show the DataExtractor button in the **Home tab / Tools group** of 64-bit MapInfo.
Include enough surrounding ribbon to identify the location; a full desktop
capture is unnecessary. Add a short arrow or outline identifying the button.
Its caption follows `ToolTitle` in `DataExtractor.xml`, so use a clear caption
such as `Data Extractor` consistently across the captures. The guide explains
the classic Tools-menu alternative in text.

This should be a ribbon screenshot even though the retained filename contains
`ToolMenu`. Do not recreate the old classic-menu image for this file.

### 3. Annotated extraction form

`execute/figures/DisplayForm.png`

Show the complete **Data Extractor 1.7.05** form with:

- Several fictional active partners, with at least one selected.
- Several SQL output definitions, with a representative selection. These are
  output definitions, not a single SQL source-table choice; entries show the
  definition name followed by `--->` and its configured output name.
- MapInfo output definitions, with at least one selected and its source table
  open in the workspace. Entries show the definition name and source table.
- `Zip extract files?`
- `Apply exclusion clause?`
- `Clear log file?`
- `Select polygons by centroids?`
- `Upload partner table to server?`
- `Selection Type`, preferably showing `Spatial and Survey Tags`.
- `Ok` and `Cancel`.

Use numbered callouts or short annotations for the three lists, additional
options, selection type and start button. Avoid covering labels or selections.
The names in the partner's SQLFiles/MapFiles values should match the selected
profile definitions so the example represents an extraction that can run.

To expose all the optional controls, use a valid profile with nonblank
`DefaultZip`, `DefaultExclusion`, `ExclusionClause` and `DefaultUseCentroids`,
plus a valid nonblank `EasyLoaderCommand`. Use Yes/No defaults as appropriate;
`DefaultEasyLoader` controls the initial upload selection. `DefaultClearLogFile`
sets the initial clear-log selection. Controls may be visible without being
checked: do not select upload or exclusion unless they are appropriate to the
example run. The prepared workspace and database should support the example.

`WorkingDir` has no form control. Its configuration and recovery behaviour are
covered in text and do not need a separate image.

## Figures no longer required

The guide no longer includes separate screenshots for:

- The introductory form, prepared-workspace overview or annotated workflow.
- Output folders, sample CSV, ZIP contents or the overview log in old section 3.3.
- The partner attribute table or XML definition in old sections 4.1.2.1/4.1.2.2.
  Current field descriptions and the appendix XML example cover these.
- The separate launch menu, missing-layer warning, unselected form and selected
  form sequence in Running the tool.
- The progress window, completion prompt, output folder or Notepad log.
- Individual classic Tool Manager, loaded-tool and classic menu screenshots.
- A profile chooser. Its simple selection step is described in text.

One annotated form replaces the repeated form images. One loading image replaces
the installation sequence. One ribbon image replaces the duplicate launch images.
A short, explicitly illustrative log excerpt is now selectable text in Running
the tool; it does not require a new PNG or purport to be a captured test result.

Unused figure images, including the old Resource screenshots, have been removed.
Only the three referenced figure PNGs remain, alongside the guide's logo and
favicon assets. No add-in installation or toolbar customisation screenshots are
required.

## Before publication

- Replace the three PNGs above and check that their contents match the captions.
- Check that version, profile, tool caption, partners and output definitions are
  consistent across the images and written examples.
- Review all three figures at normal page width in HTML and PDF.
- Rebuild the guide after replacement; figure numbers are generated automatically.
- Remove the editorial comment in `preface/preface.rst` after the refresh.
- This checklist can be retained for maintenance or removed before publication.
