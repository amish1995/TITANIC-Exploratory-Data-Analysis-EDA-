#  Titanic Dataset – Exploratory Data Analysis (EDA)

This project focuses on performing Exploratory Data Analysis (EDA) on the Titanic dataset (`train.csv`) using Python's `pandas`, `matplotlib`, and `seaborn` libraries. The aim is to understand the structure of the data, identify and handle missing values, and uncover patterns related to survival.

---

##  Data Loading and Initial Look

- The dataset was loaded into a pandas DataFrame named `train`.
- `train.head()` gave a preview of the data, showing key features:
  - `PassengerId`, `Survived`, `Pclass`, `Name`, `Sex`, `Age`, `SibSp`, `Parch`, `Ticket`, `Fare`, `Cabin`, `Embarked`.

---

##  Missing Value Analysis

###  Initial Check:
- `train.isnull()` returned a boolean DataFrame highlighting missing values.
- A heatmap (`sns.heatmap(train.isnull(), ...)`) revealed:
  - Significant missingness in `Age` and `Cabin`.
  - A few missing values in `Embarked`.

### 🔧 Handling Missing Data:
- **Age**: Imputed using a custom function based on the average age within each `Pclass`.
- **Cabin**: Dropped due to too many missing values.
- **Embarked**: Filled with the most common value (mode).
- Follow-up heatmaps confirmed successful handling of missing values.

---

## 📊 Summary Statistics (`train.describe()`)

- **Survived**: ~38% survival rate.
- **Pclass**: Mean indicates varied passenger class distribution.
- **Age**: After imputation, statistics included all values. The dataset had a wide age distribution.
- **SibSp / Parch**: Ranged from 0 to 8 (siblings/spouses) and 0 to 6 (parents/children).
- **Fare**: Notable variation, with many low-cost fares and some high-end outliers.

---

## 🧾 DataFrame Overview (`train.info()`)

- 891 entries and 12 columns.
- Showed non-null counts and data types.
- Helped verify that all missing values were addressed before modeling.

---

## 📈 Visualizations and Insights

1. **Survival Count**:
   - `sns.countplot(x='Survived', data=train)`
   - Visualized the number of survivors vs. non-survivors.

2. **Survival by Sex**:
   - `sns.countplot(x='Survived', hue='Sex', data=train)`
   - Showed females had significantly higher survival rates.

3. **Survival by Pclass**:
   - `sns.countplot(x='Survived', hue='Pclass', data=train)`
   - Higher-class passengers had better survival odds.

4. **Age Distribution**:
   - `train['Age'].hist(bins=30)`
   - Displayed the age spread of passengers.

5. **SibSp Distribution**:
   - `sns.countplot(x='SibSp', data=train)`
   - Indicated most passengers traveled with 0–1 siblings/spouses.

6. **Fare Distribution**:
   - `train['Fare'].hist(bins=30)`
   - Revealed skewness with many low fares and a few high fares.

7. **Age by Pclass**:
   - `sns.boxplot(x='Pclass', y='Age', data=train)`
   - Suggested higher-class passengers were older on average.

---

##  Data Cleaning Summary

- **Imputed 'Age'**: Based on Pclass-wise average.
- **Dropped 'Cabin'**: Too many missing values to salvage.
- **Handled 'Embarked'**: Filled missing values with the mode.

---

##  Conclusion and Next Steps

We now have:

- A clean dataset with no missing values.
- Initial insights on key variables affecting survival.
- A basic understanding of the relationship between features.

**Next Steps**:
- Convert categorical variables using encoding techniques.
- Engineer new features if needed.
- Begin building and evaluating predictive models.

---

## Libraries Used

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

---

##  File Structure

```plaintext
├── train.csv
├── titanic_eda.ipynb
└── README.md

