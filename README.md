#Using Graph to Analyze NYC Traffic Collision Data
This project uses Elastic Stack to analyze traffic collision data. Graph plugin is used to visualize the correlations between the factors contributing to collisions. The [NYPD Motor Vehicle Collision data](https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95?) analyzed in this example is from the [NYC Open Data](https://data.cityofnewyork.us/) initiative.

##### Version
This project has been implemented using the following versions:
- Elasticsearch 5.1.1
- Logstash 5.1.1
- Kibana 5.1.1
- X Pack 5.1

### Contents
* [Installation & Setup](#installation--setup)

### Installation & Setup
* Install ELK stack by following instructions in [setup guide] (https://github.com/elastic/examples/blob/master/Installation%20and%20Setup.md)

### Download data 
* Download the CSV version of the NYPD Motor Vehicle Collision dataset from the [NYC Open Data Portal](https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95?). Rename the downloaded CSV file to `nyc_collision_data.csv`.
  ```
  mkdir nyc_collision
  cd nyc_collision
  wget https://data.cityofnewyork.us/api/views/h9gi-nx95/rows.csv?accessType=DOWNLOAD -O nyc_collision_data.csv
  ```
  

