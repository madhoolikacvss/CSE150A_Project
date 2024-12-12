# CSE151A_Project

**A written report:**

**Introduction:**
 - **Why We Chose This Project**
Zooplankton, often referred to as the "grazers of the sea," form the critical base of the marine food web. Their abundance and diversity directly impact fisheries, marine ecosystems, and the global carbon cycle. However, these delicate organisms are increasingly threatened by climate change, pollution, and other human-induced stressors. Understanding the factors influencing their distribution and abundance is crucial for effective marine conservation and management.

 - **Why It's Cool**
Predicting zooplankton abundance using machine learning is a fascinating blend of biology and technology. By training models on vast datasets of environmental factors, we can uncover hidden patterns and relationships that drive zooplankton dynamics.

- **The Broader Impact**
1. Fisheries Management: Accurate forecasts can help optimize fishing quotas and reduce overfishing, ensuring sustainable fisheries which is essential in decreasing damage to the ecosystem.
2. Climate Change Research: By analyzing how zooplankton respond to changing environmental conditions, we can gain insights into climate change impacts on marine ecosystems.
3. Ocean Health Monitoring: Tracking zooplankton populations can serve as an early warning system for ecosystem degradation and pollution events.
4. Carbon Cycle Studies: Zooplankton play a vital role in the marine carbon cycle. Understanding their dynamics can help us assess the ocean's capacity to absorb carbon dioxide.

**All prior submissions:** link all notebooks, in brackets mention what milestones they correspond to
[Milestone 2 Notebook Link](https://colab.research.google.com/drive/1YpusAxOyCNkgLbNwInFFsIg0mX5Y-iJQ?usp=sharing) 
[Milestone 3 Notebook Link](https://colab.research.google.com/drive/1YpusAxOyCNkgLbNwInFFsIg0mX5Y-iJQ?usp=sharing)
[Milestone 4 Notebook](https://colab.research.google.com/drive/1EQEcjeUrm6Erm4sgytVkt5_YzZd7FKiq#scrollTo=r6h1-li8Kapq)


**Methods used:**
  
**Data Exploration:**
Two of our major data sets inlcude: Zooplanton Database from Scripps Intitue of Oceanography's Mark Ohman Lab (SIO Pelagic Intertibrates Collection) and Environmental Pollution data from Scripps' Ocean Time-series Data. We initially decided on three datasets four our first milestone. The first was Zooplankton Abundance Data (Scripps) which covered zooplankton population data (1980–2021) with columns Year, Region, and Abundance (as shown in _figure 1_). The second dataset was the Environmental Pollution, which had a range of environmental data including Depth, Salinity, Temp, d13C-DIC, DIC and ALK. Correlation between the features and Zooplankton abundance is shown in *figure 2*. The third was the Atlantic Drifters dataset, but we decided to drop it later and it was not directly used due to its focus on the Atlantic region, not Pacific which the other datasets focussed on, and differing features.

**Data Preprocessing:**
During the preprocessing stage, we performed data cleaning, normalization and feature engineering. In order to clean the data, we  removed any irrelevant columns and handled missing values. Additionally, we converted certain attribute values from string to numeric, to make them easier to work with. We then applied Min-Max Scaling to all of the continuous variables in order to standardize the data and ensure consistency. Fianlly, we also encoded any categorical attributes like 'Region', for example, using one-hot encoding.

<img width="127" alt="image" src="https://github.com/user-attachments/assets/a8585274-2d93-4b3b-9518-35ca5549de38" />
*figure 1. An example of how our Zooplankton data set looks like*

![Figure 2. Correlation betweeen pollution features](https://github.com/user-attachments/assets/a0da7cba-1fe0-4c15-a25a-8a7f3db3e7a9)


**Model 1:**
For our first model, we chose to use a simple Linear Regression model as our baseline, focusing on the relationship between the Year and Abundance to predict zooplankton population trends over time. We used Dataset 1, with Year as the predictor for Abundance. We then split the data into training (80%) and testing (20%) subsets and trained our model. Then, in order to evaluate our model we used various metrics like Mean Squared Error (MSE), Mean Absolute Error (MAE), and R² Score The model demonstrated a linear relationship between Year and Abundance. The model revealed important trends, but lacked predictive power when applied to environmental factors. Our fitting model is shown in *figure 3*
![Figure 3](https://github.com/user-attachments/assets/90c50bca-84c0-4b31-a3a1-52c19c66f677)


**Model 2:**
  #mention feature expantion. An image showing why clustering data points was an important feature is shown below:
![Figure 3](https://github.com/user-attachments/assets/666874d1-f8b1-4300-b66e-cc565aca4ceb)


Before we created our second model, we decided to modify our original linear regression model and made use of bootstrapping instead, to increase accuracy. This would help address any uncertainties regarding the performance of our first model. Additionally, we performed feature expansion and added a number of features to our data including the season, cluster assignments, and carbon storage potential, which was calculated using DIC and ALK values. We preprocessed these features, by applying Min-Max Scaling and using similar methods to those described above. For the second model itself, we used an Elastic Net Regularization model. The second model aims to improve performance by incorporating additional features and controlling for overfitting using regularization. We then used the first and second dataset to create our model, with Depth, Salinity, Temp, d13C-DIC, DIC/ALK Ratio, fractional year, cluster assignments and Carbon Storage Potential as predictors for Abundance. Similar to the firt model, we split the data into training (80%) and testing (20%) subsets 
We then trained our model which made use of Elastic Net, combining L1 and L2 regularization. Once again, we used MSE, MAE, MAPE, and R² to evaluate our model and plotted graphs to visualize training/testing error with varying regularization strengths.
This model outperformed linear regression and the engineered features (e.g., DIC/ALK Ratio, fractional year) seemed to contributed significantly to the model’s performance. We did observe minor overfitting but decided that it was within acceptable limits
Our train vs Test MSE for each fold (from *figure 4*):
![Figure 4](https://github.com/user-attachments/assets/ec0e6ca2-a377-414f-8292-37a2dc321baa)

**Results:**

**Discussion :**
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

**What We Learned**
- We probably should have explored non-linear relationships - zooplankton populations likely don't respond linearly to environmental changes.
- The seasonal encoding could be more sophisticated - maybe using cyclic features instead of categorical variables.

**The Honest Truth**
While our models show some predictive power, we must admit they're not as accurate as we'd initially hoped. It really just highlights the true scale of building ML models and that you do not actually know how hard it can be until you start digging and exploring yourself. The rather high error rates (27.4% for the first model and 53% for the second) suggest we may be missing some important factors. This makes sense, though, since zooplankton populations are affected by so many things we couldn't measure: predation, phytoplankton abundance, ocean currents, etc.

**What's Next?**
If we could continue this project, we'd love to:
- Try more advanced models like Random Forests that can capture non-linear relationships.
- Collect more frequent abundance measurements.
- Include other environmental variables like chlorophyll levels or current data.
- Better account for the temporal nature of the data - maybe using time series approaches

In the end, this project taught us that sometimes in machine learning, you don't get the amazing results you hoped for - and that's okay! The process of working through the problems, trying different approaches, and honestly evaluating your results is what really matters. Plus, now we know a lot more about both zooplankton than when we started!

