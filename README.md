**Sparkify Data Lake Project with Apache Spark**

**Introduction**
Sparkify, a music streaming startup has continued to grow their user and song database and want to move their data warehouse into a data lake. Their data currently resides in S3 in a directory of JSON logs on user activity on their app as well as a directory with JSON metadata on the songs in their app.  

The purpose of this project is to build an ETL pipeline that can extract data from an S3 bucket, process the data using Spark then load the data back into S3 as a set of dimensional tables in Spark parquet files. The Spark process is deployed on a cluster using AWS. This will allow the analytics team to continue finding insights on what the users are listening to

**SCHEMA DESIGN**
The created tables include a fact table - **‘songplays’** and four dimension tables - **‘users’, ‘songs’, ‘artists’ ** and **‘time’.**  This follows the start schema principle which is suitable for performing analytical operations to gather more insights.

**DATA**
The data for this project is available on Amazon S3.
•	Song data: s3://udacity-dend/song_data
•	Log data: s3://udacity-dend/log_data

**Song Dataset**
The song dataset is a subset of real data from the **Million Song Dataset**. Each file is in JSON format and contains metadata about a song and the artist of that song.
The files are partitioned by the first three letters of each song's track ID. Below is an example of the filepath to a file in this dataset.

s3://udacity-dend/song_data/A/A/B/TRAABJL12903CDCF1A.json
Below is an example of a single song file, TRAABJL12903CDCF1A.json.
{
    "num_songs": 1, 
    "artist_id": "ARJIE2Y1187B994AB7", 
    "artist_latitude": null, 
    "artist_longitude": null, 
    "artist_location": "", 
    "artist_name": "Line Renaud", 
    "song_id": "SOUPIRU12A6D4FA1E1", 
    "title": "Der Kleine Dompfaff", 
    "duration": 152.92036, <br>
    "year": 0    
}

**Log Dataset**
The log dataset consists of log files in JSON format generated based on the songs in the dataset above. These simulate activity logs from the music streaming app. The JSON logs on user activity have the following structure.

![log dataset structure](https://user-images.githubusercontent.com/116004104/213382358-55e12f4a-b9bb-4972-b1e9-ac778f1b545a.png)
 
**SCHEMA**
The star schema is optimized to run analytics queries for the songplay data

![schema](https://user-images.githubusercontent.com/116004104/213382539-706f8779-7462-4a9d-8851-920db1d74049.jpeg)


**Project Files**
The project workspace includes 3 files:
1.	**dl.cfg **Contains the AWS access keys
2.	**etl.py** Retrieves the song and log data from the S3 bucket, transforms the data into fact and dimensional tables then loads the table data back into S3 as parquet files.
3.	**README.md** Contains project information 

**Instructions**
1.	Set the key and secret in the **dl.cfg** file

[AWS]
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=

2.	Build the ETL pipeline to run the datasets on **etl.py**
3.	Execute the ETL pipeline script by running: **$ python etl.py**


