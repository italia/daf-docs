******************
Dataportal-private
******************

===========
What is it?
===========

The `Dataportal-private <https://dataportal-private.daf.teamdigitale.it>`__ is the web app that allows access to the functionalities of DAF, like:

* **Ingestion** form to add dataset with metadata
* **Business Intelligence** with Superset (AirBnB)
* **Graphs** with Metabase
* **Data science** with Jupyter + Sparkmagic
* Ontologies and Controlled Vocabularies repository


=======
Install
=======

Before proceeding with the installation steps, you need to install and run the following external components:

Basic Dependencies
------------------
* `daf-dataportal-backend <../local/devVM.html#dataportal>`__
* `FreeIPA <../docker/freeipa.html>`__
* `CatalogManager <../microsrv/core/catalog-manager.html>`__
* `SecurityManager <../microsrv/core/security-manager.html>`__


Features Enabling Dependencies
------------------------------
* `Superset <../docker/superset.html>`__
* `Metabase <../docker/metabase.html>`__
* `JupyterHub <../docker/jupyter.html>`__
* `CKAN <../docker/ckan.html>`__



Installation Steps
------------------
First of all, you need to clone the following GitHub repository:

.. code-block:: bash
  
  > git clone https://github.com/italia/daf-dataportal

Start in Debug Mode:

.. code-block:: bash

  > npm install
  > npm start

Start with mock server:

.. code-block:: bash

  > npm run mock

Start in Production Mode:

.. code-block:: bash

  > npm run build
  > npm install -g serve
  > serve -s build

