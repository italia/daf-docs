******************
Local Installation
******************

This guide explaines how to use the virtual machine to create test enviroment.

You can download the OVA image at the following link:

OVA Image: `download <https://developers.italia.it/static/DAF-Ubuntu16-Docker-test.ova>`_ (8.6 GB)

=======================
Virtual Machine Account
=======================

  :USER: user
  :PASSWORD: password

CHECK Virtual Machine assigned ip address (also check bridge of virtual machines before start if you use wireless or eth adapter on your pc) using command

.. code-block:: bash

 > ip a | grep enp0s3

Access to Virtual Machine:

.. code-block:: bash

 > ssh user@xxx.xxx.xxx.xxx (Virtual Machine IP)

==============
Docker image
==============
In Virtual Machine to access folder with container docker image:

.. code-block:: bash

 > sudo -i
 > cd /root/docker

All container starts automatically when Virtual Machine satrts.

===============
Configuration
===============
Add in your PC file hosts the following lines:

.. code-block:: bash

 x.x.x.x ipa.example.test superset.daf.test.it metabase.daf.test.it ckan.daf.test.it mongodb ckan metabase supersetd
 127.0.0.1 datipubblici-private.daf.test.it

When x.x.x.x is the Virtual Machine IP address


Access Docker Services
----------------------
When Virtual Machine is in run you can access to the docker services from your browser.

FreeIPA
^^^^^^^^^
Use the following link https://ipa.example.test to access to freeIPA.

The credentials are:

 :USER: admin
 :PASSWORD: adminpassword

or

 :USER: ldap
 :PASSWORD: ldap

The account ldap is used for bind docker system, every user in ldap has the same user and password.

If you are using Google Chrome do not use the modal login on your browser, because it doesn't work.

Use the login in the web page.

Actual users:

 - raffaele
 - alssandro
 - andrea
 - pierpaolo
 - david
 - alberto

CKAN
^^^^
Use the following link http://ckan:5000 to access the ckan in the Virtual Machine.

Use only LDAP user to login.

METABASE
^^^^^^^^
Use the following link http://metabase:3000 to access the metabase in the Virtual Machine.

 :USER/MAIL: admin@admin.it
 :PASSWORD: admin01

or login with LDAP users.

SUPERSET
^^^^^^^^

Use the following link http://supersetd:8088 to access the superset in the Virtual Machine.

 :USERNAME: superadmin
 :PASSWORD: password1


========
Services
========
Run in the host following command to clone daf project

.. code-block:: bash

 > git clone https://github.com/italia/daf.git

In the case sbt is not found install it:

.. code-block:: bash

 > echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
 > sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
 > sudo apt-get update
 > sudo apt-getinstall sbt


Common
------
Move on the host pc in the folder daf/common run commands:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > publishLocal

Security Manager
----------------
In your daf/security_manager folder run:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=svil.conf -Dhttp.port=9002

Catalog Manager
---------------
Move the host pc in the folder dat/catalog_manager and run commands:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=svil.conf -Dhttp.port=9001

Dataportal
----------
Clone the project daf-dataportal-backend from github using the following command:

.. code-block:: bash

 > git clone  https://github.com/italia/daf-dataportal-backend

In your daf-dataportal-backend project run following commands:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=local.conf

Front-end
---------
Clone the project  daf-dataportal from github:

.. code-block:: bash

 > git clone  https://github.com/italia/daf-dataportal

In your daf-dataportal project, add the following lines in …/src/config/serviceurl.js:

.. code-block:: bash

  apiURLSSOManager: "http://localhost:9002/sso-manager",
  apiURLDatiGov: "http://localhost:9000/dati-gov/v1",
  apiURLCatalog: "http://localhost:9001/catalog-manager/v1",
  apiURLIngestion: "http://localhost:9002/ingestion-manager/v1",
  apiURLSecurity: "http://localhost:9002/security-manager/v1",
  urlMetabase: 'http://metabase.daf.test.it',
  urlSuperset: 'http://superset.daf.test.it',

  domain:".daf.test.it"

In your .../package.json edit the line in the section scripts

.. code-block:: bash

  “start”: “PORT=80 react-scripts start”

You can run the FE in the following modality:

Start in Debug Mode:

.. code-block:: bash

  npm install
  npm start

Start in Production Mode:

.. code-block:: bash

  npm run build
  npm install -g serve
  serve -s build


For each configuration the application should be reached through the following url:

 http://datipubblici-private.daf.test.it

At the first access you click on to the button "Registati" to sign up.
After the registration access to freeIpa, search your account and add to your user groups "daf_admins"
Now logout and login to DAF - Dataportal to see admin feature