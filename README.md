# Personal_finance_dashboard
A user-friendly finance dashboard built with Streamlit for tracking, categorizing, and visualizing personal expenses and payments from CSV bank statements. This app enables you to upload your transaction data, categorize expenses, and view insightful summaries and charts—all in your browser.

Features
CSV Upload: Import your bank transactions in CSV format for instant analysis.

Automatic & Manual Categorization: Assign categories to expenses using keywords, or manually adjust them via an interactive editor.

Category Management: Add new categories and associate them with specific transaction details for future auto-categorization.

Expense & Payment Tabs: Separate views for debits (expenses) and credits (payments).

Visual Summaries: Pie chart visualization of expenses by category and tabular summaries for both debits and credits.

Persistent Categories: Categories and keywords are saved locally in a JSON file for future sessions.

Requirements
Python 3.8 or higher.

Streamlit

Pandas

Plotly

Install dependencies with:

bash
pip install streamlit pandas plotly
Usage
Prepare Your Data:
Ensure your CSV file contains the following columns:

Date (e.g., "17 Jun 2025")

Details

Amount (numbers, may include commas)

Debit/Credit ("Debit" for expenses, "Credit" for payments)

Run the App:

bash
streamlit run main.py
Interact with the Dashboard:

Upload your CSV file using the uploader.

Review and edit expense categories in the "Expenses (Debits)" tab.

Add new categories and associate keywords for automatic future categorization.

View summaries and pie charts for a quick financial overview.

Check total payments in the "Payments (Credits)" tab.

Example
text
Type: Upload your CSV file
Tab: Expenses (Debits)
- Edit categories for each transaction
- Add new categories as needed
- View pie chart of expenses by category

Tab: Payments (Credits)
- See total payments and transaction details
Customization
Change Category Logic:
Edit or expand the categorize_transactions function for more advanced keyword matching (e.g., partial matches, regex).

Personal Finance Dashboard: Code Flow
1. Imports and Setup
Imports required libraries: streamlit, pandas, plotly.express, json, os

Sets Streamlit page configuration (title, icon, layout)

Defines the path for storing categories (categories.json)

2. Session State Initialization
Checks if categories exist in Streamlit's session state; if not, initializes with "Uncategorized"

If categories.json exists, loads categories and associated keywords from the file into session state

3. Helper Functions
save_categories(): Saves the current categories and their keywords to categories.json

categorize_transactions(df): Assigns each transaction a category based on matching its "Details" field to category keywords; defaults to "Uncategorized" if no match

load_transactions(file): Reads the uploaded CSV file, cleans columns, converts "Amount" and "Date" to proper formats, and categorizes transactions

add_keyword_to_category(category, keyword): Adds a new keyword to a category and saves the updated categories

4. Main Application (main())
Displays the app title

Prompts the user to upload a CSV file of transactions

If a file is uploaded:
Loads and processes the transactions using load_transactions()

Splits the data into Debits (Expenses) and Credits (Payments)

Expenses (Debits) Tab
Allows the user to add new categories

Displays a data editor for debits, enabling category assignment for each transaction

On "Apply Changes", updates categories and adds transaction details as keywords for future auto-categorization

Shows a summary table of expenses by category

Displays a pie chart of expenses by category

Payments (Credits) Tab
Shows total payments (sum of credits).

Displays a table of all credit transactions.

5. Persistent Category Management
Any new categories or keywords added are saved to categories.json for use in future sessions.

6. End of Flow
The user can interactively categorize, review, and visualize their financial data.

All changes to categories and keywords persist across sessions



Change Currency:
Update the formatting in the code if you use a currency other than AED.

Extend Visualizations:
Add more charts or analytics using Plotly and Streamlit features.

