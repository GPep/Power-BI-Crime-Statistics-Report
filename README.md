# Power BI Crime Statistics Report

A Power BI workshop for newcomers, building a London crime statistics report
from police CSV downloads and a prepared local-authority population workbook.
The included **Power BI Bootcamp - Crime.docx** is the full workshop guide,
covering Power Query transformations, relationships, a date table, DAX measures,
report pages, drill-through, tooltips, roles, and publishing.

## Repository contents

| Path | Purpose |
| --- | --- |
| `London Crime Statistics (2026).pbip` | Open this project in Power BI Desktop. |
| `London Crime Statistics (2026).Report/` | Report definitions, visuals, themes, and static resources. |
| `London Crime Statistics (2026).SemanticModel/` | TMDL model definitions, Power Query queries, DAX, relationships, and roles. |
| `Population/Local Authorities.xlsx` | Population workbook used by the model. |
| `Population/Local Authorities.csv` | Accompanying population CSV; the current model uses the Excel workbook. |
| `metpolice-logo.gif` | Logo also included among the report's static resources. |
| `Power BI Bootcamp - Crime.docx` | Detailed workshop instructions. |

## Open and refresh

1. Use a current Windows version of Power BI Desktop that supports Power BI
   Projects (PBIP), TMDL semantic models, and the enhanced report format (PBIR).
   Enable the relevant preview features if required by your Desktop version.
2. Download crime data from [data.police.uk](https://data.police.uk/data/).
   Select **Metropolitan Police** and **City of London Police**. The workshop
   recommends at least 12 months of data.
3. Extract the downloaded crime CSVs into an `Extended Data` folder beside the
   PBIP file, retaining the extracted month-folder hierarchy. Keep unrelated
   files out of that folder: the model combines files recursively.
4. Ensure `Population/Local Authorities.xlsx` is present, then open
   `London Crime Statistics (2026).pbip` in Power BI Desktop.
5. The saved queries contain the original author's absolute local paths.
   In **Transform data**, use **Data source settings > Change Source** where
   available, or edit the relevant query's **Source** step/Advanced Editor.
   Point both **Crime** and the helper query **Sample File** at your local
   `Extended Data` folder, and **Population** at your local
   `Population/Local Authorities.xlsx`. The helper queries are grouped under
   **Transform File from Extended Data**. Check all three source references.
6. **Close & Apply**, then **Refresh** and save the project. Power BI may prompt
   for data-source access or privacy settings; configure those locally.

The population query reads `Sheet1` and shapes it into `Population`. The crime
query combines the CSV files, shapes local-authority names, and performs an
inner merge with `Population`. Follow the Word guide for the full transformation
and report-building workflow; preserve the expected source schema when replacing
data.

The local model data cache is not versioned. A fresh copy of the repository
requires the downloaded crime data, updated local paths, and a refresh before
the report can show its data. Report and model definitions are kept unchanged;
paths are not automatically portable.

## Files intentionally not versioned

- `Extended Data/`: downloaded raw crime CSVs; obtain them using the steps above.
- All `.pbix` files: the editable source is the PBIP project and its directories.
- `Power BI Bootcamp - Crime - Offline` with any extension, and `GLA` with any
  extension.
- Local Power BI caches, local/editor settings, recovery files, Office lock
  files, temporary files, and common local credential/tool-cache files.

Ignored files may remain on disk; ignoring them does not delete or relocate them.
Keep the PBIP file together with both generated project directories. Review
changes before committing, especially if Power BI adds new source connections
or machine-specific settings.

## Local Git workflow

Use `git status` and `git diff` to review changes after saving in Power BI
Desktop, then stage only the intended project changes and commit them locally.
The project is stored in a private GitHub repository. Downloaded crime data,
binary reports, and the other excluded files are not uploaded. Publishing the
report to Power BI Service is an optional, separate activity described in the
workshop.

The source definitions retain their existing machine-specific paths. Review
those paths and the included documents before sharing a copy outside your
machine. No additional license or dataset rights are granted here; consult the
original data providers' terms and the rights holders for included materials.
