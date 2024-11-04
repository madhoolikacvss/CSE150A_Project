# CSE151A_Project

Perform the data exploration step (i.e. evaluate your data, # of observations, details about your data distributions, scales, missing data, column descriptions) Note: For image data you can still describe your data by the number of classes, # of images, plot example classes of the image, size of images, are sizes uniform? Do they need to be cropped? normalized? etc.
Plot your data. For tabular data, you will need to run scatters, for image data, you will need to plot your example classes.
How will you preprocess your data? You should only explain (do not perform pre-processing as that is in MS3) this in your README.md file and link your Jupyter notebook to it. All code and  Jupyter notebooks have be uploaded to your repo.
You must also include in your Jupyter Notebook, a link for data download and environment setup requirements: 
              !wget !unzip like functions as well as !pip install functions for non standard libraries not available in colab are required to be in the top section of your jupyter lab notebook. Or having the data on GitHub (you will need the academic license for GitHub to do this, larger datasets will require a link to external storage).

Dataset 1: Zooplankton data from Scripps 
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
