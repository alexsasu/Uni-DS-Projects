# Uni-DS-Projects

"Dry Beans Multiclass Classification" was a group project made during the Big Data course taken in the 1st year of the Artificial Intelligence master program at the Faculty of Mathematics and Computer Science, University of Bucharest.

## Dry Beans Multiclass Classification

The project consisted of choosing a tabular dataset of over 1 MB in size, with at least 10 columns of features, and then applying at least three **dimensionality reduction** techniques on said dataset and feeding the reduced data to multiple machine learning models.

Our project made use of a scientific dataset that we found online, containing details about 13.611 samples from 7 types of dry beans, and 16 features (the dataset can be found [here](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset)).

<details>
<summary><b>Exploratory data analysis</b>:</summary>

![class_distribution](https://github.com/user-attachments/assets/7cebc841-7650-4da0-b25c-e45eaa9ede70)  
We observed that our dataset is imbalanced. In order to address this, we used <b>balanced weights</b> with some of our models, and we kept track of the <b>f1-score</b>.

![pca_dataset_visualization_initial](https://github.com/user-attachments/assets/62758e61-ed32-412f-a223-a7625b84098d)  
We observed that most of the bean types had similar features, with the exception of Bombay beans, which were considerably different. Due to this, and also due to the Bombay population having by far the least amount of samples, we omitted Bombay beans from the process of <b>outliers removal</b> through the <b>z-score</b>.

<img src="https://github.com/user-attachments/assets/eb0adecb-3b23-45f0-9e17-bca492baf379" width="766" height="645">  

From the above correlation matrix, we observed that the dimension features of the beans were in a strong direct relationship with other dimension features, and in a strong inverse relationship with shape features. This opened possibilities for removing multiple features that were similar to others, which we did, in an automatic fashion, through our dimensionality reduction algorithms.
</details>

Before using the dimensionality reduction techniques on our data, we first preprocessed it in the following ways:
- we first standardized it (through a **standard scaler**, in order to obtain mean 0 and variance 1 for the dimensionality reduction methods)
- and then we **removed outliers** (through the **z-score** method, by eliminating data points that were at least 3 standard deviations away from the mean)

<details>
<summary>Afterwards, we applied two <b>feature extraction</b> methods on our processed data, and one <b>feature selection</b> method, namely <b>Principal Component Analysis (PCA)</b>, <b>Linear Discriminant Analysis (LDA)</b>, and <b>Lasso variable selection property (LVS)</b>:</summary>
<br>

<b>PCA:</b>  
<img src="https://github.com/user-attachments/assets/2a5f470d-5005-44cc-9dc6-7febf3538ebc" width="518" height="352">  
We wanted to retain the minimum number of principal components that <b>explained at least 95% of the variance</b> in the data, so, from the above graph, we retained only 5 of all 16 principal components.

<br>

<b>LDA:</b>  
<img src="https://github.com/user-attachments/assets/9e953c0a-22ab-4d16-9cdf-ebbb87e72d07" width="518" height="352">  
Again, we wanted to retain the minimum number of LDA components that <b>explained at least 95% of the variance</b> in the data, so, from the above graph, we retained only 4 of all 6 LDA components.

<br>

<b>LVS:</b>  
<img src="https://github.com/user-attachments/assets/65f075ba-1770-447d-805e-022892a8dccd" width="520" height="413">  
For the method involving the Lasso variable selection property, we observed from the above graph that the range of values of 10^-1.5 - 10^1 holds the optimal value for the regularization factor. Afterwards, we arrived at a satisfactory regularization factor of 0.188 through a <b>Grid Search</b> approach monitoring the macro f1-score and through the selection of the regularization factor of the model that achieved a macro f1-score of over 0.933 (we chose this value by deeming it was satisfactory enough for a model), while selecting the least amount of features. Thus, the regularization factor of 0.188 brought the selection of just 8 features out of all 16.
</details>

<details>
<summary>And then, we fed the reduced data, as well as the data without any dimensionality reduction methods applied, to the following machine learning models trained from zero through a <b>Grid Search</b> approach: <b>Logistic Regression</b>, <b>KNN</b>, <b>Random Forest</b>, <b>SVM</b>, <b>Naive Bayes</b>; and obtained the following results:</summary>

![image](https://github.com/user-attachments/assets/fa0bc8d7-0f98-4746-ac49-e88d4e740881)

Training time for each approach, in seconds:
![image](https://github.com/user-attachments/assets/78144432-3863-4a3d-a5ae-cec2c7206e42)

As can be seen from the above two tables, the dimensionality reduction methods we applied were a success, as the models retained their performance, while training time was considerably lowered.
</details>

> Note: for further details about the project solution, please consult [this path](https://github.com/alexsasu/Uni-DS-Projects/tree/main/Dry%20Beans%20Multiclass%20Classification/Documentation) inside the repository

### Contributors:
- Alexandru-Cristian Sasu (https://github.com/alexsasu)
- Dragos-Gabriel Grigore (https://github.com/Dragos-Grigore)
- Georgiana Plaian
- Sabin Zibileanu
- Sebastian-Marian Barbu
