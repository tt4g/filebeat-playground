# Overview

Run Elasticsearch, Kibana and Filebeat on Docker.

## .env files

Create the following *.env files:

* .elasticsearch.env
* .filebeat.env
* .kibana.env
* .logstash.env

## Usage

Run `docker-compose up -d` after creating *.env files.

Try add new `.log` file to `./var/filebeat/log/`.

Example: `./var/filebeat/log/foo.log`

```plaintext
foo bar
baz qux
```

Filebeat read `foo.log` and send Logstash.

Logstash analyzes and parses the messages provided by Filebeat.
After that, the messages is sent from Logstash to ElasticSearch and stored in
the `%{[@metadata][beat]}-%{[@metadata][version]}-sample-%{+YYYY.MM.dd}` index.
In addition, the message is saved to `./var/logstash/sample_logstash_file/sample-%{+YYYY-MM-dd}.txt`.

Example: `./var/logstash/sample_logstash_file/sample-%{+YYYY-MM-dd}.txt`

```plaintext
[message] foo bar [suffix] foo
[message] baz qux [suffix] baz
```

## URL

* Elasticsearch

  http://filebeat-playground-elasticsearch-01:9200 or http://127.0.0.1:9200

* Kibana

  http://filebeat-playground-kibana:5601 or http://127.0.0.1:5601

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
