💳 Credit Card Customer Segmentation
📌 Project Overview

This project performs customer segmentation on a credit card dataset using machine learning clustering techniques. By analyzing different credit card usage behaviors, customers are grouped into meaningful segments.

These segments help financial institutions:

Understand customer spending behavior
Design targeted marketing campaigns
Improve personalized financial services
Identify high-value customers

The project applies data preprocessing, PCA (Principal Component Analysis), and K-Means clustering to discover patterns in customer credit card usage.

📊 Dataset

The dataset used is CC GENERAL.csv, which contains detailed credit card usage data for 8,950 customers.

Each row represents a customer, and the dataset includes various attributes describing their credit card activity.

Key Features
Feature	Description
CUST_ID	Unique customer ID
BALANCE	Remaining balance in the account
BALANCE_FREQUENCY	Frequency of balance updates
PURCHASES	Total purchase amount
ONEOFF_PURCHASES	Maximum one-time purchase
INSTALLMENTS_PURCHASES	Purchases made in installments
CASH_ADVANCE	Cash withdrawn in advance
PURCHASES_FREQUENCY	Frequency of purchases
ONEOFF_PURCHASES_FREQUENCY	Frequency of one-time purchases
PURCHASES_INSTALLMENTS_FREQUENCY	Installment purchase frequency
CASH_ADVANCE_FREQUENCY	Cash advance usage frequency
CASH_ADVANCE_TRX	Number of cash advance transactions
PURCHASES_TRX	Number of purchase transactions
CREDIT_LIMIT	Credit card limit
PAYMENTS	Amount paid by the customer
MINIMUM_PAYMENTS	Minimum payments made
PRC_FULL_PAYMENT	Percentage of full payments
TENURE	Duration of credit card usage
⚙️ Methodology

The project follows a complete machine learning workflow:

1️⃣ Data Loading
Dataset is loaded using Pandas
Initial inspection performed using:
df.head()
df.info()
df.isnull().sum()
2️⃣ Exploratory Data Analysis (EDA)

EDA is performed to understand the dataset and identify patterns.

Visualizations used:

Histograms
Box plots
Distribution analysis

These help detect:

Outliers
Skewed distributions
Data anomalies
3️⃣ Data Preprocessing
Handling Missing Values

Missing values in the following columns are replaced using median values:

CREDIT_LIMIT
MINIMUM_PAYMENTS
Removing Irrelevant Columns

The column CUST_ID is removed because it does not contribute to clustering.

4️⃣ Outlier Treatment

Outliers are capped using the Interquartile Range (IQR) method.

Formula used:

Lower Bound

Q1 − 1.5 × IQR

Upper Bound

Q3 + 1.5 × IQR

Values outside this range are capped to the nearest boundary.

5️⃣ Feature Scaling

All features are standardized using:

StandardScaler

This ensures that no feature dominates the clustering algorithm due to scale differences.

6️⃣ Dimensionality Reduction (PCA)

Principal Component Analysis (PCA) is applied to reduce dimensionality.

The data is reduced to 2 principal components, allowing clusters to be visualized in a 2D space.

Benefits:

Reduces feature complexity
Improves visualization
Removes correlated information
7️⃣ Clustering (K-Means)

Customer segmentation is performed using the K-Means clustering algorithm.

Finding Optimal Number of Clusters

Two methods are used:

Elbow Method

Plots inertia vs number of clusters.

Silhouette Score

Measures clustering quality.

Both methods suggest an optimal value around:

K = 3
📈 Results

The model identifies 3 distinct customer segments.

🟢 Cluster 0 — High Spenders / Frequent Users

Characteristics:

High BALANCE
Very high PURCHASES
High INSTALLMENTS_PURCHASES
High PURCHASES_FREQUENCY
High CREDIT_LIMIT
Large PAYMENTS

These customers are premium credit card users who actively use their cards for purchases.

🔵 Cluster 1 — Low Spenders / Infrequent Users

Characteristics:

Low BALANCE
Lowest PURCHASES
Very low PURCHASES_FREQUENCY
Low CREDIT_LIMIT
Low PAYMENTS

These customers use their credit cards rarely and for small transactions.

🔴 Cluster 2 — Cash Advance Users

Characteristics:

High CASH_ADVANCE
High CASH_ADVANCE_FREQUENCY
High CASH_ADVANCE_TRX
Very low PURCHASES
Low PRC_FULL_PAYMENT

These customers mainly use their cards for cash withdrawals instead of purchases.

🛠️ Technologies Used
Python 3
NumPy – Numerical computations
Pandas – Data manipulation
Scikit-learn – Machine learning algorithms
Matplotlib – Data visualization
Seaborn – Statistical visualization
▶️ How to Run the Project
1️⃣ Clone the Repository
git clone https://github.com/yourusername/credit-card-customer-segmentation.git
cd credit-card-customer-segmentation
2️⃣ Install Dependencies

It is recommended to use a virtual environment.

pip install -r requirements.txt
3️⃣ Download Dataset

Place the dataset file:

CC GENERAL.csv

inside the project directory.

4️⃣ Run the Notebook

Open the notebook using:

Google Colab
Jupyter Notebook
JupyterLab

Then run all cells sequentially.

📂 Project Structure
Credit-Card-Customer-Segmentation
│
├── CC GENERAL.csv
├── credit_card_segmentation.ipynb
└── README.md
🤝 Contributing

Contributions are welcome!

If you'd like to improve the project:

Fork the repository
Create a new branch
Make your changes
Submit a Pull Request
📄 License

This project is licensed under the MIT License.

See the LICENSE file for more details.
