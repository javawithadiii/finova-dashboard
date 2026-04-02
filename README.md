# Finova — Finance Dashboard

A clean, interactive finance dashboard built as a frontend assignment. Finova lets users track income, expenses, and spending patterns through a polished dark-mode interface — all running in a single HTML file with no build tools required.

---

## Live Preview

Open `index.html` directly in any modern browser. No server, no installation needed.

```bash
# Option 1 — just open the file
open index.html

# Option 2 — serve locally with Python
python -m http.server 8000
# then visit http://localhost:8000

# Option 3 — serve with Node
npx serve .
```

---

## Features

### Dashboard Overview
- **4 summary cards** — Total Balance, Income, Expenses, and Savings Rate with trend indicators
- **Balance Trend chart** — line chart showing cumulative balance over time, with 6-Month and All-time toggles
- **Spending Breakdown** — donut chart showing top categories by expense with a percentage legend
- **Income vs Expenses** — grouped bar chart comparing monthly income and spending side by side

### Transactions
- Full table with date, description, category, type badge, and amount
- **Search** by description or category name
- **Filter** by type (income/expense) and by category
- **Sort** by newest, oldest, highest amount, or lowest amount
- Row count summary updates dynamically with filters
- Empty state shown when no results match

### Role-Based UI (Simulated)
Switch roles using the dropdown in the sidebar:

| Feature | Admin | Viewer |
|---|---|---|
| View dashboard & charts | ✅ | ✅ |
| Browse & filter transactions | ✅ | ✅ |
| Add new transaction | ✅ | ❌ |
| Remove a transaction | ✅ | ❌ |
| Export CSV | ✅ | ❌ |

No backend required — role state is managed in JavaScript and UI elements are shown or hidden accordingly.

### Insights
- Highest spending category with a mini spark bar chart
- Month-on-month expense comparison (increase or decrease)
- Average monthly spend across all recorded months
- Net savings (all-time balance)
- Best income month
- Transaction count breakdown
- Monthly spending comparison bar chart (most recent month highlighted)

### Bonus Features
- **Dark mode** — full dark theme throughout, no toggle needed
- **Data persistence** — transactions saved to `localStorage` so data survives page refresh
- **Export CSV** — downloads all transactions as a `.csv` file (Admin only)
- **Responsive layout** — works on mobile with a hamburger sidebar, cards reflow to 2 columns
- **Empty state handling** — graceful messages when filters return no results

---

## Project Structure

```
finova/
└── index.html       # Complete app — HTML, CSS, and JS in one file
└── README.md        # This file
```

Everything is contained in a single `index.html` for simplicity. The structure inside it is:

- **CSS variables** — theming and color palette at the top in `:root`
- **Layout** — fixed sidebar + scrollable main content area
- **View system** — three views (Dashboard, Transactions, Insights) toggled by JS
- **Chart rendering** — Chart.js via CDN, re-rendered on data changes
- **State** — plain JavaScript arrays and variables; no framework needed

---

## Approach & Decisions

**No framework** — vanilla JS was chosen to keep the project dependency-free and immediately runnable. The state (transactions array, current role, active filters) is managed directly in JS variables, which is appropriate for this scope.

**Single file** — keeping everything in `index.html` makes it trivially easy to open and submit. In a production project this would be split into components.

**Mock data** — 30 transactions across 3 months (June–August 2025) are pre-loaded to demonstrate all charts and insights meaningfully. New transactions added via the form persist via `localStorage`.

**Role-based UI** — implemented as a simple string variable (`currentRole`) that controls `display` on admin-only elements. A real RBAC system would verify roles server-side, but this demonstrates the UI behavior clearly.

**Chart.js** — loaded from CDN (no install needed). Each chart is destroyed and re-created when data changes to avoid stale state.

---

## Dependencies

| Library | Version | Source |
|---|---|---|
| Chart.js | 4.4.1 | cdnjs CDN |
| DM Sans font | — | Google Fonts |
| DM Serif Display | — | Google Fonts |

No npm install, no bundler, no build step.

---

## Screenshots

> Open `index.html` in a browser to see the live dashboard.

The three main views:
- **Overview** — summary cards, trend line, donut chart, bar chart
- **Transactions** — filterable, searchable table with role-gated actions
- **Insights** — 6 KPI cards + monthly comparison chart

---

## Notes

- The app works fully offline after initial font load (fonts are from Google Fonts CDN)
- localStorage is used for persistence; clearing browser data resets to the default mock transactions
- The role switcher is intentionally in the sidebar so reviewers can easily toggle between Admin and Viewer modes
