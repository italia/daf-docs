*****************
Dataportal-private
*****************

===========
What it is?
===========

The Dataportal-private [put link]  is the webapp to access functionalities of DAF, like:
* **Ingestion** Form to add dataset with metadata
* **Business Intelligence** with Superset (AirBnB)
* **Graphs** with Metabase
* **Data Science** with Jupyter + Sparkmagic
* Ontologies and Controlled Vocabularies repository


=======
Install
=======

Before proceeding with the installation steps, you need to install and run the following external components:

Basic Dependencies
------------------
* daf-dataportal-backend [put link to documentation]
* FreeIPA [put link to documentation]
* CatalogManager [put link to documentation]
* SecurityManager [put link to documentation]

Features Enabling Dependencies
------------------------------:
* Superset [put link to docker documentation]
* Metabase [put link to docker documentation]
* JupyterHub [put link to docker documentation]
* CKAN [put link to docker documentation]



Installation Steps
------------------
First of all, you need to clone the following github repository:
* ``$ git clone https://github.com/italia/daf-dataportal``

Start in Debug Mode:
* ``$ npm install``
* ``$ npm start``

Start with mock server:
* ``$ npm run mock``

Start in Production Mode:
* ``$ npm run build``
* ``$ npm install -g serve``
* ``$ serve -s build``


