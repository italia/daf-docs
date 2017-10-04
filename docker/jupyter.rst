=======================
JupyterHub + Sparkmagic
=======================

This documentation will guide you through the setup of a dockerized version of JupyterHub with LDAP integration, Postgres backend and Sparkmagic.


******************
Installation Steps
******************

The following procedure will download the required configuration file from a GitHub repo, generate and run the required docker container with the default configuration provided. Before running ``./build.sh`` command, we suggest you to have a look at the JupyterHub and Sparkmagic configuration files,see the section below for more info.

* Clone the daf-recipes repo and enter into the JupyterHub folder
.. code-block:: bash
   
   $ git clone https://github.com/italia/daf-recipes.git
   $ cd jupyterhub

* Build ``jupyterhub`` docker image
.. code-block:: bash

   $ ./build.sh

* Start ``jupyterhub`` docker container
