# Introduction

## Overview

Welcome to my Analysis of Job Posting Of Over 710,000 Job Posting from around the world. This is a Study on Navigating the Jobs and Understanding the Job Market for Data Related Job Roles. 

The Data is Sourced from Luke Barousse's Python Course which provided the Foundation for My Analsis, Containing all info of Job Titles, Salaries, Perks, Location, Skill Required etc. through the course I gone through some very important questions like most demanded skills, Highly paid skills, skills trend around the year of 2023 and more.  

# The Problem Statement

Below are the Questions I want to answer in my Project:   
   1. What are skills most in demand for the Top 3 Data Roles.   
   2. How are In-Demand Skills trending for Data Analyst
   3. How well do jobs and skills Pay for Data Analyst
   4. What are the Optimal Skills for Data Analyst to learn? (High in Demand and High in Pay)
 
# Tools
For my Deep Dive into Data Analyst job market, I harnessed the power of several key tools:
* Python: The Backbone of my project is Python allowing me to find critical Insights. I also used following Python libraries:
   * Pandas Library: Used to analyze and play with Data
   * Matplotlib Library: Used for Visualizng the Findings
   * Seaborn Library: Helped in creating more advance Visuals
* Jupyter NOtebook: This tool i used to run my python scripts ahich let me easily include my notes and analysis
* Visual Studio Code: My go-to for executing pyhon scripts 

# The Analysis 

## 1. What are the Most Demanded Skills for the Top 3 most popular Data Roles.

To Find Out the most Demanded Skills for Roles of Data Analyst, Data Engineer and Data Scientist, I filtered out the data for those positions and also kept the data for US Locations only. Thus It Highlights which Skills will be bery much required and relevant to get Entry in the Respective Data Related Job Role.

For Details of the Process and Methods Utilized, Go Through my Notebook:  
[2_Skill_Demand](2_Skill_Demand.ipynb)

## For Data Visualization
``` python
fig, ax = plt.subplots(3,1, figsize=(8,6))

for i, title in enumerate(job_titles):
    df_plot=df_merged[df_merged['job_title_short'] == title].head(5)
    sns.barplot(df_plot, x='skill_perc', y='job_skills', ax=ax[i], hue='skill_perc', palette='dark:b_r')
    sns.despine()
    sns.set_theme(style='ticks')

    ax[i].set_title(title)
    ax[i].set_xlabel('')
    ax[i].set_ylabel('')
    ax[i].set_xlim(0,79)
    ax[i].legend().remove()
    ax[i].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'{int(x)}%'))
    
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])
    
    for n,v in enumerate(df_plot['skill_perc']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

plt.suptitle('Likelihood of Skills Requested in US Job Postings')
plt.tight_layout()
plt.show()
```

## Results
![Graph of Data Roles with Most Required Skills for each of them](/3_Project/Images/Skill_demad_for_3DataRoles.png)*Bar Chart Represnting top Skills in Demand for Top3 Data Roles*


## Key Insights
#### Data Analyst:
* SQL is the most requested skill, appearing in 51% of job postings.
* Excel follows, being requested in 41% of the job postings.
* Tableau and Python are also significant, with 28% and 27% respectively.
S* AS is less frequently requested but still notable at 19%.

#### Data Engineer:
* SQL and Python are nearly equally important, requested in 68% and 65% of job postings respectively.
* AWS (Amazon Web Services) is crucial for Data Engineers, appearing in 43% of job postings.
* Azure and Spark are also significant, each requested in 32% of the postings.

#### Data Scientist:
* Python is overwhelmingly the most requested skill, appearing in 72% of job postings.
* SQL follows at 51%, indicating its continued importance.
* R is significant as well, with a 44% request rate.
* SAS and Tableau each appear in 24% of job postings, suggesting they are also valuable skills for Data Scientists.

#### General Insights:
* Python and SQL are critical skills across all three roles, highlighting their universal importance in the data field.
* Excel and Tableau are particularly important for Data Analysts, emphasizing the need for strong data visualization and spreadsheet skills in this role.
* For Data Engineers, cloud-related skills like AWS and Azure, along with big data processing tools like Spark, are crucial.
* Data Scientists have a strong emphasis on programming skills, especially in Python and R.
* Recommendations for Job Seekers:
* Focus on Python and SQL: Given their high demand across all roles, proficiency in these languages can significantly enhance job prospects.
* Specialize According to Role: Depending on the target role, additional skills like Excel and Tableau for Data Analysts, AWS and Spark for Data Engineers, and R for Data Scientists should be prioritized.
* Stay Updated with Cloud Technologies: For Data Engineers, familiarity with cloud platforms like AWS and Azure is becoming increasingly important.
* These insights can guide both job seekers and employers in understanding the key skills required in the data industry and help align their training and hiring strategies accordingly.

======================================================================================================================

## 2. How are the In-Demand Skills are Trending for Data Analyst?

To find Out the trend of In-demand Skill for Data Analyst Role in the entire Year and tracking the trend for analysing what % of Job Postings had those skills in them and are going to be important in Next Year job Market

For Details of Process and Methods, Go through the NoteBook:      
[3_Skills_Trend](3_Skills_Trend.ipynb)

## For Data Visualization
```python
df_plot = df_piv_perc.iloc[:,:5]
plt.figure(figsize=(12,7))
sns.lineplot(df_plot, dashes=False, palette='dark', linewidth=2.1, markers=True)
sns.set_theme(style='ticks')
sns.despine()

plt.xticks(rotation=45, ha='right')
plt.title('Trending Top Skills for Data Analyst in US', fontsize=16)
plt.xlabel(2023)
plt.ylabel('Likelihood in Job Posting')
plt.legend()
ax=plt.gca()
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda y, pos: f'{int(y)}%'))


plt.show()
```

## Results
![Graph with likelihood of Skill to be in job posting of Data Analyst](/3_Project/Images/Likelihood_of_skill_in_DA_role.png)  
*Line Chartr Dipicting the the Likelihhod of Demamded Skill in a Data Analyst Job Post*


## Key Insights
1. **SQL**:
   - SQL is consistently the most requested skill, with a likelihood ranging from **55% to 50%** over the year.
   - There is a noticeable decline in SQL requests towards the end of the year, dropping to **50%** in November before a slight increase in December.

2. **Excel**:
   - Excel remains a highly demanded skill, maintaining a stable likelihood around **40-45%**.
   - An interesting spike occurs in December, where the likelihood of Excel being requested jumps to **45%**.

3. **Tableau**:
   - Tableau shows fluctuations but generally hovers around the **28-30%** mark.
   - There is a peak in July, indicating an increased demand during mid-year, followed by a decline towards October and a slight rise again in December.

4. **Python**:
   - Python is also a crucial skill for Data Analysts, with a likelihood of around **25-30%**.
   - There is a clear peak in July, similar to Tableau, suggesting a mid-year demand for Python skills.
   - The demand dips in October but sees a slight increase towards the end of the year.

5. **SAS**:
   - SAS is the least requested skill among the five, with a likelihood fluctuating around **18-22%**.
   - There is a consistent downward trend from January to June, reaching its lowest in June, followed by a steady rise towards the end of the year.

## Recommendations for Job Seekers
- **Focus on SQL and Excel**: Given their high demand, proficiency in these skills can significantly improve job prospects.
- **Leverage Mid-Year Demand**: Skills like Tableau and Python see a spike in demand around mid-year. Job seekers should be prepared to highlight these skills during this period.
- **Stay Updated with SQL**: Despite a slight decline towards the end of the year, SQL remains the most requested skill, emphasizing its importance in the field of data analysis.

These insights can help Data Analysts align their skill development with market demands, enhancing their employability and career growth.


======================================================================================================================

## 3. Comparing Salary Pay Distribution for Top Roles in Data Domain. Roles Included are 
* Senior Data Scientist
* Senior Data Engineer
* Data Scientist
* Data Engineer
* Senior Data Analyst
* Data Analyst

For Details of Process and Methods, Go through the NoteBook:  
[4_Salary_Analysis.ipynb](/3_Project/4_Salary_Analysis.ipynb)

## For Data Visualization

```python
plt.figure(figsize=(10,8))
sns.set_theme(style='ticks')
sns.boxplot(df_US_top6, x='salary_year_avg', y='job_title_short', order=title_rank)

ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))
plt.xlabel('Yearly Salary ($USD)')
plt.ylabel('')
plt.xlim(0,600000)
plt.title('Salary Distribution for Top Data Roles In US', fontsize=16)
plt.show()
```

## Result

![Box plot Show Distribution of Salary for Different Data Roles](/3_Project/Images/Box_plot_Data_sal_dist.png)
*Box Plot Showing Salry Distribution for Data Domain Job Roles*


## Key Insights

### Senior Data Scientist
- **Median Salary**: The median salary is around $150K.
- **Interquartile Range (IQR)**: Most salaries fall between $130K and $200K.
- **Outliers**: There are several outliers, with some salaries exceeding $500K.

### Senior Data Engineer
- **Median Salary**: The median salary is around $140K.
- **Interquartile Range (IQR)**: Salaries mostly range from $120K to $170K.
- **Outliers**: Numerous outliers, with some salaries approaching $400K.

### Data Scientist
- **Median Salary**: The median salary is approximately $120K.
- **Interquartile Range (IQR)**: The bulk of salaries range from $100K to $150K.
- **Outliers**: Outliers extend beyond $300K.

### Data Engineer
- **Median Salary**: The median salary is about $110K.
- **Interquartile Range (IQR)**: Salaries predominantly fall between $90K and $130K.
- **Outliers**: Some salaries reach up to $300K.

### Senior Data Analyst
- **Median Salary**: The median salary is roughly $90K.
- **Interquartile Range (IQR)**: Most salaries lie between $80K and $110K.
- **Outliers**: There are outliers with salaries going up to $200K.

### Data Analyst
- **Median Salary**: The median salary is around $70K.
- **Interquartile Range (IQR)**: The majority of salaries range from $60K to $90K.
- **Outliers**: Outliers are present, with some salaries nearing $150K.

## General Observations
- **Median Salaries**: Senior roles generally have higher median salaries compared to their non-senior counterparts.
- **Salary Ranges**: Senior positions also exhibit wider salary ranges and more significant outliers, indicating a broader spectrum of pay possibly due to experience, company size, or location.
- **Outliers**: All roles have outliers on the higher end, suggesting that top professionals in these fields can command significantly higher salaries than the median.
- **Role Comparison**: Senior Data Scientists and Senior Data Engineers have the highest salary distributions, whereas Data Analysts have the lowest.

These insights reflect the salary trends for key data roles in the U.S., highlighting the value and demand for senior positions in the data field.

======================================================================================================================

## 4. How Well Data Analyst are Paid. Comparision is Done on Skills with Highest Median Salary and Skills which are High In-Demand.

For Details of Process and Methods, Go through the NoteBook:  
[4_Salary_Analysis.ipynb](/3_Project/4_Salary_Analysis.ipynb)

## For Data Visualization
```python 
fig, ax = plt.subplots(2,1, figsize=(10,6))
sns.set_theme(style='ticks')
sns.despine()
sns.barplot(da_gr_toppay, x='median_salary', y='job_skills', ax=ax[0], hue='median_salary', palette='dark:b_r', legend=False)
ax[0].set_xlabel('Yearly Median Salary (USD)')
ax[0].set_ylabel('')
ax[0].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))

sns.barplot(da_gr_topcount, x='median_salary', y='job_skills', ax=ax[1], hue='median_salary', palette='light:b', legend=False)
ax[1].set_xlim(ax[0].get_xlim())
ax[1].set_xlabel('Yearly Median Salary (USD)')
ax[1].set_ylabel('')
ax[1].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))


plt.suptitle('Highest Median Salary vs In-Demand Skills Median Salary for Data Analyst in US')
plt.tight_layout()
plt.show()
```

## Result
!['Top pay vs Top Count Skills Median Salary](/3_Project/Images/Top_pay_vs_Top_count_median_salary.png)
*Bar Chart Comapring Median Salary for Skills with Highest Median Salary and Skills with High In Demand*

## Key Insights

### Skills with the Highest Median Salaries

1. **dplyr**:
   - Dplyr leads the chart with a median salary close to **$175K** per year, indicating its high value and demand in the market.

2. **bitbucket**:
   - Bitbucket follows closely with a median salary of approximately **$170K**, showcasing its importance for data professionals.

3. **gitlab**:
   - Gitlab skills are valued around **$165K** per year, making it a highly lucrative skill for data analysts.

4. **solidity**:
   - Solidity commands a significant salary of about **$150K**, reflecting its specialized demand in the industry.

5. **hugging face**:
   - Skills related to Hugging Face offer a median salary of around **$140K**, highlighting the value of expertise in this area.

### In-Demand Skills with Their Median Salaries

1. **python**:
   - Python remains a foundational skill for data analysts with a median salary of approximately **$80K**.

2. **tableau**:
   - Tableau expertise is valued around **$75K**, indicating its critical role in data visualization and analysis.

3. **r**:
   - The R programming language offers a median salary of about **$75K**, emphasizing its importance in statistical analysis.

4. **sql server**:
   - SQL Server skills command a median salary of around **$70K**, reflecting their necessity for database management.

5. **sql**:
   - General SQL skills are valued at approximately **$70K**, showcasing their fundamental role in data querying.

6. **sas**:
   - SAS skills offer a median salary of about **$65K**, highlighting their relevance in advanced analytics.

7. **power bi**:
   - Power BI expertise is valued at around **$65K**, emphasizing its importance in business intelligence.

8. **powerpoint**:
   - PowerPoint skills have a median salary of about **$60K**, reflecting their role in data presentation.

9. **excel**:
   - Excel commands a median salary of approximately **$60K**, showcasing its enduring value in data analysis.

10. **word**:
    - Microsoft Word skills are valued around **$55K**, highlighting their relevance in documentation.

## Recommendations for Job Seekers
- **Specialize in High-Value Skills**: Focusing on skills like dplyr, bitbucket, and gitlab can significantly increase earning potential.
- **Maintain Proficiency in Core Skills**: Skills such as Python, Tableau, and SQL remain essential and highly valued in the data analysis field.
- **Stay Updated with Market Trends**: Keeping abreast of emerging technologies and skills can help in staying competitive and maximizing salary potential.

These insights can help Data Analysts tailor their skill development to align with market demands, thereby enhancing their career growth and earning potential.

======================================================================================================================

## 5. What are the Most Optimal Skills to learn for being a data analyst i  n US. Here want to compare the Popularity and Median Salary as well to see their Demand as well as How Much These skills will be paid in the Market

For Details of Process and Methods, Go through the NoteBook:  
[5_Optimal_Skills.ipynb](/3_Project/5_Optimal_Skills.ipynb)

## For Data Visualization
```python
plt.figure(figsize=(8,6))
sns.set_theme(style='ticks')

sns.scatterplot(df_DA_skills, x='skill_perc', y='median_salary', hue='tech', palette='dark')
ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'{x:.0f}%'))
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K'))
plt.title('Data Analyst Skills in US with Likelihood in a job and Median Salary', fontsize=12)
plt.ylim(78000,100000)
sns.despine()
text=[]
for i,txt in enumerate(df_DA_skills.index):
    text.append(plt.text(df_DA_skills['skill_perc'].iloc[i], df_DA_skills['median_salary'].iloc[i], " " + txt))
adjust_text(text, arrowprops=dict(arrowstyle='->', color='gray'))

plt.tight_layout()

plt.show()
```

## Result
![Optimal Skills which have High Demad and Decent Median Slary](/3_Project/Images/Optimal_skills.png)

# Key Insights

## General Observations
- **Skill Percentage (Likelihood in a Job)**: Represents the percentage of job listings that mention each skill.
- **Median Salary**: Reflects the median salary associated with jobs that require each skill.
- **Color Coding**: 
  - Blue represents **DataBases** skills.
  - Orange represents **Analyst-Tool** skills.
  - Green represents **Programming** skills.

## Insights by Skill

### SQL
- **Skill Percentage**: ~58%
- **Median Salary**: ~$91K
- **Category**: DataBases
- **Insight**: SQL is highly demanded, appearing in over half of the job listings for data analysts, and commands a solid median salary.

### Excel
- **Skill Percentage**: ~42%
- **Median Salary**: ~$84.4K
- **Category**: Analyst-Tool
- **Insight**: Excel is a common tool among data analysts, with a significant presence in job listings, though its median salary is lower compared to more technical skills.

### Python
- **Skill Percentage**: ~33%
- **Median Salary**: ~$97.5K
- **Category**: Programming
- **Insight**: Python is associated with the highest median salary among the listed skills, emphasizing its value and growing demand in data analysis roles.

### Tableau
- **Skill Percentage**: ~31%
- **Median Salary**: ~$92.9K
- **Category**: Analyst-Tool
- **Insight**: Tableau is a valuable tool for data visualization, offering a competitive median salary and a substantial presence in job requirements.

### SQL Server
- **Skill Percentage**: ~7%
- **Median Salary**: ~$92.5K
- **Category**: DataBases
- **Insight**: SQL Server, while less commonly mentioned than SQL, still offers a high median salary, reflecting its specialized role in database management.

### R
- **Skill Percentage**: ~21%
- **Median Salary**: ~$92.5K
- **Category**: Programming
- **Insight**: R is well-regarded for statistical analysis and commands a competitive median salary, though it's less frequently required than Python.

### Power BI
- **Skill Percentage**: ~19%
- **Median Salary**: ~$90K
- **Category**: Analyst-Tool
- **Insight**: Power BI is a popular business intelligence tool, with a decent presence in job listings and a respectable median salary.

### PowerPoint
- **Skill Percentage**: ~11%
- **Median Salary**: ~$85K
- **Category**: Analyst-Tool
- **Insight**: PowerPoint, while more associated with presentations than technical analysis, still appears in a notable number of job listings for data analysts.

### Word
- **Skill Percentage**: ~11%
- **Median Salary**: ~$81.2K
- **Category**: Analyst-Tool
- **Insight**: Word is the least technical tool in the list but is still required in some job listings, with the lowest median salary among the skills.

## Overall Observations
- **High Demand, High Salary**: Skills like SQL and Python, which are highly demanded, tend to offer higher median salaries.
- **Analyst-Tool Skills**: While these skills are commonly required, they generally have lower median salaries compared to programming and database skills.
- **Specialized Skills**: Tools like SQL Server and Tableau, though less frequently mentioned, offer competitive salaries, indicating their specialized value in certain roles.

These insights highlight the importance and value of different skills in the data analyst job market in the U.S., with technical and programming skills generally commanding higher salaries.


# What I Learned from the Projects:

   **Data Cleaning Importance**

   -  At every stage of analysis I got to know that for every problem statement, there will be different approach needed for cleaning the data so that the required result can be achieved.
   
   **Data Visulization Power of Python**
   
   + Pyhthon has a very versatile set of Libraries to create awesome viusls and can be altered with your needs as well. All charts are here form Basic to advance level visuals.

   **Skill Demand for Data Analyst Role**

   * Got to know which are the skills really required in Data Analyst worka and what are some highly paid skills for data analyst role as well.

   # Insights

   * Skills Demand with their Salary Correlation.
   * Highly paid skills with most In-Demand Skills.
   * Salary Distribution of Different Data Roles.
   * Market Trend of Skills.
   * Economic Value of Skills.


# Challenges I Faced

* Data Inconsistencies: Handling Missing Data withdifferent column and Filling them sometime with careful consideration of reults so that the result were not be Skewed.
* Complex Data Visualization: Visuls were created in mind after seeing the data but coding them with logics and languages was really hard.
* Balancing the Depth and Breadth: Balancing the level of info and solving the issue with current dataset only was a bit of challenge

# Conclusion

This Entire Project was a very good foundation for me to get the gist of what skills were really mentioned in any job posting of  a Data Analyst and what are currently in demand. This helped to know the true potential of Python and its libraries as well. Its sure that to be in this domain we have to be Student for life but for now any one who is willing to carve a career in data related job roles can look up to this project for a guidance that will give them an idea of skills and their economic value so that they can strat learning the most valueable skills which are high in demand as well as have good pay associated with them.
