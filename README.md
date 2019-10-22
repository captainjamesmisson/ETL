# ETL
Extract, Transform and Load


DATA SOURCE BACKGROUND

Visited Kaggle.com.  Attempted to download Washington Post (WaPo) database on opioid usage.  Database was ~70 gb unzipped.  This file proved large and unwieldy.  Attempted to transform database into smaller text files that could then be imported into pandas.  This resulted in >800 text files.  As a result, we concluded the WaPo data base was unrealistic for our project.

We pivoted from the WaPo database and used Center for Disease Control (CDC) online data that included the most important items we wanted in the WaPo database.  In addition, the CDC data was neatly constituted in HTML tables.  Chose this as our source on opioid usage.

Decided it would be informative to compare opioid usage across time to changes in unemployment rates.  Visited the Bureau of Labor Statistics (BLS) and found unemployment data that could be easily downloaded in a CSV file.

Chose to extract data from CDC and BLS using two points in time - 2006 and 2016 - to compare pre-Global Financial Crisis levels to election year levels given opioid usage became a hot-bottom topic during latter year and was not an issue pre-recession.  Decided to utilize data from both sources at the county level as aggregating at state or national level wouldn't likely yield informative results.

ETL

1 Read BLS CSV umemployment file into dataframe using pandas
2 Split BLS combined county_state column in dataframe into individual county, state columns
3 Drop original BLS county_state column
4 Drop Puerto Rico from dataframe
5 Sort cleaned_county_df
6 Turn county and state fips codes into string
7 Drop data after decimal point for county_fips_code
8 Drop data after decimal point for county_fips_code
9 Convert county_fips_code to match format of CDC data
10 Convert state_fips_code to match format of CDC data
11 Concatenate updated county and state_fips_code into a new combined fips code
12 Insert new column to contain new_fips data
13 Repeat all stapes taken to transform 2006 BLS data for 2016 (cells 2-13)
14 Merge 2006 and 2016 BLS unemployment data by county on new_fips
15 Convert new_fips column into integer data-type
16 Assign variable to CDC url for 2016 table data and use pandas to read table into dataframe
17 Data imported as list of tables; specify element needed within table list
18 Assign variable to CDC url for 2016 table data and use pandas to read table into dataframe
19 Data imported as list of tables; specify element needed within table list
20 Merge 2006 and 2016 CDC data into single dataframe on county_fips_code
21 CDC county_fips_code includes both county code and state code prefix into contaenated code; BLS data was separate and required concatenation
22 CDC county column included both county and state abbreviation; eliminate state abbreviation from this column
23 Convert new_fips column data to integer 
24 Merge BLS and CDC dataframe into single dataframe on new_fips
25 Clean up columns in final dataframe
26 Create connection to mongo


