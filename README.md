# Holiday-Package-Prediction
## Background
Trips and Travel Company is a company based in Saudi Arabia. Saudi Arabia's tourism shows an increasing revenue every year. This should be an opportunity for the company to increase the conversion rate. Therefore, the company plans to offer a new product called "Wellness Tourism Package" to customers through telemarketing. The marketing team contacted customers randomly, but this action was not effective, it is indicated by the conversion rate customers took the product was very low, and the other hand it caused high telemarketing cost, customer pitching through telemarketing cost company up to SAR 133,072.5 in one year.

## Data Preparation
This dataset has 4.888 rows and 21 features, including target and ID. Here are the preparations for the train data and the test data as follows.
1.	Change Incorrect Value

  In the datset there are 10 numerical and 9 categorical features. Among these features, there are 2 features that have input errors. In the feature Gender, the value Fe Male should be Female and ambiguous values   in the feature MaritalStatus, the values Unmarried and Single, which are both finally replaced by Single.

2.	Feature extraction

  We make 2 features that are AgeStructure dan MarketingCost.
  AgeStructure is created by binning the feature age based on reference age structure in Saudi Arabia  which is as follows
  15-24 years : early working age
  25-54 years : prime working age
  55-64 years : mature working age

  MarketingCost is created using DurationOfPitch, NumberOfFollowups and assuming that PhoneRate = 0.5
  MarketingCost = DurationOfPitch x NumberOfFollowups x PhoneRate

3.	Missing Values

  There are at least 15.5% of rows with at least 1 missing value. To handle this issue, missing values in numerical features are replaced by the median and missing values in categorical features are replaced by     the mode.

5.	Duplicated data

  There are 99 duplicate data in data train and 3 duplicate data in data test. We remove all duplicate data.

6.	Outliers

  We tracked the outliers using the IQR method. The number of outliers in each feature was as follows. 
![image](https://github.com/FadhilahIzzatiNadifan/Holiday-Package-Prediction/assets/93127350/16efcf56-7424-4024-831e-5687b4c5f7b2)

  Based on the outlier table above, there are 5 features that contain outliers. We considered not to remove the outliers on NumberOfPersonVisiting, NumberOfFollowups, and NumberOfTrips, because the outliers are    a natural variation. So, we only remove outliers on DurationOfPitch, and MonthlyIncome.

6.	Feature Transformation

  We transform the numerical data using StandardScaler, it gives better accury for model than the other methods.

7.	Feature Encoding

  For the feature TypeOfContact and Gender we change the value to 0 and 1. Then for the rest of categorical features we transform the data using One Hot Encoder.

8.	Imbalance data

  The target, ProdTaken, has an imbalanced problem between the value 0 and 1, that is, the value 0 is greater than 1. We handle this situation with SMOTE.



