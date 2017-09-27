 
 
Security Manager
============================================================


What is?
----------

**Security Manager** is the microservices responsible to manage security of the web application and the REST API developed within DAF. Its APIs verifies user credential, produces JWT tokens needed to access DAF services and handles the SSO on the solutions integrated in the Data Portal. 

We recommend to use the local integrated environment with a set of docker described at ......

Install
--------------------
- git clone https://github.com/italia/daf
- cd daf/common
- sbt publishLocal
- cd ../daf/security-manager
- sbt 
- run
- test service on http://localhost:9000/security-manager 

The basic functionalities of the security manager needs an installation of freeIPA server whitch acts as credentials store and user authentication system.

In the next section single rest services are detailed. To test the endpoints I suggest to use a tool similar to `Postman <https://www.getpostman.com/>`_. Url's listed refers to the attacched Postman configuration.


Endpoints
-------------------
|

http://localhost:9000/security-manager/v1/token

Autenticate user and produce JWT

http://localhost:9000/security-manager/v1/ipa/user/test1

Retrive user information stored in freeIPA

http://localhost:9000/security-manager/v1/ipa/registration/request

Manage user registration request

http://localhost:9000/security-manager/v1/ipa/registration/confirm?token=123456

Register a user to the system (create the credential)



Section 3
----------

...




doduce 