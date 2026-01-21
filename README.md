# accounting-transaction-cleaner
This Python script cleans and aggregates bank transaction data for personal and business accounting, optimized for downstream summarization and analysis in Excel.

You’re welcome to clone this repository and adapt the code for your own use. For best results, format your transactions with the following columns:

Transaction Date, Processed Date, Code, Type, To/From Account Number, Details, Particulars, Amount, Balance

# Transaction Cleaning Script 🧹

This script processes raw Excel transaction files and produces a cleaned, aggregated version.

## How It Works

1. **Imports & Config**
   - Loads `pandas`, `numpy`, and `os`.
   - Sets input file(s) and output folder.

2. **Load & Normalize Data**
   - Reads Excel files into a DataFrame.
   - Cleans string columns (trims spaces, replaces `NaN`/`None`).
   - Normalizes date columns.
   - Drops unnecessary columns and filters out *November* transactions (replace with months if you need to remove).

3. **Remove Reversals ⚠️**
   - Detects reversal transactions (failed payments, payment reversals).
   - Finds matching transactions and removes both.

4. **Group & Aggregate Transactions**
   - **Valid codes:** grouped by `Code`, sums amounts.
   - **Conditional codes (Billing, Transfer, Deposit):** grouped by `Type` + `To/From Account Number`.
   - Deposits are aggregated per account to preserve source information.

5. **Final Touches**
   - Reorders columns consistently.
   - Adds a `Particulars` column to indicate **Credit** or **Debit**.

6. **Export ✅**
   - Saves cleaned transactions as `cleaned.xlsx` in the output folder.

## Usage
- Open `transac_clean_demo.ipynb` in Jupyter Notebook, VS Code, or Cursor etc.
- Run the notebook to process the transactions and generate the cleaned output.
