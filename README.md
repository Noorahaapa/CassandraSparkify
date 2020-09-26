# Songplay analytics for Sparkify using Cassandra

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app.
In the earlier excercise we used Postgres database but in this excericise we are exploring NoSQL databases and using Casandra.
ETL process retrieves and transforms the data to be inserted into three tables that are created for three prespecified queries.  
This document details the Jupyter notebook that contains the ETL process, code for creating database tables and queries for testing those tables. 

## Tables
Given the nature of NoSQL databases, a table is specified for each query.

**song_length table**
- The first table gives responses to following query: retrieve name of artist, song and song length for a session with ID 338 and item in session being 4.
- Given that the query specifies particular sessionID and iteminSession, sessionID had to be a composite primary key of SessionID and iteminSession. 

**artist_song_user table**
- The second table gives responses to query that retrieves names of artists and songs and the first and last names of user from artist_song_user table for
  a user with userID of 10 while sessionID is 182 and orders them by iteminSession.
- Given the query primary key is composite key of UserID and sessionID with iteminSession being clustering key to allow ordering.

**users_all_hands table**
- The for the third table query retrieves the first and last names of those users, who listened to song All Hands Against His Own.
- Due to a particular song being used to filter the results while we want to know information about user, a composite key of song and userID is needed.

## How it works

CasandraSparkifyProject1B.ipynb in Part I contains the code for creating the ETL process from the relevant files (event_data also included into this repository). 
Part II establishes connection to the database, Part III creates tables and tests them with queries and Part IV closes the session and database connection.

## Description of files in repository

**CassandraSparkifyProject1B.ipynb** 
- This file contains ETL process that retrieves and transforms data from event_data files.
- Also contains queries for inserting data. 
- The file also has a queries that test each table.
- The file also sets up and in the end closes connection to database.

**event_data**
- Data to be inserted into the different tables created.

**images**
- This file contains a picture of the CSV of event data for visualisation purposes.
