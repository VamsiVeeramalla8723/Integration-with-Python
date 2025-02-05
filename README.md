**Company**: CodTech IT Solutions

**Name**: Vamsi Anudeep Veeramalla

**Intern ID**: CT6WDIA

**Domain**: Power BI

**Duration**: 6 Weeks

**Mentor**: Neela Santosh Kumar

# Integration with Python Or R

## 📌 Project Overview
This project demonstrates how to integrate Python within Power BI to perform advanced data analysis and visualization. The dataset used contains sales data, and the script analyzes monthly sales trends using **Pandas, Matplotlib, and Seaborn**.

## 📂 Dataset
- **Filename**: `sales_data.csv`
- **Columns**:
  - `Date`: Sales transaction date
  - `Product`: Product name
  - `Region`: Sales region
  - `Sales`: Sales revenue for the respective date

## 🛠️ Prerequisites
Before running the script in Power BI, ensure you have the following installed:
- **Power BI Desktop**
- **Python (Version 3.x recommended)**
- Python libraries:
  ```bash
  pip install pandas matplotlib seaborn
  ```

## 📌 Steps to Integrate Python in Power BI
1. **Load the dataset** into Power BI.
2. **Enable Python scripting**:
   - Go to **File > Options and Settings > Options**
   - Navigate to **Python scripting** and set the Python directory.
3. **Open Power Query Editor**:
   - Click on **Transform Data**.
   - Select **Run Python Script** and insert the provided script.
4. **Apply transformations** and visualize the results in Power BI.

## 📝 Python Script Used
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Ensure dataset is loaded correctly
df = dataset.copy()

# Convert Date column to string first (fixes Power BI format issues)
df['Date'] = df['Date'].astype(str)

# Try converting to datetime with error handling
try:
    df['Date'] = pd.to_datetime(df['Date'], errors='coerce', format='%Y-%m-%d')
except Exception as e:
    print(f"Date conversion error: {e}")

# Drop rows where Date conversion failed
df = df.dropna(subset=['Date'])

# Aggregate sales by month
df['Month'] = df['Date'].dt.to_period('M')
monthly_sales = df.groupby('Month')['Sales'].sum().reset_index()

# Plot sales trend
plt.figure(figsize=(10, 5))
sns.lineplot(x=monthly_sales['Month'].astype(str), y=monthly_sales['Sales'], marker='o')
plt.xticks(rotation=45)
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Total Sales")
plt.grid()

# Show plot
plt.show()
```

## 📊 Expected Output
- **Sales Trend Chart**: A line chart visualizing monthly sales trends.
- **Sales by Region**: A bar chart showing sales distribution across different regions.
- **Data Table**: A table displaying raw sales data.

![Integration with Python](https://github.com/user-attachments/assets/faaa9240-6c7d-47ba-828c-d7fc45723109)




