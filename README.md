# FDNACCT Individual Project - Automated Accounting System

This project automates the accounting process for FDN Cleaning Service, a deep cleaning service business, as specified in the provided Jupyter Notebook.  It processes financial transactions for September 2024 to generate the General Journal, General Ledger, and prepares the data for the Trial Balance.  The Trial Balance itself requires manual transfer to a spreadsheet.

## Project Overview

The project uses Python and the Peewee ORM to interact with an SQLite database.  It defines database models for the chart of accounts, general journal, general ledger, and individual journal entries.  Helper functions are used to manage the complexities of debit/credit entries, balance calculations, and posting to the general ledger.

The notebook outlines the project requirements, provides the chart of accounts, lists the financial transactions, and gives instructions for generating the General Journal, General Ledger and Trial Balance (which requires manual completion in a spreadsheet).


## Features

* **Database Driven:**  Uses an SQLite database (`accounting.db`) for persistence of accounting data.  This allows for easier data management and potential expansion.
* **Automated Journal Entries & Posting:** The script automatically generates journal entries based on the provided transactions and posts these entries to the general ledger.
* **Balance Calculation:**  Balances are automatically calculated and updated for each account in the ledger.
* **Handling of Compound Entries:** The code accounts for situations requiring multiple debits or credits within a single transaction (compound entries).
* **Formatted Ledger Output:** The script outputs the ledger entries in a tabular format, making it easy to copy this data to a spreadsheet program for generating the Trial Balance.


## Requirements

* Python 3.x
* Peewee ORM: `pip install peewee`
* SQLite (usually included with Python installations)


## How to Run

1. **Install Peewee:**  Use `pip install peewee` in your terminal or command prompt.
2. **Run the Notebook:** Open the Jupyter Notebook file and execute the code cells sequentially.  The notebook will:
    * Create the `accounting.db` database if it doesn't exist.
    * Populate the database with the chart of accounts.
    * Create general journal entries for each transaction.
    * Post these entries to the general ledger and calculate balances.
    * Output a formatted ledger to the console.
3. **Create Trial Balance:** Copy the outputted ledger data (from the console or by querying the database) into a spreadsheet (Google Sheets is recommended). Create a Trial Balance on a separate sheet in this spreadsheet.


## Code Structure (Key Components)

* **`ChartOfAccounts` Model:** Defines the structure for storing account information (ID, type, title).
* **`GeneralJournal`, `GeneralJournalEntry` Models:**  Handle the storage and organization of journal entries.
* **`Ledger` Model:** Stores the general ledger entries, including balances.
* **Helper Functions:**  A suite of functions simplify the complex logic of accounting, including:
    * `get_normal_balance()`: Determines the normal balance (debit or credit) for different account types.
    * `SimpleEntry()`: A core function for creating and posting journal entries.  Handles both simple and compound entries.
    * Ledger entry creation and balance updates.


## Limitations

* **Manual Trial Balance:**  The generation of the Trial Balance is not automated.  The formatted ledger output needs to be copied to a spreadsheet and the trial balance completed manually.
* **Error Handling:**  While the code includes basic checks, more robust error handling could be added (e.g., handling invalid transaction data).
* **Reporting:**  The system currently only outputs the ledger; additional reports (income statement, balance sheet) would be valuable additions.

## Example Situation
The example used for the notebook above is as follows

---

Faith D. Nakpil recently established a business in September 2024, focusing on deep cleaning services under the name **FDN Cleaning Service**. Below are the Chart of Accounts and financial transactions for the first month of operation.

---

## FDN Cleaning Service  
### Chart of Accounts

| **Account #** | **Account Title**             |
| ------------- | ----------------------------- |
| **Assets**    |                               |
| 101           | Cash                          |
| 102           | Accounts Receivable           |
| 103           | Cleaning Supplies             |
| 104           | Prepaid Insurance Expense     |
| 111           | Cleaning Equipment            |
| 112           | Transportation Vehicle        |
| **Liabilities**|                              |
| 201           | Accounts Payable              |
| 202           | Notes Payable                 |
| 203           | Unearned Service Revenue      |
| **Owner’s Equity** |                          |
| 301           | Faith D. Nakpil, Capital      |
| 302           | Faith D. Nakpil, Drawing      |
| **Revenues**  |                               |
| 401           | Cleaning Revenues             |
| **Expenses**  |                               |
| 501           | Salaries Expense              |
| 502           | Utilities Expense             |
| 503           | Rent Expense                  |
| 504           | Advertising Expense           |
| 505           | Miscellaneous Expense         |

---

## Financial Transactions

### September 2024

| **Date** | **Transactions**                                                                                                                                     |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sept 1   | Deposited ₱52,000 cash into the bank account of FDN Cleaning Service and invested an old deep cleaning equipment originally costing ₱35,000, now worth ₱10,000. |
| Sept 3   | Purchased cleaning supplies on account, ₱21,400, from CleanFast Trading. Received Sales Invoice #3567.                                               |
| Sept 5   | Purchased cleaning equipment on account, ₱15,600, from A1 Merchandise. Received Sales Invoice #2156.                                                |
| Sept 6   | Purchased an old motorcycle for the business, costing ₱47,000. Paid ₱10,000 cash with check #001, financed the remainder by issuing a note payable.  |
| Sept 7   | Paid rent for office space for the month, ₱7,300 with check #002.                                                                                    |
| Sept 9   | Received ₱31,800 cash for cleaning services rendered. Issued OR#0001 and Service Invoice #10001.                                                     |
| Sept 10  | Paid Facebook ads for advertisement, ₱1,700 with check #003.                                                                                        |
| Sept 11  | Paid insurance for the next six months, ₱4,800 with check #004.                                                                                     |
| Sept 12  | Received ₱6,200 as advance payment for services to be performed next month. Issued OR#0002.                                                         |
| Sept 13  | Paid ₱9,000 to CleanFast Trading as partial payment, with check #005.                                                                               |
| Sept 14  | Paid miscellaneous expenses, ₱2,200 with check #006.                                                                                                |
| Sept 15  | Billed Aim High Laboratories ₱18,600 for cleaning services rendered. Issued Service Invoice #10002.                                                 |
| Sept 16  | Paid salaries, ₱8,400 with check #007.                                                                                                              |
| Sept 20  | Received ₱9,800 from Aim High Laboratories as partial payment for the September 15 bill. Issued OR#0003.                                            |
| Sept 22  | Paid partial amount of note payable issued on September 6, ₱2,400 with check #008.                                                                  |
| Sept 25  | Paid PLDT for telephone and internet expenses, ₱900 with check #009.                                                                                |
| Sept 28  | Paid employee salary, ₱7,900 with check #010.                                                                                                       |
| Sept 29  | Billed Precision Clinic ₱22,500 for cleaning services rendered. Issued Service Invoice #10003.                                                      |
| Sept 30  | Faith withdrew ₱10,000 from the business with check #011.                                                                                           |

## INSTRUCTIONS:

1. **General Journal:**
   - Before journalizing, enter columnar headings: Date, Description, P/R, Debit, Credit.
   - Journalize the transactions with descriptions and source documents. Use compound entries where necessary.
   - In the Posting Reference (P/R) column, encode the account numbers.
   - Leave a space after each journal entry.
   - **Rows 1-35:** Page 1, **Rows 36-70:** Page 2, **Rows 71-105:** Page 3.
   - **Google Spreadsheet:** Use **Sheet1**, rename the tab as **GJ**.

2. **General Ledger:**
   - Open accounts by entering account names and numbers.
   - Follow the order of accounts in the Chart of Accounts.
   - Enter columnar headings: Date, Description, P/R or F, Debit, Credit, Balance.
   - Post accounts to the ledger, with cross-referencing in the P/R column.
   - Leave a space after every account.
   - **Google Spreadsheet:** Use **Sheet2**, rename the tab as **GL**.

3. **Trial Balance:**
   - Prepare the Trial Balance for the month ending **September 30, 2024**.
   - **Google Spreadsheet:** Use **Sheet3**, rename the tab as **TB**.

---
