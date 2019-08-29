---
layout: post
title: Network Analysis using Gephi
---


<!-- more -->

# Homework 13

#My thirteenth and (sadly) final homework post dealing with the network tool Gephi!

***

Using the topographic data from our Dispatch that we extracted for the homework of lesson 10 in CSV file format, we can create a network with Gephi. Some information for this task is missing from the table still.


The CSV file for the geographical representation using Geolayout includes, ID, target, source and in this case longitude and latitude. It is the nodes file. When importing the file, the longitude and latitude data needs to be set as "Double" in order for Gephi to pick up on them as geographical inputs. After installing the Geolayer plugin, all the nodes of places can be displayed in mapform. Before importing the nodes file, an edges table with source, target and weight must be imported to the programme. The weight is in this case defined by the frequency of mentions. After several attempts, I found that restricting the data to one year yields the most visually intelligible networks, as a too complex data set is rather useless for analysis in this case. An early network with too much data looked like this:

![Failblob](/img/Earlyblob.png)

The filtered version of the dispatch data that I ended up with after I set in place filters:

![Gephi](/img/Networkmodularity.png)

In the network pictured above, I used the modularity algorithm to identify different communities within the network with a resolution of 1.0. Before doing that, I also filtered the data points to weights above 10, so as to more clearly work out the central clusters. In the year 1865, we can clearly see that the most mentioned places are among others United States, Richmond, Virginia, Charleston, England, Washington and Pennsylvania. The 'United States' is by far the most connected of the place name mentions. Maybe it is better to use a higher 'resolution' in order to decrease communities and see better what overall clusters emerge.

A useful tool in the Gephi programme is the possibility to georeference nodes using lon/lat collumns in the table. Unfortunately, after the initial placement of points with the geolayer layout, the application of the 'map of countries' reveals that something is quite off.

![Worldfail](/img/Worldfail.png)

This was also the case with the unfiltered dataset and I am keen to find out what could have gone wrong with the coordinates:

![Geolayerfail](/img/Geolayerfailish.png)

On it's own, even though without a map, you can still decipher that most mentions are clustered in the now United States territory and Europe, with far more mentions within the Eastern territory of the US overall.

***