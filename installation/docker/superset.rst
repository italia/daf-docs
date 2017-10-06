
Superset
============================================================

This guide presents how to configure and run a docker containing a `Superset <http://superset.apache.org>`_
instance.

Clone the git project:

.. code-block:: bash

 > git clone git@github.com:italia/daf-recipes.git

Go to the superset directory:

.. code-block:: bash

 > cd superset

The superset docker connects, by-default, to a test LDAP server provided by
the DAF platform. If need to configure another LDAP server proper configure
LDAP parameters inside the configuration file "superset_config.py":

 - AUTH_TYPE = AUTH_LDAP
 - AUTH_LDAP_SERVER = "ldaps://server:636"
 - AUTH_LDAP_SEARCH = "cn=users,cn=accounts,dc=test,dc=example,dc=it"
 - AUTH_LDAP_UID_FIELD = "uid"
 - AUTH_LDAP_FIRSTNAME_FIELD = "givenName"
 - AUTH_LDAP_LASTNAME_FIELD = "sn"
 - AUTH_LDAP_EMAIL_FIELD = "mail"
 - AUTH_LDAP_BIND_USER = "uid=admin,cn=users,cn=accounts,dc=test,dc=example,dc=it"
 - AUTH_LDAP_BIND_PASSWORD = "password"
 - AUTH_LDAP_ALLOW_SELF_SIGNED = True


Build superset image

.. code-block:: bash

 > ./build.sh
 > docker-compose up -d

It will start Superset, Postgres and Redis servers.
Wait some time to be sure all processes are up and running.

Run the init command to load into Superset some data for testing:

.. code-block:: bash

 > ./init.sh

Connect to http://localhost:8088/ to browse the Superset web app.

.. The first time to create admin user (admin password) - initialize db - exmaple
