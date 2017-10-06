 
Metabase
============================================================

Metabase + postgres + ldap configuration

Follow these steps to run the Docker images:

cd metabase

./build_local.sh        #it will build the images needed by docker-compoose

docker-compose up -d    # it will run all the needed containers

Then you can open the metabase home http://localhost:3000

goes to `github <https://github.com/italia/daf-recipes/tree/master/metabase>`_ for seeing how to setup metabase