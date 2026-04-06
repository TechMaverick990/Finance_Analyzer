# 💰 Finance Analyser

A personal finance expense tracking and visualization app built with React, TypeScript, and Recharts. Upload your bank CSV exports and instantly get beautiful charts, category breakdowns, vendor analysis, and spending trends — all in your browser, with no data ever sent to a server.

![React](https://img.shields.io/badge/React-19-blue?logo=react) ![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue?logo=typescript) ![Vite](https://img.shields.io/badge/Vite-8-purple?logo=vite) ![License](https://img.shields.io/badge/license-MIT-green)

---

## Features

- **CSV Upload** — Import one or more bank statement CSV files; remove any file (and its transactions) at any time
- **Smart Auto-Categorization** — 200+ keyword rules covering Canadian banks, grocers, telecoms, restaurants, and more
- **Interactive Charts** — Sankey flow diagram, pie chart by category, monthly bar/line trends, and vendor drill-down
- **Rich Tooltips** — Hover any chart element to see the category, dollar amount, and percentage of total spend
- **Transactions Table** — Search, filter by category, and delete individual entries with confirmation
- **Manual Entry** — Add transactions by hand without a CSV
- **Export to Excel** — Download any chart data or transaction list as a `.xlsx` spreadsheet
- **Export to JPEG** — Save any chart or the Transactions table as a high-res JPEG image
- **Dark Gold Theme** — Professional dark UI with high-contrast readability

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- [pnpm](https://pnpm.io/) (recommended) or npm/yarn

### Installation

```bash
git clone https://github.com/YOUR_USERNAME/finance-analyser.git
cd finance-analyser
pnpm install
pnpm dev
```

Open http://localhost:5173 in your browser.

### Build for Production

```bash
pnpm build
```

Output goes to the `dist/` folder — deployable to any static host (GitHub Pages, Vercel, Netlify).

---

## Project Structure

```
finance-analyser/
├── src/
│   ├── App.tsx          # Main application component and all UI
│   ├── types.ts         # TypeScript interfaces (Transaction, Category, etc.)
│   ├── utils.ts         # CSV parsing, auto-categorization, date helpers
│   ├── main.tsx         # React entry point
│   └── components/      # shadcn/ui component library
├── public/
├── index.html
├── vite.config.ts
├── tailwind.config.js
└── tsconfig.json
```

---

## Supported CSV Formats

The app auto-detects common Canadian bank CSV exports. Columns matched by header name (case-insensitive):

| Column | Accepted Names |
|--------|----------------|
| Date | `date`, `transaction date`, `posted date` |
| Description | `description`, `details`, `memo`, `narrative` |
| Amount | `amount`, `debit`, `credit`, `cad$` |

Tested with exports from RBC, TD, Scotiabank, BMO, CIBC, and Desjardins.

---

## Auto-Categorization

Transactions are automatically assigned a category based on vendor name keywords:

| Category | Example Vendors |
|----------|----------------|
| Groceries | Loblaws, Sobeys, Farm Boy, Metro, No Frills, Walmart |
| Restaurants & Dining | Tim Hortons, BarBurrito, Shaaz Indian Cuisine, Tealive |
| Utilities & Bills | Bell Canada, Virgin Plus, Reliance Home Comfort, Enercare |
| Travel | Air Canada, WestJet, Porter Airlines |
| Shopping | Amazon.ca, Dollarama, Canadian Tire, Best Buy |
| Entertainment | Cineplex, Landmark Cinemas |
| Finance & Banking | RBC, TD, Manulife, Security National Insurance |
| Fitness | GoodLife Fitness, Movati, Brookstreet Hotel |

To add your own rules, edit `CATEGORY_KEYWORDS` in `src/utils.ts`.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| React 19 | UI framework |
| TypeScript 5.9 | Type safety |
| Vite 8 | Build tool and dev server |
| Recharts | Charts (Sankey, Pie, Bar, Line) |
| Tailwind CSS 3 | Styling |
| shadcn/ui | UI component library |
| PapaParse | CSV parsing |
| Lucide React | Icons |

---

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) to get started.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
