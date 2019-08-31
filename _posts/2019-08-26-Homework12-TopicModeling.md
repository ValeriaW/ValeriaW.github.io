---
layout: post
title: Topic Modeling with R
---


<!-- more -->

# Homework 12


My twelfth homework post dealing with topic modeling with the R script provided!

***

Topic Models, in a nutshell, are a type of statistical language models used for uncovering hidden structure in a collection of texts. 

In this example, we were supposed to use a provided R code and jupyter notebooks to facilitate topic modeling for our dispatch of the Richmond Times.

To be completely honest, I had a lot of problems running the script and I wasn't really sure how to help myself.

In the very beginning of it, the gensim module couldn't be installed.

![problem1](/img/JupyterProblem.png)

Further, the resource 'stopwords' couldn't be installed.

![Stopwords404](/img/JupyterProblem2.png)

In the next steps, the stopwords were however generated for the specific dataset of our dispatch. 

Later I also got the 'KeyError: 'textDataLists'' and 'ModuleNotFoundError: No module named 'plotly'' and 
'NameError: name 'dictionary' is not defined'.

In an earlier run however, it succeeded at creating two graphs:

![Graph1](/img/T19_Collmn.png)

![Graph2](/img/T19spikes.png)

Topic 19 (T19), including 'treasury, notes, bonds, states, certificates, secretary, confederate, cent, richmond, payment', is seeing a considerable spike in December 1864, as can be seen in the first graph with 160 mentions.

The second graph runs from Jan 1864 through Jan 1865 but in two-month increments. It reveals that individual instances (spikes) of mentions have created the look of the first bar graph, where March 1864 described a higher occurrence than any other month before the definite upward trend beginning in September of 1864. It is more clear that overall the topic was mentioned consistently towards the end of the year until Jan 1865.