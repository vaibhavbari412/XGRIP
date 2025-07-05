
# 📊 XGRIP Sales & Profit Executive Dashboard | Power BI
> 🚀 Advanced data analytics & storytelling with multi-source integration, currency standardization, and interactive design

![Dashboard Banner](https://github.com/vaibhavbari412/XGRIP/blob/main/Xgrip%20logo.png)

---

## 📍 **Project Overview**
In this project, I built a **dynamic Power BI executive dashboard** for XGRIP, a global mobile phone accessories brand.  
The dashboard empowers stakeholders to:
- Monitor sales & profit performance across countries 🌎
- Understand product trends & returns 📦
- Explore data interactively using light/dark modes, slicers, and drillthrough 🔍

> 🔗 [**View Live Dashboard**](https://app.powerbi.com/view?r=eyJrIjoiMDE5N2U2ZTAtZDA2Zi00MDgyLWI0MjMtZTlkYjc1ODc0MWVkIiwidCI6ImY3NDM5NmYzLTgwMTUtNGI3NC1iNDY4LWNkYTA0NTEzZDg0YyJ9)

---

## 🌟 **Highlights**
✅ Light & dark executive dashboards  
✅ Integration of **PostgreSQL, MySQL, Excel, CSV, PDF**  
✅ Automated data refresh with Power BI Gateway  
✅ Currency standardization in USD for global reporting  
✅ Advanced DAX KPIs: profit margin, YoY growth, sales trends  
✅ Row-Level Security (RLS) for secure role-based access

---

## 🧩 **Data & Modeling**
| Component                | Details                                                                 |
|------------------------:|--------------------------------------------------------------------------|
| 🔗 Sources              | PostgreSQL, MySQL, Excel, CSV, PDF                                       |
| 🏛️ Schema              | Star schema combining sales, COGS, product & returns data                |
| 🛠️ Transformation      | Power Query for cleaning, merging, currency conversion                    |
| 📐 DAX Measures        | Revenue, profit margin, target sales, YoY growth, discount analysis       |

---

## 🎨 **Dashboard Design**
- Multi-page navigation: sales overview, product insights, returns analysis
- Light & dark mode toggle 🌗
- Drillthrough on products & returns for detail view
- Map visuals, donut & radar charts, custom slicer panes

![Sales Overview](https://github.com/vaibhavbari412/XGRIP/blob/main/Dark%20Dashboard.png)
![Product Analysis](https://github.com/vaibhavbari412/XGRIP/blob/main/Product%20Analysis.png)
![Map Analysis](https://github.com/vaibhavbari412/XGRIP/blob/main/Map.png)

---

## 🧮 **Example DAX Measures**

```DAX
-- 📦 Total Profit
total profit =
SUMX(
    sales,
    sales[net_sale] - sales[qty] * RELATED(products[cogs_usd])
)
```
> Calculates profit after subtracting cost of goods sold (COGS).

---

```DAX
-- 📈 Target Revenue
target revenue =
VAR LastYearSale = CALCULATE([total revenue], SAMEPERIODLASTYEAR(sales[sale_date]))
RETURN IF(
    ISBLANK(LastYearSale),
    500000,
    LastYearSale * 1.5
)
```
> Dynamically sets sales target: last year’s sales × 1.5, or fallback to 500K.

---

```DAX
-- 🔄 KPI Orders (text with arrow)
kpi orders =
VAR CurYTD = CALCULATE([total orders], DATESYTD(date_table[Date]))
VAR LastYTD = CALCULATE([total orders], SAMEPERIODLASTYEAR(date_table[Date]))
VAR Diff = CurYTD - LastYTD
VAR AbsDiff = ABS(Diff)/1000
RETURN IF(
    ISBLANK(LastYTD),
    "No sale in last year",
    IF(Diff > 0,
        FORMAT(AbsDiff, "0.0") & "K More than last year (▲)",
        FORMAT(AbsDiff, "0.0") & "K Less than last year (▼)"
    )
)
```
> Text-based KPI that shows increase/decrease vs last year, with arrow.

---

```DAX
-- 🛡️ Row-Level Security (RLS) example
[country] = "India"
```
> Restricts view to data only from India.

---

```DAX
-- 📅 Calendar Table
date_table =
ADDCOLUMNS(
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Quarter", "Q" & FORMAT([Date], "Q YYYY"),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMM")
)
```
> Creates dynamic calendar table for time intelligence.

---

## 📊 **Business Impact**
✅ Unified data across regions for consistent decision making  
✅ Identified top & low-performing products → better inventory planning  
✅ Visualized seasonal trends & profit margins → support marketing campaigns  
✅ Protected sensitive data via RLS → secure & compliant reporting

---

## 🛠️ **Tech Stack**
- **Tools:** Power BI Desktop, Power Query, DAX
- **Data Sources:** PostgreSQL, MySQL, Excel, CSV, PDF
- **Automation:** Power BI Gateway

---

## 🧰 **Key Learnings**
- Multi-source integration & standardization
- Advanced DAX for dynamic KPIs
- Interactive UX design in Power BI
- Automation & data security with scheduled refresh + RLS

---

## 🚀 **How to Use the Dashboard**
1. Open live link or PBIX locally
2. Use slicers (region, product, time)
3. Drillthrough to deep-dive product/returns
4. Toggle light/dark mode based on preference

---

## 📂 **Repository Structure**
```
📦 XGRIP_PowerBI_Dashboard
├── Images/
│   ├── dark dashboard.png
│   ├── product.png
│   ├── dark map.png
│   └── light dashboard.png
├── XGRIP_Executive_Dashboard.pbix
└── README.md
```

---

## ⭐ **Like this project?**
If you found it useful or interesting:
- ⭐ Star this repo
- 🔗 Connect on [LinkedIn](https://www.linkedin.com/in/your-profile)
- 📧 Contact: vaibhavbari@example.com

> *Data storytelling isn't just numbers — it tells the business story behind them!*
