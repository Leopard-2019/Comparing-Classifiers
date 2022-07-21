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
The original dataset (bank-full.csv) given is in .csv format.It consists of 17 columns and 6316 rows as shown below. The target/independent columns is "y" which is categorical (nominal feature), and it stands for: has the client subscribed a term deposit?. This variable is imbalance as will be later be seen. There are only two numerical columns: "age" and "balance", since the column: "duration" is only for benchmark purposes and is discarded for realistic predictive modelling.The rest of the columns are categorical (nominal). Most of the dataset provided is imbalanced before entering the modeling phase. None of the columns contain "NaN" values. Duplicates were not observed. It is thought that in order to provide more insight into the aforementioned dataset, a data preparation,i.e, data cleaning process needs to be done first.

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
</br>
<p align="center">
<img src="images/Figure17_4.jpeg" width="800px">
<h4 align="center"> Figure 4</h4>
</p>

