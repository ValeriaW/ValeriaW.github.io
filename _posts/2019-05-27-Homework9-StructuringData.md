---
title: Structuring Data and Python 11 + 12
---
<!-- more -->

# Homework 9


My ninth homework post confirming the completion of the eleventh and twelfth unit of the Python 2 course on CodeAcademy as well as the description of how to structure your data using TSV and Python!
<!-- more -->


***

![Confirmation](/img/Python11+12.png)

Reformat the scraped documents (“Dispatch”) converting into one TSV file where each article represents one record with the following information:
_1. date;_
_2. type of an entry (there are articles, advertisements, notices, etc);_
_3. header;_
_4. the text of an entry_

**Using Python to facilitate the conversion:**

```python
import re, os, csv, json

source = "/Users/valeriawidler/Documents/TNT/test/"
target = "/Users/valeriawidler/Documents/TNT/TargetPerseus"

lof = os.listdir(source)

list = []

for f in lof:
    if f.startswith("dltext"): # fileName test
        with open(source + f, "r", encoding="utf8") as f1:
            text = f1.read()

            # finding the date
            date = re.search(r'<date value="([\d-]+)"', text).group(1)

            # splitting the issue into articles
            split = re.split("<div3 ", text)

            c = 0 # item counter
            for s in split[1:]:
                c += 1
                s = "<div3 " + s # a step to restore the integrity of items
                #input(s)

                # try to find a unitType
                try:
                    unitType = re.search(r'type="([^\"]+)"', s).group(1)
                except:
                    unitType = "noType"
                    print(s)

                # try to find a header
                try:
                    header = re.search(r'<head>(.*)</head>', s).group(1)
                    header = re.sub("<[^<]+>", "", header)
                except:
                    header = "NO HEADER"
                    print("\nNo header found!\n")

                text = re.sub("<[^<]+>", "", s)
                text = re.sub(" +\n|\n +", "\n", text)
                text = re.sub("\n+", ";;; ", text)

                # generating necessary bits
                fName = date+"_"+unitType+"_"+str(c)

                # creating a dict
                dict = {
                    'id': fName,
                    'date': date,
                    'type': unitType,
                    'header': header,
                    'text': text
                }
                # appending the dict to a list
                list.append(dict)

## Writing the whole thing
# column names for the csv/tsv
csv_columns =  ['id', 'date', 'type', 'header', 'text']

# writing tsv
with open('dispatch.tsv', 'w', encoding="utf8") as f:
    writer = csv.DictWriter(f, delimiter ='\t',fieldnames=csv_columns)
    writer.writeheader()
    for data in list:
        writer.writerow(data)

# writing csv
with open('dispatch.csv', 'w', encoding="utf8") as f:
    writer = csv.DictWriter(f,fieldnames=csv_columns)
    writer.writeheader()
    for data in list:
        writer.writerow(data)

# writing json
with open("dispatch.json", "w", encoding="utf8") as f:
    json.dump(list, f)

```
