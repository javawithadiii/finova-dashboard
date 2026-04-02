# Finova – Finance Dashboard

A frontend assignment project. I built a finance dashboard where users can track their income, expenses, and spending habits. Everything runs in a single HTML file — no frameworks, no build tools, just open it in a browser.

---

## How to run it

Just download the repo and open `index.html` in your browser. That's it.

If you prefer a local server:
```bash
npx serve .
```
Then go to `http://localhost:3000`

---

## What I built

### Overview page
Shows a summary of your finances at a glance — total balance, income, expenses, and savings rate. There's a balance trend line chart, a spending breakdown donut chart by category, and a monthly income vs expenses bar chart. The line chart has a 6M / All toggle.

### Transactions page
A full table of all transactions with search, filters (by type and category), and sorting (by date or amount). Admins can add new transactions via a form and remove existing ones. Viewers can only read.

### Insights page
Some useful observations pulled from the data — highest spending category, whether expenses went up or down compared to last month, average monthly spend, best income month, and overall totals.

---

## Role-based UI

There's a dropdown in the sidebar to switch between **Admin** and **Viewer**.

- **Admin** — can add transactions, remove them, and export to CSV
- **Viewer** — read-only, all write actions are hidden

It's simulated on the frontend to demonstrate the concept.

---

## A few extras I added

- Data saves to `localStorage` so it persists on refresh
- Export to CSV (Admin only)
- Responsive layout with a hamburger menu on mobile
- Inline form validation with error messages (no ugly alert popups)
- Empty state when search/filters return nothing

---

## Tech used

- Vanilla HTML, CSS, JavaScript — no framework
- Chart.js for the charts (loaded from CDN)
- DM Sans + DM Serif Display from Google Fonts
- localStorage for persistence

---

## Folder structure

```
finova/
├── index.html   # entire app lives here
└── README.md
```

I kept everything in one file to keep it simple and easy to run without any setup.
