<h1>Visualise Data with Python</h1>
<p>Visualizing data with Python is a powerful way to transform raw numbers into meaningful insights. With versatile libraries such as Matplotlib, Seaborn, and Plotly, it is easy to create charts, graphs, and interactive dashboards that reveal trends and patterns. In this illustration, I will use Health Supplement Sales Dataset from Kaggle, to visualize the sales performance of a health company, highlighting key insights that can support data-driven decisions.</p>

<img width="416" height="213" alt="image" src="https://github.com/user-attachments/assets/29890fad-f7c8-48db-a198-8e7c9cff484d" /> <br><br>
`sales_data = pd.read_csv("Supplement_Sales.csv")`<br><br>
<img width="577" height="472" alt="image" src="https://github.com/user-attachments/assets/5dd28633-bd76-427d-b8ee-421275b32a6e" /><br>
<img width="307" height="246" alt="image" src="https://github.com/user-attachments/assets/a95f4185-805b-4b56-b8c9-f683445d4bb1" /><br>
<p>Null data is not found in the dataset, hence no data imputation is required. </p>

<b>Plot Sales Performance Trend Y2020 to Y2024</b><br>
```
sales_data["Date"] = pd.to_datetime(sales_data["Date"])

filtered_data = sales_data[
    (sales_data["Date"] >= "2020-01-01") &
    (sales_data["Date"] < "2025-01-01")
]

years = pd.Index(range(2020, 2025), name="Year")

yearly_revenue = (
    filtered_data
    .groupby(filtered_data["Date"].dt.year)["Revenue"]
    .sum()
    .reindex(years, fill_value=0)
)

plt.plot(
    yearly_revenue.index,
    yearly_revenue.values,
    marker="o",
    label="Year-wise Profit"
)
plt.show()
```
<img width="631" height="482" alt="image" src="https://github.com/user-attachments/assets/6dd05489-198f-4fdc-a153-a1612596f9da" /><br>

As Y2024 marked a total $4.4M revenue, I shall dive into Y2024 to show the breakdown of sales revenue by category. </br></br>
<b>Sales Revenue by Category in Y2024</b><br>
```
sales_data["Date"] = pd.to_datetime(sales_data["Date"])
filtered_data = sales_data[sales_data["Date"].dt.year == 2024]

category_revenue = (
    filtered_data
    .groupby("Category")["Revenue"]
    .sum()
    .sort_values(ascending=False)
)

plt.figure(figsize=(10, 6))
bars = plt.bar(category_revenue.index, category_revenue.values, color='skyblue')

plt.show()
```

<img width="1372" height="802" alt="image" src="https://github.com/user-attachments/assets/0daf88e2-6101-410a-8485-e51b1b0d4a84" /> </br>
The Vitamin and Mineral product categories contributed to strong sales performance in Y2024, with each achieving approximately $800k in sales. </br>
