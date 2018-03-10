******************
Local Installation
******************

This guide explains how to use the Virtual Machine to create a test environment.

You can download the OVA image at the following link:

OVA Image: `download <https://developers.italia.it/static/DAF-Ubuntu16-Docker-test.ova>`_ (8.6 GB)

.. warning::

   In order to use the Virtual Machine, you must have at least 20 Gb of free space in your hard drive. 

=======================
Virtual Machine Account
=======================

  :USER: user
  :PASSWORD: password

Check the IP address assigned to the Virtual Machine (also check bridge of virtual machines before start if you use wireless or Ethernet adapter on your PC) using the command:

.. code-block:: bash

 > ip a | grep enp0s3

Access the Virtual Machine via ssh:

.. code-block:: bash

 > ssh user@xxx.xxx.xxx.xxx (Virtual Machine IP)

==============
Docker image
==============
In the Virtual Machine, to access a folder with container docker image:

.. code-block:: bash

 > sudo -i
 > cd /root/docker

All the containers start automatically when the Virtual Machine starts.

===============
Configuration
===============
In your PC Hosts file, add the following lines:

.. code-block:: bash

 x.x.x.x ipa.example.test superset.daf.test.it metabase.daf.test.it ckan.daf.test.it mongodb ckan metabase supersetd
 127.0.0.1 datipubblici-private.daf.test.it

where x.x.x.x is the Virtual Machine IP address.


Access Docker Services
----------------------
When the Virtual Machine is running, you can access to the docker services from your browser.

FreeIPA
^^^^^^^^^
Use the following link https://ipa.example.test to access to freeIPA.

The credentials are:

 :USER: admin
 :PASSWORD: adminpassword

or

 :USER: ldap
 :PASSWORD: ldap

The account LDAP is used to bind docker system. Every user in LDAP has the same user name and password.

If you are using Google Chrome, do not use the modal login on your browser, because it doesn't work.

Use the login in the web page.

Actual users:

 - raffaele
 - alssandro
 - andrea
 - pierpaolo
 - david
 - alberto

CKAN
^^^^^^^^^^
Use the following link http://ckan:5000 to access the CKAN in the Virtual Machine.

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


Use alternative DNS in VPN
--------------------------
Edit the openVPN client config file and add the following rows at the end:

.. code-block:: bash

 > script-security 2
 > up /etc/openvpn/update-resolv-conf
 > down /etc/openvpn/update-resolv-conf

Edit file /etc/nsswitch.conf and comment the hosts row

.. code-block:: bash

 > # hosts: files mdns4_minimal [NOTFOUND=return] dns

=========
Services
=========
In the host, run the following command to clone the DAF project:

.. code-block:: bash

 > git clone https://github.com/italia/daf.git

In case sbt is not found, install it:

.. code-block:: bash

 > echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
 > sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
 > sudo apt-get update
 > sudo apt-getinstall sbt


Common
-------
On the host PC, go to the folder daf/common and run the following commands:

.. code-block:: bash

 > sbt
 > clean
 > compile

Security Manager
----------------
In your daf/security_manager folder, run:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=svil.conf -Dhttp.port=9002

Catalog Manager
---------------
On the host PC, go to the folder dat/catalog_manager and run the commands:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=svil.conf -Dhttp.port=9001

Dataportal
-----------
Clone the project daf-dataportal-backend from GitHub using the following command:

.. code-block:: bash

 > git clone  https://github.com/italia/daf-dataportal-backend

In your daf-dataportal-backend project, run the following commands:

.. code-block:: bash

 > sbt
 > clean
 > compile
 > run -Dconfig.resource=integration.conf

Front-end
----------
Clone the project daf-dataportal from GitHub:

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

For each configuration, the application should be reached through the following url:

 http://datipubblici-private.daf.test.it

