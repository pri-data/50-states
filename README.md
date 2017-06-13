# Data for PRI's The World 50 States project

They are two datasets stored in this repo. They are used to build the interactive widget and data visualizations for PRI's The World series [50 States](link).

## Estimates of median household income in 1989 and 2015 for counties in the US

The data are from the [Small Area Income and Poverty Estimates (SAIPE)](https://www.census.gov/did/www/saipe/index.html) by the Census Bureau . 

They were downloaded from the following webpages on May 25, 2017; 9:11am ET.
* [2015 SAIPE data](https://www.census.gov/did/www/saipe/data/statecounty/data/2015.html)
* [1989 SAIPE data](https://www.census.gov/did/www/saipe/downloads/estmod89/)

The reason to use SAIPE data for median household income is stated [here](https://www.census.gov/topics/income-poverty/guidance/data-sources.html).

### Data code sheet
* `income-2005` is the estimate of 2015 median household income in 2015 dollars. Data recorded as `.` indicates it is not available. Data recorded as `null` indicates there is major boundary change to the county making the data incomparable.
* `income-1989a` is the estimate of 1989 median household income in 1989 dollars. Data recorded as `.` indicates it is not available. Data recorded as `null` indicates there is major boundary change to the county making the data incomparable.
* `income-1989b` is the estimate of 1989 median household income in 2015 dollars. This is calculated based on the primary data in `income-1989a`. Data is recorded as `null` if the primary data is recorded as `.` or `null`.
* `change` is the percentage change between 1989 median household income estimate and 2015 median household income estimate based on 2015 dollars.

The inflation adjustment for 1989 median household income estimates is calculated using the [CPI-U-RS](https://www.census.gov/topics/income-poverty/income/guidance/current-vs-constant-dollars.html). The CPI-U-RS for 2015 is 348.2 while the CPI-U-RS for 1989 is 188.6.

### Embed the interactive widget

The [interactive widget](https://cdn2.pri.org/embeds/2017-06/50states-widget-606.html) for median household income can be embedded as an iframe.
The embed code:
```
<iframe frameborder="0" height="606" scrolling="no" src="https://cdn2.pri.org/embeds/2017-06/50states-widget-606.html" width="100%"></iframe>
```

To set the default county when the iframe is loaded, add the county FIPS code as a query string at the end of the url.
For example, the FIPS code for New York county, NY is 36061. To set the county as the default county, append `?FIPS=36061` at the end of the url.

```
https://cdn2.pri.org/embeds/2017-06/50states-widget-606.html?FIPS=36061
```

Find the FIPS of a county from the [census website](https://www.census.gov/geo/reference/codes/cou.html). 

## Employment by industry in 1990 and 2015 for counties in the US 

The data are from the [Quarterly Census of Employment and Wages (QCEW)](https://www.bls.gov/cew/) by the Bureau of Labor Statistics. 

They were downloaded from [here](https://www.bls.gov/cew/datatoc.htm#NAICS_BASED) under the "CSVs By Industry" and "Annual Averages" categories on May 11, 2017; 11:35am ET. The data are classified using the [North American Industry Classification System (NAICS)](https://www.census.gov/eos/www/naics/). However, only data of the [NAICS supersectors](https://data.bls.gov/cew/doc/titles/industry/industry_titles.htm) (except the "Unclassified" supersector) are used for the visualizations.

### Data code sheet
* `all` is the total employment in an industry. Data recorded as `0` indicates it has been suppressed. Data recorded as `null` indicates there's no such industry or there's major boundary change to the county making the data incomparable.
* `num` is the annual average of monthly employment levels for a given year. Data recorded as `0` indicates it has been suppressed. Data recorded as `null` indicates there's no such industry or there's major boundary change to the county making the data incomparable.
* `pct` is the percentage of total employment in an industry (supersector). It is calculated by dividing the employment in an industry by the total employment. Data is recorded as `null` if the primary data is recorded as `0` or `null`.
* `1990` and `2015` indicates the year of the data.
* The four-digit code after the year indicates the industry (supersector). 

#### Industry (supersector) codes and titles
* `1011` Natural resources and mining
* `1012` Construction
* `1013` Manufacturing
* `1021` Trade, transportation, and utilities
* `1022` Information
* `1023` Financial activities
* `1024` Professional and business services
* `1025` Education and health services
* `1026` Leisure and hospitality
* `1027` Other services
* `1028` Public administration
* `1029` Unclassified (excluded in this dataset)

For example, `num-1990-1025` is the total employment in the education and health services supersector in 1990.

The data of supersector "Unclassified" is not shown in this dataset. However the total employment (`num`) includes this data.

#### License
[MIT License](https://github.com/pri-data/50-states/blob/master/LICENSE)