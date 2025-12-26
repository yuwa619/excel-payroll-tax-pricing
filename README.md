# excel-payroll-tax-pricing
Excel practice workbook covering rounding, MROUND, and aggregation through tax, payroll, and pricing exercises.
# Excel Functions Practice Workbook (Rounding • MROUND • Aggregations)

Hands-on Excel workbook demonstrating practical business calculations (tax, bonuses, pricing) using core spreadsheet techniques such as absolute references and rounding to required increments.

## Contents
- [Project overview](#project-overview)
- [Workbook structure](#workbook-structure)
- [Key skills demonstrated](#key-skills-demonstrated)
- [How to use](#how-to-use)
- [Notes on data](#notes-on-data)
- [Suggested extensions](#suggested-extensions)
- [Repository structure](#repository-structure)

---

## Project overview

This project is a single Excel workbook (`Exercise 01.xlsx`) containing three short exercises built around realistic business scenarios:

1. **Invoice tax calculations** (ROUNDING sheet)
2. **Employee salary adjustments rounded to a policy increment** (MROUND sheet)
3. **Pricing with tax + aggregation (totals/averages) in the presence of errors** (AGGREGATE sheet)

The goal is to practise:
- Building consistent formulas
- Using absolute references for configurable rates
- Applying rounding rules for finance/payroll style outputs
- Producing summary calculations safely even when some rows contain errors

---

## Workbook structure

### 1) `ROUNDING`
**Scenario:** invoice list with amounts and a configurable sales tax rate.

**What’s in the sheet**
- A list of **23 invoices** with:
  - `Invoice #`
  - `Client`
  - `Amount`
  - A calculated value based on the tax rate
- A **Sales Tax rate** stored in a single cell (`G3 = 0.15`)

**Core formula pattern**
- Uses an absolute reference to keep the tax rate fixed while filling down:
  - `=$G$3*C4`

**Typical use**
- Calculate tax (and optionally extend to total including tax, and rounding to currency precision).

---

### 2) `MROUND`
**Scenario:** payroll bonus calculation with salary rounded to the nearest increment.

**What’s in the sheet**
- Employee salary list with:
  - `Salary`
  - `Bonus`
  - `New Salary` (rounded)
- A configurable **bonus rate** stored in one cell (`G2 = 0.04`)

**Core formulas**
- Bonus:
  - `=B3*$G$2`
- New Salary rounded to nearest **100**:
  - `=MROUND(B3+C3, 100)`

**Why MROUND**
- Many payroll processes require salaries to be rounded to a standard increment (e.g., nearest £100).

---

### 3) `AGGREGATE`
**Scenario:** product pricing including tax, then totals/averages across the list, with deliberate errors included.

**What’s in the sheet**
- Product list with:
  - `Price`
  - `Price (inc tax)`
- Configurable **Sales Tax** rate (`G2 = 0.12`)
- Two intentional error cases to simulate real-world messy spreadsheets:
  - A divide-by-zero style error (e.g., `... + B13/0`)
  - A misspelled function (`SUEM` instead of `SUM`) as an example of `#NAME?`

**Core formula pattern (for standard rows)**
- Price including tax:
  - `=SUM(B3*$G$2)+B3`
  - (Equivalent to `=B3*(1+$G$2)`)

**Summary section**
- Includes total and average calculations across valid rows.

---

## Key skills demonstrated
- **Absolute referencing** for “single source of truth” parameters (tax/bonus rates): `$G$2`, `$G$3`
- **Fill-down safe formulas** (copying calculations without breaking references)
- **Rounding to increments** using `MROUND()`
- **Aggregation concepts** (totals and averages) and awareness of how spreadsheet errors can affect summaries

---

## How to use

1. Download or clone the repo.
2. Open the workbook:
   - Microsoft Excel (recommended), or compatible spreadsheet software.
3. Update the configurable rates:
   - `ROUNDING!G3` (Sales Tax)
   - `MROUND!G2` (Bonus rate)
   - `AGGREGATE!G2` (Sales Tax)
4. Review the formulas in the calculated columns and confirm the outputs update correctly.

Optional checks:
- Change tax/bonus rates and confirm all dependent values recalculate correctly.
- Validate that rounding behaves as expected when values are near halfway points.

---

## Notes on data
- Data in this workbook is **synthetic / sample data** for practice.
- No confidential, personal, or organisational data is included.

---

## Suggested extensions
If you want to evolve this into a stronger portfolio piece:

- **Currency rounding**
  - Round tax and totals to 2 decimal places using `ROUND(value, 2)`
- **Invoice totals**
  - Add a `Total (inc tax)` column using `=Amount*(1+TaxRate)`
- **Error-safe summaries**
  - Use `AGGREGATE()` to calculate totals/averages while ignoring errors (useful when some rows contain `#DIV/0!` / `#NAME?`).
- **Data validation**
  - Add constraints for rates (e.g., tax between 0 and 1).
- **Presentation**
  - Convert ranges to Excel Tables, add slicers, and include a small KPI section.

---

## Repository structure
