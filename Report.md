Overview
This analysis was designed to investigate whether a neural network model could be successfully used to predict whether applicants for funding would be able to successfully use the provided funding. A dataset was provided containing a list of previous applicants with various data, including whether their funding was successful.
Details of the analysis is given below.
Results
Pre-processing
Before use in the analysis, the data was cleaned and processed
Columns
The data was provided with the following columns, with the column use indicated
* EIN�and�NAME�Identification columns :�Unnecessary data
* APPLICATION_TYPE�Alphabet Soup application type :�Feature
* AFFILIATION�Affiliated sector of industry :�Feature
* CLASSIFICATION�Government organization classification :�Feature
* USE_CASE�Use case for funding :�Feature
* ORGANIZATION�Organization type :�Feature
* STATUS�Active status :�Feature
* INCOME_AMT�Income classification :�Feature
* SPECIAL_CONSIDERATIONS�Special consideration for application :�Feature
* ASK_AMT�Funding amount requested :�Feature
* IS_SUCCESSFUL�Was the money used effectively :�Target

Data cleaning steps
The following steps were undertaken in cleaning the data
1.	Remove unnecessary columns EIN and NAME
2.	Review the number of unique entries in all columns to identify which ones could be reduced in number
o	Columns with large numbers of unique entries were APPLICATION_TYPE, CLASSIFICATION and ASK_AMT. ASK_AMT is the asked amount and so not suitable for reducing the number of categories
3.	Bin all categories in APPLICATION_TYPE with fewer than 500 applications into an Other category
4.	Bin all categories in CLASSIFICATION with fewer than 100 applications into an Other category
5.	Convert categorical data to numeric with pd.get_dummies
6.	Split data into feature and target arrays
7.	Split data into train and test datasets
8.	Scale both datasets using StandardScaler

Compiling, training and evaluating the model
Initial model
An initial model was set up consisting of two hidden layers with the relu activation, and an output layer with a sigmoid activation. The two hidden layers had 10 and 5 neurons respectively. This model was compiled with binary_crossentropy loss and the adam optimiser, and recording the accuracy and AUC metrics. The model was trained on the training dataset and evaluated on the test dataset.
These model parameters were chosen as they had been most commonly used in previous models. The number of neurons sought to provide sufficient chance for the model to perform without excessive computational requirements.
Initial model result
268/268 - 1s - loss: 0.5569 - accuracy: 0.7217 - 1s/epoch - 4ms/step
Loss: 0.5569065809249878, Accuracy: 0.7217492461204529
Optimisation 1: Increasing processing by increasing epochs
The model was tried to achieve an accuracy of 75 by increasing the number of epochs which resulted in an accuracy score of 73 which is still below the accuracy level required.
Optimization 2: Changing model by increasing neurons
The model's complexity was increased by adding neurons to second layer of the model. The input layer and output layer and model compilation were as for the initial model with epochs increased.

Summary
The models tested had an accuracy level of around the same level. The model reached the best accuracy with same complexity and increased epochs and that was around 73+ percent. the model reached it's best value with initial model and increased epochs while changing model didn�t have much impact on the accuracy.




