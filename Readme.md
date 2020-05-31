# The Battle of the Neighborhoods - Report

## 1. Introduction & Business Problem

### Problem Background

The City of New York, is one the most populous city in the United States with cultural diversity and vivid economic activities. This provides both business oppourtunities and business friendly environment, attracting many different players into the market.

Such inviting environment introduces strong competitions between existing business and new entries. Thus, any new business venture or expansion needs to be analysed carefully. The insights derived from analysis will give good understanding of the business environment which help in strategically targeting the market. This will help in reduction of risk. And the Return on Investment will be reasonable.

### Problem Description

A restaurant is a business which prepares and serves food and drink to customers in return for money, either paid before the meal, after the meal, or with an open account. The City of New York is famous for its excelllent cuisine. It's food culture includes an array of international cuisines influenced by the city's immigrant history.

1. Central and Eastern European immigrants, especially Jewish immigrants - bagels, cheesecake, hot dogs, knishes, and delicatessens
2. Italian immigrants - New York-style pizza and Italian cuisine
3. Jewish immigrants and Irish immigrants - pastrami and corned beef
4. Chinese and other Asian restaurants, sandwich joints, trattorias, diners, and coffeehouses are ubiquitous throughout the city
5. mobile food vendors - Some 4,000 licensed by the city
6. Middle Eastern foods such as falafel and kebabs examples of modern New York street food
7. It is famous for not just Pizzerias, Cafe's but also for fine dining Michelin starred restaurants.The city is home to "nearly one thousand of the finest and most diverse haute cuisine restaurants in the world", according to Michelin.

So it is evident that to survive in such competitive market it is very important to startegically plan. Various factors need to be studied inorder to decide on the Location such as :

1. New York Population
2. New York City Demographics
3. Who are the competitors in that location?
4. Segmentation of the Borough
5. Untapped markets
6. Saturated markets etc

Eventhough well funded XYZ Company Ltd. need to choose the correct location to start its first venture.If this is successful they can replicate the same in other locations. First move is very important, thereby choice of location is very important.

### Target Audience

To recommend the correct location, XYZ Company Ltd has appointed me to locate and recommend to the management which neighborhood of New York city will be best choice for starting a restaurant venture. The Management also expects to understand the rationale of the recommendations made. This would also interest anyone who wants to start a new restaurant in Newyork city.

### Success Criteria

The success criteria of the project will be a good recommendation of borough/neighborhood choice to XYZ Company Ltd based on Lack of such restaurants in that location and nearest suppliers of ingredients.

## 2. Data

One city will be analysed in this project : **Newyork City**.

We will be using the below datasets for analysing Newyork city.

***Data 1 :*** New York City has a total of 5 boroughs and 306 neighborhoods. This dataset exists for free on the [web](https://geo.nyu.edu/catalog/nyu_2451_34572).

***Data 2 :*** Newyork city geographical coordinates data will be utilized as input for the Foursquare API, that will be leveraged to provision venues information for each neighborhood.We will use the Foursquare API to explore neighborhoods in New York City.

## 3.Methodology

### Business Understanding

Our main goal is to get the optimum restaurant category for a new restaurant business in New York City for XYZ Company Ltd.

### Analytical Approach

New York city neighbourhood has a total of 5 boroughs and 306 neighborhoods. In the first part of this project, we will filter the results from Foursquare to narrow down to only catering-related locations. Clustering algorithm will then be applied onto the curated dataset. To locate the best parameters, Elbow method will be used to avoid overfitting and underfitting where possible. We will then look into the compositions of each of the neighbourhood and identify the type of restaurants for the entry strategies.

### Exploratory Analysis

***Data 1 :*** New york city Geographical Coordinates Data.

1. In this we load the data and explore data from newyork_data.json file.
2. Transform the data of nested python dictionaries into a pandas dataframe.
3. This dataframe contains the geographical coordinates of New York city neighborhoods.
4. This data will used to get Venues data from Fouresquare.
5. We used geopy and folium libraries to create a map of New York city with neighborhoods superimposed on top.

|    | name        |   stacked | borough   | geometry                                     |   Longitude |   Latitude |
|---:|:------------|----------:|:----------|:---------------------------------------------|------------:|-----------:|
|  0 | Wakefield   |         1 | Bronx     | POINT (-73.84720052054902 40.89470517661)    |    -73.8472 |    40.8947 |
|  1 | Co-op City  |         2 | Bronx     | POINT (-73.82993910812398 40.87429419303012) |    -73.8299 |    40.8743 |
|  2 | Eastchester |         1 | Bronx     | POINT (-73.82780644716412 40.88755567735078) |    -73.8278 |    40.8876 |
|  3 | Fieldston   |         1 | Bronx     | POINT (-73.90564259591682 40.89543742690383) |    -73.9056 |    40.8954 |
|  4 | Riverdale   |         1 | Bronx     | POINT (-73.9125854610857 40.8908344938913)   |    -73.9126 |    40.8908 |

[](https://github.com/louixchan/Coursera_Capstone/blob/master/images/Picture1.png)

***Data 2 :*** Foursquare dataset.

1. There are a total of 9,905 locations returned for the 306 Neighbourhoods
2. The 9,905 locations contain a total of 429 categories
3. Of the categories, 48 of them are catering-related
4. The filtered dataset contains 2,437 locations across the 306 Neighborhoods

The most common restaurant categories are as follows:

|                                 |   Venue Category |
|:--------------------------------|-----------------:|
| Pizza Place                     |              436 |
| Coffee Shop                     |              304 |
| Bakery                          |              226 |
| Café                            |              172 |
| Donut Shop                      |              165 |
| Ice Cream Shop                  |              137 |
| Bagel Shop                      |              108 |
| Fast Food Restaurant            |               94 |
| Diner                           |               90 |
| Burger Joint                    |               80 |

## 4. Results

**Neighborhood K-Means clustering based on mean occurrence of venue category:**

To cluster the neighborhoods into two clusters we used the K-Means clustering Algorithm. k-means clustering aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean. It uses iterative refinement approach. In order to obtain the optimal settings, `KElbowVisualizer` from `yellowbrick` has been used. From the visualisation below, we can see that the optimal settings is at `k=12`, i.e. 12 clusters.

[](https://github.com/louixchan/Coursera_Capstone/blob/master/images/Picture3.png)

**Interpretation of Clustering Results:**

By looking into the restaurant compositions of the individual neighborhoods, there are two main groups of clusters, one that is located closer to the city centre, with a higher proportion of café and coffee shop related restaurants, while the other is on the fringe which has a higher pizza place proportion. This shows essentially two different strategies, one for the city centre with potentially more office-targeted while the other one is for the outskirt which is more takeaway or fastfood focused.

[](https://github.com/louixchan/Coursera_Capstone/blob/master/images/Picture2.png)

**Cluster 0, 2, 3, 4**
[](https://github.com/louixchan/Coursera_Capstone/blob/master/images/Picture4.png)

**Cluster 1, 5, 6, 7, 8**
[](https://github.com/louixchan/Coursera_Capstone/blob/master/images/Picture5.png)

## 5. Discussion

1. Scope of refinement: Revise Foursquare categories
   Some of the categories may be too specific and can be grouped into a more general category to avoid overfitting
2. Introduce work demographics and residential demographics to the algorithm
3. Introduce NLP elements on restaurant menu to extract affordability and cuisine related data

## 6. Conclusion

This analysis is performed on limited data, hence a relatively width confidence interval. But if good amount of data is available there is scope to come up with better results. If there are lot of restaurants probably, there is lot of demand. In general, Café seems to be a more viable strategy for the city center while Pizza place is more towards the outskirt of it.
