# Gene-of-interest-recommendation-system-and-logistic-prediction-model-for-colorectal-carcinoma

**RESEARCH PROBLEM:**
The pressing concern addressed in this study lies within the realm of colorectal cancer, a formidable global health challenge. Despite being the third most common cancer worldwide, colorectal cancer continues to claim the lives of countless individuals. A significant proportion of cases remain undetected until advanced stages, severely limiting treatment options. Consequently, there exists an urgent need to identify specific gene markers associated with colon cancer. Early detection and targeted therapeutic interventions hold the key to mitigating fatalities and improving patient outcomes. With the rise of Precision medicine tailoring therapies specific to the patients has proved to be effective in managing and curing the condition. In this study, we are trying to create an algorithm to calculate the top genes of interest so that therapy can be specifically targeted for each patient.<br>


# Methods used in this project:

Using information obtained from the TCGA-COAD project, consisting of RNA-seq gene expression data from 481 primary tumor samples and 41 normal samples. Transcriptome profiling of normal and tumor samples in TCGA-COAD was acquired using the TCGAbiolinks R package. Samples with missing metadata were excluded, and the DESeq2 R package was employed for performing differential gene expression analysis to identify highly differential genes for further investigation.
The dataset is divided into training and testing sets using an 80:20 ratio. The system calculates and recommends the top N genes of interest to improve cancer detection precision and facilitate more focused therapeutic interventions. The RS algorithm evaluates gene precision and coverage to assess the effectiveness of gene recommendations, while the logistic regression model for diagnosis shows potential for progress in the early detection and treatment of colorectal cancer.

**Gene interest calculation:**
The gene expression data is log-transformed, and the top 1000 genes are selected and stored ina matrix form (dual mode matrix). A single gene network is constructed by cross-multiplication of the gene expression matrix with itself. A similarity matrix is constructed and used to generate the gene of interest by matrix multiplication of the similarity matrix with the gene expression matrix. The gene of interest is then sorted to get the gene ranking.<br>
<img width="476" alt="Screenshot 2024-03-26 at 5 05 08 PM" src="https://github.com/Anube9/Gene-of-interest-recommendation-system-and-logistic-prediction-model-for-colorectal-carcinoma/assets/112353734/3d64c66d-2a55-4c22-b0b1-98db93520a93"><br>

**Logistic Regression Model:**
A logistic regression model has been employed from scratch to predict the patient diagnosis from the gene expression data and covariates like age, stage of tumor and sex. Data preprocessing was performed to convert the categorical variables like stage of tumor, sex, and diagnosis into numerical indices.<br>
Model<br>
<img width="642" alt="Screenshot 2024-03-26 at 5 07 21 PM" src="https://github.com/Anube9/Gene-of-interest-recommendation-system-and-logistic-prediction-model-for-colorectal-carcinoma/assets/112353734/c1a886cc-aa94-42ac-bd6b-d79f8f8b9d51"><br>
The Python sklearn package was utilized to split the data into training and test sets, with 80% allocated to the training data and 20% to the test data. Initially, a random weight vector was generated using the np.random function, and this vector was employed to make the initial predictions prior to optimization.<br>

The data was linearly fitted by multiplying the weight vector with the x data and then transformed using the sigmoid activation function. Predictions were made based on whether the transformed data exceeded a threshold of 0.5 or not.<br>

The weight vector was optimized to minimize the loss of predictions, utilizing a regularization rate of 0.0001 and learning rate of 0.01 over 100 epochs of iterations. Subsequently, data predictions were conducted again to evaluate how the optimization affected the accuracy of predictions.<br>

# RESULTS

**Recommendation system:** The gene single network creation resulted in a gene * gene matrix. This matrix is converted into similarity with diagonals as 1 and the higher the score more similar the genes are. Gene of interest matrix is a gene * sample matrix which has the values of each gene for the sample based on their similarity. These are then ranked to get the top genes.<br>

**Logistic regression:**  The model created with sample weights that are generated at random showed that the matrix is not predicting the class 0 with all class 0 misclassified as class 1. To correct this optimization with 0.0001 regularization and 0.01 learning rate method showed that the model was able to predict all the data with 100% accuracy.


# Conclusion: 
The integration of RS and logistic regression presents a promising avenue for advancing precision medicine in colorectal cancer. By combining personalized gene recommendations with accurate prediction models, this study lays the groundwork for tailored therapeutic strategies. The ability to compute top genes of interest ensures a targeted approach to cancer treatment, a crucial step in managing and potentially curing colorectal cancer.<br>
Moving forward, the study's findings offer insights into the potential clinical applications of RS and logistic regression in the realm of cancer research. The success in optimizing the logistic regression model signifies a robust framework for enhancing diagnostic accuracy. These methodologies, when applied synergistically, contribute to a more effective and personalized approach to colorectal cancer management, holding implications for broader applications in precision medicine.<br>


