# Page Views of English Wikipedia

## Goal of the Project
The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through September 30 2017. Wikipedia traffic is from two different Wikimedia REST API endpoints, and then to be combined into a single dataset. 

## License and Terms
[MIT License](https://opensource.org/licenses/MIT)

[CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/copyleft/fdl.html)

Wikimedia's [general Terms of Use](https://wikimediafoundation.org/wiki/Terms_of_Use/en) and [Privacy Policy](https://wikimediafoundation.org/wiki/Privacy_policy).

## Relevant API
The legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_%28legacy%29/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from January 2008 through July 2016.

The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017.

## Data

### Source Data

|  Parameters | Value  | Description  |
|---|---|---|
| project  |  en.wikipedia.org |If you want to filter by project, use the domain of any Wikimedia project, for example 'en.wikipedia.org' or 'commons.wikimedia.org'. If you are interested in all pageviews regardless of project, use all-projects.|
|  access |  mobile / desktop | If you want to filter by access method, use one of desktop, mobile-app or mobile-web. If you are interested in pageviews regardless of access method, use all-access.|
|  agent |  user | If you want to filter by agent type, use one of user or spider. If you are interested in pageviews regardless of agent type, use all-agents.|
|  granularity |  monthly | The time unit for the response data. As of today, the supported granularities for this endpoint are hourly, daily, and monthly.|
|  start | date  |The timestamp of the first hour/day/month to include, in YYYYMMDDHH format|
|  end |  date | The timestamp of the last hour/day/month to include, in YYYYMMDDHH format|

Five source data are stored under  ```data``` folder. 

Data from The legacy Pagecounts API are named as ```pagecounts_desktop-site_200801-201607.json``` and ```pagecounts_mobile-site_200801-201607.json```.  

Data from The Pageviews API are named as ```pageviews_desktop_201507-201709.json```, ```pageviews_mobile-app_201507-201709.json``` and ```pageviews_mobile-web_201507-201709.json```.

### Variables of Final Data File

Final data stores in ```en-wikipedia_traffic_200801-201709.csv```

Variables shown as follows:

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

### Data Process and Analysis

For data collected from the Pageviews API, I combine the monthly values for mobile-app and mobile-web to create a total mobile traffic count for each month. For all data, separate the value of timestamp into four-digit year (YYYY) and two-digit month (MM) and discard values for day and hour (DDHH).

A visualization for analysis is shown below:

![alt text](http://i68.tinypic.com/2qi8nsy.jpg)

From the figure above, we can see that in general desktop views are much higher than mobile views. For all views, we got the highest point around October 2013, and second highest point around 2011. And we got the lowest point around August 2009. From May 2015, a new pageview definition took effect, which elimilated all crawler traffic. Dashed lines in the figure mark old definition.

```hcds-a1-data-curation.ipynb``` contains all code and information of data processing and analysis.


## Directory Structure
```
data-512-a1 (master)
|
|     .gitignore
|     License
|     README.md
|     en-wikipedia_traffic_200801-201709.csv
|     hcds-a1-data-curation.ipynb
|     page views of english wikipedia.jpg
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
