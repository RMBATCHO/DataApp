---
title: "Word Prediction App"
author: "Rolande Sonya Mbatchou"
date: "Tuesday, December 02, 2014"
output: beamer_presentation
hitheme: tomorrow
job: Data Science Capstone - John Hopkins University
knit: slidify::knit2slides
mode: selfcontained
highlighter: highlight.js
framework: io2012
widgets: []
---

## Overview

We collected a text document corpus in order to build an algorithm that will best predict the next word, given a sentence. In order to successfully achieve our goal, we made use of Natural Language Processing (NLP) techniques and packages available in R, such as the tm and RWeka packages. 

1. The first challenge for this research was to normalize the unstructured input data. 
2. The second challenge was to generate summary statistics and perform some additional parsing. 
3. Finally, we built an algorithm that will best predict the next word, using n-gram models.

--- 

## Worldcloud of BiGrams


```
## Loading required package: RColorBrewer
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 

--- 

## Algorithm Methedology

To build our algorithm, we used a back-off strategy and N-grams. N-gram is a contiguous sequence of n items from a given sequence of text. For instance, "one" is a unigram, "one child" is a bigram, and "one child syndrom" is a trigram.

- We segmented the user inputed text into n-grams from n=1 to n=4. 
- Using a 5-grams frequency table, we looked if the inputed text appeared there:

1. If yes, we would select the corresponding ngram with the higest frequency and output the following word for that sequence. 
2. If no, we backoff, using the same methedology, but with a 4-grams frequency table.
3. The default word "the", most frequent used word in our corpus, is used as the last backoff step. 

--- 

## "Word Prediction" Shiny App

You can preview and test our Shiny App [Here.](https://rmbatcho1.shinyapps.io/shinyapp/)
For our Shiny App, we built an input text box for users. Users are prompted to give a sentence. Then, they can click submit to check which word is most likely to follow.

- App Description: The App includes an input text box, along with a submit button for users to enter their word choices. Once the user information are inputed, the system activates the algorithm and outputs the entered text, the predicted word, and a wordcloud visual of inputed text.

- Notes on Functionalities: The system, automatically, removes punctuation and lower the inputed text.
