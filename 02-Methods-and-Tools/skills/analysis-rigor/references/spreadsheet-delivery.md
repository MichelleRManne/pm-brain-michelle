# Spreadsheet Delivery

## Live formulas, not pasted values

When the user asks for tables "with the calculations in them," build a **data tab** plus an **analysis tab** whose cells are formulas that reference the data tab. Put group labels in header cells and reference them (`B$6`), so the table documents itself and can be regrouped.

## The conditional-median trap (openpyxl)

There is no `MEDIANIFS`, so conditional medians need an array formula. If you write `cell.value = "=MEDIAN(IF(...))"` as a plain string, the cell **silently evaluates to 0** in Excel. The tell is that the `COUNTIFS` cells next to it are correct while the medians are 0. Fix it like this:

```python
from openpyxl.worksheet.formula import ArrayFormula
cell.value = ArrayFormula(ref="B7", text="=MEDIAN(IF(...))")  # ref = the cell's own coordinate
```

Guard division inside the array:
`=MEDIAN(IF((seg=X)*(den>0), num/IF(den=0,1,den)))`

## Google Sheets

- Sheets needs `=ARRAYFORMULA(MEDIAN(IF(...)))`, and `ARRAYFORMULA` is invalid in Excel. Emit both variants if the file goes to both places.
- Google evaluates formulas in an imported CSV, so a CSV of formula strings becomes a live tab (File → Import → Insert new sheet). Name each CSV exactly what the tab should be called.
- Data-heavy workbooks are often too large to create directly through a Drive connector. Build an .xlsx and have the user upload it (Drive converts it and keeps the formulas). Say plainly that you can't edit their existing sheet in place if the connector has no write tool.

## Verify by recalculating

Never trust a formula just because you wrote it. Recalculate headlessly and assert every cell against your independently computed figures:

```bash
soffice --headless --convert-to xlsx --outdir <NEW_EMPTY_DIR> book.xlsx
# then read with openpyxl data_only=True and compare
```

- **Use a fresh output directory each run.** LibreOffice won't overwrite an existing file, so you'd end up silently re-verifying the old build.
- Don't kill `soffice` in the same shell call you need the exit code from.
- Add an in-sheet identity check (for example, two complementary blocks must sum to exactly 1) so drift shows up at a glance.
- If a `~$name.xlsx` lock file exists, the user has the workbook open. Write to a new file.
