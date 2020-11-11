import configparser


# CONFIG
config = configparser.ConfigParser()
config.read('dwh.cfg')

DB_ROLE_ARN = config.get("IAM_ROLE","ARN")
KEY                    = config.get('AWS','KEY')
SECRET                 = config.get('AWS','SECRET')

# DROP TABLES

staging_events_table_drop = "drop table if exists staging.events"
staging_songs_table_drop = "drop table if exists staging.song_data"
songplay_table_drop = "drop table if exists production.songplays"
user_table_drop = "drop table if exists production.users"
song_table_drop = "drop table if exists production.songs"
artist_table_drop = "drop table if exists production.artists"
time_table_drop = "drop table if exists production.time"

# CREATE TABLES

staging_events_table_create= ("""
   CREATE TABLE staging.events (
   artist TEXT,
   auth TEXT,
   firstname TEXT,
   gender TEXT,
   iteminsession INT,
   lastname TEXT,
   length NUMERIC,
   level TEXT,
   location TEXT,
   method TEXT,
   page TEXT,
   registration NUMERIC,
   session_id INT,
   song TEXT,
   status INT,
   ts BIGINT,
   useragent TEXT,
   user_id INT
    )
    diststyle all;
""")

staging_songs_table_create = ("""
CREATE TABLE staging.song_data (
   artist_id TEXT, 
   artist_latitude DOUBLE PRECISION,
   artist_location TEXT,
   artist_longitude DOUBLE PRECISION,
   artist_name TEXT,
   duration DOUBLE PRECISION,
   num_songs INTEGER,
   song_id TEXT,
   title TEXT,
   year INTEGER
    )
    diststyle all;
""")

songplay_table_create = ("""
CREATE TABLE production.songplays (
    songplay_id INTEGER IDENTITY(0,1),
    start_time TIMESTAMP NOT NULL,
    user_id  VARCHAR(10) NOT NULL, 
    level  VARCHAR(10) NOT NULL, 
    song_id  VARCHAR(10) NOT NULL, 
    artist_id  VARCHAR(10) NOT NULL, 
    session_id INTEGER NOT NULL, 
    location VARCHAR(10) NOT NULL, 
    user_agent VARCHAR(10) NOT NULL
    )
    diststyle all;
""")

user_table_create = ("""
CREATE TABLE production.users (
    user_id VARCHAR(10) NOT NULL,
    first_name VARCHAR(10) NOT NULL,
    last_name VARCHAR(10) NOT NULL, 
    gender VARCHAR(10) NOT NULL,
    level VARCHAR(10) NOT NULL
    )
    diststyle all;
""")

song_table_create = ("""
CREATE TABLE production.songs (   
   song_id VARCHAR(10) NOT NULL,
   title VARCHAR(10) NOT NULL,
   artist_id INTEGER NOT NULL,
   year VARCHAR(10) NOT NULL,
   duration DOUBLE PRECISION NOT NULL)
   diststyle all;
""")

artist_table_create = ("""
CREATE TABLE production.artists (
    artist_id VARCHAR(10) NOT NULL,
    name VARCHAR(10) NOT NULL,
    location VARCHAR(10) NOT NULL,
    longitude DOUBLE PRECISION NOT NULL,
    latitude DOUBLE PRECISION NOT NULL
    )
    diststyle all;
""")

time_table_create = ("""
CREATE TABLE production.time(
    start_time TIMESTAMP NOT NULL, 
    hour INTEGER NOT NULL,
    day INTEGER NOT NULL,
    week INTEGER NOT NULL,
    month VARCHAR(10) NOT NULL,
    year INTEGER NOT NULL, 
    weekday VARCHAR(10) NOT NULL
    )
    diststyle all;
""")

# STAGING TABLES

staging_events_copy = ("""
copy staging.events from 's3://udacity-dend/log_data' 
access_key_id '{}'
secret_access_key '{}'
region 'us-west-2'
json 'auto'
compupdate off
""").format(KEY,SECRET)

staging_songs_copy = ("""
copy staging.events from 's3://udacity-dend/song_data' 
access_key_id '{}'
secret_access_key '{}'
region 'us-west-2'
json 'auto'
compupdate off
""").format(KEY,SECRET)


# FINAL TABLES

songplay_table_insert = ("""
""")

user_table_insert = ("""
""")

song_table_insert = ("""
""")

artist_table_insert = ("""
""")

time_table_insert = ("""
""")

# QUERY LISTS

create_table_queries = [staging_events_table_create, staging_songs_table_create, songplay_table_create, user_table_create, song_table_create, artist_table_create, time_table_create]

#create_table_queries = [staging_events_table_create]


drop_table_queries = [staging_events_table_drop, staging_songs_table_drop, songplay_table_drop, user_table_drop, song_table_drop, artist_table_drop, time_table_drop]

#drop_table_queries = [staging_events_table_drop, staging_songs_table_drop]


#copy_table_queries = [staging_events_copy, staging_songs_copy]

copy_table_queries = [staging_songs_copy]

insert_table_queries = []


#insert_table_queries = [songplay_table_insert, user_table_insert, song_table_insert, artist_table_insert, time_table_insert]
