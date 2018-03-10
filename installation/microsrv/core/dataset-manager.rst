
Dataset Manager
===============

The **DatasetManager** manages several operations related to the dataset, such as:

* to return the data of the dataset (or a sample of it) in a specified format;
* to create a specific view on top of a dataset;
* to get the dataset schema in a given format (e.g. AVRO);
* to create a new dataset based on an existing one but saved with a different storage mechanism or based on a transformation of the existing dataset, etc.

See `here <../../bigdataplatform/architecture/componentView/index.html>`_ for more details.

Local Installation
------------------
- Pre-requisites: JDK 8, SBT, GIT client
- git clone https://github.com/italia/daf
- cd daf/common
- sbt publishLocal
- cd ../dataset_manager
- sbt
- run
- connect to http://localhost:9000/dataset-manager

You should see a swagger UI with all endpoints described.
Nevertheless, the authorization is not required by the UI you should pass at least a Basic authorization token made by an equal user name and password.

To test the endpoints we suggest to use a tool like `Postman <https://www.getpostman.com/>`_

DAF integration note
--------------------
[TBD]

Endpoints
-------------------
[TBD]
