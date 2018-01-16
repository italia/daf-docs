
Security Manager
================

**Security Manager** is the microservices responsible to manage security of the web application and the REST API developed within DAF.
Its APIs verifies user credential, produces JWT tokens needed to access DAF services and handles the SSO on the solutions integrated in the Data Portal.

Local Installation
------------------
- Pre-requisites: JDK 8, SBT, GIT client
- git clone https://github.com/italia/daf
- cd daf/common
- sbt publishLocal
- cd ../security_manager
- sbt
- run
- connect to http://localhost:9000/security-manager

You should see a swagger ui with all endpoints described.
Nevertheless, the authorization is not required by the UI you should pass at least a Basic authorization token made by an equal username and password.

To test the endpoints we suggest to use a tool like `Postman <https://www.getpostman.com/>`_


DAF integration note
--------------------
[TBD]

Endpoints
-------------------
[TBD]
