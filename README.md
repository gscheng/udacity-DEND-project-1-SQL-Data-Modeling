# Project Summary

## Data Modeling with Postgres
### Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

A Postgres database with tables designed to optimize queries on song play analysis will be needed. The database and ETL pipeline will be tested by running queries from the Sparkify analytics team where my results will be compared with their expected results.

### Project Description
A fact and dimension tables for a star schema has been defined for this particular analytic focus, and an ETL pipeline has been created to transfer data from files in two local directories into these tables in Postgres using Python and SQL.

### Data
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json

### Schema for Song Play Analysis


### Fact Table
#### songplays (records in log data associated with song plays i.e. records with page NextSong)
- songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

### Dimension Tables
#### users (users in the app)
- user_id, first_name, last_name, gender, level

#### songs (songs in music database)
- song_id, title, artist_id, year, duration

#### artists (artists in music database)
- artist_id, name, location, latitude, longitude

#### time (timestamps of records in songplays broken down into specific units)
- start_time, hour, day, week, month, year, weekday

![Schema](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38715/1599555988/Song_ERD.png "Star Database Schema")

### Python (.py) and Jupyper Notebook (.ipynb) files
The following files are used in this project

- etl.ipynb
    - Reads and processes a single file from `song_data` and `log_data` and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
- etl.py
    - Reads and processes files from `song_data` and `log_data` and loads them into your tables. Contains code obtained from etl.ipynb
- create_tables.py
    - Drops and creates database tables. Script is run to reset database tables before each time ETL scripts are run.
- sql_queries.py
    - Contains all necessary SQL queries, and is imported into the last three files above.
- test.py
    - Displays the first few rows of each table to check database
- README.md
    - Readme file containing project summary and discussion

### Terminal Commands

The following commands can be run from the terminal in the order below.

`python sql_queries.py`

`python create_table.py`

`python etl.py`



