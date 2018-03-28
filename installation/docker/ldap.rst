*****************
LDAP Installation
*****************

This docker container allows you to start a simple LDAP server (`OpenLdap <http://www.openldap.org/>`_
) and a client (`phpLDAPadmin <http://phpldapadmin.sourceforge.net/>`_
). In particular, the Docker Compose downloads an initial database having domain *daf.test.it* and containing the user *bob* with password *password*.

Clone the git project:

.. code-block:: bash

 > git clone git@github.com:italia/daf-recipes.git

Run the docker container:

.. code-block:: bash

  > cd ./daf-recipes/ldap
  > docker-compose up -d

Check whether dockers are running:

.. code-block:: bash

  > docker ps
  e8ff9611aeff  osixia/openldap  "/container/tool/r..."  17 minutes ago  Up 17 minutes  0.0.0.0:389->389/tcp, 0.0.0.0:636->636/tcp  ldap
  6a0d0d6c3b9a  osixia/phpldapadmin  "/container/tool/run"  17 minutes ago  Up 17 minutes  0.0.0.0:80->80/tcp, 443/tcp  phpldapadmin

**Note**

The Docker Compose requires that ports 80, 636 and 389 are available. If not, change them.

Now, open your favorite browser and type *http://localhost*.

.. image:: imgs/ldap_login.png
   :scale: 50 %
   :alt: LDAP login page
   :align: center

Login as *cn=admin,dc=example,dc=org* and password *admin* to navigate inside.

.. image:: imgs/ldap_tree.png
   :scale: 50 %
   :alt: LDAP web app
   :align: center



FreeIpa Instance
-----------------------
We installed a FreeIpa server which can be used for test purposes. It can be reached at the address *91.206.129.245*.
