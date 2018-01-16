Data in use
===========

Analysis & Data visualization
-----------------------------

One of the key features of DAF is its ability to provide analytical functionalities. It offers
en environment where data scientists and analysts can perform analysis
on data, run statistical & machine learning models and produce data
visualizations and reports. At the time of this writing, the following tools are currently made
available:

-  **Notebook**: DAF creates isolated environments to run notebooks
   that can safely connect to data via HDFS or API to perform analysis.
   The notebook loads the Catalogue API by default in order to help
   dataset search and retrieval, and provides the scala, python, R kernel
   integrated with spark.

-  **BI Tool**: DAF comes with an installed BI tool to offer self service
   analysis & reporting capabilities to analysts. The BI Tool
   typically connects with the dataset that exposes JDBC connections. 
   
   ... We are currently scouting for good Open Source alternatives.

-  **Data Visualization Templates & Data Stories**: the `Data Portal <../dataportal/index.html>`__ provides users with the ability to create data visualization
   on the fly by using  Data Visualization Templates. These templates
   leverage standard D3.js and alike code embedded into
   React/AngularJS modules that connect to a given dataset via the
   exposed API and produce a graph. Users can create and share their
   analysis via Data Stories, a content entity (blog post) that can contains Data
   Visualization instances, text, notebook and Gists/Github resources.

Data Applications
-----------------

Data applications are an important component of DAF. They are software
applications that leverage/embed analysis and models previously
performed on data to offer functionalities based on those models. As an
example, consider the data scientists team has trained a model that
predicts the traffic jam in a specific point of a road, based on the
current traffic status nearby. This model can be embedded into a
microservice that takes as input the geospatial coordinates where we
want to predict the traffic and returns the prediction.

Data applications are entities modeled in DAF so as to make sure they
are easily manageable, easily searchable and possibly connected/related
to relevant other data applications and datasets. In this perspective,
the data applications will have a catalogue manager similar to the one
for datasets, so to implement data applications metadata and searching
capabilities.
