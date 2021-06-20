## Analysis of Hotel Bookings 

### Abstract
The motivation behind this project is to analyze the hotel bookings over the year 2015, to draw significant insights into the various parameters affecting the cancellation of hotel bookings, and how the booking patterns vary as a function of other factors. Several Statistical Learning methods were used in the process of data analysis using R.

### Introduction
This project focuses on the analysis of Hotel Booking Data, a publicly available dataset on www.kaggle.com. The main aim of this project is to classify the hotel bookings, under the categories ‘Canceled’ and ‘Not Canceled’ respectively. Thus, this project tackles the Classification problem. 

The analysis process was composed of detailed procedures, to yield sensible classification results, as the after-effect of several model fittings. The first step involved data cleaning and preparation. In here, the correct categorization and organization of data were involved along with eliminating predictors that otherwise held the potential to negatively affect the analysis results. After the data were deemed fit to proceed with further analyses, informed choices were made to narrow down the models to be used for data fitting in the next phase of the project.

Models used for training were- Logistic Regression, K-Nearest Neighbors, Classification Tree, Boosting, Random Forest Tree, Principal Components Analysis and K-Means Clustering. These models were used to explain the relation and interaction between the predictors and consequently for the classification of ‘is_canceled’ binary variable. These trained models were then used for prediction purposes, to predict if a specific hotel booking would be cancelled, based on the values of other predictors. These other predictors contained information about the hotel type, booking date, special preferences, country, reservation status and many other useful determining parameters. Such an analysis can help add business value to a hotel, since prior knowledge of how a booking can turn out to be, can help such an enterprise in taking strategic steps towards business development. 

### Discovery and Data Preparation
I came across this dataset on Kaggle. I searched through a significant number of datasets, with hopes of finding one that would hold significant business value, when implemented correctly. The Hotel Booking Demand dataset emerged to be one such dataset, with well-defined categories and a fair amount of data usability. This data set contains 119,390 observations off 32 variables.

All the categorical variables had to be converted to factors for analysis purposes. Before preprocessing was carried out, some exploratory analysis was done to better understand the organization of data. 

After a deeper understanding of all the data and its aggregates was obtained, the following steps went into data cleaning and preparation- 

1.	Firstly, the dataset was checked for missing values. It turned out that the ‘children’ attribute contained four missing values. These values were substituted with the corresponding values in the ‘babies’ column. 
2. After the missing values were imputed accordingly, two of the columns, namely ‘agent’ and ‘company’, containing null values were eliminated.  
3.	Following the above step, dummy-coding of variables was carried out to yield suitable numerical values for categorical attributes. This led to a large inflation in the number of predictor values. 
4.	Subsequently, predictors were checked for non-zero variances. Those with near zero variances, were eliminated since they did not contribute positively to predictions or results. The ‘nzv’ command in R served this purpose. 
Determination and elimination of correlated predictors followed the aforementioned step.  Highly correlated predictors lead to poor predictions.
The final step in pre-processing involved the scaling and centering of predictors. This was achieved through the ‘pre-process’ function of CARET. 

### Model Planning and Building
Since the problem belonged to the Classification Category, several classification models were fit over the hotel bookings dataset. However, very few of the classification models were able to yield meaningful results.  The models and their specifications are listed as follows- 
#### 3.1	Logistic Regression- 
Logistic Regression is the optimum method for binary classification problems. Since the response variable ‘is_canceled’ takes on the value of either 0 or 1, it was employed for model fitting. ROC was used as a performance metric. The ROC yielded an exact value of 1 after fitting a Logistic Regression model to this dataset. I tried transforming and manipulating the predictors in several ways, however, the output did not change. Caret’s function train() was used for fitting logistic regression. The train control method was set to CV (Cross-validation) with k = 10 folds. 
#### 3.2	KNN- 
KNN was the fit in a similar way of Logistic Regression. Surprisingly, KNN performed better than Logistic Regression in this data setting. The performance metric was again set to ROC.  
#### 3.3	Decision Tree- 
A simple decision tree was fit to the data to interpret the statistical model in a simplified way. The ‘rpart’ function in R provided the basis of training a tree model.  
#### 3.4	Random Forest-  
Random Forest was fit on the dataset following the decision tree. The dataset was split into test and training observations and predictions on the test set were obtained after fitting the model over training set. A prediction accuracy of 82.23% was obtained through this method. 
#### 3.5	Boosting- 
Yet another classification tree model used was Boosting. The ‘gbm’ method was used to fit this model. The predictions were obtained for 100 trees. 
#### 3.6	Principal Components Analysis- 
The Principal Components Analysis, (PCA), was used to better understand the predictors, and the interactions between them. Meaningful insights for 5 principal components were drawn using PCA. 
#### 3.7	K-Means Clustering-  
Lastly, K-means clustering was used after eliminating the response variable (as in PCA) to find existing sub-groups in the dataset. A few interesting patterns and clusters were observed through K-Means Clustering at different values of K. 

### Conclusion
The goal of the whole project was effectively predicting whether a hotel booking would be cancelled or not, based on the many predictors that made up the dataset. However, successfully validating the training results against test results could not materialize in this case. 
Classification methods are tougher to fine-tune. 
Logistic Regression Model yielded too accurate results, which did not follow the nature of the true observations. Boosting Tree was executed successfully during training, however, the validation yielded errors that even extensive data manipulation could not tackle. PCA and K-Means were effective in determining the relations between various predictors. 
For successful predictions of hotel cancellations, I recommend that more numeric data be incorporated into the dataset to meaningfully quantify predictions. There is a pressing need for testing this data against more statistical classification methods, to derive business value for the same. 


