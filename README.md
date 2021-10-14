# AI-Project_02_house_pricing
## 1.	Introduction
In this project we tackle the Boston house pricing dataset from Kaggle with a multiple linear regression and some statistical techniques to select the best features that can improve the performance of the model.

The main motivation for this project is show how we can handle a dataset, selecting the most relevant features for a multiple linear regression.

In this project, we only use three methods to select features:

- **Correlation coefficient** -
    This coefficient, that have values between – 1 and 1, show the correlation between two descriptors. A good way to visualize the corelation coefficient of all involved values in a dataset is the correlation matrix. In this matrix each numerical descriptor represents a column and a row, and the diagonal is the descriptor correlation intersection.
    
- **Z-score (standard score)** -
    This number is a metric of how far from the mean a data point is. This measure describes how many standard deviations below or above the mean a point is. 
    
- **P-values** -
    The p-value is the probability that a calculated statistical value is possible given a true null hypothesis. This value allows us to differentiate between statistically significant results and those product of chance in the sampling. 

## 2.	Procedure
 
To make the most of the data we delete the outliers in the dataset. There are several techniques used to treat outliers, such as the z-score, the InterQuartile Range (IQR), the outlier fences or a hypothesis test. For simplicity in this project, we decided to just erase the outliers that are lower than Q1-(2IQR) or greater than Q3+(2IQR)using the InterQuartile Range (IQR). 
Also, we made proobs with the z-score to eliminate outliers, but this metric couldn't improve the performance of the model in the probes realized.
With the data that passed the filter, we applied a null hypothesis test to determine the correlation between the characteristics and the labels. The null hypothesis probed is that the selected combination of dependent variables does not have any effect on the independent variable. With the associated p-values we selected which characteristics would be passed as parameters in the multiple linear regression. If the p-values are higher that the threshold (selection criteria) the combination of features are discarded. This technique is known as backward elimination.
Finally, the train and test sets were prepared, and the model was trained. In this step a function that train the model was implemented. This function also applies an evaluation to measure the square correlation coefficient of the model and in case of this parameter was higher than a defined value, the model is saved.

## 3.	Conclusions

The best results are obtained when outliers are removed and then backward elimination is applied, before training the model. This can lead to a correlation coefficient of 0.89.

The variation in the results is since each time a test is performed, the training and test groups are randomly selected, which affects the performance of the model.

We can also conclude that among the factors analyzed, one of those that most affects the performance of the data is the elimination of outliers. 

Also, it is relevant to notice that p-values sometimes can fail predicting variables that are correlated and in general terms this is not the best way to select the most relevant features but in this case they performed well.
