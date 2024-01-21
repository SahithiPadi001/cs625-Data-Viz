HW 4, CS 625, Fall 2023
================
Sahithi Padidela

Oct 26,2023

### Pre-requisites:

The goal of this assignment is to propose and implement charts based on questions asked about real-world data. This includes colors, fonts, and any text elements. 
For each chart, there’s an article describing the chart and an Excel data file.

## Description:
From the assignment instructions, I have choosen Dataset 2 and I have used Table 118 - Death Rates for Major Causes of Death--States and Island Areas.
As mentioned, To create charts I must use different idioms and data visualization tools.
I employed Tableau as my data visualization tool to answer the questions with appropriate charts.

# DATASET 2

## Q1: Which states had the highest death rates over all causes in 2006?

### Data Handling

* First, I downloaded the excel data from the git link. Before creating the chart I made some changes in the table 118 which have details about the deaths happened in various states of united states. 
* I made some changes to the dataset to make it appropriate for creating the chart.
* I deleted the null values and empty rows which results in meaningfull dataset. And also I removed the Island rows as they have messed up data which disturbs the whole chart.
* I employed Tableau as my data visualization tool to create the Barchart.

  Modified excel file for Q1 : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/10s0118q1.xls      

  
## Idiom : BarChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Total deaths| value, quantitative | horizontal position on a common scale (x-axis) |
| State | key, Categorical | vertical spatial region (y-axis) |


### Answer

I have choosen bar graph for visualization because it provides a clear visual representation of the values, making it easy to observe disparities and identify any patterns or outliers in the data. The vertical orientation, in particular, helps accommodate long state names without overlapping the labels, especially when the names are rotated for better readability. The length of each bar corresponds to the total death rate resulting from all diseases for a particular state. 

In 2006, the states with the highest death rates due to all causes were:
1. Mississippi - 961.2
2. Alabama -952.4
3. West Virginia - 941.3
4. Louisiana - 930.1
5. Oklahoma -920.4

These states experienced the highest total number of deaths across all causes compared to other states in 2006.

### Image of barchart for Q1 

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/q1tw.jpeg)   

#### Tableau workbook link for barchart for Q1 :

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Q1.twb   

## Q2 : Is this ordering different if you compare deaths due to disease vs. deaths due to accident, injury, and assault? In other words, which states are more hazardous to your health vs. which states are the most dangerous?

### Data Handling

* To create chart for this question, I modified the data by adding two more columns to the existing data.
* One column is the summation of deaths values due to diseases and the other column is the summation of death that are due to accident, injury, and assault. I labeled a column "Total diseases" for deaths caused by diseases and "Total 
   accidents" for deaths caused by accidents, injuries, and assaults.
*  I calculated the values manually by using the feature autosum function in excel file.
*  I employed Tableau as my data visualization tool to create the Barchart.

  Modified excel File For Q2 :  https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/10s0118q2.xls  

  ## Idiom : BarChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| State | key, Categorical | vertical spatial region (y-axis) |
| Total diseases| value, quantitative | horizontal position on a common scale (x-axis) |
| Total accidents| value, quantitative | horizontal position on a common scale (x-axis) |

### Answer

I have choosen bar graph for visualization because it provides a clear visual representation of the values, making it easy to observe disparities and identify any patterns or outliers in the data. I have created 2 sub charts, one for death due to diseases and the other for death due to accident,injury and assault.

In 2006, the states with the highest death rates due to diseases are:
1 . Alabama - 616.8
2 . Louisiana - 210.0
3 . Oklahoma - 205.0

In 2006, the states with the highest death rates due to Accidents,Injury and assault are:
1 . Alabama - 736.2
2 . Mississippi - 335.0
3 . Louisiana   - 334.0

### Image of Barchart for Q2:

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/q2tw.jpeg)

#### Tableau workbook link for barchart for Q2 :

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Q2.twb


## Further question

Question 1 - Do some states have lower rates of disease-related fatalities in correlation with higher per capita health expenditures?
Hypothesis: Because these states have greater access to and provide better healthcare services, they should have fewer disease-related fatalities.

Question 2 - Are injuries caused by firearms and deaths from assault or deliberate self-harm correlated?
Hypothesis: States with greater rates of injuries from firearms may also have higher rates of assault or self-harm fatalities, suggesting a significant relationship between these variables.




## Extra credit - Recreating the charts using Python

## DATASET 2

To recreate the chart, I first obtained the same Excel dataset[Table 118 - Death Rates for Major Causes of Death--States and Island Areas.] from the github link.
Then, In order to make some adjustments to the dataset, i uploaded it to my google drive.I accessed dataset from drive and modified without unneccesary data.
I used python to recreate bar chart from Table 118. 

Modified excel file-   https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/10s0118q12.xls

## Q1: Which states had the highest death rates over all causes in 2006?

## Data 

* The data dictionary contains two lists: "State" and "Total deaths."
* I have used Total deaths attribute on X- axis and State attribute on y-axis.

## Plot

**import pandas as pd** - Imports Pandas for data manipulation, using 'pd' as an alias.

**import numpy as np** - Imports NumPy for numerical computations, using 'np' as an alias.

**import geopandas as gpd** - Imports GeoPandas for geospatial data handling (commented out).

**import seaborn as sns** - Imports Seaborn for statistical data visualization.

**import matplotlib.pyplot as plt** - Imports Matplotlib's Pyplot module for creating visualizations.

**excel_file** = '/content/drive/MyDrive/10s0118q12.xls': Defines the file path for an Excel file.

**dataframe** = pd.read_excel(excel_file): Reads the Excel file using Pandas and stores it in a DataFrame.

**dataframe.head():** Displays the first few rows of the DataFrame for a quick data overview.


## Executed code for recreating bar chart for Q1

dataframe= dataframe.sort_values(by='Total', ascending=False)

plt.figure(figsize=(12, 10))

sns.barplot(data=dataframe, x='Total deaths', y='State' ,color='grey')

plt.xlabel('Total deaths')

plt.ylabel('State')

plt.title('State with the highest overall death rates in 2006')

plt.show()

Below provided image contains the bar chart for Q1 that is recreated using python from table 118.

 ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/q1python.png)

## Q2: Is this ordering different if you compare deaths due to disease vs. deaths due to accident, injury, and assault? In other words, which states are more hazardous to your health vs. which states are the most dangerous?

## Data

* To create chart for this question I modified the data by adding two more columns to the existing data.
* One column is the summation of death values due to diseases and the other column is the summation of death that are due to accident, injury, and assault.
* I have created two barplots to compare different causes of deaths.

  ## Executed code for recreating bar chart for Q2
  
  fig, axes = plt.subplots(1, 2,figsize=(24, 10))
  
  sns.set(style="darkgrid")
  
  dataframe = dataframe.sort_values(by='Total diseases', ascending=False)
  
  sns.barplot(x="Total diseases", y="State", label=" Total deaths due to diseases in 2006", data=dataframe, color="grey", ax=axes[0])
  
  axes[0].set_xlabel("Total diseases")
  
  axes[0].set_title("Total Deaths due to Diseases by State in 2006")
  
  axes[0].legend()
  
  sns.set(style="darkgrid")
  
  dataframe = dataframe.sort_values(by='Total accidents', ascending=False)
  
  sns.barplot(x="Total accidents", y="State", label=" Total deaths due to accidents, injury and assault in 2006", data=dataframe, color="grey", ax=axes[1])
  
  axes[1].set_xlabel("Total accidents")
  
  axes[1].set_title("Total Deaths due to Accidents,Injury and Assault by State in 2006")
  
  axes[1].legend()
  
  plt.show

  Below provided image contains the bar chart for Q1 that is recreated using python from table 118.
  
  ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/q2python.png)
  
  ## Summary

  The Python visualization in both charts is identical to the Tableau representation.

  Below provide link is Google Collaboraty link which involves python code to recreate the bar Chart : 
  
  https://colab.research.google.com/drive/1Xed_zYWgn-EKVyp6meafUFbWNCMCbFfM?usp=sharing

  

## Extra credit : Complete the full assignment with one of the other datasets.
  
   ### Pre-requisites:

   The goal of this assignment is to propose and implement charts based on questions asked about real-world data. This includes colors, fonts, and any text elements. 
   For each chart, there’s an article describing the chart and an Excel data file.

  ## Description:
  
  * From the assignment instructions, I have choosen Dataset 3 and I have used Table 102 - [Expectation of Life at Birth, and Projections] and Table 107 - [Death Rates by Age, Sex, and Race]
  * As mentioned, To create charts I must use different idioms and data visualization tools.
  * I employed Tableau as my data visualization tool to answer the questions with appropriate charts.

 # DATASET 3
 

  ## Q1 : Using Table 102, compare life expectancy for people born between 1970-1999 for the four categories, "Male", "Female", "White", "Black".

  ## Data Handling
  
  I altered Table 102, which contains information on the life expectancy for those born between 1970–1999 in the following four categories: "Male," "Female," "White," and "Black," prior to making the chart. 
  I made few modifications to dataset to create suitable chart.

  In order to compare life expectancy for those born between 1970 and 1999 for the four categories of "Male," "Female," "White," and "Black," I created a chart using Tableau. I uploaded excel file in tableau and labeled year on  x-axis 
   and measure values on y-axis.
  To acquire the desired result, I have filtered the properties in the measure values.

  Modified file for q1 : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Table102.xls

## Idiom : LineChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Year|key, Categorical| horizontal position on a common scale (x-axis) |
| Measure Values |value, quantitative | vertical spatial region (y-axis) |
| Measure Names | Categorical | Color hue | 


### Answer 

I used Line Chart to represent the data, a line chart is often considered best for displaying data trends because it effectively shows the relationship between data points through continuous lines, making it easier to visualize patterns, changes, and trends over time. Here I used the years 1970-1999 to generate multiple line chart. I used different colours for each line to make it easy to understand.

Image for line Chart for q1 :

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/lcq1.jpeg)


#### Tableau workbook link for linechart for Q1

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/ds3q1.twb


## Q2: Using Table 107, compare infant mortality rates (under 1 year) for these same categories between 1980-1999.

## Data Handling

Before creating the chart I made some changes in the table 107 which have details about infant mortality rates (under 1 year) for these same categories between 1980-1999.
I made some changes to the dataset to make it appropriate for creating the chart. 

In this question they asked compare to compare infant mortality rates (under 1 year) for these same categories between 1980-1999, to answer this question I have used Tableau for creating chart. First I uploaded the modified file into Tableau. Then, I have selected year table in this data and dropped it in the row section. After that have selected Measure Names Table and Measure values attribute and dropped them in the columns section. I have filtered the attributes in the measure values to get the output I desire.

Modified excel file for q2 : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Table107.xlsx

## Idiom : LineChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Year|key, Categorical| horizontal position on a common scale (x-axis) |
| Measure Values |value, quantitative | vertical spatial region (y-axis) |
| Measure Names | Categorical | Color hue | 

### Answer

I used Line Chart to represent the data, a line chart is often considered best for displaying data trends because it effectively shows the relationship between data points through continuous lines, making it easier to visualize patterns, changes, and trends over time.Here I used the years 1980-1999 to generate multiple line chart. I used different colours for each line to make it easy to understand.

Image for linechart for Q2

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/lcq2.jpeg)


#### Tableau workbook link for linechart for Q2

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/ds3q2.twb


## Further questions

Q1 : What are the disparities in life expectancy between this generation of males and females? Are there notable differences, and if so, what could be the cause?

Hypothesis: Throughout the whole time, women are probably going to live longer than men. This theory is supported by historical evidence that shows women typically outlive men.

Q2 : Did any public health campaigns or changes in policy occur during this time that would have affected the infant death rates in these categories?

Hypothesis: Take into account the possibility that the adoption of measures meant to lower infant mortality rates—like better access to prenatal care and newborn health programs—may have had a favorable impact on the rates, particularly in some groups.


## References

https://seaborn.pydata.org/generated/seaborn.lineplot.html

https://towardsdatascience.com/tagged/data-visualization

https://realpython.com/python-matplotlib-guide/





  







