
### Fraud Detection Analysis

**Objective:**  
To identify fraudulent transactions in a financial dataset using outlier detection methods.

**Dataset Overview:**  
- **Source:** [Fraud.csv]
- **Size:** 6,362,620 entries
- **Features:** `step`, `type`, `amount`, `nameOrig`, `oldBalanceOrig`, `newBalanceOrig`, `nameDest`, `oldBalanceDest`, `newBalanceDest`, `isFraud`, `isFlaggedFraud`
- **Target Variable:** `isFraud`

**Data Exploration:**
- **Missing Values:** No missing values present.
- **Transaction Distribution:** Imbalanced with only 0.13% of transactions labeled as fraudulent.
- **Transaction Amounts:** Fraudulent transactions have higher average amounts compared to non-fraudulent ones.
- **Transaction Types:** Major types include `CASH_OUT`, `PAYMENT`, `CASH_IN`, `TRANSFER`, and `DEBIT`.

**Correlation Analysis:**
- Low correlation between `isFraud` and other features, indicating that fraud detection may require advanced techniques beyond simple correlation.

**Sampling:**
- A 10% sample of the data was used to facilitate quicker model training and evaluation.

**Outlier Detection Methods Implemented:**
1. **Isolation Forest:**
   - **Accuracy Score:** 99.77%
   - **Classification Report:** 
     - Precision (Fraud): 0.09
     - Recall (Fraud): 0.09
     - F1-Score (Fraud): 0.09

2. **Local Outlier Factor:**
   - **Accuracy Score:** 99.75%
   - **Classification Report:**
     - Precision (Fraud): 0.01
     - Recall (Fraud): 0.01
     - F1-Score (Fraud): 0.01

3. **Support Vector Machine (One-Class SVM):**
   - **Accuracy Score:** 99.76%
   - **Classification Report:** 
     - Precision (Fraud): 0.09
     - Recall (Fraud): 0.09
     - F1-Score (Fraud): 0.09

**Conclusion:**
- All methods achieved high accuracy, but the low recall and precision for fraud detection indicate that the models struggle with the imbalanced nature of the dataset. Further tuning and potential use of additional features or methods may be necessary to improve detection of fraudulent transactions.

**Visualizations:**
- **Transaction Class Distribution:** Bar plot showing the imbalance between fraudulent and non-fraudulent transactions.
- **Transaction Amounts by Class:** Histograms illustrating the difference in transaction amounts between fraud and non-fraud.
- **Time vs Amount by Class:** Scatter plots depicting the relationship between time and amount for fraudulent and non-fraudulent transactions.
- **Transaction Types:** Bar plots showing the distribution of transaction types and their association with fraud.



# Fraud-Detection on Financial Data
This is a sample of 1 row with headers explanation:

1,PAYMENT,1060.31,C429214117,1089.0,28.69,M1591654462,0.0,0.0,0,0

step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).

type - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.

amount -
amount of the transaction in local currency.

nameOrig - customer who started the transaction

oldbalanceOrg - initial balance before the transaction

newbalanceOrig - new balance after the transaction

nameDest - customer who is the recipient of the transaction

oldbalanceDest - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).

newbalanceDest - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).

isFraud - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.

isFlaggedFraud - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.
