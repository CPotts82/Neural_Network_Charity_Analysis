# Neural_Network_Charity_Analysis
## Overview 
- Alphabet Soup is a non-profit, philanthropic foundation that donates to organizations that work towards making the world a better place and contributing to the well being of all Earth's inhabitants. Alphabet Soup wants to ensure that their donations are impactful and to avoid funding ineffective organizations. A binary classifier was designed and used to help analyze and decide whether applicants will be successful in their proposed goals if funded by Alphabet Soup. 
- Alphabet Soup has donated to over 34,000 organizations in the past 20 years. This data comes from the charity_data.csv and was explored, preprocessed and then used to train and test the neural network model. Initially there were 12 columns of metadata for each organization. Two of these columns were used as identifiers - the EIN and Name columns. There are nine columns of features that will help the model evaluate whether or not this organization will be successful. The features include application type, industry affiliation, government classification, use case for funding, type of organization, current status, income classification, if there are special considerations and finally, the amount the organization is requesting.  The final column in this dataset is the target variable for our model, this column shows if the money was used effectively. 
- In order to optimize this model, a variety of techniques were used...
## Resources: 
charity_data.csv

Google Colaboratory, Python, Pandas, Tensorflow, Scikit-learn
## Results
### Data Preprocessing
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
