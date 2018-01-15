.. Data & Analytics Framework - DAF documentation master file, created by
   sphinx-quickstart on Tue Sep 19 18:06:26 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Data & Analytics Framework (DAF) - Developer Documentation
============================================================

.. NOTE::

  This documentation refers to the Alpha version of the DAF (released in October 2017) and it is daily updated and improved.
  For comments and enhancement requests about the documentation please open an issue on `Github <https://github.com/italia/daf-docs>`_.

The `Data & Analytics Framework <https://pianotriennale-ict.readthedocs.io/en/latest/doc/09_data-analytics-framework.html>`_ (DAF, in short) is an open source project
developed in the context of the activities planned by the
Italian `Three-Year Plan for ICT in Public Administration 2017 - 2019 <https://pianotriennale-ict.readthedocs.io/en/latest/>`_,
approved by the Italian Government in the 2017.

The DAF project is an attempt to establish a centrl Chief Data Officer for the Government and Public Administration. Its main goal is to promote the exchange of data between Italian Public Administrations (PAs), to support the diffusion of open data, and to enable data-driven policies. The framework is composed by three building blocks:

* **Big Data Platform** to store in a unique repository the data of the PAs, implementing ingestion procedures to promote standardization and therefore interoperability among them. It exposes functionalities common to the Hadoop ecosystem, plus a set of (micro) services designed to improve data governance and a number of end-user tools that have been integrated with them.
* **Team of Data Experts"** (data scientists and data engineers) that knows how to manage and evolve the platform, and provide support to PA on their analytics and data management activities in a consultancy fashion.
* **Regulatory Framework** that institutionalizes this activity at government level, and gives the proper mandate to the PA that will manage the DAF, in compliance with privacy policy.

This documentation is focused on the **Big Data Platform**, and we'll refer to it as DAF for the sake of simplicity.

The Italian instance of the DAF is developed and maintanied by the `DAF Team <https://teamdigitale.governo.it/it/projects/daf.htm>`_ (part of the Digital Transformation Team of the Italian Government)  composed by data scientists and data engineers, which uses and evolves the framework to analyze data, create machine learning models and build data applications and data visualization products.

Anyway, the DAF is a generic enough tool to be re-used in other countries and other application domains. In fact, the DAF exposes the following data management and analytics functionalities:

- a **Public Dataportal**, a Web user interface providing:

   - a catalog of open-data datasets based on `CKAN <https://ckan.org>`_;
   - a content management system for *data stories*, posts where users can share their analysis, with possibility to integrate directly with the tools used (graphs and code);
   - community tools to collaborate and learn how to use the platform;

- a **Private Dataportal**, a web application with the following features:

   - a catalog of all dataset the user can access;
   - an ingestion form to govern (insert, edit, delete) dataset information and setup ingestion procedures;
   - data visualization and dashboard tools;
   - data science notebook;

- a **Hadoop Cluster** with typical applications to centralize and store, manipulate and standardize and re-distribute data and insights;
- a **Multy tenant** architecture, based on Kerberos and LDAP. 

The DAF is under development. This is a snapshot of the roadmap:

- By October 2017: Alpha release.
- By December 2017: Alpha2 release.

All contributions are welcome!

Contents:

.. toctree::
   :maxdepth: 2

    Overview <overview/index>
    Data Management <datamgmt/index>
    Data Portal <dataportal/index>
    Big Data Platform <bigdataplatform/index>
    Data Management <datamgmt/index>
    Microservices <microservices/index>
    Installation  <installation/index>
    [ITA] Manuale utente <manutente/index>
