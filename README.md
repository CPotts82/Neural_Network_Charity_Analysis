# Neural_Network_Charity_Analysis
## Overview 
- Alphabet Soup is a non-profit, philanthropic foundation that donates to organizations that work towards making the world a better place and contributing to the well being of all Earth's inhabitants. Alphabet Soup wants to ensure that their donations are impactful and to avoid funding ineffective organizations. A binary classifier was designed and used to help analyze and decide whether applicants will be successful in their proposed goals if funded by Alphabet Soup. 
- Alphabet Soup has donated to over 34,000 organizations in the past 20 years. This data comes from the charity_data.csv and was explored, preprocessed and then used to train and test the neural network model. Initially there were 12 columns of metadata for each organization. Two of these columns were used as identifiers - the EIN and Name columns. There are nine columns of features that will help the model evaluate whether or not this organization will be successful. The features include application type, industry affiliation, government classification, use case for funding, type of organization, current status, income classification, if there are special considerations and finally, the amount the organization is requesting.  The final column in this dataset is the target variable for our model, this column shows if the money was used effectively. 
## Resources: 
charity_data.csv

Google Colaboratory, Python, Pandas, Tensorflow, Scikit-learn
## Results
### Data Preprocessing
The initial data from the charity_data.csv was preprocessed before using in the neural network. This consisted of removing columns that would not be beneficial for the model and binning features that had over 10 unique values. For the initial model the following features were binned: APPLICATION_TYPE (this feature originally had 17 unique values and after it was binned was consolidated to 9) and CLASSIFICATION ( this feature had 71 unique values and was consolidated into 6). Note: the ASK_AMT feature has 8747 unique values but was not binned until the optimization step. 
- Target Variable: IS_SUCCESSFUL
- Feature Variables: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT
- Removed Variables: EIN, NAME 
### Compiling, Training and Evaluating the Model
(Initial Model from Deliverable 2)
Number of:
- Neurons:
- Hidden Layers:
- Activation Functions
Explanation:
- Achieve target performance?
- Steps taken to increase model performance:

## Summary
### Overall Results
### Recommendations
