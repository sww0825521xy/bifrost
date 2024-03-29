# ELASTIC STACK {docsify-ignore-all}

## Elasticsearch

### A Distributed RESTful Search Engine

#### [https://www.elastic.co/products/elasticsearch](https://www.elastic.co/products/elasticsearch)

Elasticsearch is a distributed RESTful search engine built for the cloud. Features include:

* Distributed and Highly Available Search Engine.
 + Each index is fully sharded with a configurable number of shards.
 + Each shard can have one or more replicas.
 + Read / Search operations performed on any of the replica shards.
* Multi Tenant.
 +  Support for more than one index.
 + Index level configuration (number of shards, index storage, ...).
* Various set of APIs
 + HTTP RESTful API
 + Native Java API.
 + All APIs perform automatic node operation rerouting.
* Document oriented
 + No need for upfront schema definition.
 + Schema can be defined for customization of the indexing process.
* Reliable, Asynchronous Write Behind for long term persistency.
* (Near) Real Time Search.
* Built on top of Lucene
 + Each shard is a fully functional Lucene index
 + All the power of Lucene easily exposed through simple configuration / plugins.
* Per operation consistency
 + Single document level operations are atomic, consistent, isolated and durable.



## Kibana

Kibana is your window into the [Elastic Stack](https://www.elastic.co/products). Specifically, it's a browser-based analytics and search dashboard for Elasticsearch.

## Filebeat

Filebeat is an open source file harvester, mostly used to fetch logs files and feed them into logstash.
Together with the libbeat lumberjack output is a replacement for [logstash-forwarder](https://github.com/elastic/logstash-forwarder).

To learn more about Filebeat, check out https://www.elastic.co/products/beats/filebeat.