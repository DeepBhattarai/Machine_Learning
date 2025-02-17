# Machine_Learning (ML) (Sochastic gradient descent Regression(SGDR))
This repository describes the implementation of the SGDR to predict the taxi price(target feature) based on the different input features(predictors).
## Data source
The data for the ML was extracted from the Kaggle website using the following link ()
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
Although the algorithm seems to converge, in order to evaluate whether this improvement is due to scaling or real improvement on the model generalization a  robust metric known as root mean squared error (rmse) was used. Upon investigation, the rmse for both raw and scaled was same indicating the failure of the model to generalize on prediction taxi price.

