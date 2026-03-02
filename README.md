# **Pharma Sales EDA Assignment: Step-by-Step Implementation Guide**

This guide provides a structured plan for your **ZG536: Foundations of Data Science** assignment. It follows the exact 9-step roadmap required by the professor, utilizing the `salesdaily.csv` dataset.

---

### **Assignment Metadata**

* **File Name:** `ZG536_FDS_Assignment1_<Your_ID>.ipynb`
* **Primary Dataset:** `salesdaily.csv` (Daily Pharma Sales)
* **Domain:** Pharmaceutical Retail / Business Analytics

---

### **Step 1: Data Loading**

**Objective:** Establish the environment and load the dataset.

* **Actions:**
* Import `pandas`, `numpy`, `matplotlib.pyplot`, and `seaborn`.
* Load the CSV file using `pd.read_csv()`.


* **Note:** Use a Markdown cell to introduce the dataset and mention why the **Daily** version was chosen for its granularity.

### **Step 2: Basic Data Exploration**

**Objective:** Understand the "anatomy" of the data.

* **Actions:**
* Use `df.head()` to see the ATC classification columns.
* Use `df.info()` to identify data types (check if 'datum' is an object or datetime).
* Use `df.describe()` to get the mean, min, and max sales for each drug category.



### **Step 3: Data Cleaning**

**Objective:** Ensure data quality (GIGO principle).

* **Actions:**
* **Date Conversion:** Convert `datum` to a proper datetime object using `pd.to_datetime()`.
* **Handling Non-numeric Markers:** Use `pd.to_numeric(series, errors='coerce')` to handle any "ghost" markers like `?` or blanks.
* **Null Values:** Check for missing data with `df.isnull().sum()`.
* **Redundancy:** Drop index columns or irrelevant metadata using `df.drop(axis=1, inplace=True)`.



### **Step 4: Univariate Analysis**

**Objective:** Look at the distribution of individual drug categories.

* **Actions:**
* Select a high-volume category (e.g., **N02BA** - Salicylates).
* **Visualization:** Plot a **Histogram** to see sales frequency and a **Boxplot** to identify outliers (days with extreme sales spikes).



### **Step 5: Bivariate Analysis**

**Objective:** Identify relationships between two variables (e.g., Sales vs. Time).

* **Actions:**
* Analyze how sales of a specific drug category change based on the **Day of the Week**.
* **Visualization:** A **Bar Plot** showing "Average Sales" on the Y-axis and "Weekday" on the X-axis. This highlights business patterns like "Monday Rushes."



### **Step 6: Multivariate Analysis**

**Objective:** Discover how different drug categories correlate with each other.

* **Actions:**
* Calculate the correlation matrix using `df.corr()`.
* **Visualization:** Create a **Heatmap** (`sns.heatmap`).


* **Business Goal:** Look for high positive correlations (e.g., do Anti-inflammatories and Analgesics always sell together?).

### **Step 7: Feature Engineering**

**Objective:** Derive new attributes to improve analysis.

* **Actions:**
* **Time Features:** Extract `Month`, `Weekday_Name`, and `Year` from the `datum` column.
* **Binary Flags:** Create an `is_weekend` column (1 for Sat/Sun, 0 for others).
* **Aggregated Totals:** Create a `Total_Sales` column that sums all ATC categories for each row.



### **Step 8: Insights and Hypothesis Generation**

**Objective:** Translate data into business intelligence (Markdown cells).

* **Sample Insight #1:** "M01AB (Anti-inflammatory) sales show a statistically significant increase of 12% during winter months (Dec-Jan)."
* **Sample Insight #2:** "There is a 0.82 correlation between N02BA and N02BE, suggesting these pain-relief categories are complementary products."
* **Sample Hypothesis:** "The spike in sales on Mondays is likely due to chronic patients refilling prescriptions at the start of the work week."

### **Step 9: Visualization**

**Objective:** Final "Storytelling" through clean charts.

* **Actions:**
* Create a **Line Plot** showing the total 6-year sales trend.
* Ensure all charts have `plt.title()`, `plt.xlabel()`, and `plt.ylabel()`.
* Use a **Pair Plot** (`sns.pairplot`) for a subset of the most popular drug categories to visualize multiple relationships at once.



---

### **Final Submission Checklist**

1. **Code Comments:** Every code block should have a comment explaining the logic.
2. **Markdown Explanations:** Use Markdown to explain the *findings* of every plot.
3. **Clean Output:** Clear all cell outputs and "Run All" before saving to ensure no errors.
4. **Specialization Context:** Briefly mention in the introduction that this analysis helps in **Inventory Optimization** (MBA context) and **Therapeutic Tracking** (Bio IT context).