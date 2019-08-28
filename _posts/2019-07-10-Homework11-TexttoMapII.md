---
layout: post
title: Text to Map II
---


My eleventh homework post dealing with text to map techniques put to use in QGIS!
<!-- more -->

# Homework 11

***

(See previous homework) Our homework task was the retrieval of relevant data that we needed to link place and other data from texts. Among other things, we needed to extract toponyms or place names, calculate their frequencies and then match these with coordinates in QGIS in order to be able to map with markers the size of which correspond to the frequency of the place name mentions in the text. 
First, in the previous homework, we created a CSV file that we can now use to create a map in QGIS.
In order to create context for the georeferenced place data points, I installed the QMS plugin and selected "Esri World Imagery" as a background layer.

![QMS_Dispatch](/img/T2MII_Europe.png)

![QMS_Dispatch2](/img/T2MII_NAmerica.png)

As can be seen in the image, the years 1861, 1862, 1863, 1864 and 1865 were coded by color but not yet by frequency of mentions. I achieved this by selecting size to represent frequency, as can be seen below:

![QMS_Dispatch](/img/T2M_World.png)

View of North America with more detail,

![QMS_Dispatch](/img/T2M_US.png)

and with city names.

![QMS_Dispatch](/img/T2M_USCities.png)

I was further very keen on creating a gif of the five different years 1861-1865, however, I could not get the plug-in timemachine to work on my mac because I was unable to install the missing module 'future' (pip install future indicated that something is wrong with my version of Python, a recurring problem).

