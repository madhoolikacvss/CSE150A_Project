# CSE151A_Project

**Bootsrap method:**

For this milestone, we first decided to modify our previous model by applying the bootstrap method, to see if we could potentially increase accuracy before testing a second model. We created bootstrap samples from the dataset and split them into training (80%) and testing (20%) sets. After this, we trained a linear regression model on each bootstrap sample and evaluated its performance using Mean Absolute Percentage Error (MAPE). We identified the best-performing model based on the lowest MAPE, and extracted its MAPE, coefficients and intercept.

**Feature Expansion:**

Then, to add on from our last milestone, we did some more feature engineering, adding the following new features:

- Carbon Storage Potential: New feature combining ALK and DIC to estimate carbon storage potential
- Fractional Year: A more continuous representation of the date to help capture temporal trends, 
- Seasons: Categorized Fractional Year into seasonal periods and created a numerical mapping for each season
- Cluster Assignment: Applied K-means clustering on salinity and alkalinity (ALK) features to capture clustering
- Scaling and normalization for the new numerical features was performed using  the MinMaxScaler to standardize values

**Training and evaluating Second Model:**

Next, we trained and evaluated our second model, which makes use of elastic net regularization. Here, we wanted to assess if a more advanced model with regularization (Elastic Net) would improve accuracy over our standard linear regression model.
We extracted Salinity, Temp, d13C-DIC, DIC/ALK Ratio, Season Numeric, Cluster, Carbon Storage Potential as predictors, and then trained the model with L1 and L2 regularization, balancing bias and variance. Performance was evaluated using cross-validation with MSE, MAE, and MAPE as metrics. Finally, we plotted the training and testing errors to analyze model performance.
Our average values were 926,082.90, and 937,254.30 for the training and testing MSE respectively. These values, along with similar MAE and R² scores, indicate minimal overfitting but room for improvement in generalization. We concluded that techniques like feature selection or dimensionality reduction could be  further explored to improve this new model's performance.


[Link to our Project Notebook](https://colab.research.google.com/drive/1EQEcjeUrm6Erm4sgytVkt5_YzZd7FKiq#scrollTo=r6h1-li8Kapq)
