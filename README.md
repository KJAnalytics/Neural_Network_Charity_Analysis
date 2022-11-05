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

For the first phase of the modeling process included:
  - 2 hidden labyers utilizing ReLU activation with 80 and 30 notes respectively.  
  - Output layer executed with sigmoid activation as the Target is binary.
  - 25,724 samples with 43 features.
  - Epochs 100


 Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense (Dense)               (None, 80)                3520      
                                                                 
 dense_1 (Dense)             (None, 30)                2430      
                                                                 
 dense_2 (Dense)             (None, 1)                 31        
                                                                 
=================================================================
Total params: 5,981
Trainable params: 5,981
Non-trainable params: 0 

Compilation was eecuted with binary_crossentrophy and adam optimizer with the output metric "Accuracy". Checkpoints were created using tensorflow.keras.callbacks ModelCheckpoints with 100 epochs utilized.  Final model output is saved as: https://github.com/KJAnalytics/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.h5 

### Optimized Model - AlphabetSoupCharity_Optimization

For the optimization phase of the modeling process included:
  
  - The addition of a third hidden layer with nodes of 80,30,10 respectively.
  - Epochs increased to 100=.
     Model: "sequential_1"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense_3 (Dense)             (None, 80)                703200    
                                                                 
 dense_4 (Dense)             (None, 30)                2430      
                                                                 
 dense_5 (Dense)             (None, 10)                310       
                                                                 
 dense_6 (Dense)             (None, 1)                 11        
                                                                 
=================================================================
Total params: 705,951
Trainable params: 705,951
Non-trainable params: 0
_________________________________________________________________


## Take Aways
One of the first learnings in this project was that processing speed with large datasets, increasing the number of Epochs significantly increases the processing times increased from 1-2 minutes to nearly 20 minutes to execute

The neural network model was not able to reach a target of 75% accuracy which from class and reading, this is a nominal level target.  With that said, the model was able to reach between 71-73% accuracy as manipulations were made to epochs, number of hidden layers, methods- sigmoid,tanh, relu.   

Nexts steps could include additional investigation to determine the existance of imbalance within the dataset and within which factors. As this is a rather large database, the use of hypertuning, suffling, among other techniques may be worth considering.  Also, as the focus was on neural, it would be worth running under different model types to see if we can learn additional information.

