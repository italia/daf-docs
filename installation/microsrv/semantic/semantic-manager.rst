
Semantic Manager
============================================================

**Semantic Manager** is the microservice designed to provide a central access point for the so-called "semantic" functionalities,
involving the usage of ontologies and core vocabularies supporting both DAF processes and the catalog front-end for users.

Local Installation
------------------
- Pre-requisites: JDK 8, SBT, GIT client
- git clone https://github.com/italia/daf-semantics
- cd daf-semantics/semantic_manager
- sbt docker:publishLocal
- sbt run
- connect to http://localhost:9000

You should see a swagger ui with all endpoints described.

To test the endpoints I suggest to use a tool similar to `Postman <https://www.getpostman.com/>`_


DAF integration note
--------------------

This microservice is currently integrated:

- with the ingestion form of DAF, providing suggestions for the "semantic" annotations of dataset fields. Those annotations are saved into the schema for the imported dataset, and act as references for the standardization of fields.
- with the public dataportal, providing a list of available ontologies and "core" vocabularies.


Endpoints
---------

There are two endpoints:

- */kb/v1/ontologies*                 : provides a list of the available ontologies
- */kb/v1/ontologies/properties/find* : enable searching by terms and language for properties which may be used for a simple annotation of dataset fields in the ingestion form (and later for standardization).

Detailed informations about the service can be found `here <https://github.com/italia/daf-semantics/tree/master/semantic_manager>`_
