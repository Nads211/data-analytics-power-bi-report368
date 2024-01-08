# Create the Data Model

### Create a Date table

In order to make use of Power BI's time intelligence functions, you will need to make a continuous date table, covering the entire time period of our data.

Create a date table running from the start of the year containing the earliest date in the Orders['Order Date'] column to the end of the year containing the latest date in the Orders['Shipping Date'] column. You can use whichever DAX formula you prefer to create the table.

Now use DAX formulas to add the following columns to your date table:
- Day of Week
- Month Number (i.e. Jan = 1, Dec = 12 etc.)
- Month Name
- Quarter
- Year
- Start of Year
- Start of Quarter
- Start of Month
- Start of Week

### Build Star Scheme Data Model

Create relationships between the tables to form a star schema. The relationships should be as follows:
- Orders[product_code] to Products[product_code]
- Orders[Store Code] to Stores[store code]
- Orders[User ID] to Customers[User UUID]
- Orders[Order Date] to Date[date]
- Orders[Shipping Date] to Date[date]

Ensure that the relationship between Orders[Order Date] and Date[date] is the active relationship, and that all relationships are one-to-many, with a single filter direction from the one side to the many side

### Create Measures table

Creating a separate table for measures is a best practice that will help us keep our data model organized and easy to navigate. You will be creating a lot of measures in this project, so it's important manage them effectively. There are two ways to do this. You can either create a new table using DAX, or you can create a new table in the data Model View with Power Query Editor. It is generally better to use the latter approach, as it makes the measures table visible in the Query Editor, which is useful for debugging and troubleshooting.


From the Model view, select Enter Data from the Home tab of the ribbon

Name the new blank table Measures Table and then click Load

### Create Key measures

Next, you are going to create some of the key measures that will be used in our report. You will need to create more as you go through the project, but these will give you a starting point for building the analysis:

Measures created:
- Total Orders: counts the number of orders in the Orders table
- Total Revenue: multiplies the Orders[Product Quantity] column by the Products[Sale_Price] column for each row, and then sums the result
- Total Profit: performs the following calculation: For each row, subtract the Products[Cost_Price] from the Products[Sale_Price], and then multiply the result by the Orders[Product Quantity] & Sums the result for all rows
- Total Customers: counts the number of unique customers in the Orders table. This measure needs to change as the Orders table is filtered, so do not just count the rows of the Customers table!
- Total Quantity: counts the number of items sold in the Orders table
- Profit YTD: calculates the total profit for the current year
- Revenue YTD: calculates the total revenue for the current year


### Create Date and Geography Hierarchies

Hierarchies allow you to drill down into our data and perform granular analysis within our report. You will create two hierarchies in this task: one for dates, to facilitate drill-down in your line charts, and one for geography, to allow you to filter our data by region, country and province/state.


Create a date hierarchy using the following levels:

Start of Year
Start of Quarter
Start of Month
Start of Week
Date

Create a new calculated column in the Stores table called Country that creates a full country name for each row, based on the Stores[Country Code] column, according to the following scheme:
GB : United Kingdom
US : United States
DE : Germany

In addition to the country hierarchy, it can sometimes be helpful to have a full geography column, as in some cases this makes mapping more accurate. Create a new calculated column in the Stores table called Geography that creates a full geography name for each row, based on the Stores[Country Region], and Stores[Country] columns, separated by a comma and a space.

Ensure that the following columns have the correct data category assigned, as follows:

World Region : Continent
Country : Country
Country Region : State or Province

Create a Geography hierarchy using the following levels:

World Region
Country
Country Region
