## Political ads on Facebook in Canada

This repository contains the data files and code used to analyze 35,000+ political and issue ads on Facebook that were seen by Canadians.

Read the story here.

The analysis was done in Python using the pandas and nltk libraries. The code is in a Jupyter notebook.

The data files are in the data folder. The data was obtained from the [Facebook Ad Library API](https://www.facebook.com/ads/library/api/?source=archive-landing-page) on several dates. 

There are three files:

### fb_ads_main.csv 
The main file with most details about each ad, including publication date, ad texts, and the page that published it. Detailed descriptions of each column can be found on the [API documentation](https://www.facebook.com/ads/library/api/?source=archive-landing-page).

Two fields were added to this file:
`ad_id` : A unique identifier for the ad, taken from the `ad_snapshot_url` field. This column can be used as a key to join to the other files.
`scrape_date` : The date that ad was fetched from the API for the first time.

### fb_ads_demographics.csv
The demographic breakdown of who saw the ad, by gender and age group. The `percentage` column is the proportion of total ad impressions by the demographic group.

### fb_ads_geography.csv
The regional breakdown of who saw the ad. Only Canadian provinces were kept in the data, even if it was seen by other countries. The `percentage` column is the proportion of total ad impressions by users in that province.