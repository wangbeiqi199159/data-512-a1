# Page Views of English Wikipedia

## Goal of the Project
The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through September 30 2017. Wikipedia traffic is from two different Wikimedia REST API endpoints, and then to be combined into a single dataset. 

## License and Terms
[MIT License](https://opensource.org/licenses/MIT) : Copyright (c) 2017 Becky Wang

[CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/copyleft/fdl.html)

Wikimedia's [general Terms of Use](https://wikimediafoundation.org/wiki/Terms_of_Use/en) and [Privacy Policy](https://wikimediafoundation.org/wiki/Privacy_policy).

## Relevant API
The legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_%28legacy%29/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from January 2008 through July 2016.

The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017.

## Variables of Final Data File

|  Column | Value  |
|---|---|
| year  |  YYYY |
|  month |  MM |
|  pagecount_all_views |  nums_views | 
|  pagecount_desktop_views |  nums_views |
|  pagecount_mobile_views | nums_views  |
|  pageview_all_views |  nums_views |
|  pageview_desktop_views |  nums_views |
|  pageview_mobile_views | nums_views  |


## Directory Structure
```
data-512-a1 (master)
|     .gitignore
|     License
|     README.md
|     en-wikipedia_traffic_200801-201709.csv
|     hcds-a1-data-curation.ipynb
|	  page views of english wikipedia.jpg
|	
|----- data
|     |      pagecounts_desktop-site_200801-201607.json
|     |      pagecounts_mobile-site_200801-201607.json
|     |      pageviews_desktop_201507-201709.json
|     |      pageviews_mobile-app_201507-201709.json
|     |      pageviews_mobile-web_201507-201709.json
```
## Important Notes

From May 2015, a new pageview definition took effect, which elimilated all crawler traffic. So data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not.
