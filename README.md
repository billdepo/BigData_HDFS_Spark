# BigData HDFS Spark
DSML NTUA Big Data Management Systems semester project.

In this course, we setup a Hadoop file system (HDFS) on two VMs on the [
grnet okeanos cloud service](https://astakos.okeanos-knossos.grnet.gr/). Also, we setup Spark in order to be used as 
the computation engine for a set of 6 queries on input data. Two VMs are utilized as a cluster for the computations.
We implement the queries in three different ways:
- RDD API reading input from csv files
- SparkSQL reading input from csv files
- SparkSQL readig input from parquet files

The input files concern charts data about songs from Spotify from year 2017 to 2021 (60 months) for a set of 69
countries detailing the chart position of a song for a specific date, country and chart (two options: viral50 and 
top 200). It also contains information on the number of streams for the song, its chart position and its
relative movement within the chart. The input files set contains 4 csv files: charts.csv, regions.csv,
chart_artist_mapping.csv and artists.csv.

Those csv files are also converted to parquet files within the HDFS and are then read by Python scripts utilizing 
either the RDD API (map-reduce transformations and actions) or SparkSQL (SQL commands) in order to derive on
results. Then, we record the results and compare the execution time required for each implementation.

Directories:
- files: contains the input csv files
- code: contains the scripts that implement the queries
- output: contains the csv files of the results generated by the queries execution (those were copied from the HDFS where they were written by the scripts)
- other: contains the execution time for each script / query implementation
- project setup: set of pdf files detailing how the VMs are setup as well as HDFS and Spar

Files:
- Report.pdf: final latex report documenting the queries, results and execution times
- Project description.pdf: pdf containing the instructions on the queries implementation


**charts.csv (~2GB):**
```

| song_id | song_name | chart_position | date                          | country_id | chart   | relative_movement | streams |
|---------|-----------|----------------|-------------------------------|------------|---------|-------------------|---------|
| 1607    | +         | 9              | 2020-01-13T00:00:00.000+02:00 | 46         | viral50 | NEW_ENTRY         | ""      |
| 1607    | +         | 11             | 2020-01-14T00:00:00.000+02:00 | 46         | viral50 | MOVE_DOWN         | ""      |
| 1607    | +         | 12             | 2020-01-15T00:00:00.000+02:00 | 46         | viral50 | MOVE_DOWN         | ""      |
| 1607    | +         | 38             | 2020-02-01T00:00:00.000+02:00 | 46         | viral50 | MOVE_DOWN         | ""      |
| 1607    | +         | 32             | 2020-02-02T00:00:00.000+02:00 | 46         | viral50 | MOVE_UP           | ""      |
```

**regions.csv (~1KB):**
```
| country_id | country_name |
|------------|--------------|
| 1          | Andorra      |
| 2          | Argentina    |
| 3          | Australia    |
| 4          | Austria      |
| 5          | Belgium      |
```

**chart_artist_mapping.csv (~3.3KB):**
```
| song_id | artist_id |
|---------|-----------|
| 15117   | 1         |
| 186929  | 2         |
| 35982   | 3         |
| 81472   | 3         |
| 154203  | 3         |
```

**artists.csv (~1.5KB):**
```
| artist_id | artist_name                        |
|-----------|------------------------------------|
| 1         | ""                                 |
| 2         | อุ๋ย Buddha Bless                  |
| 3         | !!!                                |
| 4         | !Regeringen                        |
| 5         | "\"\"\"Elena Of Avalor\"\" Cast\"" |
```
