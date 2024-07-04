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
![Graph of Data Roles with Most Required Skills for each of them](Luke_python\3_Project\Images\Skill_demad_for_3DataRoles.png)


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
[3_Skills_Trend](Luke_python\3_Project\3_Skills_Trend.ipynb)

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
![Graph with likelihood of Skill to be in job posting of Data Analyst](Luke_python\3_Project\Images\Likelihood_of_skill_in_DA_role.png)  
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
