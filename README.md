# Data Analytics Power BI Report

    This is a data analytics project using Power BI as part of course certification with AiCore.

    This is my first time using PowerBI and I enjoyed learning how to use it and seeing the powerful visualisations that can be created from it. I have used: loaded and combined csv files, loaded data from the cloud, used PowerQuery to clean the data, create measures and aggregate values, created calculated columns using DAX, create data heirarchies, use a variety of visuals, use buttons to create a navigation bar, use advanced tooltips, create drillthough page, and managed cross filtering interactions between visuals.

## Project File Structure

- **Data_Analytics_PowerBI_Report.bpix** - main report
- **Data_Analytics_PowerBI_Report.pdf** - report exported as pdf for ease
- **Source Data** - folder containing csv files used to load the data
- **navigation_bar_images** - folder with customer icons intended for the navigation bar

Supporting markdown files detailing the process:
- Milestone_2: Load and Transform Data using Power Query Editor
- Milestone_3: Create the Data Model

## The Project

The first phase of the project focuses on data loading and preparations. We will connect to an Azure SQL Database, a Microsoft Azure Storage account, and web-hosted CSV files to import the necessary components of the dataset. Once imported, we will clean and organise the data by removing irrelevant columns, splitting data-time details and ensuring data consistency. The final step involves renaming the columns to fit Power BI conventions. This sets the stage for the next parts of the project.

The next step is to construct the data model for the project. We build a comprehensive Data table to act as a basis for time intelligence in our data model. Next we establish relationships between key tables, building a star-based scheme with one-to-many relationships and single filter direction.

Following this, we create vital measures using DAX formulas, E.g. total orders, total revenue and quarter-based performance indicators. We create a Measures Table to organise all these together. We also establish date and geography hierarchies.

Finally we create the 4 page report on Power BI Desktop, using a variety of visuals and features. We utilise cross-filtering, navigation buttons, drill through and tooltip pages to create an interactive report.


## Structure

## Tables
#### 
- **Orders**
    - The Orders table is your main fact table. It contains information about each order, including the order and shipping dates, the customer, store and product IDs for associating with dimension tables, and the amount of each product ordered. Each order in this table consists of an order of a single product type, so there is only one product code per order.
    - Extracted from Azure SQL Database
- **Products**
    - The Products table contains information about each product sold by the company, including the product code, name, category, cost price, sale price, and weight.
    - Loaded from *Products.csv*
- **Stores**
    - The Stores table contains information about each store, including the store code, store type, country, region, and address.
    - Extracted from Blob Storage
- **Customers**
    - The Cutomers table contains details of the customers across 3 regions, such as name, date of birth, address, etc.
    - Loaded as a combination of 3 csv files in *Customers* folder
- **Date Table**
    - Created in this project
- **Measures Table**
    - Created in this project


## Report Pages

### Executive Summary
Report page for the high level executive summary. Purpose of this page is to give an overview of the company's performance as a whole, so that C-suite executives can quickly get insights and check outcomes against key targets.

Contains the following visuals:
- card visual showing Total Revenue, Total Profit and Total orders
- graph of revenue against time
Donut chart showing orders and revenue by country
- bar chart of orders by category
- KPIs for QUarterly revenue, customers and profit
- table of the top 10 products

### Customer Detail
Customer Detail Page focuses on customer-level analysis.

Contains the following visuals:
- Card visuals for the total distinct customers and revenue per customer
- A line chart of weekly distinct customers
- A table showing the top 20 customers by total revenue, showing hte revenue per customer and the total orders for each customer
- A donut chart showing number of customers by country, and a bar chart showing number of customers by product catagory
- A set of three card visuals showing the name, number of orders, and revenue for the top customer by revenue
- A data slicer

### Product Detail

Purpose of this report page is to provide in-depth look at which products within the inventory are performing well, with the option to filter by product and region.

Visuals:
- card visuals to show which filters are currently selected
- gauge visuals to show how the selected category's revenue, profit and number of orders are performing angainst a quarterly target.
- area chart showing relative revenue performance of each category over time
- table showing top 10 products by revenue in the selected context
- scatter graph of quantity ordered against profit per item for products in the current context.

### Stores Map

Page for the regional managers to easily check on the stores under their control, allowing them to see which sotres they are responsible for are most profitable, as well as which are on track to reach their quarterly profit and revenue targets.

Visuals and features:
- Map visual allowing drill down from high level country view, to regional detail, With bubbles denoting the Profit YTD of the store
- Slicer to filter the countries
- Drill through page that summarises each store's performance. Contains:
    - A Card visual showing the currently selected store
    - A table showing the top 5 products, with columns: Description, Profit YTD, Total Orders, Total Revenue
    - A column chart showing Total Orders by product category for the store
    - Gauges for Profit YTD against a profit target of 20% year-on-year growth vs. the same period in the previous year
- advanced tooltip to see each store's year-to-date profit performance against the profit target just by hovering the mouse over a store on the map
