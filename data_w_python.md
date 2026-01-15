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
The Vitamin and Mineral product categories contributed to strong sales performance in Y2024, with each achieving approximately $800k revenue. </br></br>


<b>Y2024 Sales Trend</b></br>
To gain deeper insights into monthly sales performance in Y2024, a multi-line trend analysis by product category was conducted. </br>
```
sales_data["Date"] = pd.to_datetime(sales_data["Date"])
filtered_data = sales_data[sales_data["Date"].dt.year == 2024].copy()

filtered_data["Month"] = filtered_data["Date"].dt.month

monthly_trends = filtered_data.pivot_table(
    index="Month",
    columns="Category",
    values="Revenue",
    aggfunc="sum"
).sort_index()

plt.figure(figsize=(12, 6))
for category in monthly_trends.columns:
    plt.plot(monthly_trends.index, monthly_trends[category], marker='o', label=category)

plt.title("Y2024 Category Sales Trend by Month")
plt.xlabel("Month")
plt.ylabel("Revenue")
plt.xticks(monthly_trends.index, [pd.to_datetime(str(m), format='%m').strftime('%b') for m in monthly_trends.index])
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.legend(title="Category")
plt.tight_layout()
plt.show()
```
<img width="1505" height="708" alt="image" src="https://github.com/user-attachments/assets/b755f43f-dbc8-4745-a4dc-edccfd4cac38" /> <br>
Since Jan 2024, Vitamin and Mineral categories have consistently outperformed other product categories in terms of sales performance. <br><br>
<b>Y2024 Sales Platform Performance </b><br><br>
After identifying the leading sales categories, sales channels are another key factor in understanding which avenues generate the strongest traction. <br>
```
sales_data["Date"] = pd.to_datetime(sales_data["Date"])

filtered_data = sales_data[sales_data["Date"].dt.year == 2024].copy()

platform_sales = filtered_data.groupby('Platform')['Revenue'].sum().sort_values()

plt.figure(figsize=(6, 3))
bars = plt.barh(platform_sales.index, platform_sales.values, color=plt.cm.Pastel1.colors)

plt.show()
```
<img width="802" height="381" alt="image" src="https://github.com/user-attachments/assets/67e5addd-072c-4a7a-812b-843d428eeb72" /> <br>
In 2024, iHerb led platform revenue with approximately $1.61M, followed by Amazon at $1.49M and Walmart at $1.34M, showing that iHerb outperformed its closest competitor by around $120k and Walmart by $268k. Together, iHerb and Amazon contributed roughly 73% of total revenue, indicating that these two platforms dominate sales, while Walmart plays a smaller role. Overall, all three platforms achieved healthy revenues above $1M, highlighting strong sales performance across channels, with opportunities to further grow Amazon and Walmart while maintaining iHerb’s lead.
<br><br>
<b> Y2024 Regional Sales Revenue Distribution</b><br>
Let's visualize the geographical distribution of sales revenue across regions. <br>

```
sales_2024 = sales_data[sales_data['Date'].dt.year == 2024]
sales_by_location = sales_2024.groupby('Location')['Revenue'].sum().reset_index()

sales_by_location['Revenue'] = sales_by_location['Revenue'].apply(lambda x: "${:,.0f}".format(x))

print(sales_by_location.sort_values(by='Revenue', ascending=False).head())

sales_by_location['Revenue_numeric'] = sales_2024.groupby('Location')['Revenue'].sum().values

fig = px.choropleth(
    sales_by_location,
    locations='Location',
    color='Revenue_numeric',
    color_continuous_scale=yellow_scale,  # use variable, not string
    title='Sales Revenue by Country (2024)',
    hover_data={'Revenue': True, 'Revenue_numeric': False},
    width=1000,
    height=600
)

fig.add_trace(
    go.Scattergeo(
        locations=sales_by_location['Location'],
        locationmode='country names',
        text=sales_by_location.apply(lambda row: f"{row['Location']}: {row['Revenue']}", axis=1),
        marker=dict(
            size=sales_by_location['Revenue_numeric'] / sales_by_location['Revenue_numeric'].max() * 30,
            color=sales_by_location['Revenue_numeric'],
            colorscale=yellow_scale,  # pass variable, no quotes
            showscale=False,
            line=dict(width=0.5, color='black')
        ),
        hoverinfo='text'
    )
)

fig.show()
```
<img width="1370" height="800" alt="image" src="https://github.com/user-attachments/assets/a070b5b5-5cea-4a55-a5d7-1fb1dff10a40" />

