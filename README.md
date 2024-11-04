# CSE151A_Project

## Dataset 1: Zooplankton data from Scripps 
This was extracted as a pdf from Scripps' website. We imported tabula to help convert pdfs into csv. It has around 90 rows of data for both the year ranged from the year ranges (1980 - 1999) and (2000 - 2021) with pooled and unpooled data. Unpooled data is noncumulative data (single samples for each cruise trip). Unpooled data is useless to us, which we got rid of. The pooled data for these years gave us about 60 rows of data. These observations give us 4-6 readings of the population of zooplankton for every year. We did not have any missing data or columns. 

  - The data had the columns ['Cruise', 'Ship', 'Date', 'Line', 'Station', 'Region', 'TowBegin','TowEnd', 'Latitude', 'Longitude', 'Abundance', 'Tows', 'Source']. Out of these, the only columns needed were: 'Date' - which tells us the year of data extraction, 'Region' - either Southern or Central California and 'Abundance' - the population of Zooplanktons in that year.
  - We dropped the other columns, we did not have any N/A in the columns we chose for this dataset.
  - We did binary encoding to represent the two regions SC and CC.
  - Since the year was a string datatype with ddmmyyyy format, we changed it to an integer representing the year only.
  - Abundance was also a string type that was converted to an int type.
  - Finally, we ordered the data set in an increasing order of the year.

## Dataset 2: BATS - Features that impact the growth of Zooplanktons
In our exploration of Dataset 2, which has 473 rows, we assessed each column's relevance and identified redundant date-related columns: Sample, Excel, and Date. These provided various date formats but added little value, so we extracted the year to create a new column called Year, dropping the others. We also noticed some column names had unnecessary whitespace, which we planned to clean up to avoid issues in later analysis. The dataset includes key columns: Station, Depth, Salinity. To facilitate analysis, we applied Min-Max normalization to the continuous variables: Depth, Salinity, Temp, d13C-DIC, DIC, and ALK, scaling them to a range of 0 to 1. This ensures all features can be compared fairly and prevents any single variable from skewing our results.
- Dataset 2 had the following columns: ['Station', 'Sample', 'Excel', 'Date', 'Depth', 'Salinity', 'Temp', ' d13C-DIC', 'DIC', 'ALK’]. We decided to keep the Depth, Salinity, Temp, d13C-DIC, DIC, ALK and Year, because these were the only attributes we found to be relevant to our exploration.
- We cleared out the whitespace for column names that originally existed in the dataset.
- We then applied Min-Max Normalization on every column except the year, to make the data easier to work with.  We did not encode any of the attributes because they all contained continuous numeric data. We then plotted a pair-plot and correlation heat-map of the data.

## Dataset 3: Atlantic drifters dataset - might be used for tests
The Lagrangian Drifters dataset is a collection of oceanographic data gathered by free-floating instruments called drifters, deployed to monitor various physical and environmental characteristics of the ocean surface. We collected data for 1 week each in each of the years in 2021, 2022, 2023, 2024. There are a total of about 40000 rows which can be collapsed by their average later on to match datasets 1 and 2.
- For dataset 3, We have combined the data from years 2021,2022,2023,and 2024. 
- The data frame had the following columns ['platform_code', 'time', 'latitude', 'longitude', 'slp', 'drogue','sst', 'battery', 'presdiff', 'salinity', 'gpsfixdel', 'windspd', 'winddir', 'conductivity', 'avgwaveperiod', 'wvht', 'domwaveperiod','domwavedir','battery']
- We have dropped the columns ['platform_code','windspd','winddir','conductivity','wvht', 'domwaveperiod','domwavedir','avgwaveperiod','gpsfixdel','salinity','drogue'] becasue the columns ['windspd','winddir','conductivity','wvht', 'domwaveperiod','domwavedir','avgwaveperiod','gpsfixdel','salinity']
were empty and ‘platform_code’,'battery' and ‘drogue’ was data related to the ships/drifters collecting the data. These columns are not useful for observing the environmental factors of the ocean.
- The remaining columns are 'latitude', 'longitude' which provide the location, slp - sea level pressure, sst - sea surface temperature, presdiff - pressure difference were converted to numerical data from 'Object' data type.

## Planning on using the datasets
- From dataset 1 we have data related to abundance from years 1980 - 2020. We have the environmental factors such as Depth, Salinity, Temperature, d13C-DIC, DIC, ALK from the same regions and these factors can be correlated to the zoo plankton abundance.
- Dataset 3 has some important features such as sea level pressure, surface level temperature etc , but they relate to the Atlantic region and not the pacific region the other two datasets are focussed on. Initially we thought of training a model on datasets 1 (output - abundance) and 2(inputs - Depth, Salinity, Temp, d13C-DIC, DIC, ALK) in pacific region and predict the zooplankton abundance in the atlantic region using the factors from dataset 3(inputs - slp, sst, presdiff), but it does not seem feasible as the input factors in dataset 3 are diffrent from those we are going to train from dataset 2.

[Jupyter Notebook Link](https://colab.research.google.com/drive/1YpusAxOyCNkgLbNwInFFsIg0mX5Y-iJQ?usp=sharing)
