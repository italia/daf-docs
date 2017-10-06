
Metabase
============================================================

.. Metabase + postgres + ldap configuration
This guide explains how to run a execute a Metabase server.

Follow these steps to run the Docker images.

Clone the git project:

.. code-block:: bash

 > git clone git@github.com:italia/daf-recipes.git

Go to the metabase directory, the images needed by docker-compose and run it:

.. code-block:: bash

 > cd metabase
 > ./build_local.sh
 > docker-compose up -d    # it will run all the needed containers

Open the metabase home http://localhost:3000

Go to `github <https://github.com/italia/daf-recipes/tree/master/metabase>`_ for seeing how to setup metabase.
