# CSE151A_Project

**A written report:**

## **Introduction:**
 - **Why We Chose This Project**
Zooplankton, often referred to as the "grazers of the sea," form the critical base of the marine food web. Their abundance and diversity directly impact fisheries, marine ecosystems, and the global carbon cycle. However, these delicate organisms are increasingly threatened by climate change, pollution, and other human-induced stressors. Understanding the factors influencing their distribution and abundance is crucial for effective marine conservation and management.

 - ### **Why It's Cool**
Predicting zooplankton abundance using machine learning is a fascinating blend of biology and technology. By training models on vast datasets of environmental factors, we can uncover hidden patterns and relationships that drive zooplankton dynamics.

- ### **The Broader Impact**
1. Fisheries Management: Accurate forecasts can help optimize fishing quotas and reduce overfishing, ensuring sustainable fisheries which is essential in decreasing damage to the ecosystem.
2. Climate Change Research: By analyzing how zooplankton respond to changing environmental conditions, we can gain insights into climate change impacts on marine ecosystems.
3. Ocean Health Monitoring: Tracking zooplankton populations can serve as an early warning system for ecosystem degradation and pollution events.
4. Carbon Cycle Studies: Zooplankton play a vital role in the marine carbon cycle. Understanding their dynamics can help us assess the ocean's capacity to absorb carbon dioxide.


**All prior submissions:** links to all our past notebooks:
[Milestone 2 Notebook Link](https://github.com/madhoolikacvss/CSE151A_Project/blob/main/Milestone_2.ipynb) 
[Milestone 3 Notebook Link](https://github.com/madhoolikacvss/CSE151A_Project/blob/main/Milestone_3.ipynb)
[Milestone 4 Notebook](https://github.com/madhoolikacvss/CSE151A_Project/blob/main/Milestone_4.ipynb)


## **Methods used:**
  
### **Data Exploration:**
Two of our major data sets inlcude: Zooplanton Database from Scripps Intitue of Oceanography's Mark Ohman Lab (SIO Pelagic Intertibrates Collection) and Environmental Pollution data from Scripps' Ocean Time-series Data. We initially decided on three datasets four our first milestone. The first was Zooplankton Abundance Data (Scripps) which covered zooplankton population data (1980–2021) with columns Year, Region, and Abundance (as shown in _figure 1_). The second dataset was the Environmental Pollution, which had a range of environmental data including Depth, Salinity, Temp, d13C-DIC, DIC and ALK. Correlation between the features and Zooplankton abundance is shown in *figure 2*. The third was the Atlantic Drifters dataset, but we decided to drop it later and it was not directly used due to its focus on the Atlantic region, not Pacific which the other datasets focussed on, and differing features.


**Data Preprocessing:**
During the preprocessing stage, we performed data cleaning, normalization and feature engineering. In order to clean the data, we  removed any irrelevant columns and handled missing values. Additionally, we converted certain attribute values from string to numeric, to make them easier to work with. We then applied Min-Max Scaling to all of the continuous variables in order to standardize the data and also encoded any categorical attributes, like 'Region', using one-hot encoding to ensure consistency. Finally, we plotted the data using pairplots and correlation heatmaps to visualize the relationship between certain features, before moving on to create our models.

|![Figure 1.](https://github.com/user-attachments/assets/a8585274-2d93-4b3b-9518-35ca5549de38)<br>Zooplankton Dataset example|![Figure 2.](https://github.com/user-attachments/assets/a0da7cba-1fe0-4c15-a25a-8a7f3db3e7a9)<br>Correlation betweeen pollution features|
|:-:|:-:|


### **Model 1:**
For our first model, we chose to use a simple Linear Regression model as our baseline, focusing on the relationship between the Year and Abundance to predict zooplankton population trends over time. We used Dataset 1, with Year as the predictor for Abundance. We then split the data into training (80%) and testing (20%) subsets and trained our model. Then, in order to evaluate our model we used various metrics like Mean Squared Error (MSE), Mean Absolute Error (MAE), and R² Score The model demonstrated a linear relationship between Year and Abundance. The model revealed important trends, but lacked predictive power when applied to environmental factors. Our fitting model is shown in *figure 3*
![Figure 3](https://github.com/user-attachments/assets/90c50bca-84c0-4b31-a3a1-52c19c66f677)



**Model 2:**


Before we created our second model, we decided to modify our original linear regression model and made use of bootstrapping instead, to increase accuracy. This would help address any uncertainties regarding the performance of our first model. Additionally, we performed feature expansion and added a number of features to our data including the season, cluster assignments, and carbon storage potential, which was calculated using DIC and ALK values. We found these added features to be very useful when it came to the accuracy of the model. The cluster feature in particular was quite significant, seeing as the data was split into distinct clusters, as shown in a figure below. We preprocessed these features, by applying Min-Max Scaling and using similar methods to those described above. For the second model itself, we used an Elastic Net Regularization model. The second model aims to improve performance by incorporating additional features and controlling for overfitting using regularization. We then used the first and second dataset to create our model, with Depth, Salinity, Temp, d13C-DIC, DIC/ALK Ratio, fractional year, cluster assignments and Carbon Storage Potential as predictors for Abundance. Similar to the first model, we split the data into training (80%) and testing (20%) subsets 
We then trained our model which made use of Elastic Net, combining L1 and L2 regularization. Once again, we used MSE, MAE, MAPE, and R² to evaluate our model and plotted graphs to visualize training/testing error with varying regularization strengths.
This model outperformed linear regression and the engineered features (e.g., DIC/ALK Ratio, fractional year) seemed to contributed significantly to the model’s performance. We did observe minor overfitting but decided that it was within acceptable limits

## **Results:**
### **Data Exploration:**

#### Datasets and their Usefulness:

The project involves two main datasets:

##### Zooplankton Abundance Data (ZooDBCrop.pdf and ZooDBCrop2.pdf):

- Abundance: This dataset contains direct observations of zooplankton abundance over time (1980-2021) at different locations and regions. It is the core of your analysis as it provides a crucial link to understanding the changes in zooplankton populations.
- Temporal trends: By analyzing the 'Abundance' data against 'Year' and 'Fractional Year', you can identify long-term trends and seasonal variations in zooplankton populations. This is crucial for detecting potential impacts of climate change and other long-term stressors.
- Spatial distribution: Information about 'Region' within the dataset helps in understanding the spatial patterns of zooplankton distribution and how it relates to environmental factors or ecological zones.

##### Environmental and Chemical Data (BATA+BERM+HAWI):

- Environmental factors: This dataset contains measurements of various environmental parameters like 'Depth', 'Salinity', 'Temp', 'd13C-DIC', 'DIC', and 'ALK'. These are potential drivers of zooplankton abundance and diversity.
- Predictive modeling: By combining this dataset with the Zooplankton Abundance Data, you can build models to predict zooplankton abundance based on environmental conditions. This can help you understand the relationships between zooplankton and their environment.
- Impacts of change: These models can further be utilized to predict how zooplankton populations might respond to future environmental changes (e.g., increased ocean temperature or acidification), informing conservation strategies.
Connection to Research Aim:

The project aims to understand the factors influencing zooplankton distribution and abundance for marine conservation and management. Here's how these datasets contribute:

- Identifying factors: By analyzing the relationships between zooplankton abundance and environmental parameters, you can pinpoint the key factors driving changes in their populations.
Predicting future trends: Using predictive models, you can forecast how zooplankton abundance might change under different scenarios. This provides crucial insight for proactive management.
- Supporting conservation efforts: The findings of your project can be used to develop strategies to mitigate negative impacts on zooplankton, ensuring the health of marine ecosystems and fisheries.

### **Data Preprocessing:**

#### Step 1: Data Loading and Cleaning

Two PDF files (ZooDBCrop.pdf and ZooDBCrop2.pdf) containing Zooplankton data are read using the tabula-py library.
Irrelevant columns (like 'Tows', 'TowBegin', etc.) are dropped.
Rows with missing values (N/A) are removed using dropna().
The 'Date' column is cleaned by removing carriage returns ("\r").
Commas are removed and the data type is changed to numeric for the 'Abundance' column.

#### Step 2: Feature Engineering

- Region: One-hot encoding is applied to the 'Region' column (originally containing 'SC' and 'CC') and converted to a binary representation (0 or 1).
- Year: The year is extracted from the 'Date' column and added as a new 'Year' column.
- Fractional Year: The 'Date' column is converted into a fractional year format (e.g., 1989.474 for June 22, 1989) to capture the temporal information more precisely. This is calculated using the pd.to_datetime function and considering leap years.

#### Step 3: Data Transformation

- Normalization: Min-Max normalization is mentioned to scale features 'Depth', 'Salinity', 'Temp', 'd13C-DIC', 'DIC', and 'ALK' to a range of 0 to 1 for the second dataset. This step is not shown in the provided code.
- Reasoning:

Data cleaning ensured data quality and consistency.
Feature engineering helps in extracting more useful information from the existing data.
Data transformation like normalization enables better performance for many machine learning models.

### **Model 1:**

#### Data Splitting: The code splits the data into training (80%) and testing (20%) sets using train_test_split. This is done to evaluate the model's performance on unseen data. A validation set is also generated to fine-tune hyperparameters if needed.

#### Model Creation and Training: A LinearRegression model is created and trained using the training data (X_train, y_train). This involves fitting the model to learn the relationship between the features and the target variable (Abundance).

#### Prediction: After training, the model is used to predict the Abundance values for the test set (X_test) and validation set (X_val).

#### Evaluation Metrics: The code uses several metrics to evaluate the model's performance, including:

- Mean Squared Error (MSE): Measures the average squared difference between the predicted and actual values. The code calculates MSE on all three data splits: training, validation, and test. Lower MSE values indicate better model performance, provided the model does not exhibit overfitting.
- Mean Absolute Error (MAE): Measures the average absolute difference between the predicted and actual values. Like MSE, lower values indicate better model performance.
- Mean Absolute Percentage Error (MAE): Measures the average percentage difference between the predicted and actual values. It provides a more intuitive representation of error in percentage terms.
- Explained Variance Score: Measures the proportion of the target variable's variance that is explained by the model. Higher values indicate better model performance.
- R-squared: Measures the goodness of fit of the model, similar to explained variance score. Higher values indicate better model performance.
Results

The code prints the calculated metrics for the validation, test, and training sets. These values indicate the model's performance on each data split. Here's an example from the code:

 
Validation Metrics:
Validation Mean Squared Error: 165367.57984873
Validation Mean Absolute Error (MAE): 322.2452069673444
Validation Mean Absolute Error Percentage (MAE): 0.012191340323124545
Validation Explained Variance Score: 0.1621615963083994
Validation R-squared: 0.16

Test Metrics:
Test Mean Squared Error: 164575.21323621
Test Mean Absolute Error (MAE): 334.8921124572971
Test Mean Absolute Error Percentage (MAE): 0.012645050953394295
Test Explained Variance Score: 0.1391014025260117
Test R-squared: 0.14

### **Model 2:**

#### Metrics Calculated:
Mean Squared Error (MSE): A measure of the average squared difference between the predicted and actual values. Lower values indicate better model performance.
Mean Absolute Error (MAE): A measure of the average absolute difference between the predicted and actual values. Similar to MSE, lower values are better.
Mean Absolute Percentage Error (MAEP): Represents the average percentage difference between the predicted and actual values. It provides a more interpretable measure of error, especially when dealing with different scales. Lower values are desirable.
Train MSE for each fold: MSE calculated on the training data for each of the 4 folds in cross-validation. Provides insight into how the model is learning from the training data.
Test MSE for each fold: MSE calculated on the test (validation) data for each of the 4 folds. Represents how well the model generalizes to unseen data.
Mean Train MSE: Average MSE across all training folds.
Mean Test MSE: Average MSE across all test folds. This is often the primary metric used to evaluate the overall performance of the model.

#### Reported Results:
- Mean Squared Error: 120093617.40425721
- Mean Absolute Error: 8260.954207096058
- Mean Absolute Percentage Error: 0.5309773201224828
- Train MSE for each fold: [38565.0537537  40494.36718402 40108.8262212  40274.79349042]
- Test MSE for each fold: [49297.55750247 34101.61424316 37795.79749319 40170.26627811]
- Mean Train MSE: 39860.76
- Mean Test MSE: 40341.31
  
![Model 2 results](https://github.com/user-attachments/assets/ec0e6ca2-a377-414f-8292-37a2dc321baa)

## **Discussion :**
Our Zooplankton Data Analysis Journey: From Confusion to (Some) Clarity
Starting out, we were pretty overwhelmed. We had two datasets that seemed impossible to reconcile: one with zooplankton abundance data from 2000-2021 (just 62 rows!) and this massive environmental dataset with 1374 samples containing all these ocean measurements. How do you even begin to work with such mismatched data?
The Big Challenge was making the data work together. The first big decision we explored as a group was figuring out how to use our limited abundance data across all those environmental samples. We initially thought about just copying the abundance values across years, but that felt too simplistic. Instead, we decided to build a model that could predict abundance values based on time, which would make our predictions more granular.

Our first modeling attempt was interesting. We started with simple linear regression but then improved it using bootstrapping (100 iterations). Looking at the results:
Best MAPE: 0.274 (about 27.4% error)
Model coefficients: Intercept around -59,194 and coefficient of 41.12
This wasn't amazing accuracy, but considering we're dealing with biological data, it's not terrible either.

As we moved into Milestone 4, we got more sophisticated with our features. 
- We first created a "Carbon Storage Potential" metric using ALK*DIC/DIC (though, looking back now, we realize the DIC cancels out - we might need to revisit this in the future)
- Added fractional years to capture time more precisely
- Built-in seasonal effects (Winter, Spring, Summer, Fall)
- Used K-means clustering on Salinity and ALK levels (n=4 clusters)

These additions made sense ecologically as zooplankton abundance definitely varies by season, and the chemical properties of the water should logically matter.

For our second model, we tried ElasticNet regression (kind of like regular regression but with some defined controls to prevent overfitting). Looking at the cross-validation results:
- Mean Train MSE: ~39,860
- Mean Test MSE: ~40,341
- MAPE: about 53%

Honestly, this performance did not match our expectations. The similar train and test errors suggest we're not overfitting too badly, but the high MAPE shows we're still missing something important in our predictions.

### **What We Learned**
- We probably should have explored non-linear relationships - zooplankton populations likely don't respond linearly to environmental changes.
- The seasonal encoding could be more sophisticated - maybe using cyclic features instead of categorical variables.

### **The Honest Truth**
While our models show some predictive power, we must admit they're not as accurate as we'd initially hoped. It really just highlights the true scale of building ML models and that you do not actually know how hard it can be until you start digging and exploring yourself. The rather high error rates (27.4% for the first model and 53% for the second) suggest we may be missing some important factors. This makes sense, though, since zooplankton populations are affected by so many things we couldn't measure: predation, phytoplankton abundance, ocean currents, etc.

### **What's Next?**
If we could continue this project, we'd love to:
- Try more advanced models like Random Forests that can capture non-linear relationships.
- Collect more frequent abundance measurements.
- Include other environmental variables like chlorophyll levels or current data.
- Better account for the temporal nature of the data - maybe using time series approaches

In the end, this project taught us that sometimes in machine learning, you don't get the amazing results you hoped for - and that's okay! The process of working through the problems, trying different approaches, and honestly evaluating your results is what really matters. Plus, now we know a lot more about both zooplankton than when we started!

