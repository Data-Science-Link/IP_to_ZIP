# IP Addresses to ZIP Codes

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Data Processing](#analysis)
	- [Latitude and Longitude](#latitude_and_longitude)
	- [Geographic Information](#geographic_information)
- [Conclusion](#conclusion)

## Introduction
Many marketing and advertising teams are starting to recognize the value of geolocating their users. Determining which country, state, or zip code the customers live in can help to:
 - Understand where your product is popular
 - Test whether marketing campaigns are equally effective between regions
 - Create targeted advertisements

 
 This *proof of concept* jupyter notebook shows that it is possible to convert user IP addresses into geolocations (latitude, longitude, zip code, country, etc.)

## Dataset
The IP addresses come from a [Kaggle competition](https://www.kaggle.com/takahiroanno/ip-address-analysis?select=ipaddresstrain.csv). These addresses were scraped from commenters on Wikipedia articles. For the purpose of this analysis we will ignore the wikipedia comments and only analyze the IP addresses.

  ![image](/docs/imgs/ip_addresses.png)

  *Excerpt of IP addresses from dataset*

## Data Processing
### Latitude and Longitude
By using ip2geotools, IP addresses were converted into latitude and longitude.

"[ip2geotools](https://pypi.org/project/ip2geotools/) is a simple tool for getting geolocation information on given IP address from various geolocation databases. This package provides an API for several geolocation databases." - Documentation

  ![image](/docs/imgs/lat_lon.png)

  *Excerpt of transformed data with Lat Lon information*

### Geographic Information
By using geopy, latitude and longitude values were converted into geographical information. Pulled geographical information includes *building, house_number, neighbourhood,city, county, state, postcode, country, and country_code.*

"[geopy](https://geopy.readthedocs.io/en/stable/) makes it easy for Python developers to locate the coordinates of addresses, cities, countries, and landmarks across the globe using third-party geocoders and other data sources." - Documentation

  ![image](/docs/imgs/full.png)

  *Excerpt of transformed data with Geo information*

### Conclusion
By using two API's, ip2geotools & geopy, we were able to:
 - Grab the latitude and longitude from the IP address
 - Grab the zip code and other geographical information from the latitude and longitude

The major limitation of the aforementioned process is the runtime of the script. Pulling latitude and longitude information from IP addresses took 0.8 seconds per entry. Pulling geographical information from latitude and longitude took 1.8 seconds per entry. Performing these operations at scale requires code optimization. Further research is needed to determine faster techniques to convert IP addresses into Zip codes. 

*"Everything is possible. The impossible just takes longer"* - Dan Brown