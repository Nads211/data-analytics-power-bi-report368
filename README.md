# data-analytics-power-bi-report368
Readme file

The first phase of the project focuses on data loading and preparations. We will connect to an Azure SQL Database, a Microsoft Azure Storage account, and web-hosted CSV files to import the necessary components of the dataset. Once imported, we will clean and organise the data by removing irrelevant columns, splitting data-time details and ensuring data consistency. The final step involves renaming the columns to fit Power BI conventions. This sets the stage for the next parts of the project.

The dataset consists of 4 tables:
- Orders fact table
- Products dimension table
- Stores dimension table
- Customers dimension table
- data table (not pre-existing, created in this project)


The Orders table is your main fact table. It contains information about each order, including the order and shipping dates, the customer, store and product IDs for associating with dimension tables, and the amount of each product ordered. Each order in this table consists of an order of a single product type, so there is only one product code per order.

