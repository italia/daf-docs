
CKAN
============================================================

CKAN is an open-source DMS (data management system) for powering data hubs and data portals.
CKAN makes it easy to publish, share and use data. It powers datahub.io, catalog.data.gov and data.gov.uk, among many other sites.

This guide will show you how to use Docker Compose to set up and run a `CKAN <https://ckan.org/>`_ instance which uses LDAP credentials to authenticate users. In particular, you can use an openLDAP Docker container or a FreeIpa instance.

Account Management Dependency
--------------------------

This configuration of CKAN needs an account management system to work with. We provide three different options, you will find more info on their respective sections:

* Local LDAP Docker
* Local FreeIPA Docker (works only with Linux)
* Remote FreeIpa Server

Ckan docker compose
-----------------------

Now that we have a LDAP server up we can run the CKAN Docker Compose. It will run an instance of Solr, Postgresql, Redis and Mongo.

First we have to build a custom image:


.. code-block:: bash

  > cd ./daf-recipes/ckan
  > ./build_local.sh

Then edit the file *ckan.ini*:

- If you are using our openLDAP server:

   .. code-block:: bash

      # LDAP Intergration with ldap and ip address
      ckanext.ldap.uri = ldap://LDAP_IP:389
      ckanext.ldap.auth.dn = cn=admin,dc=daf,dc=test,dc=it
      ckanext.ldap.auth.password = admin
      ckanext.ldap.base_dn = cn=users,cn=accounts,dc=daf,dc=test,dc=it
      ckanext.ldap.search.filter = uid={login}
      ckanext.ldap.username = uid
      ckanext.ldap.email = mail
      ckanext.ldap.ckan_fallback = True

where LDAP_IP is the IP of the LDAP docker. To know the LDAP IP, run:

.. code-block:: bash

  > docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ldap
  172.22.0.2

We know that this is not the best approach to connect containers among them (maybe it is the worst), we are using a deprecated compose file version (i.e. version 1 rather than using version 3), and we are using very heavy images. We will improve CKAN docker compose as soon as possible.

- If you are using our FreeIpa server
     .. code-block:: bash

      # LDAP Intergration with ldap and ip address
      ckanext.ldap.uri = ldap://91.206.129.245:389
      ckanext.ldap.auth.dn = uid=admin,cn=users,cn=accounts,dc=daf,dc=test,dc=it
      ckanext.ldap.auth.password = aiyaiPh8
      ckanext.ldap.base_dn = cn=users,cn=accounts,dc=daf,dc=test,dc=it
      ckanext.ldap.search.filter = uid={login}
      ckanext.ldap.username = uid
      ckanext.ldap.email = mail
      ckanext.ldap.ckan_fallback = True


Now that CKAN container is up, type *http://localhost:5000* on your browser and login as user *bob* (password *password*).

.. image:: imgs/ckan_login.png
   :scale: 50 %
   :alt: CKAN login page
   :align: center

.. image:: imgs/bob_page.png
   :scale: 50 %
   :alt: CKAN dashboard
   :align: center
