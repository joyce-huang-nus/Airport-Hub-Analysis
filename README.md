# Airport-Hub-Analysis
In this report, we analyzed the flight network worldwide. Through time series and network analytics, we investigated how the travel networks have been affected by the virus and the restrictions. However, lately as the restrictions are gradually lifted in many countries, we are expecting a recovery in tourism industry. By studying the travel networks in different stages of the regulations, hubs are identified. Coupled with the COVID policies in various countries, we aimed to optimize the airline travel operations to satisfy the needs of the newly revived tourism.


## Data Source
The main data source for this analysis is the open dataset from the OpenSky Network (1). This dataset contains flight records within certain timeframes, including information such as the departure and arrival airport and time, aircraft types, and airline code, as well as the geolocation of the aircraft.

## Exploratory Data Analysis 
![image](https://user-images.githubusercontent.com/88580416/161209197-097e16a7-2bfa-4ebd-8b4f-8ded467bf2f3.png)![image](https://user-images.githubusercontent.com/88580416/161209292-f8d5cd85-bf3a-485b-a94b-1871a459e82e.png)
Numbers of airports per country/per continent 2019/12 & 2020/12

![image](https://user-images.githubusercontent.com/88580416/161209361-9bf97dfd-a4a7-402e-a52b-5a9ad5469ccd.png)![image](https://user-images.githubusercontent.com/88580416/161209374-db47182c-4ef8-43e2-b979-727efcb53720.png)
Numbers of trips per country/per continent 2019/12 & 2020/12

## Network Analysis

To compare the network of flights pre-COVID and post-COVID, we have collected flight data from December 2019 (Pre-COVID) and December 2020 (Post-COVID). The reason why we chose the flight network in December is because the pandemic happened in some countries earlier while some later, but by the time of December 2020, most countries around the world had experienced with COVID. Therefore, we can expect more changes from the network. 

The objective for this network analysis is mainly to compare the difference between the two directed flight network in pre-covid times and post-covid times and to identify the airport hubs. By identifying the airports hubs, we can then decide which airport to reopen more flights when the influence of pandemic has worn off and the volume of flights resumes in the future.  

We set the origin and destination of each airport as nodes. If there was a trip between the origin and destination, an edge was formed. We also set the number of trips between nodes as edge attributes.

<img width="409" alt="image" src="https://user-images.githubusercontent.com/88580416/161209632-ae1fe2da-f97e-460d-b048-10f1469923ed.png">
From the basic summaries of the two flight networks, we can see that the quantities of nodes are about the same but in 2020, there were more edges than 2019. However, more edges do not mean that there were more flights because if there was a flight between the two airports, there was an edge, regardless of how many flights were flying in or out.

Moving on to a few more graph-level metrics, the diameter and average path length was slightly shorter in 2019, indicating that the flight network in 2019 was more connected. The modularity was slightly higher in 2019, meaning that there were denser connections between the airports within clusters, while sparser connections between airports in different clusters. The higher clustering coefficient in 2019 also suggested a more compacted, connected network in 2019.  On the other hand, there are more connected components in 2020. We can speculate that in 2020, the network was not as connected as 2019, so there were smaller connected components scattering in the 2020 flight network.   

Next, we can observe that the average degree and average weighted degree are slightly higher in 2019, meaning that there was more connectivity between airports in pre-COVID times. We can further look at the in-degree and out-degree distribution below:  

<img width="421" alt="image" src="https://user-images.githubusercontent.com/88580416/161209717-15820639-3010-44a4-aa1f-e7ecbb85c1c2.png">
The degree distribution in both networks have long tails and tall heads, following the power-law degree distribution on a normal scale. Interestingly, we can observe that out-degree has a longer tail in the distribution compared to in-degree. Also, it is noted that in 2019, both in-degree and out-degree has a higher max degree value than 2020.

## Identification of hubs
To identify the hubs, we took out the origin airports that have the highest out-degree value and the destination airports with the highest in-degree value.
![image](https://user-images.githubusercontent.com/88580416/161210385-d3c51c2d-6eb7-4a75-986e-da97afc11212.png) Airport hubs in December 2019

We plot the top 1000 origin airports with the highest out-degree value and destination airports with the highest in-degree value in 2019. Blue dots are origin airports and red dots are destination airports. In this graph, we can observe that a lot of origin airports in United States and Europe had higher out-degree values, especially origin airports in Europe. Meanwhile, many destination airports with higher in-degree values are in United States, followed by Europe. We can conclude that most of the connections in the airport and flight network were based in United States and Europe. Noticed that there were more origin airports with flights flying out in Latin America compared to flights flying in. Another interesting finding is that there were also more origin airports with higher degree in Australia. 

![image](https://user-images.githubusercontent.com/88580416/161210482-ee63bb91-e962-489f-a201-b8f25a09eec4.png) Airport Hubs in United States in 2019

The east part of the United States seemed to be covered with most airports with high in-degree and out-degree values. We can further analyze the airport hubs at country and city level to see which country have airport with the highest out-degree value? and which city have airport with the highest out-degree value?

![image](https://user-images.githubusercontent.com/88580416/161210536-382b25e0-6900-4726-811c-e3d3421197e9.png) Airport with the highest out-degree value in the top 30 countries (2019)

If we were to reopen only one airport in each country, then which country’s airport will have the highest out-degree value? Obviously, it’s United States, followed by Canada, Netherlands, and Germany.

![image](https://user-images.githubusercontent.com/88580416/161210611-b6732b01-25ef-4c8f-ad36-55de5b84a310.png) Airport with the highest out-degree value in the top 30 cities (2019)

In city level, the top 30 cities that have airports with highest out-degree values are all in United States. Airport at Teterboro New Jersey was the champion, followed by Chicago Illinois, Dallas Texas, and Atlanta Georgia. The result of this bar-chart is consistent with the geographic graph of the airport hubs in United States above.

![image](https://user-images.githubusercontent.com/88580416/161210693-6cae655e-e612-4296-8e12-ba9f88f434a1.png) Airport Hubs in December 2020

It is interesting that the destination airports with higher in-degree were even denser in United States, sparser in Europe, and had vanished from Latin America, Asia, and Africa. However, there are still origin airports with high out-degree in these places.




