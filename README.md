# Data Collection, Preparation and Analysis For Near Earth Objects Using NASA's Open API

# Challenges faced 
Firstly the data did not allow me to return a large data set. It was restricted to near earth objects from within the last 7 days. To overcome this we use a for loop with specified dates using the date object. We can now get a larger data set by specifying the start and end dates we want to use. The api spits out jsons and we join them together in a smart manner for later analysis.

The jsons are added in an itterative fashion so one might expect the first date to be added first, the second date specified to be added second and so on in an itterative manner. In reality the dates are added at ranodom, the same way as would be in a hashmap. If we want to analyse data by the days of the week we would have a problem. Luckily a key is added to each json item. This prevents json data being overwritten and keeps track of which date the information specified is for.

There is a lot of data and it is difficult to know what attributes to compare to one another. There are many many combination. I did not even pick all attributes for our data set. A heat map can provide insights in to what attributes may be nice to plot against eachother. and this is how |I overcame that challenghe.

# Insights Reached
The key ionsights I gained are that larger objects are potentially more hazerdous and that the distance the asteroid is from eath is not as an important factor in whetehr or not a NEO is hazerodus. The speed is also not a facotr.

Most NEO's are non hazerdous.

The range of Velocities is quiet large and is the range of brightness.

The range in size is large too.

There are many NEO's that NASA keep an eye on to see if they change trajectory and may become potentially hazerdous. You need to be within a certain miss diatnce to be within the hazerdous caregory.

# Future works
In the future other NEO attributes can be analysed such as whether it is a sentry object.

This analysis can also be conducted on other orbiting bodies such as mars. Currently these are only done for near earth objects. One could add anlaysis on near mars obnjects.

One can also add in NASA's weather service REST API and see if the trajectory of NEO's changes per day given different space weather condition. This can be pploytted in a time graph plot.

## Task Task 1 - Retrieval of data - Choosing an API
In accordance with the API list provided at https://api.nasa.gov/, we will use NASA's Near Earth Object (NEO) API.

This API provides data on asteroids and comets that come close to Earth's orbit. It is maintained by the Center for Near Earth Object Studies (CNEOS) at NASA's Jet Propulsion Laboratory (JPL). More information can be found at https://www.nasa.gov/planetarydefense/neoo/."

The data is publicly available and can be accessed through a simple RESTful API. Unfortunately, the API has a limitation: we can only gather a small data set for a maximum of seven days. This presents our first limitation. To overcome this, we make multiple RESTful API requests and append the new NEOs (near Earth objects) to our JSON set each time.

The start and end dates can be edited depending on the data set you would like to collect.

# Nasa photo of the day
Here we get NASA's photo of the day, just for fun. It is NASA's most popular API that returns a new photo every day of some space NASA related activity.

**Moon Crater**
<img width="1046" alt="image" src="https://user-images.githubusercontent.com/44605305/231741205-9dc861c2-ad78-4212-a138-e5b87092c31c.png">

## Task 1.1 - Data Cleaning and Categorization 
### Saving data set in array format
We clean and format the data into two categories: NEOs that are potentially dangerous and those that are not dangerous. We collect data on each of these near-Earth objects, namely their absolute magnitude, size, velocity, and distance. Distance here refers to miss distance, which is by how much they will miss Earth by (the closest the object comes to hitting Earth in kilometers).

We now have a dataset of hazardous and non-hazardous objects in an appropriate format.

## Task 1.2 - Data Pre-processing
The data is saved and processed so that we can easily access the attributes we wish to know about. We parse the JSON object and retrieve the interesting attributes of NEOs. They are sorted into two groups: hazardous and non hazardous NEOs. I want to see what qualities a hazardous NEO has and compare it to non-hazardous NEOs later on.

# Task 2 - Loading data set in appropriate representation - pandas data frame
<img width="988" alt="image" src="https://user-images.githubusercontent.com/44605305/231741937-68b8502f-e79b-48cc-857e-4c24b55fb41b.png">


## Part 2 - Data pre-processing
The data was pre-processed before adding it to the data set in the final step one. What I did well was that the JSON was appending in random order using a map. I used the axis as the key in a key-value pair system. This allowed me to still keep the order of the data set dates regardless of the order in which they are appended. The data set itself doesn't require traditional cleaning. For example, no one is typing span such as "brueirfeguregr;gu Object1 velocity kedhdoeiwhd" which would need to be cleaned to "Object one velocity". This is because the REST API comes from NASA and there are no bots or malicious alterations to the data.

Task 2 - Visualisations and analysis of data collected And Explanation of results
Categorical data
We mainly analyze hazardous asteroids because they are of more interest to us.

NEO stands for near-earth object, which is a comet or asteroid which is in close proximity to earth. The potentially hazardous ones are of interest to us. We want to see what kind of features these potentially hazardous objects have. Their speed, their size, their absolute magnitude and if these attributes have any correlation to one another.

Straight away we see that there are many more no hazardous NEO's

## Visuals
We create numerous visuals but the most importat of which is firstly the heat map. 
### Heat Map
This heat map shows the pairwise correlations between the attributes of the NEO asteroid data. It tells us which attributes correlate. We will naturally then opt to plot visualizations for such params that tend to correlate closer to 1 but not exactly 1. If two attributes have a correlation of 1, they are either the same attribute or are derived from that attribute. Plotting them against each other is thus meaningless. For example, plotting average size against max size would be pointless. We note that size and brightness(magnitude) would be interesting to plot against each other.
<img width="840" alt="image" src="https://user-images.githubusercontent.com/44605305/231742191-b7875383-e9c2-4350-a3ea-08928455e4fd.png">

<img width="742" alt="image" src="https://user-images.githubusercontent.com/44605305/231742219-0cf72789-f3ff-4ce5-a491-ce5f61446a5e.png">

<img width="866" alt="image" src="https://user-images.githubusercontent.com/44605305/231742252-412cf1c3-4467-47fa-bc94-8c0737a8065a.png">

<img width="860" alt="image" src="https://user-images.githubusercontent.com/44605305/231742286-f033cadf-cb48-4d68-adb1-939baa788816.png">

<img width="1068" alt="image" src="https://user-images.githubusercontent.com/44605305/231742311-f0fd9e05-056e-4933-b867-c39a9948c164.png">

<img width="854" alt="image" src="https://user-images.githubusercontent.com/44605305/231742330-1ae5c917-11fb-4417-b878-06dbebc95607.png">

<img width="1122" alt="image" src="https://user-images.githubusercontent.com/44605305/231742367-333ff8cf-7c34-4052-b261-3072845e8c2e.png">

<img width="1011" alt="image" src="https://user-images.githubusercontent.com/44605305/231742398-1963901a-affa-4092-adb4-2e0529903510.png">

<img width="1044" alt="image" src="https://user-images.githubusercontent.com/44605305/231742463-ba9ad462-a186-4a35-b939-c5aa33c9c96c.png">


<img width="930" alt="image" src="https://user-images.githubusercontent.com/44605305/231742486-7ad30c53-6021-43b0-a4e7-b978c18b3da6.png">


![image](https://user-images.githubusercontent.com/44605305/231742589-f65768fe-d022-4671-bb99-edc381a2c769.png)








