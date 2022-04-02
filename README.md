# Case-Study-Lead-Scoring
Logistic Model Building using Stats Model &amp; RFE

# Problem statement:
X Education sells online courses and needs a solution that can increase their customer lead conversions. The focus is selection of the most promising leads, i.e., the leads that are most likely to convert into paying customers.
The company needs a model wherein a lead score is assigned to each of the customer leads. The high score value would denote a high conversion chance of the prospect customer while lower score value means lower conversion chance.
The CEO, in particular, has given a ballpark of the target lead conversion rate to be around 80%.

# Solution Summary:
   ## Step1: Reading and Understanding Data
        • This step involves importing the data and inspection
   ## Step2: Data Cleaning:
        • Checking and removing the fields that have all unique values
        • Checking removing the columns with >=40% of Missing values
        • Few columns with a level “Select” means that customer did not fill info and is treated as missing
        • Treatment of Missing values
                o Imputation with mode value on categorical variables
                o Removal of rows for <1.5% missing values in numeric columns
        • Treatment of Outlier values
                o Imputation with 5th Percentile value for data in till 5th Percentile
                o Imputation with 95th Percentile value for data in above 95th Percentile
   ## Step 3: Data Analysis & Reducing Skewness
        • Identifying the columns with high number of categories but less percentage of data in them. This data is classified as “Other”.
        • Identifying and dropping columns with only 1 level. Not a value-add to model.
        • Identifying and dropping columns which are Highly Skewed Categorical Variables
        • Numerical column analysis
                o Checking the imbalance in the target variable. Calculated the conversion rate. Conversion Rate is 37.86 %
                o Analysed the numeric attributes with respect to target variable “Converted”
                o Inference: From the chart above, the leads spending more time on website are more likely to convert, thus website should be made more engaging to increase conversion rate.
        • Removing "Sales team generated" variables (To avoid overfitting)
        • Percentage of rows retained in data cleaning process = 98.2%
   ## Step 4: Data Preparation for Model
      • Converting the binary variables to 0/1
        • Dummy Variable Creation for categorical attributes and removed the column marked as `suffix` _ `Other` for these attributes. Removed original column after dummy variable addition
        • Test-Train Split (70:30 opted)
        • Feature Scaling using StandardScaler
        • Checked the correlation coefficients to see which variables are highly correlated. Dropped the highly correlated dummy variables
   ## Step 5: Model Building using Stats Model & RFE:
        • Using the Recursive Feature Elimination(RFE), we selected the top 15 important features for our model
        • Using the statistics generated, we recursively tried looking at the p-values in order to select the most significant values that should be present and dropped the insignificant values.
        • Finally, we arrived at the 10 most significant variables. The VIF’s for these variables were also found to be <2 (which is good).
        • For our final model we checked the optimal probability cut off by finding points and checking the accuracy, sensitivity and specificity.
        • We then plotted the ROC curve for the features and the curve came out be pretty decent with an area coverage of 83% which further solidified the of the model.
        • Then, checked if 76% cases are correctly predicted based on the converted column.
        • We checked the precision and recall with accuracy, sensitivity and specificity for our final model on train set.
        • Based on the Precision and Recall trade-off, we got a cut off value of ~ 0.3.
        • Then we implemented the learnings to the test model and calculated the conversion probability based on the Sensitivity and Specificity metrics and found out the Accuracy=79%; Sensitivity= 75%; Specificity=82%.
   ## Step 6: Conclusion:
        • The lead score calculated in the test set of data shows the conversion rate of 75% on the final predicted model which nearly meets the expectation of CEO.
        • Good value of sensitivity of our model will help to select the most promising leads.
        • Features which contribute more towards the probability of a lead getting converted are:
                o Lead Origin_Lead Add Form
                o What is your current occupation_Working Professional
                o Lead Source_Welingak Website
