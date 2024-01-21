HW 5, CS 625, Fall 2023
================
Sahithi Padidela

Nov 8, 2023

### Pre-requisites:  

The goal of this assignment is to gain experience creating distribution charts (histogram, eCDF, boxplot) and using them to help guide further analysis of the underlying data.

### Part 1: Create Distribution Charts

### Data Manipulation

From the assignment instructions, I have choosen "Dataset 1" and I have used Table 12 - Resident Population--States. 
Before working on the charts,I had to take the essential columns out of the dataset before I could make the charts. 
I have excluded the District of columbia from all the datasets as per the instructions.
I created a second CSV file called "dataset1.csv" and stored the required columns(1980 , 2000(July) , 2008) in xls.

Modified excel file :

https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/dataset1.csv

### Dataset 1

To start the analysis, create a boxplot, eCDF, and histogram for the distributions described below using  Vega-Lite, or Python.

## Boxplot

### Q1  Boxplot : Show the distributions of the population of all states in 1980, 2000 (either April or July), and 2008.

A Boxplot is a simple way to visualize data distribution across quartiles. Box plots can be drawn horizontally or vertically. 
Although Box Plots appear crude in comparison to a Histogram or Density Plot, they have the advantage of taking up less space, which is useful when comparing distributions across multiple groups or dataset. 
I made use of the three columns pertaining to the population of every state in 1980, 2000(July), and 2008.
It allows for easy comparison and identification of particular state populations for in-depth research by allowing the user to hover over the data points and explore population statistics for each state throughout a variety of years. The graphic aid proficiently illustrates the fluctuations and shifts in the population sizes of the states across the chosen triennial interval.

The boxplot shows the population distribution of all the states in 1980, 2000 and 2008.

Image for boxplot : 

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/boxplotq1.png)

## Executed code for creating boxplot : 

```
lengths = [len(dataframe['1980']), len(dataframe['2000']), len(dataframe['2008'])]
dataframe = pd.DataFrame(dataframe)

# Generate the boxplot
plt.figure(figsize=(8, 6))
dataframe.boxplot(column=['1980', '2000', '2008'])
plt.title('Population Distribution of States in 1980, 2000, and 2008')
plt.ylabel('Population')
plt.xticks(ticks=[1, 2, 3], labels=['1980', '2000', '2008'])
plt.show()
```


## Plot

**lengths = [len(dataframe['1980']), len(dataframe['2000']), len(dataframe['2008'])]** : This line creates a list called lengths to store the number of states for each year (1980, 2000, and 2008). It calculates the length (number of rows) of each dataset within the DataFrame for those specific years.

**plt.figure(figsize=(8, 6))** : This sets up a Matplotlib figure with a specified size of 8x6 inches where the boxplot will be displayed.

**dataframe.boxplot(column=['1980', '2000', '2008'])** : This creates a boxplot for the columns '1980', '2000', and '2008' within the DataFrame. The boxplot shows the distribution of population data for these years across the states.

**plt.title('Population Distribution of States in 1980, 2000, and 2008')** : Sets the title of the boxplot to 'Population Distribution of States in 1980, 2000, and 2008'.

**plt.ylabel('Population')** : Labels the y-axis as 'Population'.

**plt.xticks(ticks=[1, 2, 3], labels=['1980', '2000', '2008'])** : Sets the positions and labels for the ticks on the x-axis. It labels them as '1980', '2000', and '2008'.

**plt.show()** : Finally, this command displays the boxplot on the screen for you to see and analyze.


## Advantages 

* Population Trend Identification : Boxplots can be used to identify trends in the growth or stability of a state's population over time. It makes possible to identify states where population levels are comparatively steady, 
   growing, or declining steadily.

* Clear Comparison :  For different states, boxplots make it easier to compare population distributions visually across several years (e.g., 1980, 2000, 2008). As a result, variations in the median, spread, and outliers may be quickly 
   identified.


## Disadvantages

* Comparing multiple categories or subgroups within a single box plot can be complex. When comparing multiple groups or categories in a single box plot, the boxes may overlap, making it difficult to discern differences between them.
  
* Boxplots provide an oversimplified representation of the data's distribution, which may obscure intricate distribution patterns and the subtle differences in population between states.

## Observations

- From 1980 to 2008, the box plot shows that most states saw overall population growth. The boxes' upper and lower hinges, which correspond to the 25th and 75th percentiles, have moved upward to represent this growth.

- Certain states stand out as outliers in 2000 and 2008, with populations that are significantly larger than the majority. This suggests that certain states either had significant population growth or have consistently higher populations.
  
  
## Q2   eCDF and histogram : Show the distribution of the population of all states in one of the years (your chart title must indicate which year)

#### Description:

The provided code uses Python libraries - Matplotlib, Seaborn, and Pandas - to create visual representations of the population distribution among the states in the year 1980.


## eCDF 

An ECDF is an estimator of the Cumulative Distribution Function. The ECDF essentially allows you to plot a feature of your data in descending order and see the entire feature as if it were distributed across the data set.

The following eCDF shows the distribution of the population of all states in 1980.

Image for eDCF : 

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/ecdf.png)

## Executed code for creating eCDF

```
# Plot eCDF
plt.figure(figsize=(8, 6))
sns.ecdfplot(population_1980)
plt.title('Empirical CDF of Population in 1980')
plt.xlabel('Population')
plt.ylabel('Cumulative Probability')
plt.grid(True)
plt.show()

```
### Plot 

**sns.ecdfplot(population_1980)** : This line uses Seaborn, a data visualization library, to create an ECDF plot for the population_1980 data. 

**plt.grid(True)** : This command adds gridlines to the plot for better readability.


## Advantages 

-  ECDF plot provides a complete overview of the population data for the year 1980. Each point on the plot represents a specific state's population, allowing you to see the distribution of populations across the entire range.

- The ECDF plot can help identify whether the data is skewed to the right (positively skewed) or left (negatively skewed) based on the curve's direction.

## Disadvantages 

-  ECDFs do not provide bin information, which can be useful for certain types of analysis. For example, if I  wanted to see how many states fall within specific population ranges, you'd need a histogram or a bar chart.
  
-   ECDF plot may not be the most efficient tool. For example, determining the population of states in the middle 50% range would require visual estimation from the plot.

## Observations 

* The eCDF plot visualizes the cumulative probability distribution of population sizes for all states in the year 1980.

* The curve demonstrates the distribution and density of state populations across different population sizes, highlighting the spread of state sizes in 1980.

## Histogram 

The following Histogram shows the distribution of the population of all states in 1980.

Image for Histogram :

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/histogram.png)

## Executed code for creating Histogram 

```
# Plot histogram
plt.figure(figsize=(8, 6))
plt.hist(population_1980, bins=7, color='brown', edgecolor='black')
plt.title('Histogram of Population in 1980')
plt.xlabel('Population')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()
```

### Plot 

**plt.hist(population_1980, bins=7, color='brown', edgecolor='black')** : The code creates a histogram of the population data for the year 1980, dividing it into 7 bins, with brown bars and black edges to represent the distribution of 
    state populations.

## Advantages  

 - Histograms showcase the frequency distribution of values within specified intervals, allowing for detailed analysis of the occurrence and density of population sizes within those intervals.
   
 - They allow us to see how state populations in 1980 are distributed across different population ranges, providing insights into the concentration and spread of population values.

## Disadvantages 

 - Histograms group data into bins, which can lead to a loss of detail about individual data points. If I have specific information about a particular state's population, I won't see it in the histogram.
 - The interpretation of the distribution can vary based on the choice of bin size, potentially leading to different interpretations or missing out on particular details in the distribution pattern of population sizes across states and 
     years.

## Observations

- The histogram showcases the frequency distribution of population sizes among the states in 1980.
- It displays how many states fall within specific population ranges or intervals.
- The bars heights represent the count or frequency of states within each population range, providing insights into the distribution pattern of state populations in the chosen year.

# Part 2 : Further Analysis

   ### Findings from boxplot
  
   ### Observation of Boxplots : 

- Initially, I have examined the boxplot showing population distributions across 1980, 2000, and 2008 for all states.
- The boxplot allowed a comparison of population changes over these years, providing an overview of the range, median, quartiles, and presence of outliers for each year.
- By focusing on the specific states in the boxplot, significant differences in population growth between 1980 and 2008 could be observed, indicated by the shift in medians and changes in the boxplot’s spread and whiskers for these 
    states across the years.

## Finding1 : Identifying population growth for california

     I noticed that California had a significant increase in population from 1980 to 2008. To investigate this further, I created a line chart to visualize the population changes in California over the years from my dataset.

## Description 

   The code generates the linechart that compares the population of california across three different years (1980, 2000, and 2008). The data is organized into a Pandas DataFrame, enabling a clear representation of population changes 
   over time for the specified state.By plotting the data using a line chart, the visualization distinctly showcases the population growth for the selected state over the indicated years. The x-axis represents Year and Y- axis 
   represents population of california.

   This chart shows that California's population steadily increased over the years, indicating substantial population growth. The use of a line chart helped in tracking this growth over time.

   Image for linechart :
   
   ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/linechartf1.png)

## Executed code for creating Linechart
  
```
import matplotlib.pyplot as plt
dataframe = pd.DataFrame(dataframe)

# Data for California from the dataset
years = [1980, 2000, 2008]
selected_state = "California "
if selected_state in dataframe['State'].values:
state_population = dataframe.loc[dataframe['State'] == selected_state].iloc[0, 3:]

# Create a line chart
plt.plot(years, population_california, marker='o', linestyle='-', color='b')
plt.xlabel('Year')
plt.ylabel('Population of california')
plt.title('Population Growth in California')
plt.grid(True)
plt.show()

```

## Plot 

**plt.plot()** is used to create a line chart.Years is the x-axis, and state_population is the y-axis.

**plt.grid(True)** adds grid lines to the plot.

**plt.show()** is called to display the line chart.

## Advantages 

-  Line charts excel at illustrating trends over a continuous range, making it easy to observe how California's population has changed over the years (1980, 2000, 2008).
  
-  The chart allows for a straightforward comparison of population data for different years on a single plot. This makes it easy to observe the growth trajectory or any deviations.

## Disadvantages 

- Line charts may place too much emphasis on trends, potentially overshadowing individual data points. This can be a drawback if there are specific years with unique characteristics that are not clearly visible in the overall trend.
  
- Line charts can be sensitive to outliers, and a single extreme data point can disproportionately impact the visual representation of trends. This sensitivity might obscure the overall pattern.

## Observations

 - The chart clearly indicates significant population growth of california over the three indicated years.
   
 - The population more than doubled from 1980 to 2008, as evident from the steep upward slope of the line.

   ## Finding2 : Population comparision for the year 2008

   Let's start by creating a bar chart to compare the populations of the states in the year 2008. This bar chart allows you to visually compare the populations of different states in 2008.

   ## Description

   The code generates the barchart that compares the population of all states for the year 2008. The data is organized into a Pandas DataFrame, enabling a clear representation of population changes 
   over time for the specified state. By plotting the data using a bar chart, the visualization distinctly showcases the population growth or decline trends for the selected states over the indicated year.
   The x-axis represents Population in 2008 and Y- axis represents states.

   Image for Barchart :

   ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/barchartf2.png)

   ## Executed code for creating Barchart
   
    ```
   import matplotlib.pyplot as plt
   import pandas as pd
 
   # Select the year 2008 data
   population_2008 = dataframe['2008']
   dataframe_sorted = dataframe.sort_values(by='2008', ascending=True)

   # Define the states and their corresponding populations for 2008 from the sorted DataFrame
   states_sorted = dataframe_sorted['State']

   # Create a bar chart for population comparison in 2008
   plt.figure(figsize=(8, 6))
   plt.barh(states_sorted, population_2008[dataframe_sorted.index], color='brown')
   plt.xlabel('Population in 2008')
   plt.ylabel('States')
   plt.title('Population Comparison 2008 (Descending Order)')
   plt.grid(axis='x', linestyle='--', alpha=0.6)
   plt.show()

   ```

## Plot


  **dataframe_sorted = dataframe.sort_values(by='2008', ascending=True)** : Sorts the original DataFrame (dataframe) based on the population in the year 2008 in ascending order. 
  
  **states_sorted = dataframe_sorted['State']** : Extracts the 'State' column from the sorted DataFrame and assigns it to the variable states_sorted.
  
  **plt.barh(states_sorted, population_2008[dataframe_sorted.index], color='brown')** : Creates a horizontal bar chart (barh) with states on the y-axis, population on the x-axis, and the bars colored in brown.


## Advantages

   -  Bar charts offer a straightforward comparison of population sizes between different states over multiple years, allowing for a clear visual understanding of the growth or decline trends.
   
   -  The use of bars enables a direct emphasis on the magnitude of population change, providing a visual impression of the extent of growth or decline. 

## Disadvantages
   
  -  Bar charts might oversimplify more intricate population distribution details, restricting the visualization to categorical representations of population sizes without detailed insights into the entire distribution.
  
  -  When comparing multiple years for several states, the visualization might become crowded or complex, potentially making it difficult to discern specific trends or patterns for each state.

## Observations

- The bar chart clearly illustrates the significant disparities in population among states in the year 2008.
  
- The states on the right side of the chart have the largest populations in 2008. California, Texas indicating higher populations.
- 

  ## Below provide link is Google Collaboraty link which involves python code to recreate the bar Chart :
  
   https://colab.research.google.com/drive/1Vo1mx3l2YLhtvwZUOUXWZemHna0CFPwo?usp=sharing
  

  ## References

   https://datavizcatalogue.com/methods/box_plot.html
  
   https://towardsdatascience.com/what-why-and-how-to-read-empirical-cdf-123e2b922480

   https://edwinth.github.io/blog/outlier-bin/
  










