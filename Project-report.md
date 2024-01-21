Semester Project, CS 625, Fall 2023
================
Sahithi Padidela

Dec 11,2023

## Title : Twitter Airline Sentiment in relation to flight delays and cancellations.

## Description :

Flight delays and cancellations are real-world issues that impact millions of travelers. Addressing this topic in a project allows me to contribute to solving practical challenges faced by the aviation industry. Findings from this project can have practical implications for airlines, airports, and policymakers. This insight may contribute to more informed decision-making, improved operational efficiency, and enhanced passenger experiences.

##  Dataset Explanation  

My first dataset has data on flight delays and cancellations for flights withdrawing from US air terminals somewhere in the range of 2004 and 2020. Based on information gathered by the Bureau of Transportation Statistics (BTS), the US Department of Transportation (DOT) developed the dataset. I have taken 1500 segments of information for my representation project. This includes information about the airline, the flight number, the airports of origin and destination, the scheduled and actual times of departure and arrival, the cause of the delay or cancellation, and the length of time it lasted. The dataset also includes information about what caused the delay or cancellation, like mechanical problems or bad weather. By noticing the dataset, we can investigate patterns and examples in flight deferrals and abrogations over the long haul and across various carriers and air terminals.

** Data source : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/flightsdata.csv **


My second dataset is the Twitter Airline Sentiment dataset available on Kaggle. It comprises tweets from February 2015 referencing six different airlines (American, Delta, Southwest, United, US Airways, Virgin America). Human contributors on Crowdflower manually categorized each tweet into one of three sentiment categories: positive, negative, or neutral.


** Data source : https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Tweets.csv ** 

## Refined Question  

What trends emerge in the number of tweets for each airline in the Twitter airline sentiment dataset, and how do these variations manifest across different airline entities? Furthermore, what valuable insights can be extracted by delving into the correlation between sentiment confidence levels and sentiment scores?

** Google collab link  : https://colab.research.google.com/drive/1IGn6SmZjp57_cFRIEhhrfguWJOPD1oeC?usp=sharing  ** 

### Part  1 : 

What trends emerge in the number of tweets for each airline in the Twitter airline sentiment dataset, and how do these variations manifest across different airline entities?

## Idiom : LineChart


| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Dates | key, categorical | horizontal position on a common scale (x-axis) |
| Number of tweets | value, quantitative | vertical spatial region (y-axis) |





The objective is to generate a visualization illustrating the temporal trend in tweet volumes for each airline within the Twitter Airline Sentiment dataset. This involves grouping tweets by both airline and date, tallying the tweet counts. Subsequently, a Line chart can be created, with time on the x-axis, tweet counts on the y-axis, and each airline differentiated by color. This visual representation aims to unveil patterns or shifts in the frequency of tweets related to each airline over time, offering insights into potential fluctuations in public opinion or other factors influencing customer sentiment toward various airlines.

##  Data

The x-axis represents time in the form of dates. 

The y-axis represents the number of tweets.

## Plot 

``` import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('Tweets.csv')

# Convert the 'tweet_created' column to datetime format
df['tweet_created'] = pd.to_datetime(df['tweet_created'])

# Group the data by airline and date
grouped = df.groupby([df['tweet_created'].dt.date, 'airline'])['airline_sentiment'].count().reset_index()

# Pivot the data to have airlines as columns
pivot = grouped.pivot(index='tweet_created', columns='airline', values='airline_sentiment').fillna(0)

# Plot the data
pivot.plot(figsize=(10, 6))

# Set plot title and axis labels
plt.title('Number of Tweets for Each Airline over Time')
plt.xlabel('Date')
plt.ylabel('Number of Tweets')

# Show the plot
plt.show()

```

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/projectlinechart.png)  

## Explanation of Chart

Examining the graph reveals fluctuations in the tweet volumes for each airline over time. United Airlines, US Airways, and American Airlines stand out with the highest overall tweet counts, whereas Virgin America and Delta Airlines received comparatively fewer tweets. Furthermore, notable spikes in tweet volume are noticeable for specific airlines at distinct time points, suggesting a potential correlation with particular events or incidents. Analyzing these patterns provides valuable insights into the dynamics of public engagement and the impact of events on social media discussions about different airlines.The line chart, shows the total number of tweets over time for each airline separately, allowing for easier identification of trends within each airline. However, it does not show the breakdown of tweet sentiment.



### Part 2 

What valuable insights can be extracted by delving into the correlation between sentiment confidence levels and sentiment scores?

## Idiom : Stacked area chart

| Data: Attribute | Data: Attribute Type  | Encode: Channel | 
| --- |---| --- |
| Dates | key, categorical | horizontal position on a common scale (x-axis) |
| Number of tweets | value, quantitative | vertical spatial region (y-axis) |


The objective of this analysis is to delve into and comprehend the correlation between the sentiment confidence level and sentiment score within the Twitter airline sentiment dataset. The sentiment confidence level signifies the degree of certainty in the sentiment classification (positive, negative, neutral) assigned to each tweet. In contrast, the sentiment score reflects the sentiment expressed in the tweets (positive, negative), derived from the sentiment confidence level. This exploration aims to uncover patterns or relationships that can offer insights into the reliability of sentiment classifications and the expressed sentiments in the dataset.In this instance, a stacked area chart has been utilized, similar to a conventional area chart. However, instead of featuring a single line or area, it displays multiple areas layered atop one another. Each distinct area denotes a different category or variable, and the cumulative height of the stack at any specific point is the total sum of values for each category up to that point in the dataset.

## Data

The x-axis represents time (in this case, the date of the tweet)

The y-axis represents the number of tweets.

## Plot 

```
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('Tweets.csv')

# Convert the 'tweet_created' column to datetime format
df['tweet_created'] = pd.to_datetime(df['tweet_created'])

# Group the data by airline, sentiment, and date
grouped = df.groupby([df['tweet_created'].dt.date, 'airline', 'airline_sentiment']).size().unstack().fillna(0)

# Plot the data
colors = {'negative': '#FF3333', 'neutral': '#FF9900', 'positive': '#33FF33'}
grouped.plot(kind='area', stacked=True, color=[colors[col] for col in grouped.columns], figsize=(10, 6))

# Set plot title and axis labels
plt.title('Distribution of Sentiment for Each Airline over Time')
plt.xlabel('Date')
plt.ylabel('Number of Tweets')
plt.xticks(rotation = 45)

# Show the plot
plt.show()

```

The newly derived visulization looks like this which is a stacked area chart

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/areachart.png) 

## Explanation of Chart


Here are several noteworthy observations derived from the stacked area chart I generated:

####  American Airlines and United Airlines:
Both airlines exhibit predominantly negative sentiment overall, evident in the consistently larger red (negative) area throughout the entire time span.

#### Delta Airlines and Southwest Airlines:
These airlines showcase a more balanced distribution of sentiment. While negative tweets exist, there's a notable presence of neutral (blue) and positive (green) tweets in their respective stacks.

#### Temporal Variation in Tweet Volume:
The overall tweet volume fluctuates over time, with noticeable peaks and troughs for all airlines. For instance, a significant surge in tweets is evident around February 23, 2015, suggesting a potential association with a specific event or news story that sparked extensive Twitter conversations.

####  Single-Day Dominance:
Certain days witness one airline dominating the conversation. For example, on February 18, 2015, Virgin America's stack surpasses others, indicating a potential correlation with a specific event or promotion on that particular day.

####  Consistency and Variation in Sentiment:
Each airline's sentiment appears relatively stable over time, with some fluctuations. United Airlines consistently maintains a negative sentiment, though there are days with slightly more positive sentiment. This implies that external factors, such as events or news stories, may influence sentiment, but overall, sentiments for each airline remain fairly consistent.

## Final Thoughts 

Developing the visualizations for the Twitter Airline Sentiment dataset in relation to flight delays and cancellations proved to be an engaging and insightful journey. The process involved careful consideration of the dataset's nuances, exploratory data analysis, and the strategic choice of visualization types to convey meaningful insights.The most time-consuming aspect of the project was the meticulous data preparation. Cleaning and organizing the Twitter Airline Sentiment dataset to ensure accurate representation in visualizations demanded careful attention to detail. Fortunately, Kaggle provides a well-structured dataset, but handling textual data and ensuring consistency in sentiment classifications required thoughtful preprocessing.

In total, the development process, from data preparation to the final visualization implementations, spanned approximately 1 week. This timeframe includes initial exploratory data analysis, multiple iterations of visualization development, and refining visual elements for clarity.Reflecting on the project, the investment in time was well worth the outcome. The visualizations not only provide a clear representation of tweet trends and sentiment dynamics but also serve as a tool for storytelling, enabling stakeholders to grasp key insights from the Twitter Airline Sentiment dataset effectively. This project reinforced the importance of the iterative process in data visualization, where each iteration brings improved clarity and depth to the final visual representations.


** The approriate headline that I could think of for this is:  "Exploring Twitter Sentiment: Comparative Analysis of Five Major Airlines Through Stacked Area Charts"  **

## Visualization principles

The code adheres to several essential visualization principles:

Appropriate Chart Type: A stacked area chart effectively communicates changes in tweet quantity over time, enabling the comparison of multiple airline categories.

Appropriate Color Scheme: A thoughtfully chosen color scheme assigns distinct colors to each airline, facilitating easy differentiation and enhancing visual appeal.

Simplified Chart: Unnecessary elements such as legends, borders, and shading are removed, resulting in a simplified chart that reduces visual clutter and improves readability.

Clear and Concise Labels: Clear and concise x-axis and y-axis labels communicate the measured variable and its unit, contributing to enhanced clarity.

Clear and Concise Title: The chart's title is succinct and transparent, effectively conveying the primary message without unnecessary complexity.

Appropriate Font Sizes and Styles: Deliberate choices in font sizes and styles optimize readability, emphasizing important elements like the title and axis labels.

Providing Context: Data labels accompany the chart, offering additional context about the displayed data and assisting readers in understanding its implications.


## **Annotations: **


I started by importing necessary libraries such as pandas for data manipulation and matplotlib for visualization. Then, I loaded the 'Tweets.csv' dataset into a Pandas DataFrame and converted the 'tweet_created' column to a datetime format for better time-based analysis.Next, I grouped the data by airline and date, counted the number of tweets for each group, and organized the result into a pivoted DataFrame. Using this pivoted data, I created a stacked area chart to visualize tweet trends over time for different airlines.To enhance the chart's appearance, I added a title, x-axis and y-axis labels, adjusted font sizes, and introduced grid lines for clarity. Finally, I included data labels by iterating over each column in the pivoted DataFrame, annotating the chart with column names and their respective sums at the last data point.


## Conclusion 

In summary, the stacked area chart effectively conveys the temporal distribution of tweets for each airline. The implementation of visualization principles, including an apt color scheme, simplified design, clear labels, and informative data labels, enhances the chart's visual appeal, readability, and informational value. Noteworthy findings from the chart reveal that Southwest Airlines received the highest tweet volume, followed by American Airlines and Delta Airlines. This underscores the significance of social media monitoring for airlines, offering insights into customer sentiment and areas for service improvement. Overall, this chart exemplifies the power of data visualization in presenting intricate information in a straightforward and impactful manner.

## References 

 Kaggle : https://www.kaggle.com/usdot/flight-delays
 
 Kaggle :  https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment
 
 https://medium.com/@rtripath/sentiment-analysis-of-airline-tweets-using-bert-830d06148822
 
 https://brand24.com/blog/search/sentiment+analysis


























 






