# Dockerized ESRI Geoportal Catalog Server and Harvester 
This project bundles all prerequisites needed to run the geoportal server and a harvester are captured in this docker composition. The docker-compose.yml creates two containers, one running Tomcat with the [geoportal-server-catalog](https://github.com/Esri/geoportal-server-catalog) and the [geoportal-sharvester](https://github.com/Esri/geoportal-harvester). The second container provides the Elasticsearch server for storing and indexing the data stored in the catalog server.

## Releases and Downloads
- 2.5.0 - The  

## Installation
 
In order to 
```bash
$ docker-compose build
$ docker-compose up
```

## Requirements

* Docker

