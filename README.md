# Project 1: Song Play Analysis with RDBMS

## Summary
* [Purpose of database](#purpose-database)
* [Database schema](#database-schema)
* [Porject structure](#project-structure)
* [Runing procedure](#runing-procedure)

------------------------------------------
#### Purpose of database
This Postgres database is to help Sparkify to optimize queries on song play analysis based on the JSON metadata about the songs and user activities on their new music streaming app. 

#### Databaase schema
Using the song and log datasets, a star schema is created for queries on song play analysis. Following tables are included:
##### Fact Table 
1. **songplays** - records in log data associated with song plays i.e. records with page `NextSong` 
    + *songplay_id (PK), start_time (FK), user_id (FK), level, song_id (FK), artist_id (FK), session_id, location, user_agent*

##### Dimension Tables 
2. **users** - users in the app 
    + *user_id (PK), first_name, last_name, gender, level*
3. **songs** - songs in music database
    + *song_id (PK), title, artist_id, year, duration*
4. **artists** - artists in music database
    + *artist_id (PK), name, location, lattitude, longitude*
5. **time** - timestamps of records in **songplays** broken down into specific units
    + *start_time (PK), hour, day, week, month, year, weekday*
    
##### Project Structure 
In addition data files, this project includes the following files:
+ `test.ipynb` - This notebook is to check the database and help to know if tables are created and data are ingested correctly 
+ `create_tables.py` - This script will drop old tables (if exist) ad re-create new tables
+ `etl.py` - This script is to build ETL processes which will read JSON every file contained in /data folder, parse them, build relations though logical process and ingest data 
+ `etl.ipynb` - It is a notebook that helps to know step by step what `etl.py` does
+ `sql_queries.py` - This file contains variables with SQL statement in String formats, partitioned by CREATE, DROP, INSERT statements plus a FIND query 

##### Running procedure 
You will not be able to run `test.ipynb`, `etl.ipynb`, or `etl.py` until you have run `create_tables.py` at least once to create the `sparkifydb` database, which these other files connect to.






