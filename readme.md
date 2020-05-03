# Dataset Exploration Public Bike network in San Francisco
## by Miguel Granica


## Dataset

> The database contains the record of the trips made by bicycle in the city of San Francisco during the last 10 months. It has more than 2.5 million records. Which have temporal information and the georeferenced coordinates of the start and end stations of each route, allowing the establishment of paths and their respective duration. Finally, it provides us with user data, such as what type of subscription they have. the csv file with the gather data is attached with the documentation.
We gathered the data using the requests library. in total we extracted 10 .zip files containing the information of the different months that we concatenated to form a single database of files. It contains 2.5 million rows contained in 16 columns.
We use the geopy function to calculate the distance between the departure and arrival stations. This will help us understand the transfer speeds and how much it is reduced at times of greatest congestion. As you are working with a large number of registers, we will divide the process into steps so as not to overstress the cpu.
to perform more accurated results we remove the inconsistent values:
    - duration: drop all the travels that have last more than 6hs, thay can be usefull but in porpuse of our investigation they generate a lot of noise
    - distance: with the same logic we considere that all the distances above 50 milles as outliers. (i.e. 3er quartile= 1.5 miles)
In boths we will remove all the 0 values.


## Summary of Findings

> Summarize all of your findings from your exploration here, whether you plan on bringing them into your explanatory presentation or not.
The variables of interest, duration of the journey and distance traveled have expected distributions. the duration of the trips should be scaled with the log function, in order to obtain a normal distribution that had its peak between 8 and 10 minutes. instead the distance presents a left squeded curve, to obtain these results it had to be scaled as well. This variable was obtained as a result of performing the distance function of geopy. With these variables we can not only understand the rhythm of the transfers but also what type of routes users are taking.
the distribution of the distance traveled by bike is according to what we expected. a left squeded distribution. with the pick of the distance traveled in less than 1.5 milles.
the number of trips during the weekend is reduced. In Monday, Friday it also has a slight decrease in the number of trips compared to the other days of the week. This may be due to the growth of the home office, or also to the transfer to the second residences in the suburbs of the city, directly after to end and/or to start the week.
We observe that during rush hour, between 8 and 10 in the morning and between 17 and 19 at night, 40% of the trips happen. We can say that it is a transport service widely used to run daily commutes from home-work or educational center. This indicates to us that San Francisco has a well connected bike-network that does not affect the duration of the trips and ensures users good performances.
25 stations are involve in more than a millon of travels in the last ten months. the number of bikes that are in circulation between only this 25 stations is amazing. with more than 80.000 travels San Francisco Caltrain (townsend st at 4th st) is the most requiered station in the San Francisco bay.
both the distance of the tours of the customers and the duration is greater than that of the subscribers. This can be explained because it is not their main means of transport or even because they are using it in a recreational way. However, the speed is higher in the case of subscribed users.
around 5 in the morning the average distance traveled by subscribers exceeds that of customers, however, after 9 in the morning their descent is much more abrupt.
Regarding the duration we see a considerable increase between 12 and 16 hours among the custumers, these values ​​may indicate tourist or recreational tours.
The speeds have some parallelism, with a peak of 7.5 mph on average at 5 in the morning.


## Key Insights for Presentation

> The tremendous increase in miles traveled has been abruptly interrupted by COVID-19 and the respective suspension of service. 500,000 miles traveled per month to 0 miles in less than two months. In short, this curve, more than the evolution of the use of the public bicycle network, shows us the impact of the pandemic, and the response of citizens.
we highlight how customers fluctuate less throughout the day. the interesting thing about these plots is to see how the peaks of the subscribers work as a mirror. in other words, when a station has many departures one morning, during the afternoon it will receive the respective returns. conversely, the stations in the work areas receive many arrivals in the morning and many departures in the afternoon. It is a great indication of the distribution of land uses and also helps to maintain the correct distribution of bicycles within the network.