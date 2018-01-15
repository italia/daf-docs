End-user features: Dataportal & API
===================================

DAF offers functionalities to its users (policy makers, analysts, data scientists, civic hackers, data journalists and informed citizens) via a web application (that we call Dataportal) and an ecosystem of API to access the data and other core functionalities. All DAF users will be exposed to almost the same functionalities, but they will be able to access only the dataset they have have been granted access to.


Dataportal
----------

The Dataportal is the DAF user interface, a place where users can have access to most of DAF functionalities and contents, based on their role and access grants. It is a web applications offering a *public area* where users can have access to contents that can be released publicy, and a *private area* where authenticated users can manage and use all data she have grant access to based on her role and organization, and functionalities like data visualization, business intelligence and data science.

Here are some basic content and features accessed and managed via the dataportal:

* **dataset metacatalog**: a catalog where to search for datasets, their info according to DCAPAP_IT profile, correlated datasets, related information and datastories made by using the dataset, the list of API with which using the dataset, and other operational info useful to use the dataset with the integrated tools.
* **data stories**: blog posts that integrate data visualizations and scripts to tell the whys and the results of a data analysis. Data stories are design to stimulate discussion around an data related themes, and allows the community to comment an propose further analysis.
* **data applications**: software with a user interfaces that expose functionalities based on data and models trained on them. Data applications can be done by the DAF team, public administration or can be proposed by the community, and will be organized in a related section of the dataportal.
* **news & blog**: blog post containing news related to the data world, together with how-to and tutorial on how to use the DAF and dataportal.
* **Data visualization & Business Intelligence**: we integrated two open source tools, Metabase and Superset, where user can explore data managed by DAF and create graphs and dashboards.
* **Data science**: a Jupyter Hub notebook as been integrated and connected to the Hadoop cluster to allow for data manipulation, analysis and data science. Users can take advantage of the capability of Apache Spark and its libraries to run SQL queries on top of Hadoop, integrate different datasets and traing machine learning model using MLlib library.


API
---

The DAF exposes automatically an API to interact with datasets. Users can use standardized interfaces to access the datasets to:

* get statistical and metadata info
* download the dataset (up to a certain limits)
* run SQL like queries on datasets

The use of API will allow users to build their applications easily and with the guarantee toaccess to the most updated data available.
