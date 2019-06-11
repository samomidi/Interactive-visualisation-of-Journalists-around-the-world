# Interactive-visualisation-of-Journalists-around-the-world
Interactgive visualisation of journalist killed, imprisoned or missing dataset in Tableau

# Data
COMMITTEE TO PROTECT JOURNALISTS: JOURNALISTS MISSING, IMPRISONED, KILLED
The Committee to Protect Journalists maintains data of journalists who have gone missing, 
been imprisoned or killed for reasons related to their work. The database goes back to 1992 
and contains more than 2,500 entries, with details such as the journalists background and nationality, 
organisations they have worked for, or circumstances of their deaths. The data can be found on StudRes. 
Information can be found on the Committee to Protect Journalists’ website.

# Exploratory Analysis and Data Cleaning
In order to get some basic ideas about the dataset, after some sketching and loading the data in Tableau, I decided to get some statistical view on the dataset using R Studio. I referenced couple of countries, jobs and Statuses in order to figure out duplicate observations and number of NULL and NA values. I then decided to split the data into smaller chunks in order to evaluate some of the assumptions. Also, chose combination of the columns which don’t have collinearity with other columns. In other words, I made sure I am not including two columns that telling the same story.
Finally, data cleaning which required to rename some of the values. Such as converting small letters to capital and splitting job column to “Main duty” in Tableau in order to plot Status against jobs which eventually leaded to conclusion of having more casualty among “Broadcast reporters” and “camera operators” (for additional dimension) in the later.
In the process of data cleaning there were number of journalists who did not have primary nationality, therefore, I decided to classify them as “Stateless” journalist in order to better address this group. Additionally, some journalists did not have gender specifies and I decided to categorize them as “Unknown” which can be seen in the related dashboard for gender vs Map view.

# Visual Mapping
For the main visualization, I used the following visual variables to encode data attributes:

![Capture](https://user-images.githubusercontent.com/32543461/59290396-5d3cc400-8c70-11e9-8a3d-c9f446211337.JPG)

Justification: Since this visualization requires names of 118 countries with limited space on the page and mostly categorical data, using spatial region and its implementation should be done tactfully in order to make the message and story clear to the user since effective use of space is important in every visualization. As mentioned on my sketches various methods have been designed and implemented to show the top countries. Also, from trial and experiment it seemed that combination of map and bar chart along with attribute coding mentioned above can convey the message in more effective way. However, I should emphasize that significance of programming in Tableau to achieve sorting the bar chart in order to show top countries is essential in this visualization.

# Interaction
As described in the initial sketches (attached) various methods have been designed on paper and implemented on Tableau. Using Five Design Sheet method, filtered, categorized, combined and generated ideas. Eventually I decided to use map on the top of the dashboard and bar chart below the map. As the bar chart can be sorted by the help of four calculated fields to query each value of Status field (Calculated filed called: Imprisoned, Killed and Missing), a filter (Called: Filter) to query the aforementioned calculated fields using “Case switch statement” and a parameter which the mentioned case statement works according to its value.
Please note that in order to not to face any issue when opening this project on another machine I reverted the map background to the default.

![Dash 1](https://user-images.githubusercontent.com/32543461/59290988-c113bc80-8c71-11e9-97a8-5ffe4f7f25e8.JPG)

Per figure 1 we can see that the counties are sorted according to the Killed status (Red Color) and user can choose any status value of Imprisoned, Missing or Killed and in addition user can choose Alphabetical order from drop down menu.

On top of the sort drop down menu user can filter the values of status in order to highlight the desired category of status in the map and the bar chart at the same time. As it can be seen on figure 2 bar chart is sorted according to imprisoned while user has filtered and highlighted the values of Killed and this has been reflected on both map and bar chart.

![Dash 2](https://user-images.githubusercontent.com/32543461/59291046-e30d3f00-8c71-11e9-9171-78cf1eccbbc5.JPG)

Using combination of filter (Select status to filter) and defined parameter as dropdown menu (sort countries by) user can not only figure out the top countries in every category, but also they can get insight of a different values on both map and the bar chart while the can hover over the bar chart or map if they desire to get information more specifically about a particular country.
For instance, per figure 3 user has sorted the bar chart per Killed value while hovering the mouse cursor on the Missing journalists from Mexico and it has been reflected on the map as well. Also, more details, which is the number of missing journalists in Mexico have been provided using tooltip box.


![Dash 3](https://user-images.githubusercontent.com/32543461/59291080-f5877880-8c71-11e9-920b-f83503086095.png)

# Additional Dimensions
## Map Vs Year
The question for this section is, what has happened in every country at particular year. In the Map- Year Dash. We have map view on the type and year view on the bottom. User can hover over a particular year and check for instance how many journalists have been killed on that year. Also, provided filter using cards let user to further filter the data by value of status or limited range of the years as well as number of the records. Figure 4 shows 73 journalists have been killed in year 2013 by user hovering over the year view plot and filtered countries have been filtered in map view as well.


![Map-year Dash](https://user-images.githubusercontent.com/32543461/59291147-16e86480-8c72-11e9-945b-4efac0d9a5bd.png)

## Jobs vs Type of death and year
In this section I am trying to answer which type of journalist’s job resulted in more casualty in a specific year?

![Job-death-year](https://user-images.githubusercontent.com/32543461/59291175-2667ad80-8c72-11e9-8386-f82b34db7940.jpg)

As illustrated in figure 5 user can point to a certain year on the bottom graph and filter out the result of the table on top. for instance, user can figure out what type of job ended with what type of death. As mentioned in explanatory analysis per my investigation most of the casualties belongs to the group of broadcast reporters and camera operators. Again, user can filter out per status values and limit the range of the years.

## Gender Vs Status and Countries
Another interesting question for this dataset can be proportion of genders per each category of Status (Imprisoned, Missing and Killed). As illustrated per figure 6, user has pointed to the females who were killed, and the related countries are reflected in the map by red dots while the tooltip box informing the user of the number of killed females.

![Gender Vs Status and countries](https://user-images.githubusercontent.com/32543461/59291215-3c756e00-8c72-11e9-81f5-55aa7ebcef76.jpg)

## Distinct Values Vs Duplicates
In order to get more insight of the dataset I designed a dashboard called Distinct Vs Duplicates. So, user can easily compare the values in case they are interested in both views.

![Distinct Vs Duplicate](https://user-images.githubusercontent.com/32543461/59291235-4b5c2080-8c72-11e9-9529-1fa7a7c30d6d.png)

In figure 6 I used show marks label in order to better understand the change. For instance, user is hovering their mouse on Russia on the top bar chart and we can see 92 missing is being shown, while on the bottom bar chart (Distinct values) the number of missing is significantly reduced as there is no more duplicates.

# Future Work
As future work enhancements can be done such as:
1- A new feature can be, sorting the countries according to Status value and limit the countries to top 5 or top 10 and then zoom in the bar chart. This way user can have a better view of the top countries without distraction of rest of the country’s names in the visualization.
2- Since in visualization it is important to effectively use the spatial space, we can implement a feature that by selecting top 5 countries in bar char, the reflection of that in map happens in a way that only the top five to be shown. This specifically is more useful when our result contains small countries adjacent to each other and it is sometimes difficult to read. However, in the current visualization we can zoom in.
3- In the “Type of death-Job-year” dashboard we can include enhancement in a way that when user selects a year the jobs table on the top get descending order. This way user can see which job of journalists has more casualties. This requires movement of the columns which requires more research and it this stage I am not sure if it is possible in Tableau.
