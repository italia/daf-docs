
Ingestion Manager
=================

The **IngestionManager** manages all the data ingestion activities
related to the datasets. The IngestionManager provides an API to ingest data from a data source into the DAF platform.

See `here <../../bigdataplatform/architecture/componentView/index.html>`_ for more details.

Local Installation
------------------
- Pre-requisites: JDK 8, SBT, GIT client
- git clone https://github.com/italia/daf
- cd daf/common
- sbt publishLocal
- cd ../ingestion_manager
- sbt
- run
- connect to http://localhost:9000/ingestion-manager

You should see a swagger UI with all endpoints described.
Nevertheless, the authorization is not required by the UI you should pass at least a Basic authorization token made by an equal user name and password.

To test the endpoints we suggest to use a tool like `Postman <https://www.getpostman.com/>`_


DAF integration note
--------------------
[TBD]

Endpoints
-------------------
[TBD]
