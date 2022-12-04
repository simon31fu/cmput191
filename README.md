# CMPUT 191 Assignment 3

The goal of the assignment was to examine the concept of purchasing power parity. Similar to the Big Mac index tool that examines the same concept, we created a similar index that instead examines the prices of Red Bull by country.

Let's start by creating a few user defined functions:
![UDFs](1.png "UDFs")

These functions make displaying and scraping tables more efficient, and was the first cell we coded incase we needed to display or scrape multiple tables.

Next we create our tables:
![tables](2.png "Tables")

We decided to first make a seperate table for each of the columns we needed, with the rationale that it would make cleaning and tidying up data further on more efficient. The first table includes Red Bull prices by country, followed by another table for country currencies and their respective currency codes, then another of exchange rates between countries, and finally one table for country tax rates.

Then we clean our data:
![clean](2.png "Tidying Up")

First all the tables need to be normalized, relabelled, and formatted. The process involves relabelling columns, dropping any columns that are not needed, stripping, and splitting values (described in depth in the code cell comments). After tidying up our tables, we join them together to make one full table.
![join](2.png "Combine")

Of course, there were unexpectedly some issues:
![manual](2.png "Manual")
Because our tax rate table contained extra information, it had to be manually cleaned. With comments made in the code cell for rationales of specific value changes.
Once our tax rates were cleaned, we reformatted our columns again and added another column for prices in domestic currency to complete cleaning and tidying our data.
