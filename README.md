<p align="center">
  <img src="docs/images/cover.png" alt="Osmus for Revit" />
</p>

<p align="center">
  <a href="https://github.com/sumer-alhussein/Osmus-download/releases/latest"><b>Download the latest release</b></a> ·
  <a href="#installation">Installation</a> ·
  <a href="#updates">Updates</a> ·
  <a href="#tools">Tools</a> ·
  <a href="#changelog">Changelog</a> ·
  <a href="#contributors">Contributors</a> ·
  <a href="https://github.com/sumer-alhussein/Osmus-download/issues">Report an issue</a>
</p>

# About Osmus

**Osmus** is a free add-in for **Autodesk Revit 2023, 2024, 2025, 2026 and 2027** that adds an *Osmus* ribbon tab with
productivity tools for BIM managers, architects and engineers:

- **Sheet composition & revisions** — create and rename sheets from Excel, apply revisions in bulk, build sheet sets
  by revision, write sheet scales into a parameter.
- **Selection helpers** — pick only walls or rooms, grab hidden elements or title blocks, drop grouped elements from a selection.
- **Model tools** — batch find/replace in model text, re-center rooms, create stair paths for whole floor plans, create standard worksets.
- **Cleanup** — purge unused view templates and filters, unplaced rooms and imported patterns.
- **Session helpers** — colour view tabs per document, switch the UI theme, and a *Warden* that double-checks risky commands.
- **Exports Manager** — batch export sheets and views to **PDF, DWG and DWF/DWFx** with saved profiles and custom file naming rules,
  and an export monitor to follow every file, cancel, and retry the ones that failed.
- **Automatic updates** — new versions are downloaded in the background and installed when Revit closes.

Osmus is developed by Sumer Alhussein. Contact: **sumer.alhussein@gmail.com**

# Installation

## Requirements
- Windows 10/11, 64-bit
- Autodesk Revit 2023, 2024, 2025, 2026 or 2027

## Install
1. Download an installer from the [releases page](https://github.com/sumer-alhussein/Osmus-download/releases/latest):

   | File | Installs for | Location |
   |---|---|---|
   | `Osmus-<version>-SingleUser.msi` | You only — no administrator rights needed | `%AppData%\Autodesk\Revit\Addins\<year>` |
   | `Osmus-<version>-MultiUser.msi` | Every user of the computer — needs administrator rights | `C:\ProgramData\Autodesk\Revit\Addins\<year>`, and `C:\Program Files\Autodesk\Revit\Addins\2027` for Revit 2027 |

2. **Close Revit**, run the installer and tick the Revit versions you use. It takes a few seconds.
3. Start Revit: the **Osmus** tab appears in the ribbon. If Revit asks whether to load the add-in, choose *Always Load*.

A newer version installs over the previous one — no need to uninstall first, and from 2.0.0 on Osmus installs new
versions itself (see [Updates](#updates)). Both installers are unsigned, so Windows SmartScreen may show
*"Windows protected your PC"*: click **More info → Run anyway**.

<details>
<summary>Alternative: Autodesk bundle</summary>

`Osmus.bundle.zip` is the Autodesk application bundle. Extract it into a folder named `Osmus.bundle` (the
`PackageContents.xml` must be directly inside it) in one of these folders:

- `%AppData%\Autodesk\ApplicationPlugins` — for you only, every Revit version;
- for every user: `C:\ProgramData\Autodesk\ApplicationPlugins` (Revit 2023–2026) and
  `C:\Program Files\Autodesk\ApplicationPlugins` (Revit 2027, which no longer reads `C:\ProgramData`).

Revit loads the version matching each release automatically.
</details>

<details>
<summary>Silent install (IT deployment)</summary>

```bat
msiexec /i Osmus-2.0.0-MultiUser.msi /qn
```
Installs every Revit version silently (log with `/l*v osmus-install.log`). Users who are not administrators are
told about new versions in *About* but never get the Windows prompt: deploy updates the same way.
</details>

## Updates

From version 2.0.0, Osmus keeps itself up to date:

- When Revit starts, Osmus looks for a new version on this page in the background and downloads it — Revit never waits for it.
- An **Update ready** button then appears on the *Osmus* tab: click it to restart Revit and install the update now.
  Otherwise it installs when you close Revit (with the installer's progress bar; an all-users installation asks an
  administrator to confirm).
- The next time Revit starts, a message confirms the update — or, if it could not be installed, links to its download.
- **About** shows the update status, a **Check now** button and the **Update automatically** switch (on by default).

The update uses the same kind of installation as yours (single-user MSI, all-users MSI or bundle), and every download
is checked against the checksum published with the release. Versions before 2.0.0 cannot update themselves: install
2.0.0 once from the [releases page](https://github.com/sumer-alhussein/Osmus-download/releases/latest).

## Uninstall
Windows **Settings → Apps → Installed apps → Osmus → Uninstall**, with Revit closed. The add-in files are removed
from the Revit add-ins folder; your export profiles (`Documents\OsmusExportProfiles`) and settings
(`%AppData%\Osmus`) are kept and can be deleted by hand.

# Tools

The tools are grouped the way they appear in the ribbon.

## Osmus
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/Osmus.png" width="56" /> | **About** | Shows the installed version, the Revit version and links to this page, the releases, documentation, license and contact — and the [updates](#updates): status, *Check now* and the *Update automatically* switch. | Click *About*. |
| <img src="docs/images/tools/General_Update.png" width="56" /> | **Update ready** | Appears when a new version of Osmus has been downloaded. | Click to restart Revit and install it now; otherwise it installs when you close Revit. |

## Sheet Composition
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Import_SheetsExcel.png" width="56" /> | **Sheets to Excel** | Saves the Excel template used to create or rename sheets (`Number`, `Name` columns). | Click, choose a folder → `Import sheets.xlsx` is created. **Shift + click** fills it with the sheets already in the model, so you can rename them. |
| <img src="docs/images/tools/Import_CreateSheets.png" width="56" /> | **Create/ Update Sheets** | Creates the sheets listed in the template; sheet numbers that already exist get the name from the template instead. | Fill the template, click, pick the file, then pick the title block type for the new sheets. |
| <img src="docs/images/tools/Revision_BulkRev.png" width="56" /> | **Bulk Revision** | Adds one revision to many sheets at once (sheets that already carry it are skipped). | Click, choose the revision, tick the sheets, *Finish*. **Shift + click** removes the revision from the ticked sheets instead. |
| <img src="docs/images/tools/Revision_RevSet.png" width="56" /> | **Sheet Set by Revision** | Creates a sheet set (for printing/exporting) holding every sheet that carries the chosen revision. | Click, choose the revision. An existing set with that name is deleted and re-created. |
| <img src="docs/images/tools/Sheets_SheetScaleParameter.png" width="56" /> | **Sheet Scale Parameter** | Copies each sheet's *Scale* (e.g. `1 : 100`) into a text parameter, so it can be scheduled or shown in title blocks. | Create a text parameter bound to *Sheets* (project or shared) first. Click: every sheet is selected — refine with `Ctrl + click`, `Shift + click` or the search box — choose the parameter on the left, *Copy Scale*. |

## Selection
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Select_PickWalls.png" width="56" /> | **Pick Walls** | A selection mode that only accepts walls. | Click, then click or window-select in the view; only walls are picked. Press *Finish* (or Esc) when done. |
| <img src="docs/images/tools/Select_PickRooms.png" width="56" /> | **Pick Rooms** | A selection mode that only accepts rooms. | Same as *Pick Walls*, for rooms. |
| <img src="docs/images/tools/Select_GetHidden.png" width="56" /> | **Get Hidden Elements** | Turns on *Reveal Hidden Elements* and selects everything hidden in the active view. | Open the view, click. Review the selection, then unhide or leave as is. |
| <img src="docs/images/tools/Select_GetTtbs.png" width="56" /> | **Get Sheet Title Blocks** | Selects the title blocks of the selected sheets (for editing their parameters in one go). | Select sheets in the Project Browser, click. |
| <img src="docs/images/tools/Select_RemoveGrouped.png" width="56" /> | **Remove Grouped Elements** | Removes grouped elements and groups from the current selection, leaving the loose elements. | Make a selection, click. |

## Model
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Edit_EditModelText.png" width="56" /> | **Edit Text** | Find and replace text in model text elements, optionally adding a prefix and a suffix. | Select model text (or click first and pick it), then fill in *Find*, *Replace with*, *Prefix*, *Suffix* and tick *Match case* if needed. |

## Rooms
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Select_CenterRooms.png" width="56" /> | **Re-center Rooms** | Moves room locations (and their tags in the active view) to the centre of the room's bounding box. | Select the rooms, click. |

## Annotate
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Tools_StairPathPro.png" width="56" /> | **Stair Path Pro** | Creates stair path annotations for every stair in the selected floor plans — including stairs from linked models if you want. | Click: every floor plan is selected — refine with `Ctrl + click`, `Shift + click` or the search box — choose the stair path type (and whether to include linked models) on the left, *Create Paths*. |

## Collaboration
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Workset_Create.png" width="56" /> | **Create Worksets** | Creates the office-standard worksets (AR Interior, AR Facade, AR Structure, AR FFE, AR Site, Z_Link …) that are missing from the model. | In a workshared model, click, tick the worksets to create. The tool offers to rename *Shared Levels and Grids* to *AR Grids and Levels*. |

## Cleanup
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Audit_PurgeTemplates.png" width="56" /> | **Purge View Templates** | Lists the view templates not used by any view or view type. | Click, tick what to delete, *Finish*. |
| <img src="docs/images/tools/Audit_PurgeFilters.png" width="56" /> | **Purge View Filters** | Lists the view filters not used by any view or view template. | Click, tick what to delete, *Finish*. |
| <img src="docs/images/tools/Audit_PurgeRooms.png" width="56" /> | **Purge Unplaced Rooms** | Lists the rooms that are not placed in the model. | Click, tick what to delete, *Finish*. |
| <img src="docs/images/tools/Audit_DeletePatterns.png" width="56" /> | **Delete Imported Patterns** | Deletes every fill and line pattern whose name starts with *Import* (left behind by CAD imports). | Click — there is no list; deletion is immediate (use *Undo* if needed). |

## Monitoring
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Settings_Warden.png" width="56" /> | **Warden** | Asks *"are you sure?"* before commands that often hurt model health: *Model In-Place*, *Import CAD* and *Paint*. | Click to turn it on or off; the state is remembered the next time Revit starts. |

## Windows
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Settings_ColourTabs.png" width="56" /> | **Colored Tabs** | Colours the view tabs by document, so views of different models (and links) are easy to tell apart. Revit 2023 and 2024. | Click to turn it on or off; remembered between sessions. After turning it off, restart Revit to get the default tab colours back. |
| <img src="docs/images/tools/Settings_UiToggle.png" width="56" /> | **Light / Dark mode** | Switches the Revit user interface between light and dark theme (Revit 2024 and later). | Click to switch. **Shift + click** also sets the drawing canvas to dark. |

## Export
| | Tool | What it does | How to use |
|---|---|---|---|
| <img src="docs/images/tools/Export_Schedule.png" width="56" /> | **Schedule to Excel** | Exports the schedule shown in the active view to an Excel file. | Open a schedule view, click, choose a folder → `Export schedule.xlsx`. |
| <img src="docs/images/tools/Dev_ExportsManager.png" width="56" /> | **Exports Manager** | Exports sheets and views to **PDF**, **DWG** and **DWF/DWFx** in one go, with saved profiles, per-format options and custom file names. | See below. |

### Using the Exports Manager

1. **Profile** — pick a profile or *More → Save As* to create one. Everything in the window (formats, options,
   naming rules, save location, the list shown) is stored in the profile. With *Auto-save profile on Export* ticked,
   the profile is saved every time you export.
2. **Save Location** — the folder that receives the files; each format goes into its own `PDF`, `DWG` or `DWF` sub-folder.
   Leave it empty to export to `Documents\Osmus\<project name>`.
3. **Select Model** — the host model or one of its loaded links.
4. **Sheets List / Sheets / Views** — show the sheets of a sheet list schedule, all sheets, or the exportable views
   (floor plans, ceiling plans, 3D). Everything is selected by default; use `Ctrl + A`, `Ctrl + click` and
   `Shift + click` to refine, or the search box to filter.
5. **Custom file name** — click the pencil next to the *file name* box to build the naming rule from sheet/view
   parameters, project information and date/user values, each with a prefix, suffix and separator. Sheets and views
   have separate rules; the defaults are `<Sheet Number> - <Sheet Name>` and `<View Name>`.
6. **Export PDF / DWF / DWG** — switch each format on or off and open its options (paper, zoom, colours, raster
   quality, *Combine into a single file*, DWG export setup, xrefs…).
7. **Export** — opens the **export monitor**, which exports the files one by one and shows each of them with its
   format and status, a progress ring with the percentage, the start time, the elapsed time and an estimate of the
   time left. A file that could not be written (for example a PDF that is still open in a viewer) is marked as
   failed with the reason: close the file and click **Retry** on that row, or **Retry failed** for all of them.
   **Cancel** stops after the current file; **Resume** picks up the remaining ones. **Open export folder** opens
   the destination and **Open log** the log of the run (`%TEMP%\Osmus\Logs`), handy when reporting a problem.

<p align="center">
  <img src="docs/images/export-monitor.png" width="620" alt="The export monitor while exporting" />
</p>

# Changelog

## 2.0.1

- *Sheet Scale Parameter* and *Stair Path Pro* dialogs work like the Exports Manager: everything is selected when they
  open, the selection shortcuts and the number of selected items are shown under the list, the options sit on the
  left, and the action button says what it does (*Copy Scale*, *Create Paths*).
- Stair Path Pro shows the level, scale and discipline of each floor plan.

## 2.0.0

**New**
- Revit 2027 support. The all-users installer puts the Revit 2027 add-in in `C:\Program Files\Autodesk\Revit\Addins\2027`,
  where Revit 2027 now loads add-ins for all users.
- [Automatic updates](#updates): Osmus checks for a new version when Revit starts, downloads it in the background and
  installs it when Revit closes — or right away with the *Update ready* button. *About* has the update status,
  *Check now* and an *Update automatically* switch (on by default). A message at the next start confirms the update.

**Changes**
- F1 on a ribbon button opens the tool's section of this page.
- Warden, Colored Tabs and Light / Dark mode say what they turned on or off.

## 1.5.0

**Exports Manager**
- Export monitor: the *Export Complete* dialog is replaced by a window that follows the export file by file, with a
  progress ring and percentage, the start time, the elapsed and the estimated remaining time. You can cancel the run,
  see why a file failed and retry it (or all failed files), and open the export folder or the log from there.
- A file that is open in another program (for example the previous PDF in a viewer) was reported as exported although
  nothing was written; it is now reported as failed with the reason, and can be retried after closing it.
- Sheet or view names with characters Windows does not allow in file names no longer fail the PDF and DWG exports.
- Every export is logged to `%TEMP%\Osmus\Logs` (add-in and Revit versions, project, settings, one line per file with
  its duration or error).

## 1.4.0

**New**
- Osmus logo in the installer and the About dialog.
- About dialog with the add-in version, the Revit version and links to this page, releases, documentation, license, issues and contact.
- *Sheet Scale Parameter* (Sheet Composition): copies each selected sheet's Scale into a text parameter bound to sheets.
- Exports Manager: separate file name rules for sheets and views (defaults `<Sheet Number> - <Sheet Name>` and
  `<View Name>`), everything selected by default with keyboard/mouse hints, parameters added by double-click in the
  *Custom File Name* dialog.
- Colored Tabs is a one-click toggle; Colored Tabs, Warden and the last export profile are remembered between sessions.

**Fixes**
- Exports Manager: the *Export PDF* switch was not saved in the profile and came back on after a restart. Profiles now
  also remember the list shown (Sheets List / Sheets / Views) and the selected sheet list.
- Exports Manager: saving naming rules in Revit 2024 failed with *"Enum underlying type and the object must be same type"* and left the template empty.
- Faster rule editing (file names are no longer regenerated on every keystroke); separators are saved; DWF options fixed.

**Installer**
- New MSI installers (single-user and all-users) that follow the Autodesk add-in folder conventions, with one
  feature per Revit version (2023–2026), plus the `Osmus.bundle.zip` Autodesk bundle. Existing *Osmus Kit for
  Revit 2024* installations are upgraded in place.

## 25.05.01
- Support for Revit 2023, 2025 and 2026 alongside 2024.

## 25.04.01
- First public release of Osmus.

# Contributors

| Release | Contributors |
|---|---|
| 2.0.1 | Sumer Alhussein |
| 2.0.0 | Sumer Alhussein |
| 1.5.0 | Sumer Alhussein |
| 1.4.0 | Sumer Alhussein |
| 25.05.01 | Sumer Alhussein |
| 25.04.01 | Sumer Alhussein, Ghanem Ghanem, Mahmoud Al-Bzour |

Osmus started from the [geeWiz](https://github.com/aussieBIMguru/geeWiz) add-in template by Gavin Crump (MIT).

# License and support

Osmus is provided under the [end user license agreement](LICENSE.txt). It is an independent add-in and is not
affiliated with or endorsed by Autodesk, Inc.

Questions, bugs and ideas: [open an issue](https://github.com/sumer-alhussein/Osmus-download/issues) or write to
**sumer.alhussein@gmail.com**.
