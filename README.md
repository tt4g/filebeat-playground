# Overview

Run Elasticsearch, Kibana and Filebeat on Docker.

## URL

* Elasticsearch 

  http://filebeat-playground-elasticsearch-01:9200 or http://127.0.0.1:9200

* Kibana

  http://filebeat-playground-kibana:5601 or http://127.0.0.1:5601

## .env files

Create the following *.env files:

* .elasticsearch.env
* .kibana.env
* .logstash.env

## Commands

### Up

Launch Elasticsearch, Kibana and Filebeat.

````bash
docker-compose up -d
````

Only build container.

````bash
docker-compose build
````

### Down

Stop and remove docker container and networks.

````bash
docker-compose down --volumes
````

Down and remove all images.

````bash
docker-compose down --rmi all --volumes
````

### List

List images.

````bash
docker-compose images
````

List containers.

````bash
docker-compose ps
````

### Delete

````bash
docker-compose rm
````
