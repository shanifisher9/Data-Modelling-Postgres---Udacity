# Sparikfy Database Creation

The purpose of creating a database is to get insights from the data and have it easily accessible. Therefore, I have created a star schema database that will be easy to read, understand and draw insights from your data.

Using this technique you will have one fact table with information about the songs that were played using Sparkify and then dimension tables that will help you get more information about the songs ex: who played them, who the artist was. The fact table is Songplays while Users, Song, Artists, and Time are the dimension tables. Using the dimension tables to join with the fact table will help you get the most useful information from your data.

I used the star schema technique to create your databases because it has the most simplified queries and can create fast calculation. This will help you  get the most useful information from your data.

### Tables

In the Database there are 5 different tables 

1. Songplays - This is the information about the songs that were played while using your app. This is the fact table.
    a. Columns: songplay_id, start_time, user_id, level, artist_id, location, user_agen
    
2. Users - This is the users who have your app.
    a. Columns: user_id, first_name, last_name, gender, level

3. Song - This has a list of all your songs.
    a. Columns: song_id, title, artist_id, year, duration

4. Artists - This is a list of all artists.
    a. Columns: artist_id, name, location, latitude, longitude

5. Time - The time that is in the table SongPlays but broken down into smaller units of time.
    a. Columns: start_time, hour, day, week, month, year, weekday

The first column in all the dimension tables is the Primary Key and using this column will allow you to connect the data to the SongPlays table.

To access all the data together each table would need to be joined to the SongPlays data. The SongPlays table is connected to each of the other tables using the Primary Key column in the tables. 

### Data

The data came from two JSON files, song_data and log_data. The song_data is data about the songs on your app and the log_data is data about the interface of your app.

I have used python/pandas to load the data into Postgresql which will allow you to run your queries and get insight from the data.

I used pandas because it is the easiest to read and load json file data. Additionally, I have used Postgresql because it is the easiest to integrate with pandas and easy to use.

### Loading The Data

To read and load the data you first need to run the create_tables.py script. It is easiest if you open a new console and run it from there. After you will need to run etl.py to help load your data into the tables.

Once both of those files are run you can access your data and write some SQL scripts in Postgresql. You can use the test.ipynb to run some test queries or complex queries and see how the data looks.

For example: If you wanted to count the amount of users that have a paid account on your app you can run:
> %sql SELECT COUNT(level), level FROM songplays GROUP BY level;

Another example: If you wanted to see how many users paid for your app and what gender they are you can use the query: 
> %sql SELECT COUNT(songplays.level), songplays.level, gender FROM songplays JOIN users ON users.user_id =songplays.user_id GROUP BY songplays.level, gender;

This could help see if you want to make a promotion or an incentive to buy the paid plan.

Additionally, you can look at the python notebook called Untitled.ipynb to look at some sample visualizations that I made.
