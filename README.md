# **New York vs. Seoul


## Summary

Let's assume that we want to find a neighborhood of Seoul that has as similiar environment as possible to that of Manhattan for a reason such as relocation or real-estate investment. So we fo for segmenting and clustering the neihborhodds of the Seoul, S.Korea, and determining which district in Seoul is most similar or dissimilar to Manhattan, NY.


[//]: # (Image References)

[image1]: ./figures/seoul1.png "seoul"
[image2]: ./figures/newyork1.png "newyork"
[image3]: ./figures/seoul2.png "seoul"
[image4]: ./figures/newyork2.png "newyork"

---

## Intro.
Notebook contains the following steps.
* Download and Explore Dataset
* Explore Neighborhoods in Seoul
* Analyze Each Neighborhood
* Cluster Neighborhoods
* Examine Clusters

## Data
The Districts (Gu) of Seoul are the twenty-five [gu "districts"; 구; 區](https://en.wikipedia.org/wiki/List_of_districts_of_Seoul) comprising Seoul, South Korea. The gu vary greatly in area (from 10 to 47 km2) and population (from less than 140,000 to 630,000). Songpa is the most populated, while Seocho has the largest area. Gu are similar to London's or New York's boroughs or Tokyo's 23 special wards, and a gu's government handles many of the functions that are handled by city governments in other jurisdictions. This city-like standing is underscored by the fact that each gu has its own legislative council, mayor and sister cities. Each gu is further divided into dong or neighborhoods. Some gu have only a few dong while others (like Jongno-gu) have a very large number of distinct neighborhoods

- Seoul7.csv
To get longitude and latitude information for each area, i have downloaded data from [a Korean govenment site](https://www.data.go.kr/dataset/3045281/fileData.do). There are 25 files that include addresses and coordinates of each area of 25 districts in Seoul. Each coordinate of area is calculated by mean() function of every addressable building coordinates' information of the area. For the convenience, I downloaded those 24 files, merged them into 1 file, and placed .csv file on the server

- Seoul_loc2.csv
Note that The coordinates information in the data file has KR2000 system. We need to change it to wgs84 system. I used pyshp and pyproj packages to convert it. The conversions, however, turned out to be erroneous and in such a case I simply used Nominatim geolocation, which was enough since the comparision was made between Manhattan, New York City and Seoul, S. Korea.

**Seoul**
![alt text][image1]

**New York**
![alt text][image2]

## Methodology
Seoul covers an area of 605/km2, has an estimated population of 9.8M(2018), and has 25 districts, and New York City covers an area of 783/km2(land only), has an estimated population of 8.1M, and has 5 boroughs. Considering size, we first compare 2 cities by grouping boroughs of NY and districts of Seoul.
In order to find similarity and dissimilarity of two cities, Seoul, S.Korea and New York City, I segmented each city into boroughs or districts, and clustered them.

- k-means(k=5)
Manhattan is 59/km2 big and has an estimate population of 1.6M, and Gangnam-gu is 35.55/km2 bia and has an estimated population of 0.65M. For the problem of finding most similar district to Manhattan, we need some distance measurement. Euclidean or Cosine distance measurement will not be adapted naively. we'll leave this problem as a future work.

**Seoul**
![alt text][image3]

**New York**
![alt text][image3]


## Results
Since New York City has 5 boroughs, I devided districs of Seoul into 5 clusters. Each cluster seems to be representative as followings.
-  Gangnam-gu,Gangseo-gu,Gwanak-gu,Nowon-gu,Dongdaemun-gu,Seocho-gu,Seongbuk -gu,Songpa-gu,Yeongdeungpo-gu,Yongsan-gu
-  Jungnang-gu,Gangdong-gu,Gangbuk-gu,Guro-gu,Dobong-gu,Yangcheon-gu,Eunpyeong -gu
-  Gwangjin-gu,Mapo-gu,Seodaemun-gu,Seongdong-gu
-  Jongno-gu,Jung-gu
-  Geumcheon-gu

## Discussion
-  Gangnam-gu,etc., group is a commercial place and center activity
-  Jungnang-gu,etc., group is outskirt residential with parks
-  Gwangjin-gu,etc., group is residential with coffee shops and cafes but less fast foods
-  Jongno-gu,etc., group is Cultural & Tourist area & Hub
-  Geumcheon-gu group is residential with fast foods

Manhattan is a place of Park,Exhibit,Art Museum,Yoga Studio,Plaza,Bakery,Garden,Bookstore,American Restaurant,Coffee Shop. And Exhibit, Art Museum seem to be important distinguishing features when Mahattan is compared with districs of Seoul.

The only group with those features is Group0(Jongno-gu, Jung-gu), since it is a place of, Korean Restaurant, Historic Site,Palace,Art Gallery,Art Museum,Italian Restaurant,Japanese Restaurant,Bookstore, Coffee Shop,Tea Room.

So, travelling folks!, if you want to find a neighborhood like Manhattan in Seoul, it is not Gang-nam as in Psy's song, but Jongro-gu in Seoul.