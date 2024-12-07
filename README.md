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


PS: reminder to make this public, add all notebook links 
TODO:
- fitting graphs
