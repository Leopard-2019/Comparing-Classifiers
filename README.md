<h1>Comparing-Classifiers</h1>
This python application using jupyter notebookm compares the results of k-nearest neighbors, logistic regression, decision trees, and support vector machines classification models using dataset related to the marketing of bank products over the telephone.

</br>
The current CRISP-DM Process Model for Data Mining (see Figure 1) was followed.

</br>
</br>
<p align="center">
<img src="images/Figure1_CRISP_DM_Model.jpeg" width="300px" height="300px">
<h4 align="center"> Figure 1</h4>
</p>

<h2>Business Understanding</h2>
The Business goal is  to come up with a machine learning classification model to identify if a future client will subscribe a term deposit or not based on several independent variables such as education level, marital status, if has housing loan or not, personal loan or not, etc. The machine learning classification model is selected by ranking up four different machine learning models: KNeighborsClassifier, Logistic Regression, Support Vector Machine, and Decision Tree by their metrics and other indicators such as the Precision-recal curve, and confusion matrix. The dataset used to train those four models is related to the marketing of bank products over the telephone as mentioned before. The analysis will be done using python & jupyter notebook.

<h2>Data Understanding</h2>
The original dataset (bank-full.csv) given is in .csv format.It consists of 17 columns and 6316 rows as shown below. The target/independent columns is "y" which is categorical (nominal feature), and it stands for: has the client subscribed a term deposit?. This variable is imbalance as will be later be seen. There are only two numerical columns: "age","balance", and "pdays" since the column: "duration" is only for benchmark purposes and is discarded for realistic predictive modelling, and the columns" day" and "month" were not considered numerical for obvious reason during the classification process..The rest of the columns are categorical (nominal). Most of the dataset provided is imbalanced before entering the modeling phase. None of the columns contain "NaN" values. Duplicates were not observed. It is thought that in order to provide more insight into the aforementioned dataset, a data preparation,i.e, data cleaning process needs to be done first.

</br>
</br>
<p align="center">
<img src="images/Figure17_2.jpeg" width="300px">
<h4 align="center"> Figure 2</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_3.jpeg" width="1000px">
<h4 align="center"> Figure 3</h4>
</p>


<h2>Data Preparation</h2>
The first step was check if there were any null values, and also make sure that there was not duplicates present in the dataset as well. As it is observed in Figure 4, there were initially no null values nor duplicates.

</br>
</br>
<p align="center">
<img src="images/Figure17_4.jpeg" width="800px">
<h4 align="center"> Figure 4</h4>
</p>

Columns: "job", "education", "poutcome", and "contact" have a feature with the same name: "unknown", so it was decided to replace it wiht different name to avoid potential problems in the foregoing analysis as indicated by Figure 5:

</br>
<p align="center">
<img src="images/Figure17_5.jpeg" width="800px">
<h4 align="center"> Figure 5</h4>
</p>


More insight into the dataset can be gained before finalizing the data preparation by doing the histograms for most of the categorical columns as shown on Figures 6, 7, and 8. All categorical columns/independent variables are nominal.

</br>
<p align="center">
<img src="images/Figure17_6.jpeg" width="1000px">
<h4 align="center"> Figure 6</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_7.jpeg" width="1000px">
<h4 align="center"> Figure 7</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_8.jpeg" width="1000px">
<h4 align="center"> Figure 8</h4>
</p>


<h3>Treatment of Outliers in Numerical Columns: "age", "balance", and "pdays"</h3>
The presence of outliers in the numerical columns: 'age", "balance", and "pdays" (see Figures 9, 10 and 11) indicated by the respective boxplot demands a careful and efective treatment before moving into the modeling phase. The histograms of the aforementioned columns have been also added for completeness.

</br>
<p align="center">
<img src="images/Figure17_9.jpeg" width="1000px">
<h4 align="center"> Figure 9</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_10.jpeg" width="1000px">
<h4 align="center"> Figure 10</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_11.jpeg" width="1000px">
<h4 align="center"> Figure 11</h4>
</p>

One passes was applied to the aforementioned columns in order to remove the outliers. The values equal to -1 was removed from the column "pdays". The aforementioned pass consisted on applying the well known Inter quartile range (IQR) method. Figure 13, 14, and 15 shows the final results after applying this method to remove the outliers. As it can be observed, this pass was very effective, i.e., removing the majority of the outliers. As an additional comments, the target column "balance" shows a distribution skewed to the left, i.e, it was felt there was no need  to use its logarithm during modelling phase.

</br>
</br>
<p align="center">
<img src="images/Figure17_12.jpeg" width="1000px">
<h4 align="center"> Figure 12</h4>
</p>

</br>
</br>
<p align="center">
<img src="images/Figure17_13.jpeg" width="1000px">
<h4 align="center"> Figure 13</h4>
</p>

</br>
</br>
<p align="center">
<img src="images/Figure17_14.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

<h4>Treatment of Categorical Features</h4>

<h3>Nominal Features</h3>
Nominal features are categorical features that have no numerical importance. Order does not matter. Most of the columns were found to fall in this category as follows: "job", "eudcation","contact","month", "day", "marital",and "poutcome". The Pandas getdummies function was used to creates dummy variables was used to treat them. A dummy variable is a numerical variable that encodes categorical information, having two possible values: 0 or 1. 
Those encoded features were added to the existing dataset using the panda function contact as shown  on Figure :

</br>
<p align="center">
<img src="images/Figure17_Nominal.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

Binary data is also nominal data, meaning they represent qualitatively different values that cannot be compared numerically.There were three independent variables considered as binary: 'default' 'housing', ;'loan' all of them with 'yes' and 'no'.

</br>
<p align="center">
<img src="images/Figure17_binary.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

<h3>Ordinal Features</h3>
None of the independent variables were considered to be treated as a ordinal feature, not even poutcome, since there were a bunch of 'unknown' and 'other' items listed, beside 'failure' and 'success'.

</br>
</br>

Since, most of the columns have values between 0 or 1, it was decided to scale the columns: "balance" as follow:

<p align="center">
<img src="images/Figure17_divided.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

<h3>Splitting the variables</h3>
Splitting the dependent variable from the independent variables and assigning them to y and X respectively was done as follows:

</br>
<p align="center">
<img src="images/Figure17_splitting1.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

The independent variables dataset is comprised by 77 columns and 6316 rows. Figure 33 shows the histogram for the columns comprising X dataset. Please keep in mind that the intention is not being able to see the label, just the bars, etc in the histogram, because there are too many histogram.

</br>
<p align="center">
<img src="images/Figure17_histo.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>

<h3>Cross-Validation Approach used</h3>
Although, the dependent variable is imbalanced, the HoldOut Cross-validation was used. In this technique, the whole dataset is randomly partitioned into a training set and validation set using the train_test_split function. The stratify parameter was used  to preserve  the dataset proportions for better prediction and reproduceability of results as follows:

</br>
</br>
<p align="center">
<img src="images/Figure17_splitting2.jpeg" width="1000px">
<h4 align="center"> Figure 14</h4>
</p>


<h2>Modelling</h2>
Although, working with imbalance data is always a challenge for any particular Machine Learning Model, four models were considered for the analysis: KNN, Logistic Regression, Support Machine Vector, and Decision Tree. The metric used to estimate the optimum parameters for each model was 'roc_auc', since it works quite well for imbalance data. The statistical results of the analysis are shown below:

<h4>KNeighborsClassifier</h4>
The supervised learning algorithmK-nearest neighbors (KNN) was used for classification in this analysis.The pipeline model is shown on Figure. 
                  
</br>
<p align="center">
<img src="images/Figure17_knn_1.jpeg" width="400px">
<h4 align="center"> Figure 36</h4>
</p>

The GridSearchCV function was used to optimized several hyper-parameters tested (see Figure). The optimum values for those, and the metrics results are shown on Figure 43. The differences between the validation test and the predicted by the model are shown as a histogram plot (Figure 44). As done in the previous model, the K-fold cross-validation technique was also used to estimate metrics (see Figure 45). The regression coefficients of the 10 features selected are shown on Table 4.

</br>
<p align="center">
<img src="images/Figure17_knn_2.jpeg" width="800px">
<h4 align="center"> Figure 36</h4>
</p>

</br>
<p align="center">
<img src="images/Figure17_knn_metric.jpeg" width="400px">
<h4 align="center"> Figure 36</h4>
</p>




<h2>Evaluation</h2>
As it can be observed,  the model with better metrics is Logistic Regression, although, it consumed more elapsed time for fitting than the rest of the models. However, the reason for that is that the option probability=True was used in this model, in order to be able to make it worked to generate a later its precision- recall curve. This type of curve works much better for moderate to large imbalanced data than the ROC-curve. This curve  indicates that the best model is the Decision Tree model (green line), which consumed less elapse time, and its metrics are not that far from the SVC. As a result, it was thought that the Decision Tree model was the winner for classifying this dataset.

