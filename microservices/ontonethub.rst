 
OntoNetHub
============================================================


What is?
----------

**OntoNetHub** is a microservice meant to deal with the management of ontology networks. 
This include the upload, deletion, storage, and indexing of an ontology part of a network.

OntoNetHub is designed as an extension of Apache Stanbol and released as a Docker component. Hence, users need Docker to build and run OntoNetHub.


Install Standalone.
--------------------

- git clone https://github.com/teamdigitale/ontonethub
- docker-compose build
- docker-compose up
- connect to http://localhost:8000/stanbol/ontonethub
 
To test the endpoints it's possible to use a tool similar to `Postman <https://www.getpostman.com/>`_


DAF Integration
-------------------

This microservice currently provides functionalities to the semantic_manager, which takes care of integrating them to DAF and the public dataportal:

- with the ingestion form of DAF, providing suggestions for the "semantic" annotations of dataset fields.
- with the public dataportal, providing a list of available ontologies and "core" vocabularies.


Endpoints
-------------------

There is a list of available endpoints:

- */stanbol/ontonethub/ontology*                       : can be used to add a new ontology using a POST request.
- */stanbol/jobs/{job_id}*                             : provides informations about the status of a job associated with the upload of an ontology. 
- */stanbol/ontonethub/ontology/{ontology_id}*         : can be used with a GET request to access the information about the specific ontology.
- */stanbol/ontonethub/ontology/{ontology_id}*         : can be used with a DELETE request for deleting an existing ontology.
- */stanbol/ontonethub/ontology/{ontology_id}/source*  : can be used with a GET request for obtaining a representation of the ontology in JSON-LD.
- */stanbol/ontonethub/ontologies/find*                : can be used for querying the OntoNetHub and retrieving OWL entities from the ontologies managed by it.


Detailed informations about the service can be found `here <https://github.com/teamdigitale/ontonethub>`_


