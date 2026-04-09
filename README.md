Credit Card Customer Segmentation
📌 Project Overview
This project aims to perform customer segmentation for a credit card dataset. By analyzing various credit card usage behaviors, customers are grouped into distinct segments using clustering techniques. This can help financial institutions understand their customer base better, tailor marketing strategies, and develop personalized services.

📊 Dataset
The dataset used is CC GENERAL.csv, which contains detailed credit card usage information for 8950 customers. Each row represents a customer, and columns include various attributes such as:

CUST_ID: Customer ID
BALANCE: Balance amount left in their account to make purchases
BALANCE_FREQUENCY: How frequently the balance is updated
PURCHASES: Amount of purchases made from the account
ONEOFF_PURCHASES: Maximum purchase amount done in one-go
INSTALLMENTS_PURCHASES: Amount of purchase done in installment
CASH_ADVANCE: Cash in advance given by the user
PURCHASES_FREQUENCY: How frequently the purchases are being made
ONEOFF_PURCHASES_FREQUENCY: How frequently one-off purchases are made
PURCHASES_INSTALLMENTS_FREQUENCY: How frequently purchases in installments are made
CASH_ADVANCE_FREQUENCY: How frequently cash in advance is being paid
CASH_ADVANCE_TRX: Number of transactions made with cash in advance
PURCHASES_TRX: Number of purchase transactions made
CREDIT_LIMIT: Credit limit of the customer
PAYMENTS: Amount of payments made by the customer
MINIMUM_PAYMENTS: Minimum amount of payments made by the customer
PRC_FULL_PAYMENT: Percentage of full payment paid by the customer
TENURE: Tenure of credit card service for the customer
⚙️ Methodology
The project follows a standard machine learning pipeline:

Data Loading and Initial Inspection: The CC GENERAL.csv dataset is loaded into a Pandas DataFrame. Initial inspection involves viewing the first few rows (df.head()) and checking for missing values (df.isnull().sum()).

Exploratory Data Analysis (EDA): Histograms and box plots are generated for all numerical features to understand their distributions and identify the presence of outliers.

Data Preprocessing:

Missing values in CREDIT_LIMIT and MINIMUM_PAYMENTS are imputed with their respective medians.
The CUST_ID column is dropped as it's not relevant for clustering.
Outlier Treatment: Outliers in all numerical features are capped using the Interquartile Range (IQR) method (values below Q1 - 1.5*IQR are set to Q1 - 1.5*IQR, and values above Q3 + 1.5*IQR are set to Q3 + 1.5*IQR).
Feature Scaling: All features are scaled using StandardScaler to ensure that no single feature dominates the clustering process.
Dimensionality Reduction (PCA): Principal Component Analysis (PCA) is applied to reduce the dimensionality of the data to 2 components for visualization purposes. This helps in plotting the clusters in a 2D space.

Clustering (K-Means):

The K-Means algorithm is used for customer segmentation.
Optimal K Determination: The Elbow Method (plotting inertia vs. number of clusters) and Silhouette Score (plotting silhouette score vs. number of clusters) are employed to determine the optimal number of clusters.
After outlier treatment, both methods suggest an optimal number of clusters, with the silhouette score peaking around k=3.
K-Means is then run with n_clusters=3.
Cluster Analysis and Visualization:

Customer segments are assigned to the original DataFrame.
Cluster Profiling: The mean of each feature for each cluster is calculated to understand the characteristics and behaviors of each segment.
Heatmap: A heatmap visualizes the cluster profiles, making it easy to compare the features across different clusters.
PCA Scatter Plot: The clusters are visualized in a 2D scatter plot using the first two principal components, with cluster centroids marked to show their positions.
📈 Results
The K-Means clustering identified 3 distinct customer segments:

Cluster 0 (High Spenders/Frequent Users):

High average BALANCE.
Very high PURCHASES, ONEOFF_PURCHASES, and INSTALLMENTS_PURCHASES.
High PURCHASES_FREQUENCY and PURCHASES_TRX.
Relatively high CREDIT_LIMIT and PAYMENTS.
Lower CASH_ADVANCE compared to Cluster 2.
Likely affluent customers who use their credit card extensively for various types of purchases.
Cluster 1 (Low Spenders/Infrequent Users):

Low average BALANCE.
Lowest PURCHASES (one-off and installments).
Lowest PURCHASES_FREQUENCY and PURCHASES_TRX.
Lower CREDIT_LIMIT, PAYMENTS, and MINIMUM_PAYMENTS.
These customers have minimal credit card activity and likely use their cards infrequently for small transactions.
Cluster 2 (Cash Advance Users):

High average BALANCE.
Significantly high CASH_ADVANCE, CASH_ADVANCE_FREQUENCY, and CASH_ADVANCE_TRX.
Very low PURCHASES, PURCHASES_FREQUENCY, and PURCHASES_TRX.
Relatively high CREDIT_LIMIT and PAYMENTS, but very low PRC_FULL_PAYMENT.
These customers primarily use their credit cards for cash advances rather than purchases, often carrying higher balances and making minimal full payments.
🛠️ Technologies Used
Python 3.x
numpy (for numerical operations)
pandas (for data manipulation and analysis)
scikit-learn (for preprocessing, PCA, and clustering)
matplotlib (for plotting and visualization)
seaborn (for enhanced statistical data visualization)
▶️ How to Run the Notebook
Clone the repository:
git clone <repository-link>
cd <repository-name>
Install dependencies: It is recommended to use a virtual environment.
pip install -r requirements.txt
(Create a requirements.txt file containing the listed Technologies Used).
Download the dataset: Place the CC GENERAL.csv file in the same directory as the notebook, or update the path in the code.
Open and run the notebook: You can open the .ipynb file in Google Colab, Jupyter Notebook, or JupyterLab and run all cells sequentially.
📂 Project Structure
.  
├── CC GENERAL.csv               # The raw dataset
├── credit_card_segmentation.ipynb  # The Jupyter Notebook containing the analysis
└── README.md                    # This file
🤝 Contributing
Contributions are welcome! If you have suggestions for improvements, please feel free to open an issue or submit a pull request.

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
