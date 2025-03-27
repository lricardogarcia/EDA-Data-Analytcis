# 🏠 Python Project EDA & Data Viz - AirBnB Listing 2024 (New York)  

## 📌 Project Overview  
This project performs **Exploratory Data Analysis (EDA) and Data Visualization** on the 2024 **New York AirBnB Listings dataset**. The goal is to clean, analyze, and extract meaningful insights about **pricing, availability, hosts, and neighborhoods**.  

The dataset includes **20,770 listings** with 22 attributes such as `price`, `room type`, `neighborhood`, `availability`, and **ratings**. The analysis follows a structured **5-step process**:  

1. **Importing Dependencies**  
2. **Loading & Exploring the Dataset**  
3. **Data Cleaning & Preprocessing**  
4. **Exploratory Data Analysis (EDA)**  
5. **Feature Engineering & Insights**  

---

## 📂 Dataset Information  
- 📄 **File:** `new_york_listings_2024.csv`  
- 🔢 **Rows:** 20,770  
- 📊 **Columns:** 22  

### **Columns Description**  
| Column | Description |  
|--------|------------|  
| `id` | Unique listing ID |  
| `name` | Name/Title of the listing |  
| `host_id` | Unique host ID |  
| `host_name` | Name of the host |  
| `neighbourhood_group` | Borough (Manhattan, Brooklyn, etc.) |  
| `neighbourhood` | Specific neighborhood |  
| `latitude` & `longitude` | Location coordinates |  
| `room_type` | Type of listing (Entire home, Private room, etc.) |  
| `price` | Nightly price in USD |  
| `minimum_nights` | Minimum nights required |  
| `number_of_reviews` | Total reviews |  
| `last_review` | Date of the last review |  
| `reviews_per_month` | Average monthly reviews |  
| `calculated_host_listings_count` | Number of listings per host |  
| `availability_365` | Number of available days per year |  
| `license` | Licensing information |  
| `rating` | Listing rating |  
| `bedrooms`, `beds`, `baths` | Number of rooms/beds/baths |  

---

## 📌 Steps of the Analysis  

### 🔹 **1. Importing Dependencies**  
We use the following libraries for data analysis and visualization:  
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline
```

### 🔹 **2. Loading & Exploring the Dataset**  
We load the dataset and perform an initial inspection:  
```python
data = pd.read_csv('new_york_listings_2024.csv', encoding_errors='ignore')
```
- View the first 5 rows: `data.head()`  
- View dataset shape: `data.shape` → **(20770, 22)**  
- Check data types & missing values: `data.info()`  

### 🔹 **3. Data Cleaning & Preprocessing**  
To ensure clean data for analysis, we perform:  
✅ **Handling Missing Values:**  
```python
data.dropna(inplace=True)  # Removing missing values
```
✅ **Removing Duplicates:**  
```python
data.drop_duplicates(inplace=True)
```
✅ **Data Type Conversion:**  
```python
data['id'] = data['id'].astype(object)
data['host_id'] = data['host_id'].astype(object)
```

### 🔹 **4. Exploratory Data Analysis (EDA)**  
#### **📊 Univariate Analysis**
✅ **Outlier Detection in Price**  
```python
sns.boxplot(data=data[data['price'] < 1500], x='price')
plt.show()
```
✅ **Price Distribution**  
```python
plt.figure(figsize=(8, 5))
sns.histplot(data=data, x='price', bins=100)
plt.title('Price Distribution')
plt.ylabel("Frequency")
plt.show()
```
✅ **Availability Distribution**  
```python
sns.histplot(data=data, x='availability_365')
plt.title('Availability Distribution')
plt.ylabel("Frequency")
plt.show()
```

#### **📊 Comparative Analysis**  
✅ **Average Price per Borough**  
```python
data.groupby('neighbourhood_group')['price'].mean()
```
**Results:**  
| Borough | Avg. Price ($) |  
|---------|--------------|  
| Bronx | 107.99 |  
| Brooklyn | 155.13 |  
| Manhattan | 204.14 |  
| Queens | 121.68 |  
| Staten Island | 118.78 |  

### 🔹 **5. Feature Engineering & Insights**  
✅ **Price per Bed Calculation**  
```python
data['price_per_bed'] = data['price'] / data['beds']
```
✅ **Average Price per Bed by Borough**  
```python
data.groupby('neighbourhood_group')['price_per_bed'].mean()
```
**Results:**  
| Borough | Avg. Price per Bed ($) |  
|---------|----------------------|  
| Bronx | 74.71 |  
| Brooklyn | 99.78 |  
| Manhattan | 138.70 |  
| Queens | 76.33 |  
| Staten Island | 67.72 |  

---

## 📊 Key Insights & Findings  
✅ **Manhattan has the highest average price per listing ($204.14), while Bronx has the lowest ($107.99).**  
✅ **The most common room type is ‘Entire home/apt’, making up the majority of listings.**  
✅ **High prices do not always mean high occupancy – availability varies significantly.**  
✅ **Hosts with multiple listings tend to charge higher prices.**  

---

## 🚀 How to Run This Project  
### 🔹 **Requirements**  
- Python 3.x  
- Required Libraries:  
  ```bash
  pip install pandas numpy matplotlib seaborn
  ```
  
### 🔹 **Run the Script**  
To execute the full analysis, run:  
```bash
python airbnb_analysis.py
```

---

## 📈 Future Enhancements  
🚀 **Advanced Machine Learning:** Predict pricing trends.  
📍 **Geospatial Analysis:** Visualize property locations using **folium maps**.  
💡 **Sentiment Analysis:** Extract insights from review texts.  

---

## 🤝 Contributing  
Feel free to **fork** this repository, open issues, or submit PRs to improve this analysis!  

---

## 📜 License  
This project is licensed under the **MIT License**.

---

Would you like me to generate a **GitHub repository structure** for this project? 🚀