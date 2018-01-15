
Ingestion Manager
=================

The **IngestionManager** manages all the data ingestion activities
associated to datasets. The IngestionManager provides an API to ingest data from a datasource
into the DAF platfom

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

You should see a swagger ui with all endpoints described.
Nevertheless, the authorization is not required by the UI you should pass at least a Basic authorization token made by an equal username and password.

To test the endpoints we suggest to use a tool like `Postman <https://www.getpostman.com/>`_


DAF integration note
--------------------
[TBD]

Endpoints
-------------------
[TBD]
