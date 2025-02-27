---
title: Services
last_updated: Sep 15, 2020
template: howto-guide-template
originalLink: https://documentation.spryker.com/v5/docs/services
originalArticleId: 0e4f58e4-8a89-44e9-96ff-864c483461a0
redirect_from:
  - /v5/docs/services
  - /v5/docs/en/services
related:
  - title: Deploy File Reference - 1.0
    link: docs/scos/dev/the-docker-sdk/page.version/deploy-file-reference-1.0.html
  - title: Docker SDK
    link: docs/scos/dev/the-docker-sdk/page.version/the-docker-sdk.html
---

## General Information
This page describes configuration options of the services shipped with Spryker in Docker by default.  Find the list of the services below:

*     Database
*     ElasticSearch
*     Kibana UI
*     RabbitMQ
*     Swagger UI
*     Redis
*     Redis GUI
*     MailHog
*     Blackfire
*     New Relic

{% info_block infoBox %}

* Before you start configuring a service, make sure to install or update Docker SDK to the latest version:
```bash
git clone https://github.com/spryker/docker-sdk.git ./docker
```
 
* After enabling a service, make sure to apply the new configuration:
    1. Bootstrap docker setup:
    ```bash
    docker/sdk boot {deploy.yaml | deploy.dev.yaml}
    ```

    2. Once the job finishes, build and start the instance:
    ```bash
    docker/sdk up
    ```




{% endinfo_block %}

## Database 
In Docker SDK, [PostgreSQL](https://www.postgresql.org/) is provided as a service by default, but you can switch to MySQL or MariaDB as described below.

### MySQL
[MySQL](https://www.mysql.com) is an open source relational database management system based on Structured Query Language (SQL). MySQL enables data to be stored and accessed across multiple storage engines, including InnoDB, CSV and NDB. MySQL is also capable of replicating data and partitioning tables for better performance and durability.

See [MySQL documentation](https://dev.mysql.com/doc/) for more details.

#### Configuration
Follow the steps below to switch database engine to MySQL:
1. Adjust `deploy.*.yaml` in the `services:` section:
```yaml
...
services:
    database:
        engine: mysql
        ...
        endpoints:
            localhost:3306:
...
```
2. Regenerate demo data:
```bash
docker/sdk clean-data
docker/sdk demo-data
```

### MariaDB

[MariaDB](https://mariadb.org/) is a community-developed, commercially supported fork of the [MySQL](https://www.mysql.com/) relational database management system.

See [MariaDB knowledge base](https://mariadb.com/kb/en/) for more details.

#### Configuration
Follow the steps below to switch the database service to MariaDB:

1. Adjust `deploy.*.yaml` in the `services:` section:

```yaml
...
services:
    database:
        engine: mysql
        version: mariadb-10.4
        ...
        endpoints:
            localhost:3306:
...
```
2. Regenerate demo data:

```bash
docker/sdk clean-data
docker/sdk demo-data
```

## ElasticSearch

[Elasticsearch](https://www.elastic.co/elasticsearch/) is a search engine based on the Lucene library. It provides a distributed, multitenant-capable full-text search engine with an HTTP web interface and schema-free JSON documents. 

See:
* [Configure Elasticsearch](/docs/scos/dev/back-end-development/data-manipulation/data-interaction/search/configure-elasticsearch.html) to learn more about Elastcisearch configuration in Spryker.
* [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) for more information on Elasticsearch.

### Configuration

Adjust `deploy.*.yaml` in the `services:` section to open the port used for accessing ElasticSearch:
```yaml
services:
    search:
        engine: elastic
        endpoints:
            localhost:9200
                protocol: tcp
```
 
## Kibana UI

[Kibana](https://www.elastic.co/kibana) is an open source analytics and visualization platform designed to work with Elasticsearch. You use Kibana to search, view, and interact with data stored in Elasticsearch indices. You can easily perform advanced data analysis and visualize your data in a variety of charts, tables, and maps. 

See [Kibana documentation](https://www.elastic.co/guide/en/kibana/current/index.html) to learn more.

In Docker SDK, Kibana UI is provided as a service by default.

### Configuration
Follow the steps to configure an endpoint for Kibana UI:
1. Adjust `deploy.*.yaml` in the `services:` section:
```yaml
services:
    ...
    kibana:
        engine: kibana
        endpoints:
            {custom_endpoint}:
```
2. Adjust host file:
```bash
echo "127.0.0.1 {custom_endpoint}" | sudo tee -a /etc/hosts
```

## RabbitMQ

[RabbitMQ](https://www.rabbitmq.com/) is a messaging broker - an intermediary for messaging. It gives your applications a common platform to send and receive messages, and your messages a safe place to live until received.

### Configuration

Adjust `deploy.*.yaml` in the `services:` section to open the port used for accessing RabbitMQ:
```yaml
services:
    broker:
    ...
        endpoints:
    ... 
            localhost:5672:
                protocol: tcp
            api.queue.spryker.local:
```
## Swagger UI

[Swagger UI](https://swagger.io/tools/swagger-ui/) allows anyone—be it your development team or your end consumers—to visualize and interact with the API’s resources without having any of the implementation logic in place. It’s automatically generated from your OpenAPI (formerly known as Swagger) Specification, with the visual documentation making it easy for back end implementation and client-side consumption.

See [Swagger UI documentation](https://swagger.io/docs/open-source-tools/swagger-ui/usage/installation/) for more details.

In Docker SDK, Swagger UI is provided as a service by default.

### Rest API Reference in Spryker

Spryker provides the basic functionality to generate [OpenApi schema specification](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md) for REST API endpoints. This document provides an overview of REST API endpoints. For each endpoint, you will find the URL, REST request parameters as well as the appropriate request and response data formats.

### Configuration
Follow the steps to configure an endpoint for Swagger UI:
1. Adjust `deploy.*.yaml` in the `services:` section:
```yaml	
services:
    ...
    swagger:
        engine: swagger-ui
        endpoints:
            {custom_endpoint}:
```

2. Adjust the `host` file:
```bash
echo "127.0.0.1 {custom_endpoint}" | sudo tee -a /etc/hosts
```

## Redis

[Redis](https://redis.io) is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes with radius queries and streams. 

See [Redis documentation](https://redis.io/documentation) for more details.

### Configuration

Adjust `deploy.*.yaml` in the `services:` section to open the port used for accessing Redis:
```yaml
services:
    key_value_store:
        engine: redis
        endpoints:
            localhost:16379:
                protocol: tcp
```


## Redis GUI
[Redis Commander](http://joeferner.github.io/redis-commander/) is a web management tool that provides a graphical user interface to access Redis databases and perform basic operations like view keys as a tree, view CRUD keys or import/export databases.

### Configuration
Follow the steps to configure an endpoint for Redis Commander: 

1. Adjust `deploy.*.yaml` in the `services:` section:

```yaml
services:
...    
    redis-gui:
        engine: redis-commander
        endpoints:
            {custom_endpoint}: //redis-commander.spryker.local:
```

2. Adjust hosts file:
```bash
echo "127.0.0.1 {custom_endpoint}" | sudo tee -a /etc/hosts
```




## MailHog

[MailHog](https://github.com/mailhog/MailHog) is a mail catcher service that is used with Spryker in Docker for Demo and Development environments. Developers use this email testing tool to catch and show emails locally without an SMTP (Simple Mail Transfer Protocol) server.

With the MailHog service, developers can:

* configure an application to use MailHog for SMTP delivery;
* view messages in the web UI or retrieve them via JSON API.

{% info_block infoBox %}

By default the following applies:
*  `http://mail.demo-spryker.com/` is used to see incoming emails.
* Login is not required

{% endinfo_block %}
### Configuration
Adjust `deploy.*.yaml` in the `services:` section to specify a custom endpoint:
```yaml
services:
        ...
        mail_catcher:
                engine: mailhog
                endpoints:
                          {custom_endpoint}:
```
  
## Blackfire
[Blackfire](https://blackfire.io/) is a tool used to profile, test, debug, and optimize performance of PHP applications. It gathers data about consumed server resources like memory, CPU time, and I/O operations. The data and configuration can be checked via Blackfire web interface.

### Configuration

Follow the steps to enable Blackfire:

1. Adjust `deploy.*.yaml` in the `image:` section to enable the Blackfire PHP extension:

```yaml
image:
    tag: spryker/php:7.3 # Use the same tag you had in `image:`
    php:
        ...
        enabled-extensions:
            - blackfire
```

2. Adjust `deploy.*.yaml` in the `services:` section to configure Blackfire client:

```yaml
services:
    ...
    blackfire:
        engine: blackfire
        server-id: {server_id}
        server-token: {server_token}
        client-id: {client_id}
        client-token: {client-token}
```

### Alternative Configuration

Use the following configuration if you are going to change server or client details often, or if you don’t want to define them in your deploy file.

Follow the steps to enable Blackfire:

1. Adjust `deploy.*.yaml` in the `image:` section to enable the Blackfire PHP extension:

```yaml
image:
    tag: spryker/php:7.3 # Use the same tag you had in `image:`
    php:
        ...
        enabled-extensions:
            - blackfire
```

2. Adjust `deploy.*.yaml` in the `services:` section to enable Blackfire service:

```yaml
services:
    ...
    blackfire:
        engine: blackfire
```

3. Pass Blackfire client details:

```bash
 BLACKFIRE_CLIENT_ID={client_id} BLACKFIRE_CLIENT_TOKEN={client-token} docker/sdk cli
 ```

4. Pass Blackfire server details:

```bash
BLACKFIRE_SERVER_ID={client-token} BLACKFIRE_SERVER_TOKEN={server_token} docker/sdk up
```

{% info_block warningBox "Note" %}

You can pass the server details only with the `docker/sdk up` command.

{% endinfo_block %}

It is not obligatory to pass all the details as environment variables or define all the details in the deploy file. You can pass the details in any combination. 

## New Relic
[New Relic](https://newrelic.com/) is a tool used to track the performance of services, environment to quickly find and fix issues.

The solution consists of a client and a server. The client is used to collect the data about applications in an environment and send it to the server for further analysis and presentation. The server is used to aggregate, analyse and present the data.

### Configuration

Follow the steps to enable New Relic:

1. Adjust `deploy.*.yml` in the `docker:` section:

```yaml
docker:
    newrelic:
        license: {new_relic_license)
```

2. Adjust `deploy.*.yml` in the `image:` section:

```yaml
image:
    tag: spryker/php:7.3 # the image tag that has been previously used in `image:`
    php:
        ...
        enabled-extensions:
            - newrelic
```

### Alternative Configuration

Use this configuration if you are going to change New Relic license often or don’t want to define it in the deploy file.

Follow the steps to enable New Relic:

1. Adjust `deploy.*.yml` in the `docker:` section:

```yaml
docker:
    newrelic:
```

2. Adjust `deploy.*.yml` in the `image:` section:

```yaml
image:
    tag: spryker/php:7.3 # the image tag that has been previously used in `image:`
    php:
        ...
        enabled-extensions:
            - newrelic
```

3. Pass the New Relic license:

```bash
NEWRELIC_LICENSE={new_relic_license} docker/sdk up
```
{% info_block warningBox "Note" %}

You can pass the New Relic license only with the `docker/sdk up` command.

{% endinfo_block %}

