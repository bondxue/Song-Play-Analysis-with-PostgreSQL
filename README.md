# Project 1: Song Play Analysis with RDBMS

## Summary
* [Purpose of database](#purpose-database)
* [Database schema](#database-schema)
* [Porject structure](#project-structure)
* [Data cleaning](#data-cleaning)
* [Runing procedure](#runing-procedure)

------------------------------------------
### Purpose of database
This Postgres database is to help Sparkify to optimize queries on song play analysis based on the JSON metadata about the songs and user activities on their new music streaming app. 


--------------------------------------------
### Databaase schema
Using the song and log datasets, a `star schema` is created for queries on song play analysis. 

![schema](images/schema.PNG)

Following tables are included:
#### Fact Table 
1. **songplays** - records in log data associated with song plays i.e. records with page `NextSong` 
    + *songplay_id (PK), start_time (FK), user_id (FK), level, song_id (FK), artist_id (FK), session_id, location, user_agent*
    ![songplay table](images/songplay_table.PNG)

#### Dimension Tables 
2. **users** - users in the app 
    + *user_id (PK), first_name, last_name, gender, level*
    ![songplay table](images/users_table.PNG)
3. **songs** - songs in music database
    + *song_id (PK), title, artist_id, year, duration*
    ![songplay table](images/songs_table.PNG)
4. **artists** - artists in music database
    + *artist_id (PK), name, location, lattitude, longitude*
    ![songplay table](images/artists_table.PNG)
5. **time** - timestamps of records in **songplays** broken down into specific units
    + *start_time (PK), hour, day, week, month, year, weekday*
    ![songplay table](images/time_table.PNG)

--------------------------------------------
### Project Structure 
In addition data files, this project includes the following files:
+ `test.ipynb` - This notebook is to check the database and help to know if tables are created and data are ingested correctly 
+ `create_tables.py` - This script will drop old tables (if exist) ad re-create new tables
+ `etl.py` - This script is to build ETL processes which will read JSON every file contained in /data folder, parse them, build relations though logical process and ingest data 
+ `etl.ipynb` - It is a notebook that helps to know step by step what `etl.py` does
+ `sql_queries.py` - This file contains variables with SQL statement in String formats, partitioned by CREATE, DROP, INSERT statements plus a FIND query 

--------------------------------------------
### Data Cleaning
When we create **songplays** table, we set `start_time` and `user_id` to be `NOT NULL`, which will prevent the entry of NULL values into the table for those cloumns. 

--------------------------------------------
### Running procedure

To create the `sparkifydb` database and tables, we need to run `create_tables.py` from the terminal. Then run `test.ipynb` to confirm the creation of your tables with the correct columns. Next, we need to run `etl.ipynb` from the terminal also to read all files from `song_data` and `log_data` into tables. Finally, we need to run `test.ipynb` to confirm your records were successfully inserted into each table.









