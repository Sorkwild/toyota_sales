# Car sales analisys

In this project i decided to create analitical report for imaginary toyota representatives. I analize used cars sales at USA market. This work could be made for any or all of car brands, but it would take much more time and resources. So I decided to narrow the task down.
## Orginal dataset:

https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data

## Dataset description:

The "Vehicle Sales and Market Trends Dataset" provides a comprehensive collection of information pertaining to the sales transactions of various vehicles. This dataset encompasses details such as the year, make, model, trim, body type, transmission type, VIN (Vehicle Identification Number), state of registration, condition rating, odometer reading, exterior and interior colors, seller information, Manheim Market Report (MMR) values, selling prices, and sale dates.

### Columns:

- year: year, when car was produced
- make: vehicle brand
- model: specific model of a vehicle
- trim: exact version of a vehicle
- body: body type of a vehicle
- transmission: manual or automatic
- vin: unique identification for each vehicle
- state: state of registration
- condition: scaled expression of a vehicle's condition
- odometer: vehicle's mileage
- color: main exterior color
- interior: main interior color
- seller: dealership's name
- mmr: estimated market value
- sellingprice: factual value, for which vehicle was sold
- saledate: date and time of sale


## Used tools:

- VS Code IDE v1.99
- Microsoft Power BI v2.140.1577.0
- Git Hub

## Work steps:
### Problem definition
As a representative I wanted to find out main stats for our sales through two years. What brands and models are our bestselling ones, which dealer makes the most sales and brings the most income. 

### Data processing:
Working with dataset I use VS Code and Python libraries pandas, numpy, math and plotly express. Since I got dataset not only for toyota related brands, I needed to filter it. 

First step is detecting missed values and filling them with appropriate values. I found missing values in columns: 
- trim
- body
- transmission
- condition
- odometer
- color
- interior

For filling missing values in body column I created dictionary, that I filled manually. For trim, color, interior and transmission columns I used same function, returning most common value for the model. With such approach I managed to get decently accurate values. 

To fill missing values in condition and odometer columns I created a function, that finds two closest records according to model, trim and year, and returns mean value of their condition field. 

After all missing values were filled, I checked for duplicates. There're no fully duplicated records. 

Next step is detecting anomalies in dataset. I checked for outliers according to odometer and price fields. For detecting I used interquartile range method. Found outliers were deleted from dataset. 

Resulting dataset was recorded into "toyota_sale.csv" file for further processing in Microsoft Power BI

### Report building:

In Power BI I've changed data format for columns with numeric and date\time values to get more accurate results in the report. 
I also created column with vehicle's age at the time of sale, and with difference betweeen estimated price and factual one. 

First page in report contains main information about sales: pie chart for brand sales, sales by time, most popular models and map with information on sales by region. To get that map working I loaded Excell table with full names of the regions and their abbreviations. 

I also added custom switch to change data on the report from moneywise to saleswise. 

Second page of report contains more in-depth information on sales. Here I got barchart for top 10 dealers, showing their sales by timeperiod. Group of tables with most popular models and colors of cars sold. In addition I put table with data on three top-selling dealers and their earnings and card with total income for brand as well. On this page I also keep switch, allowing user to choose between certaing brands. 