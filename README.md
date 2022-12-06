# CMPUT 191 Assignment 3

The goal of the assignment was to examine the concept of purchasing power parity. Similar to the Big Mac index tool that examines the same concept, we created a similar index that instead examines the prices of Red Bull by country.

### Purchasing Power Parity
* "The rates of currency conversion that try to equalize the purchasing power of different currencies, by eliminating the different price levels between countries (OECD) (https://data.oecd.org/conversion/purchasing-power-parities-ppp.htm)
* Macroeconomic analysis measure
* Can be used to predict and forecast exchange rates, create economic policy, and examine real changes in foreign exchange securities and derivatives
* Can also be used to normalise GDP figures

### Why a Red Bull Index?
* Red Bull is the archetype brand of the energy drink market, having created the market when it first released its product in 1987. Over 10 billion cans have been sold since (https://www.redbull.com/int-en/energydrink/red-bull-is-safe)
* Red Bull is also the most valuable energy drink brand in the world, according to Interbrand (https://interbrand.com/best-global-brands/red-bull/), and uses premium positioning to resist price adjustments due to competing brands

## Our Analysis

### Creating functions
Let's start by creating a few user defined functions, which we drew from labs and assignments:

![UDFs](1.png "UDFs")

These functions make displaying and scraping tables more efficient, and was the first cell we coded.

### Importing Data
Next we create our tables:


![tables](2.png "Tables")

We imported our tables separately for the data needed, with the rationale that data cleaning would be easier on separate tables we joined later on. 
* The first table includes Red Bull prices in USD by country (250mL can as at April 2021)
* The second table gives country currencies and their codes and symbols
* The third table contains exchange rates between countries' currencies and USD
* The final table contains countries' goods and services/value-added taxes rates

### Data Clean
We then cleaned our data:

![clean](3.png "Tidying Up")

Tables needed to be relabelled and formatted. The following cleans were made: 

#### Red Bull Price Table: 
* "Countries" column was relabelled as "Country"
* "Red Bull Prices" column was relabelled as "Price"
* "Rank" was dropped


#### Currencies Table:
* "Country and Currency" was replaced with "Country". A for loop was used to split the country off the currency name, and then reinserted into the table
* "Currency Code" was dropped

#### Exchange Rate Table:
* Every year of exchange rates were dropped except 2021 (we actually just made a new table from the one column)
* "Currency" was dropped (we only needed countries)

#### Tax Rate Table
* We stripped the phrase "Last reviewed XYZ dat" using the same procedure as the currencies table
* We also had to manually clean extra information (notes) from the tax rates, but we waited to see which countries would be retained after the join.

### Join
We proceeded to join our data.

![join](4.png "Combine")

Because we knew we would have to manually clean the tax rates, edits were made to the specific rows where notes had been added (e.g., multiple tax rates were given):

![manual](5.png "Manual")

Once our tax rates were cleaned, we reformatted our columns again, and added another column for prices in the domestic currency to complete cleaning and tidying our data. Finally, we had a single table with:
  - 18 total countries
  - Red Bull prices (250mL can, USD)
  - Currency symbol
  - Exchange rate to USD (2021 average)
  - Tax rate (%)
  - Price in own currency

### Local Tax Rates

![bonus](6.png "Local Tax Rates")

To complete the bonus, we took our completed table, which included a tax rate column, and multiplied the price in countries' own currencies as well as in USD by the cleaned tax rate (decimal) plus one, and rounded the result.

### Currency Symbols

![currency](7.png "Displaying Currencies")

As we had already imported currency symbols earlier, we only needed to create a column that concatenates the respective currency symbol to the price. We did this with a loop that generated what we needed as strings, which we appeneded to a list, and used as a column to insert into the table.

### CAD Prices and Price Differences
For this task, we first generated the prices in CAD using the USD prices we already had (calling the CAD price with a reference, not finding it and inserting a constant). From there, we formatted and then displayed CAD price and CAD price difference in a bar chart.

![bar](8.png "Bar Chart")

### External Factor: Human Development Index (HDI)
For Q6 we decided to look at the Human Development Index (HDI), as Red Bull themselves claim (printed on every can!) that their product is "Appreciated worldwide by top athletes, students, busy professionals, and travellers on long journeys." By taking HDI to approximate volume of knowledge workers, our hypothesis is that countries with more students and professionals will have higher prices for Red Bull.

Our code was fairly straightforward, as we first scraped the HDI data, cleaned it, then put it in our finished table from earlier. We used the same procedures as above.

![HDI](9.png "HDI")

Here is a table with our HDI column:

![HDI_table](10.png "HDI Table")

Bar chart:

![HDI_bar](11.png "HDI Bar Chart")

Scatter:

![HDI_scatter](12.png "HDI Scatter Chart")

With our Red Bull Price Index, we came to the conclusion that the price of Red Bull is not consistent throughout the world. 
* We determined that the lowest price of Red Bull for the countries examined is in Turkey
* Mexico has the highest price

Furthermore, after considering whether HDI can be price deflation/inflation factor, we also came to the conclusion that HDI does not seem to not have an influence on the price of Red Bull in a given country. 

The greatest difficulty, aside from planning our approach to the assignment, was manually cleaning the tax rate data early on. 
