
Jupyter
============================================================

This guide will show you how to use Docker Compose to set up and run a `JupyterHub <https://jupyterhub.readthedocs.io/en/latest/>`_  instance
which uses ldap credentials to authenticate users.


Account Management Dependency
--------------------------

This configuration of Ckan needs an account management system to work with. We provide three different options, you will find more info on their respective sections:

* Local LDAP Docker
* Local FreeIPA Docker (works only with linux)
* Remote FreeIpa Server


JupyterHub
-----------------

This docker container runs a JupyterHub instance which is connected with a postgresql database.

Run the docker container:

.. code-block:: bash

  > cd ./daf-recipes/jupyterhub
  > docker-compose up -d

Check whether dockers are running:

.. code-block:: bash

  > docker ps
  8350963ac06c        jupyterhub_jupyterhub   "/wait_db_is_ready.sh"   16 minutes ago      Up 16 minutes       0.0.0.0:8000->8000/tcp                       jupyterhub
  6a0d0d6c3b9a        osixia/phpldapadmin     "/container/tool/run"    17 minutes ago      Up 17 minutes       0.0.0.0:80->80/tcp, 443/tcp                  phpldapadmin
  e8ff9611aeff        osixia/openldap         "/container/tool/r..."   17 minutes ago      Up 17 minutes       0.0.0.0:389->389/tcp, 0.0.0.0:636->636/tcp   ldap
  cee2d35feaaf        postgres:9.6            "docker-entrypoint..."   2 hours ago         Up 2 hours          0.0.0.0:5432->5432/tcp                       postgresjupyterhub

To open the interactive shell type *http://localhost:8000* and login as user *alice* (password *password*).

.. image:: imgs/jupyter.png
   
