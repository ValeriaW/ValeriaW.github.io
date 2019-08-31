---
layout: post
title: Topic Modelling
---


<!-- more -->

# Homework 12


My twelfth homework post dealing with topic modeling!

***

Our homework task was the retrieval of relevant data that we need to link place and other data from texts. Among other things, we need to extract toponyms or place names, calculate their frequencies and then match these with coordinates in QGIS in order to be able to map with markers the size of which correspond to the frequency of the place name mentions in the text. 
First we need to get the following values to create a CSV file which can then be used for creating a map in QGIS: placename, timeParameter, latitude, longitude and frequency.


```python

import re, os

source = "/user/valeriawidler/documents/TNT/Perseust"

lostTopo = []
dictTopo = {}

def collectToponyms(source):
    lof = os.listdir(source)
    for f in lof:
        if f.startswith("dltext"): # fileName test
            with open(source + f, "r", encoding="utf8") as f1:
                text = f1.read()
                toponymsToDict(text, dictTopo)
    csvExport()


def csvExport():
    resultsCSV = []

    for key, value in dictTopo.items():
        if value > 1: # this will exclude items with frequency 1
            newVal = "%09d\t%s" % (value, key)
            resultsCSV.append(newVal)

    resultsCSV = "\n".join(sorted(resultsCSV, reverse=True))
    print(len(resultsCSV)) # will print out the number of items in the list
    resultsToSave = "\n".join(resultsCSV)
    with open("freqResult.csv", "w", encoding="utf8") as f9:
        f9.write(resultsCSV)


def toponymsToDict(text, dictTopo):
    for i in re.findall(r"<placeName[^<]+</placeName>", text):
        tgn = re.search(r"tgn", i)
        try:
            if tgn:
                reg = re.search(r'reg="([^"]+)"', i).group(1)
                key = re.search(r'key="([^"]+)"', i).group(1)
                # I don't like this but time...
                newKey = key + "\t" + reg
                # I think I don't need the region name, therefore I just go for key
                dictUpdate(dictTopo, newKey)
                #print(dictTopo)
        except:
            lostTopo.append(i)

def dictUpdate(dic, key):
    # I wanted to try a list as value for each key, but I couldn't do it, I have no time for this :(
    if key in dic:
        dic[key] += 1
    else:
        dic[key]  = 1


collectToponyms(source)
print(lostTopo)

```


<!-- more -->



***
