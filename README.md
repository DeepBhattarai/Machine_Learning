# Machine_Learning (ML) (Sochastic gradient descent Regression(SGDR))
This repository describes the implementation of the SGDR to predict the taxi price(target feature) based in the different input features(predictors).
## Data source
The data for the ML was extracted from the kaggle website using following link ()
## Objective
The primary objective of this project was to train the mdoel for predicting the taxi price given multiple input feature.
## Methodologies and requirements
The data was converted into pandas dataframe which was then used for data cleaning,processing. Along with this an exploratory data analysis was performed in the dataset.The Sciki-learn library was used for SGDR analysis.
## Summary after conducting EDA
1. The data distribution were evenly distributed except for Trip_price and Trip_Distance_km.
2. The data for Trip_price and Trip_Distance_km were positively skewed.
3. It was observed that Trip_Price and Trip_Distance_km was highly correlated after anlaysing pairplot and correlation matrix.
4. Although datas for Trip_Price and Trip_Distance_km were logarithm transformed it was not used as standardization was applyed for machine learning model.
 ![image](https://github.com/user-attachments/assets/77a0449a-2688-4f8b-8075-6b83fd5a4fc9)
_**Figure 1 :** Pairplot for the selected 5 features._
## SGDR algorithm
