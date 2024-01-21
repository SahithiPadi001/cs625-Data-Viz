HW 3, CS 625, Fall 2023
================
Sahithi Padidela

Oct 5,2023

### Pre-requisites:

The goal of this assignment is to give you experience with multiple
visualization tools by creating charts as closely as possible. This includes colors, fonts, and any text elements. 
For each chart, there’s an article describing the chart and an Excel data file.

## Description:
From the assignment instructions, I have choosen Section 1: Population Dataset.  As mentioned, To create charts I must use different idioms and data visualization tools.
I employed Tableau as my data visualization tool to generate a bar chart, scatterplot, and multiple line chart.


## Idiom : BarChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Language| key, categorical | horizontal position on a common scale (x-axis) |
| Number | value, quantitative | vertical spatial region (y-axis) |


##  Data
For Barchart , I have used Table 53 -[ Languages spoken at Home by Language:2009].First,I downloaded the excel data from the git link and uploaded the excel file into Tableau.I manually removed the unnecesary data  and null values from the dataset.I have filtered the attributes to get the output I desire.I used Language(Attribute) on the x-axis and Number(Attribute) on the y-axis to display BarChart from this dataset

 Modified Excel File : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/12s0053%20.xls

In summary, It takes two attributes - Languages and Numbers to generate barchart with the language on x-axis and Number on y-axis and adds titles and labels to complete the visualization. Below provided screenshot contains the bar chart that is created using the dataset from section1[Table-53].

 #### Screenshot for barchart: 
 
 ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/screenshotbar.png)

 #### Tableau workbook link for barchart:
 
 https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Barchart2.twb

 
 ## Idiom  : Scatter Plot


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Age | key, categorical |  horizontal position on a common scale (x-axis) |
| Measure Values | value, quantitative |vertical spatial region (y-axis) |


## Data 

For ScatterPlot, I have used  Table 08 [Intercensal  resident Population by sex and Age]. I used Tableau for this chart.I downloaded excel sheet from the link and again uploaded the excel file into tableau. The dataset contains population data categorized by age groups over a span of 10 years. 
Each row represents an age group, and each column represents the population count for that age group in each of the 10 years. I have used Age  on X-axis and Measure Values on y-axis.

 * The Age (Attribute) contains a range of ages, from less than five years to more than 85 years.
 * We have Years(Attribute), with a period range of 2000 to 2009.
   
 Modified Excel File : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/12s0008.xls

## Customizations
 * I have choosen the Age group from Year 2000 to avoid the messy graph.
 * The dot size should be increased to make the points more visible.

Below provided screenshot contains the Scatterplot that is created using dataset from section 1[Table-08].

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/screenshotscatter.png)

### Tableau workbook link for Scatter plot: 

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/scatterplot2.twb

 ## Idiom : Mutiple LineChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Age | key, categorical | horizontal position on a common scale (x-axis) |
| Measure Values | value, quantitative | vertical spatial region (y-axis) |


## Data
 For Mutiple Line Chart, I have used  Table 72 [Persons living alone by sex].I used Tableau for this chart.I downloaded excel sheet from the link and again uploaded the excel file into tableau. This dataset appears to be a tabular dataset representing various demographic age groups over a span of several years.I have used Age(Attribute) on x-axis
 
 * Years: The dataset spans from 1985 to 2009, covering a period of 25 years.
 * Age Groups: The dataset is segmented into different age groups. The age groups range from 15 years and 75 years and more.

 Modified Excel File : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/12s0072.xls

## Customizations 
* I used the years 1985, 1995, 1999, 2003, and 2009 to generate multiple charts.
* I differentiated each line using different colours to get easily understand.

Below provided screenshot contains the Mutiple linechart that is created using dataset from section 1[Table-72].

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/screenshotline.png)

### Tableau worbook link for Mutiple Line Chart

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/linechart3.twb


# Reflection 

## BarChart

Using the guidelines provided, we must use a different tool to recreate the chart.
To recreate the chart, I first obtained the same Excel dataset[Table -53 Languages spoken at Home by Language:2009] from the github link.
Then, In order to make some adjustments to the dataset, i uploaded it to my google drive.I accessed dataset from drive and modified without unneccesary data.
I used python  to recreate bar chart from Table 53. I have entered the values manually in the code to avoid messy data from the dataset and to get more clarity.

Below provided screenshot contains the code for recreating barchart

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/recreatess.png)

## Data 

* The data dictionary contains two lists: "Language" and "Number."
* I have used Language attribute on X- axis and Number attribute on y-axis.

 Below provided screenshot contains the bar chart that is recreated using the dataset from section1[Table-53].
 
![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/ssbarchart1.png)

  Below provide link is Google Collaboraty link which involves python code to recreate the bar Chart.
  
  https://colab.research.google.com/drive/1dMbnfWraW1lRRTMFI_pbK3c7dAfPn8C0?usp=sharing
  

## Plot

* print(df) imports the dataset from the drive.
* df = pd.DataFrame(data): This line converts the data dictionary into a pandas DataFrame.
* df["Number"] = df["Number"].str.replace(',', '').astype(int): This line cleans the "Number" column by removing commas and converting the values to integers.
* plt.xlabel("Language"): Adds a label to the x-axis.
* plt.ylabel("Number"): Adds a label to the y-axis.
* plt.tight_layout(): Ensures that labels and elements fit within the figure.
* plt.show(): Displays the bar chart.

# References 
* https://chat.openai.com/c/c2c35d34-1e8d-4c50-9008-3a9fe5b60f8f
* <https://vega.github.io/tableau/docs/line.html>



  











