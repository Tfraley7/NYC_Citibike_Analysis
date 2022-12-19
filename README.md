# NYC_Citi_Bike_Analysis
Analysis on bike rides for Citi Bike
<br/>
<p align="center">Tyrone Fraley<br/>
UC Berkley Extension<br/>
August 31, 2022<br/>
<p/>
<br/>
<p align="center">
  <img width="460" height="200" src="Images/Bicycle.jpeg">
</p>
<br/>

## Overview of the Analysis

Working for Citibike I was tasked to analyze and visualize bike ride analysis to convince investors that a bike-sharing program in Des Moines could be a great proposal. The main focus on this analysis would be to focus on trip analysis. To start the analysis it was vital for me to use Pandas to alter the "tripduration" column within the data set, because the "tripduration" values were all integer values and needed to be datetime datatypes. 
Once the datatype for the "tripduration" column was adjusted to datetime it was then important for me to visualize the data through tableau. The first objective was to gather the length of time in which bicycles were used by all riders and their genders. Then to show how many bike trips there were for all riders and genders based on every hour for each day of the week. Finally, in tableau there would also be the amount of bike trips based on each type of user and gender based on each day of the week. The full Tableau story can be viewed here: https://public.tableau.com/app/profile/tyrone.fraley/viz/Citibike_16709584665220/Story1?publish=yes
<br/>
### Results

Using pandas datetime format I was able to change the "tripduration" column from integer to datetime format. This can be done by using pd.to_datetime(). In this instance after creating a data frame (bike_df). I then assigned the datetime format as follows: bike_df["tripduration"] = pd.to_datetime(bike_df['tripduration'], unit='s').
<br/>
<p align="center">
  <img width="460" height="200" src="Images/bike_df_datetime.png">
</p>
<br/>
The next step of the analysis within pandas was to change the gender column to string values and change the values in the gender column as well. To change the column's values to string format I used the followign code: bike_df['gender'] = bike_df['gender'].astype(str). At the beginning the values in the gender column were represented as numbers from 0 - 2. However, this had to be adjusted to "UNKNOWN", "MALE", and "FEMALE". To change the values I used the following code: bike_df['gender'] = bike_df['gender'].replace(['0', '1', '2'], ['UNKNOWN', 'MALE', 'FEMALE']).The columns went under such adjustments for better visualization in tableau.

Now that the data set looked much cleaner I exported it into a csv file that was then uploaded within Tableau. In Tableau I first created the "Checkout Times for Users" graph. To accomplish this I took the count of records within the data set and placed it in the rows section. I then added "Tripduration" to the columns twice. One representation based on hour and the other representation based on minutes. Tripduration based on hour was also added to the filters and i chose 0,1,2, as my hours. Doing so allowed me to split the graphs into three sections. Minutes was adjusted to reflect 60 minutes for each occurence with a skip rate of 20 minutes. From this graph we can understand that max amount of riders were 146,752 and their rides lasted 5 minutes. As a minimum there were 33 rides which lasted 59 minutes each.
<br/>
<p align="center">
  <img width="460" height="200" src="Images/CheckoutTimesForUsers.png">
</p>
<br/>
The next step was to plot the "Checkout Times by Gender" The purpose of this graph was the same as the "Checkout Times for Users" graph, but based on genders. The same parameters were set in place, except I added the "Gender" column to the color and then I took "Gender" to the filters section so that I could filter by gender. With this data now visualized i could see that the "Unknown" gender category had 7,389 max rides at a duration of 11 minutes. The The 'Female' gender category had 34,151 max rides at a duration of 6 minutes. The 'MALE' category had the most rides (108,087) with a duration of 5 minutes. The 'UNKNOWN' category had the most long term rides (15 rides) at a duration of 59 minutes. The 'MALE' gender category came in at 12 rides at a duration of 59 minutes. The 'FEMALE' gender category had the least longest duration of rides at 6 rides for 59 minutes. 
<br/>
<p align="center">
  <img width="460" height="200" src="Images/CheckoutTimesforGenders.png">
</p>
<br/>
To figure out how many trips were accomplished by weekday per hour ("Trips by Weekdayp per Hour"). I took the "Stoptime" column and added it to columns based on week day. Rows contained the "Starttime" column and I based it on hours. In addition, count of instances was added to the color marker. The most trips started on at 6pm with a total of 44,905 rides and ended on a Thursday. he least amount of trips started at 3 am with a total of 360 rides and ended on a Tuesday.
<br/>
<p align="center">
  <img width="460" height="200" src="Images/TripsByWeekdayPerHour.png">
</p>
<br/>
To visualize "Trips by Gender (Weekday per Hour)." I kept the ssame format as "Trips by Weekdayp per Hour," but added "Gender" to the columns and the filters. When observing rides by start/stop time. The 'Unknown' gender category had their most rides at 12pm on Saturday with a total of 5,569 rides. The 'FEMALE' gender category had their most rides on a Thursday at 6pm with a total of 11,336 rides. The 'MALE' gender category had their most rides on a Thursday at 6pm with a total of 30,740 rides.
<br/>
<p align="center">
  <img width="460" height="200" src="Images/TripsByGender(WeekdayPerHour).png">
</p>
<br/>
The next graph is "User Trip by Gender," which observes how many trips were conducted by gender. To plot the results I used "Gender" as a filter and column, "Usertype" as a row and filter, and "Starttime" based on weekday as a row. Finally, count of occurences was placed as a color marker. In the User Trip by Gender graph we can see that the most rides occur amongst  'FEMALE' and 'MALE' gender categories when they are Subscribers. However, for the 'UNKNOWN' gender category we see more Customer Usertypes riding bikes than 'UNKNOWN' Subscribers.
<br/>
<p align="center">
  <img width="460" height="200" src="Images/UserTripByGender.png">
</p>
<br/>
Finally, I wanted to add the starting and ending locations of rides. To plot the "Starting Locations" graph I used "Start Station Latitude" as my row section and "Start Station Longitude" as my column section. The Starting Locations map shows which areas have the least to most starting points for rides. To plot the "Ending Locations" graph I used the same values as the "Starting Locations" graph, but the variables were added to the rows and columns oppositely from the the "Starting Locations" graph. 
<br/>
<p align="center">
  <img width="460" height="200" src="Images/StartingLocations.png">
</p>
<br/>
<br/>
<p align="center">
  <img width="460" height="200" src="Images/EndingLocations.png">
</p>
<br/>

### Summary
The data set shows us that the most rides came from the "MALE" category. However, the least amount of rides came from the "Unknown" category. In addition, Fridays (233, 638 trips) and Tuesdays (204,479 trips)yeilded the greatest amount of trips. These trips came from the "Male" gender category. To understand more about why the customer's chose to check out the bikes, may be helpful in future campaigns. 
