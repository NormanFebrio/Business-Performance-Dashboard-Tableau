# Sales Performance, Customer Behavior, & Account Receivables Dashboards in One Workbook

---

## Background

The director wants to see how is the business going. He wants to know the sales performance, customer behaviors, & account receivables of each customer. The dashboards should be developed in one workbook so that it didn't make the director confuse to shift among workbooks. He also wants to see the dashboard based on **Invoice** or **Sales Order** data, depends on what he wants.

---

## Goals

-  Developed some dashboards to answer all the director's questions in one workbook
-  Interactive dashboards so that director can see the dashboard based on his desires
-  Toggle to switch between **Invoice** & **Sales Order** data

---

## Dashboards

### Sales Performance (SP)

Questions to be answered:

- How much revenue we made this month & Year-to-Date (YTD)?
- How was the performance compared to the previous period?
- Who are the most and least performing salesperson?
- Which items contribute the most to the revenue?". 

![Sales Performance Dashboard](/assets/Sales_Performance_Dashboard.png)

### Customer Performance (CP)

Questions to be answered:

- How much they spend?
- When was his/her last transaction?
- What items they bought previous year?
- What items they bought this year?
- What items they bought previous year but not in this year?

![Customer Dashboard](/assets/Customer_Dashboard.png)

### Customer Behavior & Geoloc (CB)

Questions to be answered:

- How are the customer & revenue distributions on each segment?
- How is the customer retention on each segment?

![Customer Behavior & Geoloc Dashboard](/assets/Customer_Behavior_Dashboard.png)

### Account Receivables (AR)

Questions to be answered:

- How much the account receivables the company has?
- How much the account receivables each salesperson has?

![Account Receivable Dashboard](/assets/Receivable_Dashboard.png)

---

## Parameters & Filters

This workbook uses **4 parameters** and **8 filters** to control what data is displayed. Some of them are shared across multiple dashboards, while others are scoped to specific dashboards due to dataset differences.

---

### Parameters

| Parameter | Options | Connected Dashboards |
|-----------|---------|----------------------|
| **Pilih Analisis** | MTD, YTD, Last 30D | SP, CP |
| **Data INV/SO** | Invoice, Sales Order | SP, CP |
| **Hanya Sales Terpilih** | Yes, All Sales | CP, CB |
| **Range Aging** | Global, < 7 D, >= 7 D, >= 30 D, >= 60 D, >= 90 D, >= 180 D, >= 365 D | AR |

---

### Filters

#### Shared Filters (SP - CP - CB)

The following filters are linked across the Sales Performance, Customer Performance, and Customer Behavior & Geoloc dashboards. Selecting a value on any one of these dashboards will update the data on the other two simultaneously.

| Filter | SP | CP | CB |
|--------|:--:|:--:|:--:|
| Cabang (Branch) | ✅ | ✅ | ✅ |
| Sales Name | ✅ | ✅ | ✅ |
| Kategori Produk (Product Category) | ✅ | ❌ | ❌ |
| Cluster Name | ❌ | ✅ | ✅ |
| Customer Name | ❌ | ✅ | ❌ |

> ✅ Affected &nbsp;&nbsp; ❌ Not affected

#### AR-Specific Filters

The Account Receivables dashboard uses its own independent set of filters and is **not linked** to the shared filters above.

| Filter | AR |
|--------|----|
| Cabang (AR) (Branch) | ✅ |
| Sales (AR) | ✅ |
| Customer (AR) | ✅ |

**Why are AR filters separate?**

The AR dashboard uses a different dataset from the other three dashboards. The relationship key used across SP, CP, and CB is `Sales Name` — however, in the AR context, data is viewed per customer, and a single customer can be associated with more than one salesperson. Forcing a shared filter on `Sales Name` would cause incomplete AR data to appear, as records tied to unselected salespersons would be excluded even if they belong to the same customer. To preserve data integrity, AR filters are kept independent.
