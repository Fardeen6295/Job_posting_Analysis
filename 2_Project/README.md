# Customer and Sales Data Analysis

## Objective
The objective of this analysis is to gain insights into customer demographics, product performance, and various sales metrics to guide strategic decisions.

## Tasks

### 1. Customer Demographics
- **Identify Key Demographics**: Analyze customer data to identify key demographic segments.
- **Clean Data**: Ensure customer data is clean and ready for detailed analysis.

### 2. Customer Details for Further Study
- **Extract Customer Details**: Prepare a detailed dataset of customers for further study and segmentation.

### 3. Product Performance
- **Top Performing Products**: Identify the best-performing products based on sales and customer ratings.
- **Worst Performing Products**: Identify products that are underperforming.

### 4. Ratings Analysis
- **Category Ratings**: Analyze ratings to understand the performance of different product categories.

### 5. Orders Analysis
- **Orders by Location**: Analyze order data to understand geographic distribution.

### 6. Revenue Analysis
- **Revenue by Region**: Analyze revenue distribution across different regions.
- **Customer Segments**: Break down revenue by different customer segments.
- **Payment Methods**: Analyze revenue distribution by payment methods.

### And More
- **Additional Insights**: Explore other relevant insights as identified during the analysis process.

---
# Tools
For my Deep Dive into Data of Retail Chain Analysis, I harnessed the power of several key tools:
* Python: The Backbone of my project is Python allowing me to find critical Insights. I also used following Python libraries:
   * Pandas Library: Used to analyze and play with Data
   * Matplotlib Library: Used for Visualizng the Findings
   * Seaborn Library: Helped in creating more advance Visuals
   * Plotly Express: For Creating more Engaging and Interactive Visuals
* Jupyter NOtebook: This tool i used to run my python scripts ahich let me easily include my notes and analysis
* Visual Studio Code: My go-to for executing pyhon scripts
---
# The Analysis
## 1. Let's See the Customer Demographic First by Gender and Income
I have used Seaborn and Plotly Express for them. Feel Free to go through the actual procedure at here.
[Notebook](Retail_Transactions.ipynb)
### For Data Visualization
``` Python
plt.figure(figsize=(8,3))
sns.barplot(data=gen, x='count', y='Gender', hue='Gender', palette='cividis')
sns.set_theme(style='ticks')
sns.despine()
for n, v in enumerate(gen['count']):
    plt.text(v,n,f'{v/1000:.1f} K')
plt.xlim(0,200000)
plt.xlabel('Number of Customers')
plt.ylabel('Gender')
plt.title('Gender Distribuition of Customers', fontsize=14)
plt.show()
```
### Result of Code
![Male-Female Customer Counts](Job_posting_Analysis/2_Project/Visuals/MaleFemale.png)

### Key Insights
Male are more in number as comapred to Females.

### Gender By Income Level
Let's See the Distribuition by Income Level as well
### For Data Visualization
``` Python
fig = px.bar(data_frame=df_new.groupby(['Gender','Income']).size().reset_index(name='Count'),
        x='Gender', y='Count', color='Income', barmode='group', title='Gender Distribution with Respect to Income Level of Customers',
        labels={'Gender':'Customers Gender', 'Count':'Number of Customers'}, width=700,
        color_discrete_sequence=px.colors.sequential.Inferno
        )
fig.show()
```
### Result of Code
![Male Female by Income Level](2_Project\Visuals\Male_Female_Income.png)

## 2. Let's See the Overall Revenue Trend and Category Wise As well.
Revenue Trend of Entrie Year Give details about pattern and Category wise best performance by Month so we can get to know their Peak and Low Era.
### For Data Visualization
``` Python
sns.lineplot(Monthly_grp,x='Month', y='Amount', linewidth=2.5, marker='s', markersize=7, color='black')
sns.set_theme(style='ticks')
sns.despine()
ax = plt.gca()
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda y,pos: f'${y/1000000} M'))
plt.xlabel('2023-24')
plt.ylabel('(USD $) in Millions')
plt.title('Revenue Trend for Year 2023-24')
plt.show()
```
### Result of the Code
![Revenue Trend of Entrie Year](2_Project\Visuals\Rev_trend.png)

## Revenue Trend By Different Category
### For Data Visualization
```Python
plt.figure(figsize=(12,8))
sns.set_theme(style='ticks')
sns.lineplot(data=trend_cat, legend=True, dashes=False, markers=True, linewidth=4, markersize=9, palette='tab10')
ax = plt.gca()
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'$ {x/1000000} M'))
plt.xlabel('Year 2023')
plt.ylabel('Revenue in USD ($)')
plt.title('Revenue Trend of Different Categories at Store', fontsize=18)
plt.show()
```
### Result of Code
![Revenue Trend by Categories](2_Project\Visuals\Rev_trend_by-Category.png)

## 3. We Also want to see Which Customer Segmenst Brings More Revenue and which is Low.
Understand Revenue Distribuition by Customer Segements Helps a lot for Marketing Decision.
```python
plt.figure(figsize=(10,3))
ax = sns.barplot(data=cust_seg, x='Revenue', y='Customer_Segment', hue='Count', palette='dark:b_r')
sns.set_theme(style='ticks')
sns.despine()
ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${x/1000000}M'))

plt.ylabel('Customer Segments')
plt.xlabel('Revenue in USD($)')
plt.title('Revenue and Count of Customer of Segments')
plt.xlim(0,220000000)
for n, v in enumerate(cust_seg['rev_%']):
    plt.text(v+1000000,n,f'{v}% of Total Rev', color='white')

x, y = ax.get_legend_handles_labels()
ax.legend(x[::-1], y[::-1], title='Count')

plt.show()
```
### Result of Code
![Revenue by Customer Segment](2_Project\Visuals\Rev_by_Customer_segments.png)
### Key Insights 
Regualr Customer Contribute the MAX while Premium are at LOW.

## 4. We want to see Which Category Segmenst Brings More Revenue and which is Less.
Understand Revenue Distribuition by Categories Segements Helps a lot for Manufacturing Decision.
```python
sns.barplot(data=cat_rev, x='Total_Amount', y='Product_Category', hue='Total_Amount', palette='dark:b_r', legend=False)
sns.set_theme(style='darkgrid')
sns.despine()
ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'$ {x/1000000} M'))
plt.xlim(0,115000000)
plt.xlabel('Revenue USD ($)')
plt.ylabel('Categories')
plt.title('Revenue for Different Category (2023)', fontsize=14)
for n, v in enumerate(cat_rev['Total_Amount']):
    plt.text(v+1000000,n,f'${v/1000000:.1f} M')
plt.show()
```
### Result of Code
![Revenue by Categories](2_Project\Visuals\Rev_by_Category.png)
### Key Insights 
Electronics are Highest Contibutor here.

## 5. We want to see Which Brand is Responsible for That Category being High or Low
Understand Revenue Distribuition by Brand help in finding top Brands.
```python
fig = px.bar(data_frame=cat_brd, x='Product_Brand', y='Total_Amount', color='Product_Category', barmode='group', color_discrete_sequence=px.colors.qualitative.Bold,
             title='Revenue by Category and Brand')
fig.update_layout(
    paper_bgcolor = 'white',
    plot_bgcolor = 'grey',
    yaxis = dict(tickprefix='$ '),
    xaxis = dict(tickangle=-45, automargin=True), margin=dict(t=40,b=0))
fig.update_traces(textfont_color='white')
fig.show()
```
### Result of Code
![Revenue by Categories and their Brand](2_Project\Visuals\Rev_by_Category_Brand.png)
### Method 2 By Seaborn


