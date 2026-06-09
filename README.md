<div align="center">

<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI"/>
<img src="https://img.shields.io/badge/Status-Complete-10B981?style=for-the-badge" alt="Status"/>
<img src="https://img.shields.io/badge/Theme-Professional%20Navy-0F2044?style=for-the-badge" alt="Theme"/>

# 🏭 Global Manufacturing Intelligence Dashboard

**A multi-page Power BI report analysing workforce performance, production costs, and operational efficiency across global manufacturing markets.**
</div>

---

## Overview

This dashboard provides a comprehensive view of manufacturing operations across multiple countries and industries. It connects workforce data - salaries, performance, tenure - with production cost metrics to surface strategic insights for leadership and operations teams.

Built entirely in **Power BI Desktop** with a custom Professional Navy theme, it requires no external database or API connection. Just open and explore.

---

## Pages Overview

| Page | Description |
|------|-------------|
| 📦 **Product** | Production cost breakdown by country and industry · Cost-per-unit trends · Automobile vs. other sector comparisons |
| 👥 **Employee** | Salary trends over time · Performance ratings by department and region · Headcount distribution · Average tenure |
| 📖 **Story Telling** | Executive narrative - 7 curated insights derived directly from the data, written for leadership consumption |

---

## Key Findings

> Full narrative available on the **Story Telling** page inside the dashboard.

- 🇯🇵 &nbsp;**Japan** is the only market with a positive salary-performance correlation - a replicable model for other regions
- 📉 &nbsp;**Average salaries have declined since 2021**, creating compounding talent retention risk if left unaddressed
- 🌏 &nbsp;**Asia-Pacific leads on cost efficiency** - Japan holds the second-lowest cost per unit after China
- 🚗 &nbsp;**The automobile sector** records the highest average production costs across all industries in scope
- 🏆 &nbsp;**Logistics is the top-performing department** globally - highest performance rating and longest average employee tenure
- 🇺🇸 &nbsp;**The USA shows the clearest salary-to-cost link** - highest salaries directly correlate with highest production costs, flagging automation as a strategic priority

---

## Getting Started

### Prerequisites

- [Power BI Desktop](https://powerbi.microsoft.com/desktop) (free) — Windows only

### Installation

```bash
# Clone this repository
git clone https://github.com/your-username/manufacturing-dashboard.git

# Navigate to the project folder
cd manufacturing-dashboard
```

### Opening the Dashboard

1. Launch **Power BI Desktop**
2. Go to **File → Open report** → select `Manufacturing_Analysis_Dashboard_Redesigned.pbix`
3. If prompted about data sources, click **Edit** and point each query to the CSV files.
4. Click **Close & Apply** - visuals will populate automatically

---

## Repository Structure

```
manufacturing-dashboard/
│
├── 📊 Manufacturing_Analysis_Dashboard_Redesigned.pbix   # Main Power BI file
│
└── 📄 README.md
```

---

## Data Model

```
Orders                          Details
──────────────────              ──────────────────────────
Order ID  (PK) ──────────────── Order ID  (FK)
Order Date                      Amount
CustomerName                    Profit
State                           Quantity
City                            Category
                                Sub-Category
                                PaymentMode
```

> **Relationship:** `Details[Order ID]` → `Orders[Order ID]` · Many-to-One · Single direction

---

## DAX Measures

| Measure | Formula | Purpose |
|---------|---------|---------|
| `Total Sales` | `SUM(Details[Amount])` | Gross revenue |
| `Net Profit` | `SUM(Details[Profit])` | Total profit |
| `Profit Margin %` | `DIVIDE([Net Profit], [Total Sales], 0) * 100` | Margin rate |
| `Avg Order Value` | `DIVIDE([Total Sales], DISTINCTCOUNT(Details[Order ID]), 0)` | AOV |
| `Total Quantity` | `SUM(Details[Quantity])` | Units sold |
| `Profit Status` | `IF([Net Profit] >= 0, "Profitable", "Loss")` | Conditional flag |
| `Sales Rank` | `RANKX(ALL(Details[Sub-Category]), [Total Sales], , DESC, DENSE)` | Sub-category ranking |

> ⚠️ **Note:** Use `Net Profit` — not `Total Profit` - to avoid conflicts with Power BI's auto-generated implicit measure on the `Profit` column.

---

## Theme

This report uses a custom **Professional Navy** theme. To reapply after any Power BI update:

**View → Themes → Browse for themes → select `theme/EcommerceDashboard.json`**

| Role | Hex | Preview |
|------|-----|---------|
| Primary accent | `#2563EB` | ![#2563EB](https://img.shields.io/badge/-%232563EB-2563EB) |
| Sky blue | `#0EA5E9` | ![#0EA5E9](https://img.shields.io/badge/-%230EA5E9-0EA5E9) |
| Emerald | `#10B981` | ![#10B981](https://img.shields.io/badge/-%2310B981-10B981) |
| Amber | `#F59E0B` | ![#F59E0B](https://img.shields.io/badge/-%23F59E0B-F59E0B) |
| Purple | `#7C3AED` | ![#7C3AED](https://img.shields.io/badge/-%237C3AED-7C3AED) |
| Deep navy | `#0F2044` | ![#0F2044](https://img.shields.io/badge/-%230F2044-0F2044) |
| Page background | `#F1F5F9` | ![#F1F5F9](https://img.shields.io/badge/-%23F1F5F9-F1F5F9) |

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-analysis`)
3. Commit your changes (`git commit -m 'Add regional breakdown page'`)
4. Push to the branch (`git push origin feature/new-analysis`)
5. Open a Pull Request

---

## License

Distributed under the MIT License. See `LICENSE` for more information.

---

<div align="center">

Made with ❤️ using &nbsp;<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black" alt="Power BI" style="vertical-align:middle"/>

</div>
