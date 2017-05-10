---
layout: essay
type: essay
title: "Big Data"
date: 2017-05-04
labels:
  - Software Engineering
  - Big Data
  - Big Data Algorithms
---

# Big Data#
Big data is a term that is often used to describe large sets of collected data that can either be structured or unstructured in nature. These data sets are commonly processed and used to create models, make predictions or make smarter decisions. [1] Three terms are commonly referenced when describing big data, volume, velocity and variety.

Volume describes the sheer amount of data that is collected. Many data points from even a single event can recorded, stored and processed. Large server centers and supercomputers are commonly used to process the large quantity of data. [2]

Velocity describes the high frequency in which data is being collected and stored. Because of large scale sensor networks and the ever growing amount of interactions that occur over time, infrastructure needs to be in place to deal with fast flowing and time-sensitive data. [2]

Variety describes the various data formats and types that can be collected. Data types can range from numerical, strings, to even audio or video files. This large variety of data allows us to make sophisticated predictions and decisions on a deeper level than ever before. [2]

Section 2 of this report will discuss the applications of big data and its relationship with the Internet of Things (IoT). Section 3 of this report will discuss algorithms that are used to process and make decisions from big data. Section 4 of this report will contain my conclusions.

# Section 2 - Applications of Big Data#
Big data has a lot of applications, frequently in the background of our lives. Approximately 2.5 quintillion bytes of data is produced every day. [3] This turns out to be approximately 340 megabytes of data for each person on Earth right now.

The first application of big data is in social media. As you can imagine, social media can generate large networks of friends and connections as well as data points such as “likes” or “interests” that are captured and processed every day. The primary issue with collecting data about social media is that the data is unstructured and because of the large volume of data, it isn’t practical or even possible for humans to process all this data.

Also, companies like Facebook or Twitter are not the only ones concerned about big data, the companies that utilize these social media services as advertisement, customer interaction, or their main revenue stream, rely on data to make educated decisions and predictions about the future. [4]

For example, if a company monitors a twitter handle for comments that are made about its new line of products, certain keywords such as “great” or a smiling emoji in a tweet is a good indicator that that particular customer was satisfied. By monitoring the vast amount of tweets, a company can get an idea if the population generally favors or disfavors its new product.

The second application of big data is within sports, more specifically in baseball. The analytics of big data is commonly referred to as Sabermetrics. Every pitch and the resulting play has been recorded for every single one of the 162 baseball games per season by each of the 30 teams since 1876.

The first instance of Sabermetrics being put in the eye of the public was in 2002. The Oakland Athletics coined the term “Moneyball” in which they used big data to find the players that would offer the best statistics for their price. The analytics allows the Athletics to finish in first place in the American League West winning a total of 103 games. This concept of Moneyball took Major League Baseball by storm and started a revolution that other teams soon follow suit. [5]

Baseball statistics like Wins over Replacement [Player] (WAR) or On-Base-Plus-Slugging Adjusted for Park (OPS+) are stats that literally quantify a player’s ability to win games. There is a large community around fantasy baseball that also delve into and use all of this available data to compete and win large sums of money. [6]

In today’s modern game, nearly all teams have statisticians and access to the big data that they apply to their defensive formations, team lineups, and pitching changes. Almost every single move is carefully calculated and weighed with influence of big data, significantly different than the game used to be played. [7]

The third application of big data is in the financial market, more specifically in the Stock Market. Stocks are rising and falling, buying and selling, and market strengths change nearly every second. There is a large amount of data to analyze. Big data is often used in this case to find trends in stocks, i.e. determine which stocks are on the rise to buy and which are on the fall to sell.

Current data can also be compared to past data in order to create more robust models and make more accurate predictions. Because of the vast amount of data collected over the lifetime of the Stock Market, big data algorithms are frequently used to process and model the large data sets. [8]

The fourth application of big data is in Health Care. More specially, IBM Watson Health is engaged in many projects such as mapping the Human Genome or Personalized Health Patient Engagement.

The interesting thing about the Personalized Health Patient Engagement is that there is integration with the Internet of Things (IoT). Medical sensors such as stethoscopes, pacemakers, and other telemetry devices are used to gather patient data and can be run against the millions of past cases and other doctor’s finding to give you a more educated opinions.

The Internet of Things is a term that is commonly used to describe the vast amount of connected devices that interface with each other and the cloud in order to work together to actuate, predict or gather information. [9] Commonly, large sensor networks are place in the field to gather data such as meteorological data or even proximity data. Because of the large scale and time dependence of some types of data, we can clearly see that this ties into the problems with big data.

The real value in the IoT is the integration of all the data in order to make more educated and large scale decisions and predictions than ever before. Also, with the help of big data, we are able to process large quantities of fast moving and variable data that would be inconceivable otherwise. Many Intelligent Transport Systems (ITS) are implemented in cities that are starting to move towards being “Smart”er such as GPS on buses provided by TheBus. [9]

# Section 3 - Big Data Algorithms#
Hadoop is an open-source software framework that is used to process big data with MapReduce being its primary programming model. Hadoop operates by splitting files into large blocks and distributing them across computing nodes in a cluster of computers. This approach of computing assigns each individual node to process only the data they have access to. This takes advantage of data locality. This essentially allows parallel computing that isn’t bottlenecked by the network connection between nodes. [10]

MapReduce is a programming model that is used by Hadoop in which the procedure is characterized by first a Mapping procedure in which the data is filtered and sorted and a Reducing method that performs a summary operation. Another characteristic is that processing is distributed over servers that run various tasks in parallel in such a manner that is redundant and as a result, fault tolerant. [11]

The typical hardware that these are designed for are multiprocessor systems, clusters of computers, or commercial off the shelf processors in racks. The hardware lends itself to parallel computing and the distribution of tasks across a network.

An example of MapReduce in action is counting the number of words in a novel. Given the input of a novel which is a large set of strings, we can distribute a page or two to each node over a large network of nodes. Each individual node will count the occurrences of each word on a given page and then combine its result with the results from other nodes in order to get a large total.

Another example of MapReduce in action is determining the maxima and minima from a sequence of values. For example, we are given a set of data that quantifies energy uses over various years and we want to determine which year did we use the most and least amount of energy. As a result, we can send the data for a year out to each individual node and have it compute the total energy consumption, then compare the data from other nodes in order to find the maximum and minimum values.

Stream Algorithms are algorithms that are designed to process a stream data with certain restriction on memory or processing time per input data. Because of these constraints, sketches are typically used which are generalizations or a summary of the data stream that is currently in memory.

Morris’ algorithms is an algorithm that looks for a specific substring in an input string by observing when a failed comparison occurs, the word itself has sufficient information to determine where the next match could potentially begin. This allows the algorithm to avoid rechecking previously matched characters.

The count-min sketch problem utilizes a probabilistic data structure in the form of a hash table will less entries that the length of the input. The sketch can then be queried for the frequency of a given event and return an estimate of the frequency within a tolerable error with a certain probability.

The data structure is essentially a two-dimensional array and with each new event arrives we apply the hash function and obtain a column index and use the current row index. The simplest query is a point query in which it asks for the current count of the input event. The estimated count is given by the smallest value in the table for the input event.

# Section 4 - Concluding Remarks#
Overall, big data has contributed largely to the way that we make decisions and predictions. The applications range from social media, Sabermetrics, the Stock Market and Health Care. The wave of the Internet of Things also assist in the gathering and distribution of big data. Because of these, new algorithms needed to be developed such as MapReduce and Stream Algorithms that are specifically designed to process big data.

# References#
[1] S. Insights, B. Insights and W. Data?, "What is Big Data and why it matters", Sas.com, 2017. [Online]. Available: https://www.sas.com/en_us/insights/big-data/what-is-big-data.html. [Accessed: 03- May- 2017].

[2] "Big data", En.wikipedia.org, 2017. [Online]. Available: https://en.wikipedia.org/wiki/Big_data. [Accessed: 03- May- 2017].

[3] "Surprising Facts and Statistics About the Big Data Industry", CloudTweaks, 2017. [Online]. Available: https://cloudtweaks.com/2015/03/surprising-facts-and-stats-about-the-big-data-industry/. [Accessed: 03- May- 2017].

[4] "Forbes Welcome", Forbes.com, 2017. [Online]. Available: https://www.forbes.com/sites/onmarketing/2012/06/28/social-media-and-the-big-data-explosion/#1d90734a6a61. [Accessed: 03- May- 2017].

[5] "2002 Oakland Athletics season", En.wikipedia.org, 2017. [Online]. Available: https://en.wikipedia.org/wiki/2002_Oakland_Athletics_season. [Accessed: 03- May- 2017].

[6] V. &rarr;, "Beyond Moneyball: How Big Data Is Changing Baseball", SportTechie, 2017. [Online]. Available: http://www.sporttechie.com/2014/11/11/sports/mlb/beyond-moneyball-how-big-data-is-changing-baseball/. [Accessed: 03- May- 2017].

[7] F. Page, "MLB Stats, Scores, History, & Records | Baseball-Reference.com", Baseball-Reference.com, 2017. [Online]. Available: http://www.baseball-reference.com/. [Accessed: 03- May- 2017].

[8] "The “Big Data” Solution For Wall Street", Stock Forecast Based On a Predictive Algorithm | I Know First |, 2017. [Online]. Available: https://iknowfirst.com/the-big-data-solution-for-wall-street. [Accessed: 03- May- 2017].

[9] D. Carlson, "Internet of Things (EE 491)", University of Hawaii at Manoa, 2017.

[10] "Apache Hadoop", En.wikipedia.org, 2017. [Online]. Available: https://en.wikipedia.org/wiki/Apache_Hadoop. [Accessed: 03- May- 2017].

[11] "MapReduce", En.wikipedia.org, 2017. [Online]. Available: https://en.wikipedia.org/wiki/MapReduce. [Accessed: 03- May- 2017].
