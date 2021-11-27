---
layout: post
title: "Project A"
date: 2021-11-24T18:26:38+01:00
description: "A little backgroud on what was already discovered during part A"
featured_image: "/images/group.jpg"
draft: false
---
This blog post focuses on providing the full analysis performed during the first part of the project.
### Gathering the Data
To explore The Office, several datasets were used:
- First, all characters that played in the office from the first season to the final one were extracted using [The Offica Wiki (Dunderpedia)](https://theoffice.fandom.com/)
- A description of each character is downloaded from [Dunderpedia](https://theoffice.fandom.com/). The data is used to extract the sentiment of each character and will be later compared to the sentiment extracted from the episodes transcript. We would like to validate that the character description is based on the character development over all seasons.
- Later on, we want to analyse the episode ratings and their change over time. For this, the [IMDB](https://www.imdb.com/title/tt0386676/episodes/_ajax) is used to extract the episode title, the rating, total votes and air date.
- The guests, directors and writers are extracting using [Kaggle data](https://www.kaggle.com/andreal314159/the-office-analysis-for-datacamp/data). This data wil be used to analyse the impact of guests, directors and writers on the ratings.
- For a more in-depth analysis of the episode ratings, a new [Kaggle dataset](https://www.kaggle.com/nasirkhalid24/the-office-us-complete-dialoguetranscript/version/1?select=The-Office-Lines.csv) is used to colect the Complete Dialogue Transcript.

### Basic Statistics
After the data was downloaded, the network was generated and the giant connected component was extracted. Using the NetworkX DiGraph the networks and its properties were stored. During the preliminary analysis performed, the following was descovered:
- The total number of unique characters was found to be 298 (the dataset does not contain any duplicates)
- The total number of nodes is 255 with 17 isolated nodes
- The total number of isolated nodes in graph after removal is equal to 0
- The total number of links was found to be equal with 1196
- The top connected character for the in-degrees is Michael Scott with a degree of 108
- The top connected character for the out-degrees is Andy Bernard with a degree of 33
- The memory usage for all the data is equal to 6.75 MB

#### The in- and out-degree distributions
To plot the binned in and out degree distributions, the binning vector of both degrees was computed and used to create the graphs presented below:
![The in- and out-degree binned distributions](/images/binned_distribution.png)
- The first observation is that the maximum out-degree in almost 4 times smaller than the maximum in-degree, which could have also be seen when finding the top connected characters for the in- and out-degrees, Michael and Andy.
- In the in-degree plots it can be seen that the majority of nodes, nearly 100, have a degree of 0, and the degree ranges until 120. Hence, the distribution shows that a large number of characters point to a smaller number of characters. While in the out-degree plots, the degree distribution changes slower than the in-degree, and the degrees are more concentrated between 0 and 10, in comparison to the in-degree.
- The in-degree distribution is different from the out-degree distribution because of the network's nature. In this network, the link is defined between two characters, A and B, if there exists a hyperlink in character's A page that links to B's page. Popular characters will therefore be linked by a lot of other characters, which can account for higher in-degrees. Therefore, for less popular characters, will have links pointing to other characters, but very little links pointing to them, which can cause the large amount in-degrees close to 0.
- The out-degree might be limited by the page length and the fact that every character includes a low number of hyperlinks on its page.
- After calculating the best minimal values for the power law fit, the exponent of the in-degree sistribution was found to be equal to 1.9982 and the exponent of the out-degree distribution was found to be equal to 2.6148

###### Comparison between the degree distribution of the undirected graph to a random network with the same number of nodes and probability of connection p.
![The Binned degree sistribution](/images/graph_partA.png)
#### Visualization of hte network
![The Office Network](/images/network.png)
