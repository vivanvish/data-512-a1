## Wikipedia Page View Stats: 2008 - 2018
### Project Goal
The main goal of the project is to provide a well documented, fully reproducible process that construct, analyze,
and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through September 30 2018.

## Data Source
The data are retrieved using the **Wikimedia REST APIs**. Two different APIs were used to retrieve data from varying time ranges.
- **Legacy Pagecounts API**: The Legacy Pagecounts API was used to retrieve desktop and mobile traffic data from December 2007 through July 2016.
[Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [Endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)
- **Pageviews API**: The Pageview API was used to retrieve desktop, mobile app and mobile web traffic data from July 2015 through September 2018.
[Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [Endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)

Please refer the [Wikimedia REST API Terms of Service](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions) to know more.
The data is licensed under the [MIT](https://opensource.org/licenses/MIT) license.


## Data 
All the raw data were retrieved using REST APIs are store in `.json` format. Following are the raw data files:
#### Retrieved using Pagecounts API.(Jan 2008 - Jul 2016)
- pagecounts_desktop-site_200801-201607.json  : Page visit counts from the desktop website version. 
- pagecounts_mobile-site_200801-201607.json   : Page visit counts from the mobile website version. 
#### Retrieved using Pageview API. (Jul 2015 - Sept 2018)
- pageviews_desktop_201507-201809.json        : Page visit counts from the desktop website version.
- pageviews_mobile-app_201507-201809.json     : Page visit counts from the mobile app version.
- pageviews_mobile-web_201507-201809.json     : Page visit counts from the mobile website version.

##### Analytical Dataset
The raw files were processed and combined to create the final dataset for conducting our analysis. The steps involved during processing and
consolidating the raw data are described in detail alongside the code. 

The file is stored as `en-wikipedia_traffic_200712-201809.csv`. It has the following structure:

Column | Value | Description |
| ------------- |:-------------:| -----|
year | YYYY | Year corresponding to the data.(2008-2018)|
month | MM | Month corresponding to the data.(2008-2018)|
pagecount_all_views | num_views | Total page views retrieved from Pagecount API. |
pagecount_desktop_views | num_views | Desktop version page views retrieved from Pagecount API. |
pagecount_mobile_views | num_views | Mobile version page views retrieved from Pagecount API. |
pageview_all_views | num_views | Total page views retrieved from Pageview API. |
pageview_desktop_views | num_views |  Desktop version page views retrieved from Pageview API. |
pageview_mobile_views | num_views |  Mobile version (Website + App) page views retrieved from Pageview API. |

All data files are stored in the `data` folder.

## Code
All the code involved in this project are saved as a `Jupyter notebook` : `hcds-a1-data-curation.ipynb`.

The notebook was divided into 3 sections:
- Data Acquisition: Covers the portion of acquiring the data from REST APIs and saving the raw data as `.json` files. 
- Data Processing: Covers the portion of processing and consolidating the raw data files into a `dataframe` format.
- Analysis: Involves exploring the analytical dataset and plotting the time series graphs and saving the plot.

The notebook runs on Python 3.6 and the following packages are needed to run:
- datetime
- json
- matplotlib
- numpy
- os
- pandas
- requests

The final result is saved as a .png file which also has been published here as : `wiki_pageviews_2008_2018.png`

## License
The code is licensed under [MIT](LICENSE).

## Contact
In case of any queries, please contact me at vishnn@uw.edu

