# Machine_Learning (ML) (Sochastic gradient descent Regression(SGDR))
This repository describes the implementation of the SGDR to predict the taxi price(target feature) based on the different input features(predictors).
## Data source
The data for the ML was extracted from the Kaggle website using the following link (https://www.kaggle.com/code/nani123456789/taxi-trip-fare-pre/input)
## Objective
The primary objective of this project was to train the model for predicting the taxi price given multiple input features.
## Methodologies and requirements
The data was converted into a pandas data frame which was then used for data cleaning, and processing. Along with this, an exploratory data analysis was performed in the dataset. The Sciki-learn library was used for SGDR analysis.
## Summary after conducting EDA
1. The data distribution was evenly distributed except for Trip_price and Trip_Distance_km.
2. The data for Trip_price and Trip_Distance_km were positively skewed.
3. It was observed that Trip_Price and Trip_Distance_km were highly correlated after analysing the pairplot and correlation matrix.
4. Although data for Trip_Price and Trip_Distance_km were logarithm transformed it was not used as standardization was applied for the machine learning model.
 ![image](https://github.com/user-attachments/assets/77a0449a-2688-4f8b-8075-6b83fd5a4fc9)
_**Figure 1:** Pairplot for the selected 5 features._
## SGDR algorithm
Upon using sckit-learn SGD regressor on raw data no convergence was observed as described in the graph below indicating that the model is not learning on its own. The potential cause for this could be uneven ranges for the features or improper selection of learning rate.
![image](https://github.com/user-attachments/assets/2b0cefcc-e767-493b-9c53-f4165ae9e23d)

_**Figure 2:** Mean squared error(MSE) evolution on raw data for SGDR._

### Scaling of the features
 Following the feature normalization an improvement in MSE was observed reducing from 1*10^26 to 450 as shown in the figure below:
 ![image](https://github.com/user-attachments/assets/0ce8e5f9-f01b-4e40-a89f-388a547dfd32)
 
_**Figure 3:** Mean squared error(MSE) evolution on scaled data._

Although the algorithm seems to converge, in order to evaluate whether this improvement is due to scaling or real improvement in the model generalization a  robust metric known as root mean squared error (_RMSE_) was used. Upon investigation, the rmse for both raw and scaled was the same indicating the failure of the model to generalize on prediction taxi prices.

### Learning rate evaluation
One of the key parameters for a good machine learning model is to have an optimized learning rate. As a result, different learning rates were evaluated such as 0.01(base case),0.001 and 0.0001. On learning rates of 0.01 and 0.001, no convergence was seen whereas on learning rate of 0.0001, a convergence to low _MSE_ was observed. One of the downfalls of using such a low learning rate could be that, it might be fluctuating on the local minima. So a further investigation should be conducted on it for assurance.
![image](https://github.com/user-attachments/assets/ddb0f47e-d852-42ae-aaad-df4233f25297)

_**Figure 4:** MSE evolution on raw data using different learning rates._

### Feature engineering
One of the many ways to improve the model is to perform feature engineering but in our case, this didn't have a positive impact as seen in the figure below:
![image](https://github.com/user-attachments/assets/e0530794-a9c5-4894-b4ad-5d4f8c785505)

_**Figure 5:** MSE evolution after feature engineering of degree 2 for different learning rates._

### Tabulated weight and bias for each evaluation
|Name|learning_rate|w1|w2|w3|w4|w5|b|
|----|-------------|----|----|----|----|----|----|
|Raw_data|0.01|9.01E10|-8.47*E10|-1.21*E11|-1.45*E11|8.49*E8|-6.52*E10|
|Scaled_data|0.01|31.71|0.22|9.84|5.52|8.2|56.95|
|Raw_data|0.0001|1.57|-2.42|12.65|2.76|0.27|-10.43|
|Feature_engineered|0.01|9.01*E10|-8.47*E10|-1.21*E11|-1.45*E11|8.49*E8|-6.52*E10|

## Principal composition analysis
Since the model involves all the features that could not provide good performance I tried to reduce the dimension by performing PCA. The explained variance was more or less similar for the principal components. (This is normally done earlier to reduce the large dataset dimension I am performing this for exploratory/research purposes.)
|Principal_Components|Explained_Variance(%)|
|--------------------|---------------------|
|PC1|21.6|
|PC2|21.3|
|PC3|19.2|
|PC4|19.1|
|PC5|19.0|

Scores and Load diagram was created to see if there was any clustering or not. Analysing the result there was no such phenomenon observed.
![image](https://github.com/user-attachments/assets/5838d962-ac02-4ace-a728-0f481bff448d)

_**Figure 6:** Scores and Loadings plots from PCA._

### Improvements and future analysis
1. Collecting more datasets for better model representation/building.
2. At a learning rate of 0.0001 model seems to generalize quite well. Further investigation is needed for an informed conclusion.








