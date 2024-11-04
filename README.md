# CSE151A_Project

Dataset 1 was extracted as a pdf from Scripps' website. We imported tabula

## Dataset 1: Zooplankton data from Scripps 
  - The data had the columns ['Cruise', 'Ship', 'Date', 'Line', 'Station', 'Region', 'TowBegin','TowEnd', 'Latitude', 'Longitude', 'Abundance', 'Tows', 'Source']. Out of these, the only columns needed were: 'Date' - which tells us the year of data extraction, 'Region' - either Southern or Central California and 'Abundance' - the population of Zooplanktons in that year.
  - We dropped the other columns, we did not have any N/A in the columns we chose for this dataset.
  - We did binary encoding to represent the two regions SC and CC.
  - Since the year was a string datatype with ddmmyyyy format, we changed it to an integer representing the year only.
  - Abundance was also a string type that was converted to an int type.
  - Finally, we ordered the data set in an increasing order of the year.

## Dataset 2: BATS - Features that impact the growth of Zooplanktons
- Dataset 2 had the following columns: ['Station', 'Sample', 'Excel', 'Date', 'Depth', 'Salinity', 'Temp', ' d13C-DIC', 'DIC', 'ALK’]. We decided to keep the Depth, Salinity, Temp, d13C-DIC, DIC, ALK and Year, because these were the only attributes we found to be relevant to our exploration.
- We cleared out the whitespace for column names that originally existed in the dataset.
- We then applied Min-Max Normalization on every column except the year, to make the data easier to work with.  We did not encode any of the attributes because they all contained continuous numeric data. We then plotted a pair-plot and correlation heat-map of the data.

## Dataset 3: Atlantic drifters dataset - might be used for tests
- For dataset 3, We have combined the data from years 2021,2022,2023,and 2024. 
- The data frame had the following columns ['platform_code', 'time', 'latitude', 'longitude', 'slp', 'drogue','sst', 'battery', 'presdiff', 'salinity', 'gpsfixdel', 'windspd', 'winddir', 'conductivity', 'avgwaveperiod', 'wvht', 'domwaveperiod','domwavedir','battery']
- We have dropped the columns ['platform_code','windspd','winddir','conductivity','wvht', 'domwaveperiod','domwavedir','avgwaveperiod','gpsfixdel','salinity','drogue'] becasue the columns ['windspd','winddir','conductivity','wvht', 'domwaveperiod','domwavedir','avgwaveperiod','gpsfixdel','salinity']
were empty and ‘platform_code’,'battery' and ‘drogue’ was data related to the ships/drifters collecting the data. These columns are not useful for observing the environmental factors of the ocean.
- The remaining columns are 'latitude', 'longitude' which provide the location, slp - sea level pressure, sst - sea surface temperature, presdiff - pressure difference were converted to numerical data from 'Object' data type.
