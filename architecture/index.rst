Big data platform
=================

More precisely, you can think the Big Data platform as an environment
offering capabilities for:

-  *storing and managing datasets*: users can register datasets and to
   load them on the platform specifying the ingestion models (e.g.
   batch, streaming), the serialization formats (e.g. Avro, Parquet),
   the desired serving layers (e.g. HBase, Impala), metadata, etc;
-  *processing and analysing datasets*: the platform provides an
   environment composed by a set of tools for data scientists and
   analysts. By using these tools these ones can perform analysis on
   data, run statistical and machine learning models, and produce data
   visualizazions and reports;
-  *redistributing datasets, developing data application, publishing
   insights*: the platform provides tools for enabling the publication
   of opendata, data stories, data application, etc.

   The following image provides an architectural overview of the DAF:

   `Update and Insert
   Image <https://docs.google.com/presentation/d/1LDDrG7VsYoXXIbfbg6tQ9z7DfHw7ukkNnwVygt6jOOQ/edit>`__

   -  the `DAF architecture <../architecture/>`__


DAF Architecture
================


The DAF (Data Analytics Framework) is a platform originally designed to
gather and store data coming from different Italian public
administrations. As a consequence, it provides efficient and easy to use
ingestion mechanisms for allowing external organisations to simply
ingest their data into the platform with minimal human intervention. The
DAF platform shouldn’t only provide support for data at rest and fast
data (streaming), but also for storing and managing collections of
unstructured data, textual documents. Besides providing those storing
capabilities the next main goal is to provide a powerful mechanism for
data integration, i.e. a way for integrating data that traditionally
reside on separate silos. Enabling the correlation of data sets normally
residing on different systems/organizations can become a very powerful
enabling factor for discovering new insights on the data. The platform
should allow the data scientists to access its computational power for
implementing advanced analytics algorithms.

Take a tour of the DAF architecture looking at:

.. toctree::
   :maxdepth: 1

    Logical View <logicalView>
    Component/microservice View <componentView/index>
    Deployment View <deploymentView>
