# Architecture

## Component structure

- `src/App.jsx` is the top-level component. It owns the transactions state and passes transaction data and callbacks to child components.
- `src/Summary.jsx` receives the transactions array and calculates total income, total expenses, and balance before rendering the summary cards.
- `src/TransactionForm.jsx` owns the form field state, validates and converts the entered amount to a number, and calls `onAddTransaction` with a new transaction.
- `src/TransactionList.jsx` receives transactions and categories, owns the type and category filters, and renders the filtered transaction table.
- `src/App.css` contains shared styles for the summary, form, filters, and transaction table.

## Data flow

`App` is the source of truth for transactions. `TransactionForm` sends new transactions to `App` through `onAddTransaction`; `App` appends them to state. The updated array is then passed to both `Summary` and `TransactionList`, keeping totals and the table in sync. Filtering is local to `TransactionList` and does not modify the source transactions.

Transaction amounts are stored as numbers, including the initial data and newly submitted transactions.
