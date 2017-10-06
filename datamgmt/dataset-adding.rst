Adding a new Dataset
====================

From a user perpective, adding a new
dataset is a rather simple operation: it is
sufficient for the user to successfully complete the registration procedure and use the related available function.

From the DAF perspective, adding a new dataset entails creating a
new instance of the DatasetCatalog, which holds
all metadata information about the dataset as well as the operational information
required for backend operations purposes.

Data can be added synchronously (i.e., data is saved in DAF at the same
time the dataset is created in the
`CatalogManager <../bigdataplatform/architecture/componentView/index.html#id1>`__) or at a later
time (with an append operation on an existing dataset).

In the following we describe the ingestion procedure that has been implemented in the presence of a new dataset. For each step of the procedure, we provide details of which microservices are used to perform the required tasks.

Create a new Dataset in the CatalogManager
------------------------------------------

This is the first step to be performed to create a new dataset. It is a
compound activities that span from receiving metadata information about the
dataset, performing a series of checks on the coherence of the information, and
storing it into the CatalogManager.

Step 1. Send metadata information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Metadata information is sent either via a webform or by directly calling the
``catalog-ds/add/{info}`` API (see the `related
doc <../bigdataplatform/architecture/componentView/api_catalogManager.html>`__ for more
details on the APIs). This metadata information is then used in the
following steps of the pipeline in order to perform the proper checks on them.

Step 2. Coherence checks
~~~~~~~~~~~~~~~~~~~~~~~~

The metadata information is passed to a specific service that is responsible for performing 
coherence checks on them. The checks aim at verifying the following
conditions:

-  in case the dataset is linked to a standard schema, it checks that
   the dataschema and the conversion rules are coherent with respect to
   the standard schema;
-  in case the insert procedure has also data to be ingested, it checks
   that the defined dataschema is coherent with what is inferred from
   the data. The coherence check step returns a report object with information
   about the performed test.

Step 3. Evaluation of automatically generated fields
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The information collected so far in the process is then sent to a module that evaluates the
automatically generated information to be stored into the
CatalogManager, such as the dataset URI, the type of dataset (Standard,
or Ordinary dataset), etc.

Step 4. Save the metadata information in the Catalog Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add Data to the new created Dataset
-----------------------------------

If the input information contains indication of data to be associated
with the new dataset, then the pipeline of the process continues with the following
steps.

Step 5. Store the data
~~~~~~~~~~~~~~~~~~~~~~

The dataset URI is enough to store the dataset in the appropriate
HDFS folder and format.

Step 6. Activate services based on the data ingested
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every time new data comes in (either in the case of the creation of a new
dataset, or in the case data is ingested into an existing dataset), the
system activates a list of services. Based on what is defined in
the ``operational`` part of the metadata, these services perform operations to enable
services on the dataset or to generate/update analytics information on the dataset. Some
examples of such kinds of services include:

-  add the dataset in the Hive metacatalog and expose a JDBC connection
   to it
-  calculate automatic statistics on the dataset fields
-  add an index in ElasticSearch to allow for searching in the content of
   the dataset
