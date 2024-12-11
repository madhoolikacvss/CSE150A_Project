# CSE151A_Project
**Introduction**
This project investigates the environmental factors influencing zooplankton abundance, utilizing data from multiple datasets. By integrating and analyzing zooplankton abundance data from the Pacific Ocean and environmental factors such as temperature, salinity, and carbon chemistry, the study aims to build predictive models. These models can inform better understanding of marine ecosystems, with implications for climate research and ocean health.

**All prior submissions:** link all notebooks, in brackets mention what milestones they correspond to
[Milestone 2 Notebook Link](https://colab.research.google.com/drive/1YpusAxOyCNkgLbNwInFFsIg0mX5Y-iJQ?usp=sharing) 
[Milestone 3 Notebook Link](https://colab.research.google.com/drive/1YpusAxOyCNkgLbNwInFFsIg0mX5Y-iJQ?usp=sharing)
[Milestone 4 Notebook](https://colab.research.google.com/drive/1EQEcjeUrm6Erm4sgytVkt5_YzZd7FKiq#scrollTo=r6h1-li8Kapq)

**A written report:**
look at the past notebooks and grab information here :)
<h2>Methods used:</h2>
  
- **Data Exploration:**
We initially decided on three datasets four our first milestone. The first was Zooplankton Abundance Data (Scripps) which covered zooplankton population data (1980–2021) with columns Year, Region, and Abundance. The second dataset was the BATS Environmental Features, which had a range of environmental data including Depth, Salinity, Temp, d13C-DIC, DIC and ALK. The third was the Atlantic Drifters dataset, but we decided to drop it later and it was not directly used due to its focus on the Atlantic region and differing features.

- **Data Preprocessing:**
During the preprocessing stage, we performed data cleaning, normalization and feature engineering. In order to clean the data, we  removed any irrelevant columns and handled missing values. Then we applied Min-Max Scaling to all of the continuous variables in order to standardize the data. Finally, we added features to our data including ratios, seasonal categories, cluster assignments, and combined features like carbon storage potential.

- **Model 1:**
For our first model, we chose to use a simple Linear Regression model as our baseline, focusing on the relationship between the Year and Abundance to predict zooplankton population trends over time. We used Dataset 1, with Year as the predictor for Abundance. We then split the data into training (80%) and testing (20%) subsets and trained our model. Then, in order to evaluate our model we used various metrics like Mean Squared Error (MSE), Mean Absolute Error (MAE), and R² Score The model demonstrated a linear relationship between Year and Abundance. The model revealed important trends, but lacked predictive power when applied to environmental factors.

- **Model 2:**
For our second model, we used an Elastic Net Regularization model. The second model aims to improve performance by incorporating additional features and controlling for overfitting using regularization. We used the first and second dataset to create our model, with Depth, Salinity, Temp, d13C-DIC, DIC/ALK Ratio, fractional year, cluster assignments and Carbon Storage Potential as predictors for Abundance. Similar to the firt model, we split the data into training (80%) and testing (20%) subsets 
We then trained our model which made use of Elastic Net, combining L1 and L2 regularization. Once again, we used MSE, MAE, MAPE, and R² to evaluate our model and plotted graphs to visualize training/testing error with varying regularization strengths.
This model outperformed linear regression and the engineered features (e.g., DIC/ALK Ratio, fractional year) seemed to contributed significantly to the model’s performance. We did observe minor overfitting but decided that it was within acceptable limits

- **Results:**
- **Discussion :**
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

*** What We Learned (And What I'd Do Differently)
- We probably should have explored non-linear relationships - zooplankton populations likely don't respond linearly to environmental changes.
- The seasonal encoding could be more sophisticated - maybe using cyclic features instead of categorical variables.

*** The Honest Truth
While our models show some predictive power, we must admit they're not as accurate as we'd initially hoped. It really just highlights the true scale of building ML models and that you do not actually know how hard it can be until you start digging and exploring yourself. The rather high error rates (27.4% for the first model and 53% for the second) suggest we may be missing some important factors. This makes sense, though, since zooplankton populations are affected by so many things we couldn't measure: predation, phytoplankton abundance, ocean currents, etc.

** What's Next?
If we could continue this project, we'd love to:
- Try more advanced models like Random Forests that can capture non-linear relationships.
- Collect more frequent abundance measurements.
- Include other environmental variables like chlorophyll levels or current data.
- Better account for the temporal nature of the data - maybe using time series approaches

In the end, this project taught us that sometimes in machine learning, you don't get the amazing results you hoped for - and that's okay! The process of working through the problems, trying different approaches, and honestly evaluating your results is what really matters. Plus, now we know a lot more about both zooplankton than when we started!


PS: reminder to make this public, add all notebook links 
TODO:
- fitting graphs
