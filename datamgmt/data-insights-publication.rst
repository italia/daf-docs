Data Publication
================

The standardized data and the rich collected metadata makes possible to expose data in automatic ways via standard API as soon as
a new dataset gets created in DAF. In particular, at the time of this
writing, we are implementing the following methods:

-  **Storage Manager**: it is made by a set of microservices that
   exposed the following basic functionalities for data retrieval:

-  ``{API}/getDataset/{retrieve option}/{output format}/{dataset id, or dataset URI}``:
   this endpoint is created by default and returns the dataset
   identified by either its id or URI.
   ``{retrieve option}``: this specifies filters on the data to be
   retrieved (e.g. it can be a bulk extraction, it can return only a sample,
   ecc.) ``{output format}``: this option specifies the format in which
   data is retrieved. The default option is JSON.
-  ``{API}/getDS/{keyword}/{dataset id, or dataset URI}``: this is a
   simplified version of the previous endpoint that uses specific
   configuration of it to simplify the access.
-  ``{API}/searchDS/{search options}/{output options}``: this allows users to
   search the dataset catalogue to find datasets based on the search
   criteria defined in ``{search options}``.
-  **JDBC Connection**: Some dataset can be configured (via the
   Catalogue Manager) to expose a JDBC connection, managed either via
   Impala or SparkSQL
-  **HDFS Access via Notebook**: data can also be accessed using
   Notebook for analysis. Technically, this is done via access to HDFS,
   and defined user profiling rules.

Data insights publication
=========================

In order to allow the publication of insights arising from data analysis
activities, the platform provides the
*Data Portal* where users
can access to DAF functionalities and data products. The
Data Portal extends the features typically offered by popular data
catalogues (in Italy dati.gov.it) with the following:

-  **Data Visualization Templates**: they are modules that generate a
   specific data visualization based on a specified data source. They
   provide users with both already implemented
   standard visualizations (e.g., line graph, bar chart, pie chart, etc.)
   and custom graphs in d3.js (or any other supported javascript graph
   libraries) that can be created by the users themselves and natively integrated with the DAF
   API exposing data. Data Visualization Templates are also managed by
   their CMSs, in order to help in search and reusability.

-  **Data Stories**: they are entities containing stories and analysis
   about a specific phenomena described with data, and can be made of
   text, Data Visualization objects, notebooks, gists/github resources.
   They are basically the way users create data related content in the
   Dataportal.

-  **Social & Collaboration**: Users can create their own Data Stories
   and share them on the platform so that other users can read and/or fork
   them to build a new Data Story on top of an existing one.

-  **User Profile**: a restricted area where the user can see and manage
   the content (s)he created, as well as have access to personal data that
   is available in DAF (i.e., the citizen dashboard). In successive releases, the latter
   functionality will be accessed with a 2nd/3rd level SPID (the Italian national system for e-ID); meanwhile
   for the first releases a lighter registration may be considered sufficient.
