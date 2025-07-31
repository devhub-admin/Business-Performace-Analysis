![Static Badge](https://img.shields.io/badge/Excel-%2300B050?style=flat-square&logo=excel&label=Platform)
![Static Badge](https://img.shields.io/badge/Completed-green?style=flat-square&label=Status)
![Static Badge](https://img.shields.io/badge/July%202025-blue?style=flat-square&logo=excel&label=Last%20Updated)

## :rocket: Project Description
This **_fictitious_** `Excel` dashboard project is a comprehensive visual covering three related aspects of business performance - Sales, Product, and Logistics. It provides both high-level and granular views of company performance across years, geographies, products, and product-lines. Equips decision-makers with necessary insights needed to streamline business operations, pricing strategies, and drive organizational growth.

## :pushpin: Objectives
+ Track revenue, profit, and order metrics over specified duration - yearly, quarterly, monthly.
+  Track product performance and pricing efficiency.
+  Monitor supply chain trends, freight costs and shipments.

## :brain: Insights
+ Identify sales patterns overtime based on such needs as region, product line, or year
+ Understanding the impact of discounts on gross margins
+ Flagging logistical bottlenecks
+ Monitoring lead times and regional demands

## :hammer_and_wrench: Tools Used

This project combined several powerful tools to facilitate data analysis, modeling, and visualization. The following is a breakdown of each tool, how it was used, and relevant examples where applicable.

---

### Microsoft Excel

  Used for summary statistics, lookups / dynamic array builders, and visualizations. Excel provided an intuitive platform for quick calculations.
  
  + Summary Statistics: Functions such as `MAX()` and `MIN()` were used to understand data distributions and determine outliers.
  + Lookup: Functions like `OFFSET()` were used to dynamically reference a range of data based on its size or position. Critical when the size of the data varied. Example `=OFFSET($G$4,1,0,COUNTA($G$5:$G$14),3)`  
  + Visualizations: Built-in charts such as **_Filled Maps_** were used to explore spatial trends and relationships between variables.
  
##### Pivot Tables
  
  The data set involved over **_60,000_** records. Pivot tables played a crucial role in
  
   + Summarizing thousands of records into compact insights.
   + Enable drill-down by region, time or product.
 
 Combined with Excel's `GETPIVOTDATA()` function to allow for referencing of Pivot Table results as formulas 
 
 ```js
//Example 
 =GETPIVOTDATA("[Measures].[Sum of OrderQuantity]",'A-product_analysis'!$R$18)
 ```

> Although a majority of statistical computations and transformations were done via `DAX` in data model and `Power Query` respectively, Excel played a vital role -- provided a flexible and friendly interface for presenting, and interacting with results. 

### Power Pivot (DAX)

  Power Pivot enabled advanced data modelling. **DAX (Data Analysis eXpression)** was used to define relationships in the data model, logic and KPI's (Key Performance Indicators).

  + Measures: defined aggregations used in reports or visual e.g., `Revenue := SUM('D-data'[SalesAmount])`
  + Calculated Columns: used for row-level calculations.

### Power Query (M Code)

  Power Query was used as the **ETL (Extract, Load, and Transform)** engine. It handled:
  
  + Data import
  + Cleaning and normalizing data
  + Removing nulls, duplicates, and splitting columns

```js
//Sample M Code 
let
    Source = Csv.Document(File.Contents("C:\Users\Lenovo\Desktop\Comprehensive-Business-Analysis\FactInternetSales.csv"),[Delimiter=",", Columns=23, Encoding=65001, QuoteStyle=QuoteStyle.None]),
    #"Promoted Headers" = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"ProductKey", Int64.Type}, {"OrderDateKey", Int64.Type}, {"DueDateKey", Int64.Type}, {"ShipDateKey", Int64.Type}, {"CustomerKey", Int64.Type}, {"PromotionKey", Int64.Type}, {"CurrencyKey", Int64.Type}, {"SalesTerritoryKey", Int64.Type}, {"SalesOrderNumber", type text}, {"SalesOrderLineNumber", Int64.Type}, {"OrderQuantity", Int64.Type}, {"UnitPrice", Currency.Type}, {"UnitPriceDiscountPct", Percentage.Type}, {"DiscountAmount", Currency.Type}, {"ProductStandardCost", Currency.Type}, {"TotalProductCost", Currency.Type}, {"SalesAmount", Currency.Type}, {"TaxAmt", Currency.Type}, {"Freight", Currency.Type}, {"CarrierTrackingNumber", type text}, {"OrderDate", type date}, {"DueDate", type date}, {"ShipDate", type date}}),
    #"Filtered Rows" = Table.SelectRows(#"Changed Type", each true),
in
    #"Filtered Rows"
 ```
### Microsoft Project
  
  Used for project planning, task and timeline management. Created Gantt Chart, and milestone tracking to ensure timely delivery of project deliverables. 
  
### Shields.io
  
  Used to create appealing badges for the README.md file. The badges provide key information on project status, platform, and month of last update.
  
  Access _Shields.io_ from https://shields.io
  
---
## :bar_chart: Dashboards

This section shows dashboards covering **Sales**, **Product**, and **Logistics** performance. They are equipped with interactive visuals and **slicers** for dynamic filtering by such criteria as time, region, and PO (Production line). The dashboards help simplify complex data set, and highlight key trends thereby supporting strategic decision-making. Collectively, they offer a holistic view of how business areas relate and evolve over time.


### Sales Overview

This dashboard monitors sales performance over time — tracking revenue, tax liabilities, and contribution across years, quarters, and months.

![Sales Overview](https://raw.githubusercontent.com/devhub-admin/Business-Performace-Analysis/main/Comprehensive-Business-Analysis/Images/Sales%20Overview.PNG)

### Product Performance

This dashboard dives into individual product performances, analyzing sales volume, cost, and margin realization.

![Product Performance Overview](https://raw.githubusercontent.com/devhub-admin/Business-Performace-Analysis/main/Comprehensive-Business-Analysis/Images/Product%20Performance.PNG)


### Logistics Overview

This dashboard provides insights into supply chain and logistics metrics including lead times, sales orders by geography, average freight costs, and shipments.

![Logistics Overview](https://raw.githubusercontent.com/devhub-admin/Business-Performace-Analysis/main/Comprehensive-Business-Analysis/Images/Logistics.PNG)
---

## :package: Installation guide
  
To explore and interact with the Business Performance Analysis Dashboards, follow these steps:  

1. Download or Clone repository

    ```js
    git clone https://github.com/devhub-admin/Business-Performace-Analysis.git
    ```

    Alternatively, click `Code > Download ZIP` and extract to local machine

2. Open Excel dashboard

    Navigate to the Comprehensive-Business-Analysis folder and open the `Dashboard.xls` file. Use **Microsoft Excel (2016 or later)**

    > :bulb: Allow external connections if prompted.

3. Enable Add-ins

    Ensure the following Excel Add-ins are enable:

    + Power Pivot
    + Power Query

    Else enable them via:
    ```js
    File → Options → Add-ins → Manage COM Add-ins → Go → Check required tools
    ```

4. Explore Dashboard
  
    Use the *slicers* to:
  
    + Filter data by year, region etc.
    + Gain actionable insights through visuals and summary statistics


## :memo: Contact 

If you have feedback, questions, and collaboration enquiries reach out:

**_Email:_** chisomale01@outlook.com

**_Github:_** @devhub-admin

> Always open to connecting with fellow data enthusiasts and professionals in analytics. 


## :books: Acknowledgements
 
Special thanks to the individuals and resources that inspired and capacitated the completion of the project

  + Mynda Treacy _(@MyOnlineTrainingHub_) - for her amazing dashboarding tutorials that shaped design of the project.
  + Luke Barousse _(www.youtube.com/@LukeBarousse)_ - for simplifying complex data concepts. 
  + Excel Bible – a go-to reference that strengthened my Excel capabilities.   

