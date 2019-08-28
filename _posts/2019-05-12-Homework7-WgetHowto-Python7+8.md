---
layout: post
title: Webscraping with Wget - How-to-Guide by me and Python 7 and 8
---

# Homework 6

My sixth homework post confirming the completion of the seventh and eighth unit of the Python 2 course on CodeAcademy!
<!-- more -->


***

![Confirmation](/img/Python7+8.png)


How-to-guide for the scraping of “Richmond Times Dispatch” from http://www.perseus.tufts.edu/hopper/dltext?doc=Perseus%3Atext%3A2006.05.0001 using Wget!

With the following commands, wget allows for the scraping of data from websites:

wget link

wget -i file_with_links.txt

wget -i links.txt -P ./folderYouWantToSaveTo/ -nc

In order to download all issues of the "Richmond Times Dispatch" with Wget, we needed to find the original link that would form the basis for the scraping of each issue.
After opening the link to one article, it became apparent that this xml download link would not yield the issue link that we are looking for. 
After some scrutinising of the page (and further encouragement by Mr. Romanov), we discovered that the site was nice enough to provide the .xml file download link for the whole issue in the fineprint at the bottom of the page.
When comparing the article and issue link, one could see that the link is altered with a "dl" before __text__ and by extrapolation, adding dl to every article URL would end our search for the needed links. The links to the articles, we could easily download from the source code of the webpage. 
Then, we achieved the addition of the missing letters using Regular Expressions.
Finally, use wget in Terminal with the links.




<!-- more -->


***
