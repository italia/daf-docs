
Semantic Repository
============================================================

**Semantic Repository** is the microservice designed to provide basic functionalities for managing ontologies/vocabularies
(and data, in the future) using the well-know [RDF4J](http://rdf4j.org/) interface as an abstraction over triplestores.

The idea is to have a list of core functionalities for a catalog service of queryable ontologies, which can be implemented over an external triplestore, and it will evolve accordingly.

Local Installation
------------------
- Pre-requisites: JDK 8, SBT, GIT client
- git clone https://github.com/italia/daf-repository
- cd daf-semantics/semantic_repository
- sbt docker:publishLocal
- sbt run
- connect to http://localhost:9000

You should see a swagger UI with all endpoints described.

To test the endpoints I suggest to use a tool similar to `Postman <https://www.getpostman.com/>`_.

DAF integration note
--------------------
[TBD]

Endpoints
---------

There is a list of basic endpoints:

- */kb/v1/ontologies*        : using this endpoint, it is possible to add new ontologies using HTTP POST with parameters. By conventions the user should assign a prefix / context pair (which willbe unique in the underlying repository catalog).
- */kb/v1/ontologies/remove* : the endpoint is dedicated to remove an existing ontology, using the context where it was published.
- */kb/v1/contexts*          : a list of the existing context can e retrieved: by convention ontologies are published on assigned contexts, which will be different from the ones used for data.
- */kb/v1/prefixes*          : this endpoint returns the full list of used prefix / namespace pairs, where the namespace usually coincide with an assigned contexts on the underlying repository.
- */kb/v1/prefixes/lookup*   : this endpoint can be used for retrieving the namespace associated to a given prefix.
- */kb/v1/prefixes/reverse*  : this endpoint can be used for retrieving the prefix associated to a given namespace.
- */kb/v1/triples*           : provides the amount of available triples.
- */kb/v1/triples/{prefix}*  : provides the triples count for a given context.


Detailed information about the service can be found `here <https://github.com/italia/daf-semantics/tree/master/semantic_repository>`_.
