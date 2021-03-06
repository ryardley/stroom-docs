![Stroom](resources/logo.png)

> A published HTML version of these documents are available to view at [here](https://gchq.github.io/stroom-docs/). You can also download a _PDF_ version or a zip file of all the HTML documentation from [here](https://github.com/gchq/stroom-docs/releases).

If you'd like to jump straight in then see the [Quick Start Guide](quick-start-guide/quick-start.md). 

Alternatively, if you'd just like to see Stroom running then follow the very simple steps [here](dev-guide/docker-running.md).

A series of _HOWTO_ Recipes for various elements of Stroom can be found [here](HOWTOs/StroomHowTos.md)

# Stroom

Stroom is a data processing, storage and analysis platform. It is scalable - just add more CPUs / servers for greater throughput. It is suitable for processing high volume data such as system logs, to provide valuable insights into IT performance and usage.

Stroom provides a number of powerful capabilities:

* **Data ingest.** Receive and store large volumes of data such as native format logs. Ingested data is always available in its raw form.
* **Data transformation pipelines.** Create sequences of XSL and text operations, in order to normalise or export data in any format. It is possible to enrich data using lookups and reference data.
* **Integrated transformation development.** Easily add new data formats and debug the transformations if they don't work as expected.
* **Scalable Search.** Create multiple indexes with different retention periods. These can be sharded across your cluster.
* **Statistics.** Record counts or values of items over time, providing answers to questions such as "how many times has a specific machine provided data in the last hour/day/month?"
* **Dashboards.** Run queries against your indexes or statistics and view the results within custom visualisations.

# Benefits

System event data can come from many kinds of technology, this makes it highly heterogeneous with many different formats in use. As technologies are invented, new event types and log formats must be understood and processed correctly. Technology changes so rapidly that the auditing team risks being left behind.

Stroom is designed to offer a way to mitigate this risk, and has matured into an application that scales well to billions of events a day - sufficient to ingest and process the system events generated by the IT of a large organisation.

The person who introduces a new log format is probably best placed to describe it. Stroom provides these experts with tools that make it easy to normalise data, essentially crowdsourcing the problem. An organisation can ask their employees to configure Stroom whenever they introduce a new technology, and have confidence that it will be able to be properly audited.

# Architecture

Stroom 5.x is a Java web application that runs on _Apache Tomcat_, with _Apache Lucene_ indexes over a compressed data store. It uses two _MySQL_ RDBMSs to persist application configuration and metadata. 

Stroom v6.x uses a more service oriented architecture with a number of additional peripheral services such as stroom-auth, stroom-stats, stroom-query-elastic, stroom-annotations, etc. The core Stroom application and the majority of the services all run on _DropWizard_ using embedded _Jetty_.

Currently Stroom has only been tested with _Google Chrome_. For this reason some functionality may not work correctly in other browsers. Now that Stroom is an open source project, support for other browsers will be improved.

There are several optional components for different use cases:

* **Stroom Proxy** - An application that receives and forwards data to Stroom.
* **Stroom Stats** - An HBase based service for storing and querying aggregates of event data.
* **Stroom Stats** - An HBase based service for storing and querying aggregates of event data (still in development).
* **Stroom Annotations** - A service for recording data relating to events or records in Stroom (still in development).
* **Stroom Query Elastic** - A service to allow Stroom dashboards to query Elastic Search indexes.
* **Stroom Agent** - An application that extracts data from sources. 
* **Event Logging XML Schema** - A common language for describing audit events.
* **Event Logging JAXB Library** - A Java library to help client systems send events to Stroom.
* **Content Packs** - Transformation packages for standard log formats (e.g. Windows, Linux) into Logging Events XML.

# Screenshots

Some screenshots of the application can be seen [here](screenshots.md).

# State of the Project

Stroom v5.0 and v5.1 represent the first open source releases of Stroom and are suitable for use in a production environment. Stroom v6.x is currently in development with alpha and beta releases available for testing.

# Future

Although Stroom is a mature product it is receiving more active development effort than ever. Work is underway to evolve the existing architecture and add new features:

* A rule engine for notifying analysts about particular event scenarios
* Scalable temporal state storage that could be used by rules or dashboards
* New visualisations to improve analysis
* A modularised, micro-service-based architecture
* Further integration with the Hadoop ecosystem

# Developers and Contributors

If you want to contribute to the development of Stroom or its related repositories please see [here](CONTRIBUTING.md).

For details of how get started setting up a Stroom development environment see [here](dev-guide/stroom-in-an-ide.md).

# Stroom Content

A lot of the power of Stroom comes from the content that is developed within it. The content includes XSLT transformations, data-splitter definitions, dashboards, visualisations, processing pipeline definitions, etc. The content developed within Stroom can be exported and shared between other Stroom installations. The content can be packaged into convenient content pack zip files.

Generic Stroom content is available [here](https://github.com/gchq/stroom-content/releases)

Stroom visualisations (for use in dashboards) are available [here](https://github.com/gchq/stroom-visualisations-dev/releases)

