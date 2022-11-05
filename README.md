# Neural_Network_Charity_Analysis

## Project Scope
The Alphabet Soup Foundation is looking to modernize their  practices with the development of a predictive model to assess an applicant's success.  Upper leadership has become interested in Deep Learning Modeling.  Output from this model is a success predictor to be utized in the decision making process.



## Resources
- Python's TensorFlow library will be utilized to create, train, and evaluate data gathered from previous loan data provided as charity_data.csv
- Python 3.7.7, Anaconda Navigator 1.9.12, Conda 4.8.4, Jupyter Notebook 6.0.3

##  Preprocessing
- Review of the dataset includes 2 columns, one for EIN and one for the NAME of the organization requesting data.  As this information should be an annomoyous in the model without a direct link to particular organizations, these two columns were dropped.
- A review of the column contents was completed using df.nunique().
  - IS_SUCCESSFUL, SPECIAL_CONSIDERATIONS, and STATUS are Yes/No columns and will be treated as Binay in the analysis.
  - Of the 3 Variables above - IS_SUCCESSFUL is chosen as the Target as it represents a measure of effectiveness of the donation.
  - Features selected for the model include: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT 
  - Assessing results for potential bin creation using .CLASSIFICATION to determine if bins were necessary. 
    - Initial model APPLICATION_TYPE was selected.
    - For optimized Model ASK_AMT was selected.
  - Transforming categorical data using OneHotEncoder 
  - Splitting of the data into training and test sets
  
## Modeling and Analysis

Modeling is executed utilizing the TensorFlow library for Python and the Keras Method.  Two programs were created with the original modeling  https://github.com/KJAnalytics/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_new.ipynb and https://github.com/KJAnalytics/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimization.ipynb

### Initial Model - AlphabetSoupCharity_New

For the first phase of the modeling inputs included:
  - 2 hidden labyers utilizing ReLU activation with 80 and 30 notes respectively.  
  - Output layer executed with sigmoid activation as the Target is binary.
  
      _________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_6 (Dense)              (None, 80)                3520      
_________________________________________________________________
dense_7 (Dense)              (None, 30)                2430      
_________________________________________________________________
dense_8 (Dense)              (None, 1)                 31        
=================================================================
Total params: 5,981
Trainable params: 5,981


Non-trainable params: 0




To speed up the training process, we are using the activation function ReLU for the hidden layers. As our output is a binary classification, Sigmoid is used on the output layer.
For the compilation, the optimizer is adam and the loss function is binary_crossentropy.
The model accuracy is under 75%. This is not a satisfying performance to help predict the outcome of the charity donations.
To increase the performance of the model, we applied bucketing to the feature ASK_AMT and organized the different values by intervals.
We increased the number of neurons on one of the hidden layers, then we used a model with three hidden layers.
We also tried a different activation function (tanh) but none of these steps helped improve the model's performance.
Summary
The deep learning neural network model did not reach the target of 75% accuracy. Considering that this target level is pretty average we could say that the model is not outperforming.
Since we are in a binary classification situation, we could use a supervised machine learning model such as the Random Forest Classifier to combine a multitude of decision trees to generate a classified output and evaluate its performance against our deep learning model.
