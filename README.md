![alt text](https://github.com/alliesegre/

# Ironhack Final Project: Exploring Femicides cases in Turkey - regional characteristics and politics.
#### *Alice Segre*
#### *Data Analytics, Jan21 FT, Berlin, 12.03.21*

## Content
- [Project Description](#project-description)
- [Code and Resources Used](#code-and-resources-used)
- [Dataset](#dataset)
- [Cleaning](#cleaning)
- [Analysis](#analysis)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Visualization](#visualization)

## Project Description
This repository contains my project for the Ironhack Bootcamp Final Project. My objective was to explore the topic of femicides in Turkey (2010-2017). 
Specifically, my first research question was:
Are there any demographics patterns in connection to regions that have more cases?<br/>
Considering the increasing polarization of the country towards a right-wing, conservative and religious party (AKP), my second research question was:
Can we find patterns of polarization on a regional level, and any relation between political attitudes and number of cases? <br/>
*My final presentation*: *insert* <br/>

## Code and Resources Used
- Python Version: 3.7 <br/>
- Packages: pandas, numpy, sklearn, matplotlib, seaborn <br/>
#### Sources: <br/>
- Arslantaş, D., & Arslantaş, Ş. (2020). Keeping power through opposition: party system change in Turkey. New Perspectives On Turkey, 62, 27-50. doi: 10.1017/npt.2020.1
- Aydogan, A., & Slapin, J. (2012). Left-Right Reversed: Parties and Ideology in Modern Turkey. SSRN Electronic Journal. doi: 10.2139/ssrn.2165409
- Kavakli, K. (2020). Women’s Murders and the Interaction Between Gender (In)equality and Economic Development: A Subnational Analysis in Turkey. Journal Of Interpersonal Violence, 088626052096716. doi: 10.1177/0886260520967164
- Kumbaracıbaşı, A. (2019). Analyzing Party Positions and Electoral Dynamics in Turkey. International Journal Of Political Science And Urban Studies, 382-405. doi: 10.14782/ipsus.623236
- List of political parties in Turkey. (2021). Retrieved 11 March 2021, from https://en.wikipedia.org/wiki/List_of_political_parties_in_Turkey 
<br/>

## Dataset
My main datasets came from: wm_replication_dataset_2020_09_25.tab - Kerim Can Kavakli Dataverse. (2021). Retrieved 11 March 2021, from https://dataverse.harvard.edu/file.xhtml?persistentId=doi:10.7910/DVN/T1LUIY/OPTXAO&version=2.0 <br/>
And they were created for the research by Kavakli for the article Women’s Murders and the Interaction Between Gender (In)equality and Economic Development: A Subnational Analysis in Turkey. Journal Of Interpersonal Violence <br/>

To further explore the political aspect, I have generated the political dataset using election results (2009-2014-2019) reported by 
- PARTİ İL SEÇİM SONUÇLARI. (2021). Retrieved 11 March 2021, from https://secim.haberler.com/2014/illerde-durum/

## Cleaning
The main dataset for the research was the: region information, which included information on regional demographics<br/>
Additionally, two other datasets had to be considered: 
- victim level dataset (to count number of cases per region + have information on the cases)<br/>
- elections dataset, created from research on municipal elections of 2009, 2014, 2019. 

#### ** Cleaning of regions demographics*<br/>
Selected only the years matching the victim level database<br/>
The data columns were checked for null values. <br/>
The data type of each column was checked. <br/>

#### ** Cleaning of victim level data*<br/>
All the fields were translated from Turkish to English. <br/>
The location information was cleared so that only a column with the provinces <br/>
The excuses given for the murders <br/>
Data columns were renamed and stylized as snake_case.
After merging with demographics, I scaled the count to count per 100k per region. <br/>

#### ** Cleaning of elections data*<br/>
Scaled the elections results based on party orientation. Then weighted the scale based by percentage of votes party won with.<br/>
Assigned election results to region demographics, based on the following logic: <br/>
- 2010 - 2012 attitude: election results from 2009
- 2013 - 2016 attitude: election results from 2014
- 2017 attitude: election results from 2019

## Analysis
I looked at:<br/>
Multicollinearity Matrix <br/>
After running the multicollinearity checks (heat map, VIF) I decided to drop the ethnic turkish as it was correlated with ethnic kurdish, ln-casualty, all_wm_prov, knows_wm_prov.
VIF showed that no other column needed to be removed.<br/>

![alt text](https://github.com/alliesegre/turkey_femicides_ironhack/blob/main/Sources/corr_matrix.PNG)
![alt text](https://github.com/alliesegre/turkey_femicides_ironhack/blob/main/Sources/countvsgdp.PNG)<br/>


#### Transformation
Removing outliers on target variable only: <br/>
- Using Z-score<br/>
Tranformation:
- used Normalizer

 
## Model Training and Evaluation
First,  transformed the data and split the data into train and test sets with a test size of 40%.
I tried three different models and evaluated them based on the r score. <br/>
- Liner Regression – Final Model. 
- Random Forest Regressor 
- KNeighborsRegressor
<br/>
### Model performance
All three models worked quite badly on the prediction work:<br/>
- Liner Regressio : r^2= 0.03
- Random Forest Regressor : r^2 = -0.01
- KNeighborsRegressor : r^2 = -0.004<br/>

### Clustering as Alternative
I clustered in 8 custers, only two show a particular relevance:
- both have  a high percentage of kurdish population, and having either center or rigt wing political attitudes
![alt text](https://github.com/alliesegre/turkey_femicides_ironhack/blob/main/Sources/Clusters.PNG)<br/>

## Conclusion
In conclusion, with the current amount of data, it is not possible to predict the number of cases that will happen in each region.
However, the clustering does show some patterns for what concerns politics and ethnicity.
I will further explore patterns in Tableau.

## Future Work
- My hypothesis was that it would be possible to find patterns connected to the demographics and the politics of each region.
- Unfortunately, the data collected has gaps, and the years covered do not give enough chances to define clear trends. 
#### Further research should :
- cover the count of female suicides as well, as many femicides are apparently reported as suicides.
- compare between countries
- attempt to define political attitudes with surveys or other proxis, as the collection of only three elections was not enough to see the yearly changes.

## Visualization
- Tableau link: 

