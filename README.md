# **New York vs. Seoul**


## Summary

Let's assume that we want to find a neighborhood in Seoul that has as similiar environment as possible to that of Manhattan. And this may be for the purpose of relocation, travel, or real-estate investment. So we fo for segmenting and clustering the neihborhoods of Seoul, S.Korea, and determining which district in Seoul is most similar to Manhattan, NY.


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
The number of districts (Gu) of Seoul is the twenty-five [gu "districts"; 구; 區](https://en.wikipedia.org/wiki/List_of_districts_of_Seoul). The gu vary greatly in area (from 10 to 47 km2) and population (from less than 140,000 to 630,000). Songpa-gu is the most populated, while Seocho-gu has the largest area. Gu is similar to London's or New York's borough or Tokyo's ward.

- Seoul7.csv
To get longitude and latitude information for each area, i have downloaded data from [a Korean govenment site](https://www.data.go.kr/dataset/3045281/fileData.do). There are 25 files that include addresses and coordinates of each area of 25 districts in Seoul. Each coordinate of area is calculated by mean() function of every addressable building coordinates' information of the area. For convenience, I downloaded those 24 files, merged them into a file.

- Seoul_loc2.csv
Note that the coordinate data in the file has KR2000 system. We need to change it to wgs84 system. I used pyshp and pyproj packages to convert it. The conversions, however, contains errors, so i used Nominatim geolocation for comparison.

**Seoul**
![alt text][image1]

**New York**
![alt text][image2]

## Methodology
Seoul, an area of 605/km2 with 9.8M(2018) population, has 25 districts. New York, an area of 783/km2(land only) with 8.1M population, has 5 boroughs. Considering size, we first compare 2 cities by grouping boroughs of NY and districts of Seoul.

Features of two cities, i vectorized venue categories and venue's frequency of neighborhood. Then i clustered them with k-means(k=5) for a quick (first 5) analysis and comparison. Numerical similarity measurement(i.e., Euclidean or Cosine distance) for the entire dimesions was not calculated.
  
**Seoul**
![alt text][image3]

**New York** 
![alt text][image3]


## Results
Since New York has 5 boroughs, I divided districts of Seoul into 5 clusters. Each cluster seems to be representative as followings.
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

So, travelling folks!, if you want to find a neighborhood like Manhattan in Seoul, it is not Gang-nam as in Psy's song, but Jongro-gu in Seoul, according to my simple data science analysis!