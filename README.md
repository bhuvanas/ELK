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
* [Download data](#download data)
* [Loading Collision data into Elasticsearch](#Loading Collision data into Elasticsearch)

### Installation & Setup
* Install ELK stack by following instructions in [setup guide] (https://github.com/elastic/examples/blob/master/Installation%20and%20Setup.md)
* Install the X-Pack in Kibana and Elasticsearch 

  ```shell
  <path_to_elasticsearch_root_dir>/elasticsearch-plugin install x-pack
  <path_to_kibana_root_dir>/bin/kibana-plugin install x-pack
  ```

* Run Elasticsearch & Kibana

  ```shell
  <path_to_elasticsearch_root_dir>/bin/elasticsearch
  <path_to_kibana_root_dir>/bin/kibana
  ```


The following assumes the default username and password of "elastic" and "changeme".  These can be changed as detailed [here](https://www.elastic.co/guide/en/shield/current/native-realm.html).

### Download data 
* Download the CSV version of the NYPD Motor Vehicle Collision dataset from the [NYC Open Data Portal](https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95?). 
Rename the downloaded CSV file to `nyc_collision_data.csv`.

  ```
  mkdir nyc_collision
  cd nyc_collision
  wget https://data.cityofnewyork.us/api/views/h9gi-nx95/rows.csv?accessType=DOWNLOAD -O collision_data.csv
  ```
  
### Loading Collision data into Elasticsearch
* Load the Collision data into Elasticsearch using Logstash by running the following command:
```
cat collision_data.csv | <path_to_logstash_home>/bin/logstash -f logstash_collision.conf
```

### Configure Kibana for Index
  
  * Access Kibana by going to `http://localhost:5601` in a web browser
  * Connect Kibana to the `nyc_collision` index in Elasticsearch
      * Click the **Management** tab >> **Index Patterns** tab >> **Create New**. Specify `movie_lens_users` as the index pattern name, ensuring **Index contains time-based events** is **not** selected, and click **Create** to define the index pattern.
  * Open graph
      * Click on **Graph** tab.
 ### Explore Recommendations
    
   * Select index `index name` in the upper left. 
   * Add the field `contributing_factors` as graph nodes using the (+) icon.  Select an appropriate icon/colour for the node types. 
   * search for all the matching using '*'.Expand nodes to see the correlated contributing factors. 
   * Try turning off **Settings** >> **Significant Links** to see the connections.
