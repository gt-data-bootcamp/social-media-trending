#  Data Science Bootcamp | Social Media Trending

<!-- ABOUT THE PROJECT -->
## About The Project

In this project we set out to identify social media trends across multiple platforms.  
We wanted to see if what are the most popular key words (a.k.a tags/hashtags) which are used on videos.

## Extract

For this first version, we choose to use two different data sets for two platforms.

**Trending YouTube Video Statistics** (https://www.kaggle.com/datasnaek/youtube-new?select=USvideos.csv)
    - This is a CSV format data file.

**TikTok Trending Videos Statistics** (https://www.kaggle.com/erikvdven/- tiktok-trending-december-2020?select=trending.json)
    - This is a JSON format data file.

## Transform & Load

Data Transformation (cleaning, joining, filtering, aggregating, etc).

1. To start we need to clean up and filter the data sets.   We've filtered out older trend dates, and fields which were unnecessary. 
2. We renamed the columns to ensure uniformity of the datasets
3. We then merged the data into PostreSQL, in order to support future reporting.

## Analysis (https://docs.google.com/presentation/d/1STc-LUqwqCwEm3fiB2TaOD-XVJluneNe8IW-HpZf3os/edit#slide=id.p)

Based on the current data set, we have identified these as the top 5 tags used in the most popular videos, based on views.


| Tag       | Total Views for all videos |
|-----------|----------------------------|
| "Pop"     | 1350499920                 |
| "funny"   | 906181483                  |
| "comedy"  | 725433295                  |
| "Rap"     | 536997523                  |
| "Records" | 517401466                  |

Based on the current data set, we have identified these as the bottom 5 tags.

| Tag              | Total Views for all videos |
|------------------|----------------------------|
| "kentucky"       | 559                        |
| mondkapje        | 484                        |
| ikdoenietmeermee | 484                        |
| regering         | 484                        |
| ikdoenietmee     | 484                        |

There are many words used to help make videos more "searchable".  Using some popular tags or key words to identify videos, may impact how many view you get.
We would need more analysis to validate this completely, but we believe it is interesting none the less.

## Setup the application

Setup :

1. Clone the repo.
2. Create a functional user for the database.
Example:

``` sql
CREATE ROLE trends_project WITH
    LOGIN
    NOSUPERUSER
    INHERIT
    NOCREATEDB
    NOCREATEROLE
    NOREPLICATION
    ENCRYPTED PASSWORD 'XXXXXXX';  -- Choose your own !!....
```

3. Create a PostreSQL database.

``` sql
CREATE DATABASE trending_db
    WITH 
    OWNER = trends_project
    ENCODING = 'UTF8'
    LC_COLLATE = 'English_United States.1252'
    LC_CTYPE = 'English_United States.1252'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1;  -- Tweak if you need
```

4. Update DB connection parameters in notebook to align to appropriate 

``` python
# Connect to Database 
rds_connection_string = "trends_project:XXXXX@localhost:5432/trending_db"
engine = create_engine(f'postgresql://{rds_connection_string}')
```

<!-- CONTRIBUTING -->
## Contributing Only Section

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Clone the Repo
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


<!-- LICENSE -->
## License

None at this time.


<!-- CONTACT -->
## Contact

timmcgowan
danielle16
