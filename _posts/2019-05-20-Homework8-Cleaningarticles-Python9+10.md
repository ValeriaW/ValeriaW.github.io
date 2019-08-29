---
title: Cleaning articles and Python 9 + 10
---
<!-- more -->

# Homework 8


My eighth homework post confirming the completion of the ninth and tenth unit of the Python 2 course on CodeAcademy as well as the description of how to clean your data using Python!
<!-- more -->


## How to:

The first part of the homework we had to complete was the creation of clean copies of issues from the scraped data, while keeping the originals intact.

```python
import re
import os

path = "/Users/valeriawidler/Documents/TNT/Perseust"
newFolder = "/Users/valeriawidler/Documents/TNT/Cleandata"
listOfFiles = os.listdir(path)

for f in listOfFiles:
  with open(path+f, "r", encoding="utf8") as f1:
      # read data
      data = f1.read()
      # removes markup from each file
      text = re.sub("<[^<]+>","", data)
      # rename file and folder
      newFile =  newFolder + f + "_modified.xml"

      with open(newFile, "w", encoding="utf8") as f9:
          # write text
          f9.write(text)

```

The second part of the homework required us to then create clean copies of each article, using a python script. Again, while keeping the originals intact.


```python
import re
import os

path = "/Users/valeriawidler/Documents/TNT/Perseust"
newFolder = "/Users/valeriawidler/Documents/TNT/Cleandata/articles"
listOfFiles = os.listdir(path)

for f in listOfFiles:
    with open(path+f, "r", encoding="utf8") as f1:
        data = f1.read()
        # date variable in the format YYYY-MM-DD
        date = re.search(r'<date value="([\d-]+)"', data).group(1)
        # serves to split the text into articles
        splitting = re.split(r"<div3 type=\"article\"", data)
        # important counter variable
        counter = 0
        # generating a new path name with the date
        newPath = newFolder + date + "/"

        # if path does not exist, create it
        if not os.path.exists(newPath):
            os.makedirs(newPath)
        # looping through the split sections
        for i in splitting[1:]:
            # counter for numbering
            counter += 1
            # updating the header
            i = "<div 3 " + i
            # removes markup
            text = re.sub("<[^<]+>","", i)
            # creating new file path and name 
            newFile =  newPath + date + "_" + str(counter) + ".xml"
            # write over into a new file
            with open(newFile, "w", encoding="utf8") as f9:
                f9.write(text)

```

***

![Confirmation](/img/Python9+10.png)