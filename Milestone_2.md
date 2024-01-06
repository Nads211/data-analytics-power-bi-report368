# Milestone_2: Load and Transform Data using Power Query Editor

## Load and Transform Orders Table

**Source**: Azure SQL Database
server_name = my-server-maya.database.windows.net
database_name = orders_db
username = maya
password = AiCore127!

**Import Method**: SQL server database data connector. Enter the Database credentials and import the orders_powerbi table

**Transformations**:
- delete [Card Number] column to ensure data privacy
- use the Split Column feature to separate the [Order Date] and [Shipping Date] columns into two distinct columns each: one for the date and another for the time. Creates [Order Date], [Order Time], [Shipping Date], [Shipping Time] columns.
- Filter out and remove any rows where the [Order Date] column has missing or null values to maintain data integrity
- renamed the columns to align with Power BI naming conventions
- Change data types for better formatting

## Load and Transform Products Table

**Source**: Download Products.csv file.  and then use Power BI's Get Data option to import the file into your project

**Import Method**: Text/csv data connector

**Transformations**:
- Remove Duplicates function on the product_code column to ensure each product code is unique
- transformed [weight ] column into [Weight in kg] to make for easier comparison to units
    - used the Column From Examples feature to generate two new columns from the weight column - [Weight Values] and [Weight Units]
    - replace any blank entries in [Weight Units] with kg. (Although, this means that the few products that are listed in ml are now in kg which is a data discrepancy. But for the sake of following indtructions for this course, we include this step here for simplicity) 
    - convert the data type in [Weight Values] to a decimal number
    - This resulted in some errors during the conversion. Replaced those error values with the number 1. (Again, this introduced false values but we continue for simplicity. This affects those products sold in multi-packs where the weight was listed as 2x50g for eg., so string '2x50' conversion to decimal caused errors.)
    - created a new calculated column named [Weight in kg], such that if the unit in the units column is not kg, divide the corresponding value in the values column by 1000 to convert it to kilograms. Formula used: `= if [Weight Units] <> "kg" then [Weight Values] / 1000 else [Weight Values]`
    - Remove unneeded coluns [Weight Values] and [Weight Units]
- renamed the columns to align with Power BI naming conventions
- Change data types for better formatting


## Load and Transform Stores Table

**Source**: Blob Storage 
credentials:
- account_name = powerbistorage2
- Account Key = ZPUQ+verSniHMG7EqR5/VAQc0aUYYG1utLQQuke0JQqR18TRRZI1/vTX65OqeXfUgWAugYLL73Gp+AStozRNKw==
- Container Name = data-analytics

**Import Method**: Azure Blob Storage data connector, then extract Stores table into the project

**Transformations**:
- renamed the columns to align with Power BI naming conventions
- Removed [Source.Name] column as this is not needed and was created from the combination of the files 
- Change data types for better formatting

## Load and Transform Customers Table

**Source**: Downloaded to local machine in a Customers.zip file. The zip file contains three CSV files, each with the same column format, one for each of the regions in which the company operates.

**Import Method**: Using the Folder data connector, the Combine and Transform button was used to import the data where Power BI automatically appended the three files into one query.

**Transformations**: 
- created [Full Name] column by combining the [First Name] and [Last Name] columns
- Removed [Source.Name] column as this is not needed and was created from the combination of the files
- renamed the columns to align with Power BI naming conventions
