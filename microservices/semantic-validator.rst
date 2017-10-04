 
Semantic Validator
============================================================

What is?
----------

**Semantic Validator** is the microservice designed to provide a simple way for validating RDF metadata dataset against a specific Ontology on an underlying triplestore. 
The validator is currently based on a set of queries (about 150 for DCAT-AP_IT) returning a record of information for the rules broken by the dataset, the most important infos are:
  
  - Class name: the class involved in the rule (ex: Organization for DCAT-AP_IT)
  - Rule ID: the broken rule id (ex: 207 for DCAT-AP_IT) 
  - Error description: the problem description (ex: "vcard:hasURL should be a resource" for DCAT-AP_IT)

Install Standalone.
--------------------
- git clone https://github.com/italia/daf-semantics
- cd daf-semantics/semantic_validator
- sbt docker:publishLocal
- sbt run
- connect to http://localhost:9000

You should see a swagger ui with all endpoints described. 

To test the endpoints I suggest to use a tool similar to `Postman <https://www.getpostman.com/>`_

DAF Integration
-------------------

This microservice will be integrated with the front-end component "semantic_frontend" in the block called "Public Manager" as you can see in the DAF architecture main schema.

Endpoints
-------------------

There are two endpoints:

- */validator/validate*   : in order to validate a document
- */validator/validators* : in oder to ghe the list of available validators 

Detailed informations about the service can be found `here <https://github.com/italia/daf-semantics/tree/master/semantic_validator>`_


