# Working with CSV Data and the Pandas Library in Python

This lesson covers:
- Reading and writing **CSV files**  
- Using the **Pandas library** for data manipulation  
- Performing **basic data analysis**  

---

## Soureces
- [pandas documentation](https://pandas.pydata.org/docs/#pandas-documentation)
- [API reference](https://pandas.pydata.org/docs/reference/index.html)

---
## 1. Introduction to Pandas

- **Pandas** is a powerful Python library for **data analysis and manipulation**  
- Provides two main data structures:
  - `Series` → 1D labeled array  
  - `DataFrame` → 2D labeled table (like a spreadsheet)  

```python
import pandas as pd
```

---

## 2. Reading CSV Files

```python
data = pd.read_csv("data.csv")
print(data)
```

- `read_csv()` loads a CSV file into a **DataFrame**  
- Common options:
  - `sep=";"` → specify separator if not comma  
  - `header=None` → no header row  
  - `index_col=0` → use first column as index  

---

## 3. Exploring Data

```python
# View first 5 rows
print(data.head())

# View last 5 rows
print(data.tail())

# Get basic info
print(data.info())

# Summary statistics
print(data.describe())
```

- Quickly check **structure, columns, and statistics**  

---

## 4. Accessing Data

```python
# Access a column
print(data["Name"])

# Access multiple columns
print(data[["Name", "Age"]])

# Access a row by index
print(data.iloc[0])

# Access row by label (if index set)
print(data.loc[0])
```

- `iloc` → integer-location based indexing  
- `loc` → label-based indexing  

---

## 5. Filtering and Selecting Data

```python
# Filter rows where Age > 25
filtered = data[data["Age"] > 25]

# Filter with multiple conditions
filtered = data[(data["Age"] > 25) & (data["City"] == "Toronto")]
```

- Use **boolean conditions** for filtering  

---

## 6. Modifying Data

```python
# Add a new column
data["Score"] = [90, 85, 78]

# Modify column values
data["Score"] = data["Score"] + 5

# Drop a column
data = data.drop("Score", axis=1)

# Rename columns
data = data.rename(columns={"Name": "Full Name"})
```

---

## 7. Sorting Data

```python
# Sort by a column
data_sorted = data.sort_values(by="Age")

# Sort descending
data_sorted = data.sort_values(by="Age", ascending=False)
```

---

## 8. Saving Data

```python
# Save DataFrame to CSV
data.to_csv("updated_data.csv", index=False)
```

- `index=False` prevents writing row numbers  

---

## 9. Aggregation and Grouping

```python
# Group by a column and calculate mean
grouped = data.groupby("City")["Age"].mean()
print(grouped)
```

- Useful for **summarizing data by categories**  

---

## 10. Key Takeaways

- **Pandas** simplifies reading, manipulating, and analyzing CSV data  
- Use `read_csv` and `to_csv` to handle files  
- Access, filter, and modify data efficiently with **DataFrames**  
- Sorting, grouping, and aggregations help with **data analysis tasks**  

Mastering Pandas is essential for **data science, analytics, and real-world Python applications**.
