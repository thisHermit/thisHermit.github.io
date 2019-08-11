---
layout: post
title: "Best Place for Restaurant in Scarborough Toronto"
date: "2019-08-11 17:17:01 +0530"
---

## Introduction

### Description & Discussion of the Background

Scarborough is an administrative division in Toronto, Ontario, Canada.
Situated atop the eastern the Scarborough Bluffs, it occupies the
eastern part of the city. It is also a popular destination for new
immigrants in Canada to reside.

Its population density is 3,367.6/km2 (8,722/sq mi) and has a total
size of 187.70 km2 (72.47 sq mi) ([more info here](https://en.wikipedia.org/wiki/Scarborough,_Toronto)).

Being present in the largest city of Canada, and the fact that it is a
popular immigration location, it has a lot of diversity. As a result,
this increases the potential in revenue for recreational activities as
more people from different cities with different tastes settle there.
Therefore it is advantageous to have information about the existing
restaurants to gain a competitive edge over other such businesses.

To find a good location to set up a new restaurant could be tricky. We
can use some algorithms to simplify this process.

### Data Description

The data is retrieved from these sources

* Postal Code and name is retrieved from [Wikipedia](https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M).
* I used the Geospatial Coordinates from [here](https://cocl.us/Geospatial_data)
* I used Foursquare API to get the most common venues of the Neighborhoods and also their popularity in the form of likes.

## Methodology

I used BeautifulSoup to get the data from Wikipedia and then converted
it to Pandas Dataframe
![]({{ site.url }}/assets/Screenshot_2019-08-11_19-30-40.png)

Then I mereged with the Geospatial Coordinates. 
![]({{ site.url }}/assets/Screenshot_2019-08-11_19-32-24.png)

Here is a map of the Neighborhoods in discussion.
![]({{ site.url }}/assets/scarborough_map.png)

Then using the Foursquare API the venues in the Neighborhoods are collected. This is a sample of the result.
![]({{ site.url }}/assets/venues_list.png)

The Venue Categories are converted into a one hot form to apply K means to it later.
![]({{ site.url }}/assets/one_hot.png)

The most common 10 venues for each Neighborhood is found and added as a column in the dataset.
![]({{ site.url }}/assets/most_common_venues.png)

Then the likes for the individual neighborhoods are added.
![]({{ site.url }}/assets/venues_with_likes.png)

Now, the mean for all the likes for each venue category in each neighborhood is found.
![]({{ site.url }}/assets/likes_for_neighborhoods.png)

Using the previous dataset the likes for the venues are found.
![]({{ site.url }}/assets/likes_for_common_venues.png)

The number of likes are summed for each row if the most common venue is a Restaurant.
![]({{ site.url }}/assets/restaurant_likes.png)

## Results

As a initial exploratory analysis, the neighborhood is sorted on the basis of likes.
![]({{ site.url }}/assets/sorted_rests.png)

Elbow Method is used to find the appropriate number of clusters.
![]({{ site.url }}/assets/elbow_method.png)

This is the final result after applying k means
![]({{ site.url }}/assets/clustered_map.png)

## Discussion

Data from more social media outlets could be collected to perform a
better evaluation of the popularity of the venues. Also some other
algorithms for clustering could be performed which work on less data and
higher dimensional datasets.

## Conclusion

In this study, the optimal location to open a new restaurant was found
by clustering the localities by taking in account their similarities and
dissimilarities in popularity. This model can be useful for stakeholders
as a starting point for opening a new restaurant in Scarborough, Toronto.
