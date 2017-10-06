******************
Installation Guide
******************

This section provides installation information for all DAF components, except for the Big Data Platform. Based on your development needs, you will be able to install separately only the components you require for your task. Almost every component has dependencies to other components, this will be documented in the installation guide of each component.

In general, components developed internally are available via github repositories, meanwhile external ones have been dockerized with all needed dependencies and configurations. 

Several components are dependent to LDAP and/or FreeIPA. In this case, we offer you three alternatives: a dockerized LDAP, a remote FreeIPA test server, or a dockerized FreeIPA (working with Linux only at the moment). All of them will have test accounts already created for you.


.. toctree::
   :maxdepth: 1

    Dataportal-public <../dataportal/dataportal-public>
    Dataportal-private <../dataportal/dataportal-private>
    CatalogManager <../microservices/catalog-manager>
    SecurityManager <../microservices/security-manager>
    FrontendManager <../microservices/frontend-manager>
    FreeIpa Docker <docker/freeipa>
    LDAP Docker <docker/ldap>
    CKAN Docker <docker/ckan>
    Superset Docker <docker/superset>
    Metabase Docker <docker/metabase>
    JupyterHub Docker <docker/jupyter>
