
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


np.random.seed(42)
n_samples = 1000

data = {
    "Age": np.random.randint(18, 70, n_samples),
    "Annual_Income": np.random.randint(20000, 150000, n_samples),
    "Num_Bank_Accounts": np.random.randint(1, 10, n_samples),
    "Num_Credit_Card": np.random.randint(1, 6, n_samples),
    "Interest_Rate": np.random.randint(0, 20, n_samples),
    "Num_of_Loan": np.random.randint(0, 5, n_samples),
    "Delay_from_due_date": np.random.randint(0, 30, n_samples),
    "Outstanding_Debt": np.round(np.random.uniform(0, 10000, n_samples), 2),
    "Credit_Utilization_Ratio": np.round(np.random.uniform(0.1, 0.9, n_samples), 2),
    "Credit_History_Age": np.random.randint(1, 30, n_samples),
    "Payment_of_Min_Amount": np.random.choice(["Yes", "No"], n_samples),
    "Credit_Score": np.random.choice(["Poor", "Standard", "Good"], n_samples, p=[0.3, 0.4, 0.3])
}

df = pd.DataFrame(data)

plt.style.use('seaborn-darkgrid')
fig, axes = plt.subplots(2, 2, figsize=(14, 10))


sns.countplot(data=df, x="Credit_Score", ax=axes[0, 0])
axes[0, 0].set_title("Distribution of Credit Score")


sns.histplot(df["Annual_Income"], kde=True, ax=axes[0, 1], bins=30)
axes[0, 1].set_title("Annual Income Distribution")

sns.boxplot(data=df, x="Credit_Score", y="Num_Credit_Card", ax=axes[1, 0])
axes[1, 0].set_title("Credit Score vs Number of Credit Cards")

sns.violinplot(data=df, x="Credit_Score", y="Credit_Utilization_Ratio", ax=axes[1, 1])
axes[1, 1].set_title("Credit Score vs Utilization Ratio")

plt.tight_layout()
plt.show()
