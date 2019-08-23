## Political ads on Facebook in Canada

This repository contains the data files and code used to analyze 35,000+ political and issue ads on Facebook that were seen by Canadians.

[Read the story here](https://www.cbc.ca/news/politics/facebook-political-ads-canadian-federal-election-1.5246710).

The analysis was done in Python using the pandas and nltk libraries. The code is in the Jupyter notebook [`facebook_political_ads_canada.ipynb`](https://github.com/robroc/facebook-political-ads/blob/master/facebook_political_ads_canada.ipynb).

The data files are in the `data` folder. The data was obtained from the [Facebook Ad Library API](https://www.facebook.com/ads/library/api/?source=archive-landing-page) on several dates. 

The API queries were made with Faceook page IDs, which can be obtained from Facebook's [ad library report](https://www.facebook.com/ads/library/report/) for Canada.

Example of an API call made:

`https://graph.facebook.com/v3.3/ads_archive?ad_reached_countries=['CA']&ad_type=POLITICAL_AND_ISSUE_ADS&ad_active_status=ALL&fields=page_name,page_id,funding_entity,ad_creative_body,ad_creative_link_caption,ad_creative_link_description,ad_snapshot_url,currency,spend,ad_creation_time,ad_delivery_start_time,ad_delivery_stop_time,region_distribution,impressions,demographic_distribution&limit=250&search_page_ids=2771074019597750,230258673663722,551408801597287&access_token=<API-TOKEN>`

There are three data files:

### fb_ads_main.csv 
The main file with most details about each ad, including publication date, ad texts, and the page that published it. Detailed descriptions of each column can be found in the [API documentation](https://www.facebook.com/ads/library/api/?source=archive-landing-page).

Two columns were added to this file:

* `ad_id` : A unique identifier for the ad, taken from the `ad_snapshot_url` field in the API. This can be used as a key to join with the other files. Note: the `ad_snapshot_url` field was removed from the data because it contains the API token.
* `scrape_date` : The date that ad was fetched from the API for the first time.

### fb_ads_demographics.csv
The demographic breakdown of who saw the ad, by gender and age group. The `percentage` column is the proportion of total ad impressions by the demographic group.

### fb_ads_geography.csv
The regional breakdown of who saw the ad. Only Canadian provinces were kept in the data, even if it was seen in other countries. The `percentage` column is the proportion of total ad impressions by users in that province.