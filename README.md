# Industrial Copper Modeling
Skills take away From This Project: Python scripting, Data Preprocessing, EDA, Streamlit
Domain: Manufacturing

Problem Statement:
The copper industry deals with less complex data related to sales and pricing. However, this data may suffer from issues such as skewness and noisy data, which can affect the accuracy of manual predictions. Dealing with these challenges manually can be time-consuming and may not result in optimal pricing decisions. A machine learning regression model can address these issues by utilizing advanced techniques such as data normalization, feature scaling, and outlier detection, and leveraging algorithms that are robust to skewed and noisy data. 
Another area where the copper industry faces challenges is in capturing the leads. A lead classification model is a system for evaluating and classifying leads based on how likely they are to become a customer . You can use the STATUS variable with WON being considered as Success and LOST being considered as Failure and remove data points other than WON, LOST STATUS values.

The solution must include the following steps:
  Exploring skewness and outliers in the dataset.
  Transform the data into a suitable format and perform any necessary cleaning and pre-processing steps.
  ML Regression model which predicts continuous variable ‘Selling_Price’.
  ML Classification model which predicts Status: WON or LOST.

Approach: 
1.Data Understanding: Identify the types of variables (continuous, categorical) and their distributions. Some rubbish values are present in ‘Material_Reference’ which starts with ‘00000’ value which should be converted into null. Treat reference columns as categorical variables. INDEX may not be useful.
2.Data Preprocessing: 
  Handle missing values with mean/median/mode.
  Treat Outliers using IQR or Isolation Forest from sklearn library.
  Identify Skewness in the dataset and treat skewness with appropriate data transformations, such as log transformation(which is best   suited to transform target variable-train, predict and then reverse transform it back to original scale eg:dollars), boxcox     transformation, or other techniques, to handle high skewness in continuous variables.
  Encode categorical variables using suitable techniques, such as one-hot encoding, label encoding, or ordinal encoding, based on their nature and relationship with the target variable.
3.EDA: Try visualizing outliers and skewness(before and after treating skewness) using Seaborn’s boxplot, distplot, violinplot.
4.Feature Engineering: Engineer new features if applicable, such as aggregating or transforming existing features to create more informative representations of the data. And drop highly correlated columns using SNS HEATMAP.
5.Model Building and Evaluation:
  Split the dataset into training and testing/validation sets. 
  Train and evaluate different classification models, such as ExtraTreesClassifier, XGBClassifier, or Logistic Regression, using   appropriate evaluation metrics such as accuracy, precision, recall, F1 score, and AUC curve.   
  Optimize model hyperparameters using techniques such as cross-validation and grid search to find the best-performing model.
  Interpret the model results and assess its performance based on the defined problem statement.
  Same steps for Regression modelling.(note: dataset contains more noise and linearity between independent variables so itll perform well only with tree based models)

Conclusion:
*1.] Given dataset contains potential outliers in selling price(TARGET VARIABLE),so applying log transform instead box-cox transformation cause it can handle large ranges of data, and the transformation is easily reversible.*

*2.] It also contains right skewness in trainable parameters quantity tons, using BOX_COX transformation as it is best suited for reasonable imputation for treating outlier.*

*3.] Skewness in thickness, width are treated by making box-cox.*

*4.] Model achieves best R2 score of 0.93 with EXTRA TREE regressor, 300 with RIDGE regressor during 1st training where no outliers were removed. after outlier removal, model achieves same result of 0.95 nearer with EXTRA TREE but with RIDGE regressor 0.93 R2score.*
