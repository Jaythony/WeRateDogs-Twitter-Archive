# Data Wrangling Report (WeRateDogs)
> This report is a breakdown of my data wrangling process for the project: **Wrangling and Analyzing WeRateDogs Twitter Archive.**

## Importing Required Libraries

I began by importing all the libraries and packages I needed for this project first **(pandas, numpy, requests, os, json, matplotlib.pyplot, and seaborn).**

## Data Gathering

Three(3) datasets were used in this project.
1. The tweet archive of Twitter user @dog_rates, also known as WeRateDogs, served as the primary dataset for this project. This was made available in a CSV file. I saved this file in the same directory as my notebook and read it into a pandas DataFrame using the pandas read_csv() method. This DataFrame had columns like tweet_id, text, timestamp, dog name, retweet and reply status, etc.


2. The second dataset was an image prediction file containing the results of running images in the WeRateDogs Twitter archive through a neural network that classifies breeds of dogs. It contained the top three predictions for one image in each tweet (dog breed, confidence score and whether or not image is that of a dog) alongside each tweet ID, image URL and image number. This file is hosted on Udacity's servers and I downloaded it programmatically using the Requests library and the given url. I then used the pandas read_csv() method to load this data into a DataFrame.


3. The third dataset was obtained from querying the Twitter API for each tweet's JSON data using Python's Tweepy library. Each tweet's entire set of JSON data was written to its own line in a file called tweet_json.txt file. I read this .txt file line by line, extracting the tweet ID, retweet count, and favorite count into a pandas DataFrame.

## Assessing Data
I assessed my data visually and programmatically and identified **eight (8) quality issues and four (4) tidiness issues** which I documented.

**Note:** The following key points guided my assessment:

* I wanted only original ratings that **have images.** Some tweets were replies and some others were retweets, I didn't want those. Tweet_ids not in the image_prediction dataset meant tweet didn't have an image, such tweets were not relevant to my analysis. Also, some images were classified as "not_dogs", I didn't want those as well.
* The fact that some of the rating numerators were greater than the denominators did not need to be cleaned, however, I only considered ratings with a denominator of 10.


## Cleaning Data
At this point, I addressed and cleaned the **eight (8) quality issues and four (4) tidiness issues** I documented while assessing. 

**To achieve this:** 
1. I made copies of my 3 datasets so that changes/cleaning were only done on these copies.
2. I used the define-code-test framework and clearly documented it.
3. I merged individual pieces of data according to the rules of tidy data to get a high-quality and tidy master pandas DataFrame.

## Storing Data
I saved my gathered, assessed, and cleaned master dataset to a CSV file using the pandas to_csv() method.

## Analyzing and Visualizing Data
Finally, I analyzed my master data set to get insights and produced visual representations of these insights with the help of matplotlib and seaborn.
