# CSE151A_Project

Dataset 1 was extracted 

### Dataset 1: Zooplankton data from Scripps 
  - The data had the columns ['Cruise', 'Ship', 'Date', 'Line', 'Station', 'Region', 'TowBegin','TowEnd', 'Latitude', 'Longitude', 'Abundance', 'Tows', 'Source']. Out of these, the only columns needed were: 'Date' - which tells us the year of data extraction, 'Region' - either Southern or Central California and 'Abundance' - the population of Zooplanktons in that year.
  - We dropped the other columns, we did not have any N/A in the columns we chose for this dataset.
  - We did binary encoding to represent the two regions SC and CC.
  - Since the year was a string datatype with ddmmyyyy format, we changed it to an integer representing the year only
  - Abundance was also a string type that was converted to an int type
  - Finally, we ordered the data set in an increasing order of the year 

Dataset 2: BATS - Features that impact the growth of Zooplanktons
- 

Dataset 3: Atlantic pollution factors - might be used for tests
- For dataset 3, I have combined the data from years 2021,2022,2023,and 2024. 
The data frame had the following columns ['platform_code', 'time', 'latitude', 'longitude', 'slp', 'drogue','sst', 'battery', 'presdiff', 'salinity', 'gpsfixdel', 'windspd', 'winddir', 'conductivity', 'avgwaveperiod', 'wvht', 'domwaveperiod','domwavedir']
