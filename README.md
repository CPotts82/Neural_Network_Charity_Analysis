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
- In the first optimization attempt, the number of hidden layers was kept at 2 and the nodes were also kept the same at 36. The activation functions were the same as well because I wanted to see if the fact that the ASK_AMT column now being binned would improve the initial model.  

![ModelOpt_1](https://user-images.githubusercontent.com/106348899/198891297-78be0cc2-88b6-47cc-af23-1193a4245a00.png)

The accuracy of this first attempt was less than the original model. The loss was much higher than the original and unacceptable for this organization. This shows that binning the ASK_AMT column may not effect the model that much or maybe this needs to be rebinned in a different way.  

![Accuracy1](https://user-images.githubusercontent.com/106348899/198891305-d69120a5-f85e-47d2-b372-1674999db9dd.png)

- In the second attempt to increase the accuracy of this model, an additional hidden layer was added and the number of nodes was adjusted to 34. Just two less than the previous attempt. The activation functions were kept the same with the new hidden layer using the relu function. 

![ModelOpt_2](https://user-images.githubusercontent.com/106348899/198891645-61fd98b5-fd7c-4b2b-a67f-6fb6bea2ba30.png)

The accuracy for this model was even less than the first optimization attempt. The accuracy was 64.2% and the loss was 1.7. Both of these values are unacceptable. 

![Accuracy2](https://user-images.githubusercontent.com/106348899/198891656-f509f733-d3c6-4264-bb26-c430aad576a0.png)

- In the final attempt to increase the performance of this model, a 4th hidden layer was added and the number of nodes was increased from 34 to 44. The first and second layer activation functions were kept as relu, the third layer's activation function was changed to tanh and the fourth and final ouput layers used the sigmoid function. 

![ModelOpt_3](https://user-images.githubusercontent.com/106348899/198892031-44398e67-4c95-4102-a53c-ef1048aaa647.png)

The performance of this model was better than the last two attempts. The accuracy improved to 67.6% and the loss dropped to 68.6%. These results are still not ideal for Alphabet Soup but we are now moving in the right direction. 

![Accuracy3](https://user-images.githubusercontent.com/106348899/198892071-571eedfc-7ec9-4269-8721-b677cf49cc3d.png)

Note: all models used 100 epochs to train

## Summary
### Overall Results
The results of the four attempts of the neural network show that the first model had the best performance in terms of accuracy at 68.9%. The final attempt to optimize this model had a much better loss percentage at 68.6% versus the first model's 85.89%. More work needs to be done on this model to increase the accuracy to above 75% and to decrease the loss as much as possible. 
### Recommendations
I believe the deep learning models used in this analysis were a bit too complex for this dataset. Ultimately the model was only trained on 44 features. I would recommend using a simplified version of this neural network. Using only 1 hidden layer and fewer nodes would possibly work. I would keep the activation function for the final ouput as 'sigmoid' but use trial and error to decide on the activation function for the hidden layer. I would also recommend different binning combinations for the three features that are binned. 
