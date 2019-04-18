# Foursquare-Neighborhood-Segmentation
Capstone project for IBM Data Science Professional Certification
-----------------------------------------------------------------
__Introduction:__ Brooklyn is on the rise while The Bronx is unfortunately in decline. I myself am a native New Yorker and grew up and spent most of my life in The Bronx. I very much like my neighborhood, but it's a long commute to lower Manhattan and it has an older median age. I have been thinking about relocating to Brooklyn to be closer to lower Manhattan and to be around more people my age. In this project I want to segment the different neighborhoods in both The Bronx and Brooklyn to see which, if any, neighborhoods in Brooklyn are closely related to my neighborhood in The Bronx. I am going to use the Foursquare API to compare the neighborhoods based on the venues (restaurants, bars, gyms, etc...) present in the different neighborhoods.

__Getting the Data:__ In order to create the data frame I needed to first download a json file. This json contains all the names, the borough, and latitude and longitude of every neighborhood in New York City. The code below is how I extracted the json file from the internet: 

![image](https://user-images.githubusercontent.com/35437820/56395484-ce2fa480-6208-11e9-919c-a19c5e003d8c.png)

All of the relevant data I needed was in the features key. So I defined a new variable that included the features data . Below is what the data looked like before I transformed the data into a _Pandas_ dataframe:

![image](https://user-images.githubusercontent.com/35437820/56395606-3ed6c100-6209-11e9-9b23-87b66d425784.png)

The feature key contains the four items I need for my dataframe (Borough, Neighborhood, Latitude and Longitude). Next I created a blank Pandas data frame, and then looped the json data into the new _Pandas_ data frame using the for loop below:

![image](https://user-images.githubusercontent.com/35437820/56395723-c15f8080-6209-11e9-9f2b-608e130e8f3b.png)

Now that my data is in a _Pandas_ dataframe, it'll be much easier to manipulate and examine. Since I am only interested in neighborhoods in The Bronx and Brooklyn, I simply dropped all the rows that contained neighborhoods in Manhattan, Queens and Staten Island. Yes, Staten Island is still technically a borough of NYC. I know it's easy to forget about. Next I needed to get the top 100 venues within a 750 meter radius of each neighborhood using the Foursquare location API. I used the code below to do that:

![image](https://user-images.githubusercontent.com/35437820/56395857-4e0a3e80-620a-11e9-8d9b-8b4b5025e52c.png)

From here I needed to transform the json data into a Pandas dataframe like I did above and merge the 2 dataframes together in order to have one dataframe. Now that the data frame was complete I was ready to do some exploration and further manipulation of the data.

__Exploratory Data Analysis:__ Once I had my dataframe created I was ready to explore the data. For this project I wanted to map out the neighborhoods and eventually group them into 5 different clusters. Firstly I just wanted to map out the different neighborhoods and make sure my map looked good.  So the first thing I did was plot out the neighborhoods of the Bronx and Brooklyn using the Python Folium library. I used the latitude and longitude of each neighborhood and the map came out as below:
