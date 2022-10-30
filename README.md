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

![Preprocessing](https://user-images.githubusercontent.com/106348899/198889461-5b7c9fcc-296f-44ff-b890-ca6e75d364a6.png)

The data was then encoded, merged into the dataframe (encoded columns merged, original columns dropped), and split into training and testing data. After the data was split it was then scaled by scikit-learns StandardScaler.

### Compiling, Training and Evaluating the Model
After the data was preprocessed and processed, the model was built using the keras module with the Sequential and Dense classes from the Tensorflow library. The model was compiled with "binary_crossentropy", the "adam" optimizer and using the "accuracy" metric. The trained model was set up to save after every 5 epochs. 
Number of:
- Neurons: 36 neurons were chosen because I wanted a large number of neurons but not an overabundance therefore I kept this number between the number of input variables (43) and the output variable (1). 
- Hidden Layers: 2 hidden layers were chosen because I wanted to keep this first model fairly simple. To see what kind of accuracy could be expected of a simple neural network, then add more layers to the optimization models if needed. 
- Activation Functions: 'relu', relu', 'sigmoid' - for the first hidden layer, second hidden layer and output layer respectively. I chose relu for the hidden layers because there was no negative input and I have had the most success using this activation function over others in trial runs. The sigmoid function was used in the output layer because ultimately we were looking for probability of a donation to be effective. 

![Initial_Model](https://user-images.githubusercontent.com/106348899/198890615-53fee6ca-fd84-48a0-a632-3d7206d04f2b.png)


Explanation:
- This model did not meet the target expectation of 75% accurate. The accuracy of this model was 68.9% with a loss of 85.9%. For this particular situation of making sure donations are going to legitimate and effective organizations, I think the company would want higher accuracy and lower loss percentages. 

![Metrics1](https://user-images.githubusercontent.com/106348899/198890625-aa4139c1-b61d-4479-9d9d-8f3ab4545229.png)

### Optimization of the Model
In order to optimize the model, the first thing that I did was bin the ASK_AMT column. It had 8747 unique values that needed to be binned so I could ensure it was not skewing the model. This feature was binned into two different categories, it was split up by binning amount counts less than 500. The APPLICATION_TYPE and CLASSIFICATION features were binned the same as the first model. After binning the ASK_AMT column I preprocessed and processed the data in the exact same way as the first model. The input features increased by 1, from initially 43 input features now to 44 due to the binning of the ASK_AMT feature.
- In the first optimization attempt I kept the same number of hidden layers at 2 but increased the number of nodes from 

## Summary
### Overall Results
### Recommendations
