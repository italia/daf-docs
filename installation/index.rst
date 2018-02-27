******************
Installation Guide
******************

This section provides installation information for all DAF components, except for the Big Data Platform. Based on your development needs, you will be able to install separately only the components you require for your task. Almost every component has dependencies to other components, this will be documented in the installation guide of each component.

In general, components developed internally are available via github repositories, meanwhile external ones have been dockerized with all needed dependencies and configurations. 

Several components are dependent to LDAP and/or FreeIPA. In this case, we offer you three alternatives: a dockerized LDAP, a remote FreeIPA test server, or a dockerized FreeIPA (working with Linux only at the moment). All of them will have test accounts already created for you.

The best way to have everything installed and properly configured is to use the Virtual Machine.

See the Local Installation guide to know how to configure the Virtual Machine or, if you want to run only few components, please follow the component installation guide you find at the links below.


.. toctree::
   :maxdepth: 1

    Local Installation <local/dockerVM>
    CatalogManager <microsrv/core/catalog-manager>
    IngestionManager <microsrv/core/ingestion-manager>
    SecurityManager <microsrv/core/security-manager>
    DatasetManager <microsrv/core/dataset-manager>
    StorageManager <microsrv/core/storage-manager>
    FrontendManager <microsrv/dataportal/frontend-manager>
    Dataportal-public <dataportal/dataportal-public>
    Dataportal-private <dataportal/dataportal-private>
    Semantics <microsrv/semantic/index>
    FreeIpa Docker <docker/freeipa>
    LDAP Docker <docker/ldap>
    CKAN Docker <docker/ckan>
    Superset Docker <docker/superset>
    Metabase Docker <docker/metabase>
    JupyterHub Docker <docker/jupyter>

