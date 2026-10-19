# FinTrack Pro

FinTrack Pro is a browser-based finance dashboard built with HTML, CSS, and JavaScript. It includes a login and registration flow, transaction tracking, a cash-flow chart, profile settings, and a currency display preference.

## What this app does

- Shows a login and register screen
- Lets users create accounts and store them in localStorage
- Validates login credentials
- Opens a dashboard after successful login
- Displays financial summary cards
- Shows a monthly cash flow chart using Chart.js
- Lets users add, delete, and filter transactions
- Supports dark mode
- Lets users update their profile name and preferred display currency
- Saves accounts, preferences, and transactions in browser storage

## Project flow

### 1. Authentication screen

When the page loads, the app checks for an existing signed-in user.

- If a user session exists in `sessionStorage` or `localStorage`, the dashboard is shown
- Otherwise, the authentication screen is shown

The login/register screen includes:

- Login and Register tabs
- Username and password fields
- A Remember me checkbox
- Links for switching between the forms

### 2. Registration flow

When a user clicks Register:

- inputs are validated
- password length is checked
- duplicate usernames are prevented
- the new account is saved in localStorage under `fintrack_accounts`
- the account starts with USD as its display currency
- the user is returned to the login form

### 3. Login flow

When a user logs in:

- the entered username and password are checked against saved accounts
- if the credentials match, a session is created
- Remember me stores the session in `localStorage`; otherwise it uses `sessionStorage`
- the dashboard is shown
- the user's name is displayed in the top navbar

### 4. Dashboard flow

After login, the dashboard shows:

- total current balance
- total income
- total expenses
- total transactions count
- cash flow chart
- transactions list
- dark mode toggle
- add transaction modal
- Settings page for profile name and preferred currency

### 5. Transactions flow

The Add Transaction button opens a modal with fields for:

- description
- type (income or expense)
- category
- amount
- date

When submitted:

- data is added to the current user's transaction list
- totals update automatically
- chart updates automatically
- transaction table refreshes

Transactions are stored separately for each user. The chart and summary values are recalculated from the signed-in user's transactions.

### 6. Delete and reset flow

Users can:

- delete individual transactions
- reset all transactions for the current user

These actions update localStorage and recalculate dashboard values.

### 7. Dark mode flow

The dark mode toggle:

- changes CSS classes on the body
- stores the state in localStorage
- keeps the selected mode on refresh

### 8. Profile and currency settings

The Settings page lets the signed-in user:

- change their profile name, which also updates the dashboard navbar
- select a display currency from USD, INR, EUR, GBP, CAD, AUD, and JPY

The selected currency is saved with the user's account and is used for summary cards, transaction amounts, and chart labels. Changing the currency changes the displayed currency format only; it does not convert stored amounts using exchange rates.

## How it works technically

This app uses:

- HTML for structure
- CSS for layout and styling
- JavaScript for interactivity
- localStorage for persistence
- Chart.js for the chart UI

## Key storage items

The app stores data in browser storage:

- `fintrack_accounts` -> registered accounts, including each user's name and currency preference
- `fintrack_current_user` -> remembered signed-in user in `localStorage`, if Remember me is selected
- `fintrack_current_user` in `sessionStorage` -> signed-in user for the current browser session when Remember me is not selected
- `fintrack_dark_mode` -> dark mode preference
- `fintrack_transactions_<userId>` -> transactions belonging to a specific user

## What I learned

From this project, I learned:

- how to build a login/register layout in HTML and CSS
- how to switch between forms using JavaScript
- how to store data using localStorage
- how to validate form input
- how to manage dashboard state after login
- how to update UI values after data changes
- how to use Chart.js with dynamic data
- how to build a reusable modal flow
- how to keep the app state consistent between refreshes
- how to save profile preferences and use a selected currency across dashboard views
- how to organize a front-end project into one single HTML file with embedded logic

## How to run it

1. Open `index.html` in a browser.
2. Register a new account.
3. Log in with that account.
4. Use the dashboard to add transactions, update profile settings, and view the totals and chart.

## Notes

This is a frontend demo project, not a production authentication or finance application. Account credentials and financial data are stored in browser storage, and passwords are not protected by a backend or secure password hashing. Do not use real passwords or sensitive financial information. The selected currency only changes formatting; it does not perform foreign-exchange conversion.
