# SHS-SNF-Deliverable
## Data Overview
- Dataset source: https://data.cms.gov/provider-data/dataset/5sqm-2qku
- Volume: 600000+ rows, 15 columns
- Columns/Attributes: CMS Certification Number (CCN), Facility Name, Address, City, State, Zip Code, County Name, Phone Number, CMS Region, Measure Code, Score, Footnote, Start Date, End Date
- Attributes used for metric creation: Measure Code, Score
- For correlation, pivoted columns by Measure Code using Jupyter Notebooks
- Data dictionary source: https://data.cms.gov/provider-data/sites/default/files/data_dictionaries/nursing_home/NH_SNFQRP_Data_Dictionary.pdf

## Deriving and Understanding the Metric
- Metric Name – Cost per Successful Return Score (CSR Score)
- It is derived from Medicare Spending Per Beneficiary Score (MSPB Score) and Successful Return Score
### Formula:
#### Cost per Successful Return Score = (1/MSPB Score) / Successful Return Score
As a lower MSPB Score indicates greater value and efficiency of the Skilled Nursing Facility and a higher Successful Return score indicates the rate at which residents return to home and community from a SNF, a reciprocal of the former was taken to normalize both attributes. Higher the CSR Score, the more efficient the SNF is in terms of its impact on the community and its beneficiaries

##### NOTE: This is not a dollar-value equivalent, it is only a numerical representation of the cost or efficiency of the SNF

## Dashboarding in Tableau
### Initial Analysis for Understanding Data:
- Filled Map - MSPB Score by State (Mainland US)
- Heat Map - Average Successful Return Score by State (Mainland US)
- Packed Bubbles - Falls Causing Injuries by CMS Region Number
### Advanced Analysis:
- Filled Map - Clustering of Mainland US States
- Scatter Plot - Correlation of different variables with MSPB Score
- Creation of Calculated Field / Metric - Cost per Successful Return Score (CSR Score)
### Solution:
- Symbol Map - Best Skilled Nursing Facilities in Mainland US (95th percentile CSR Score)
- Horizontal Bar Chart - Top 3 Skilled Nursing Facilities in each US State by CSR Score


## The Process
The best resources to understand the dataset were: Data Dictionary file and a YouTube video detailing how to read various Score columns in the dataset. Using these, I realized the relative orientation of each Score based range. 

Initially, I created simple graphs to understand the contents of the dataset. These graphs were scatter plots, geographical maps, and other plots. From some of these geographical maps, I was able to see a few obvious clusters of data which meant I could try implementing clustering on any of these columns.

For clustering, the idea was to divide each of the Score columns filtered by their Measure Codes and find clusters that could explain the values in any format. For various views, clustering did not seem like the best solution, however, the graphical view showed promise. After implementing clustering, I discovered that each geographical cluster had multiple outliers as seen from the clustering map. This is where I decided to look for other approaches.

While finding correlation for various variables with MSPB Score, I found that the Successful Return Score had high correlation with MSPB Score along with 2 or 3 other columns. Now, to derive a more refined view of the dataset and to provide a much more accurate representation of the solution, I would have gone ahead with 3 columns derived from the highest slopes in Trend Lines and lowest p-values, however, as this introduces the problem of high variance, I decided to go ahead with the simplest solution with the best R-squared value in the Trend Line.

Lastly, while creating the last dashboard to display the solution and the implementation of the metric, I decided to go ahead with two views: one geographical map of all the best SNFs in Mainland US, and the second one with a state-wise top 3 horizontal bar-graph solution. This was done for two different types of consumers in mind: customer who would prefer interstate travel and those who would prefer intra-state travel to find the best Skilled Nursing Facilities for their loved ones.

## References
- Tableau Story URL - The Very Best of SNFs Around

### References:
#### Youtube - https://www.youtube.com/watch?v=xyYLgUmae3c
#### Data Dictionary - https://data.cms.gov/provider-data/sites/default/files/data_dictionaries/nursing_home/NH_SNFQRP_Data_Dictionary.pdf
#### GitHub URL - 
