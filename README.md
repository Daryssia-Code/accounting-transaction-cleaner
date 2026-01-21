# accounting-transaction-cleaner
This a python script to help clean and aggregate bank transactions for personal and business accounting use, optimizing for further summary/accounting in excel. You are welcome to clone this repo and change code for your personal use.

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
