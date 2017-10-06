Metadata & Schemas
====================================

`Dataset <../dataset/>`__ is the main concept of DAF. There exist two types of datasets each having different required sets of rules and information, more stringent for the *standard* datasets, less for *ordinary* datasets.

Several *metadata* can be used to describe a dataset. Some metadata are
useful to implement search/discovery mechanisms, others provides
operational information.

Generally speaking, metadata are of three macro types:

-  **DCAT-AP(_IT)**: this kind of metadata defines a standard way to specify descriptive information of the datasets. It defines metadata about theme, geographic location, who
   produced the dataset, who is responsible of the dataset, title and description of the dataset, and so on. DCAT-AP_IT is the Italian extension of the European metadata profile DCAT-AP `Data Catalogue Application
   Profile <https://joinup.ec.europa.eu/asset/dcat_application_profile/description>`__. You can find the metadata schema DCAT-AP(_IT) in json `here <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/md-dcatapit.json>`__ and `an example application; <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/example/data-dcatapit.json>`__
-  **DataSchema**: this type of metadata involves the data content. Thus, it regards features and the associated
   type, optional constraints on the values that the features can take,
   as well as semantic information, optional theme and categories of
   each features.
   You can find the `DataSchema schema here <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/md-dataschema.json>`__ and an `example application; <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/example/data-dataschema.json>`__
-  **Operational**: this type of metadata is related to the operational back-end, such as
   dataset URI, physical storage URL, standard schema conversion,
   transformation pipeline, associated API for retrieval and ingestion,
   etc.
   You can find the `Operational schema here <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/md-operational.json>`__ and an `example application here <https://github.com/lilloraffa/daf-project/blob/master/datamgmt/metadata/example/data-operational.json>`__

In addition to the metadata types previously identified, the Big Data platform relies on the concept of *standard schema*, which is described below.

Standard Schema
---------------

A *standard schema* defines a *standard dataset*.

A standard schema declares the existence in the DAF of a specific standard dataset
and contains a set of information describing its structure and content.

More precisely, a standard schema defines all the rules and details that
a data source must oblige to if it wants to belong to a specific
standard dataset.

Thus, the standard schema includes the following information:

-  specific information on the dataset that is not foreseen in DCAT-AP(_IT) metadata profile;
-  the list of required fields, with information, among the other, about their format, constraints if any, nature (e.g. measure or a dimension), domain specific information that will help the programmatic use of the data in specific contexts;
-  the list of optional fields, with the same information listed for the required ones;
-  the associated DCAT-AP(_IT) metadata id;
-  information about where the data set is stored and how.
-  information about the owner of the data and the group (list of users) that has the rights to access the data.

... You can find the metadata of the `standard schema
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/schema-prototype.json>`__,
and a `Standard Schema example
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/mobility/shema-gtfs_fare_attributes.json>`__.

For example, let’s imagine we want to build a standard dataset describing the phenomena “Bike Sharing” and let’s suppose that we have multiple data sources each of which collecting bike sharing data for a specific geographic area (e.g. a town). 
In order to be eligible to insert data into the “Bike Sharing” standard dataset, each data source must provide data following the rules defined in the related standard schema provided by the DAF owner. The resulting dataset will then be able to describe a unique phenomena in a consistent way across multiple data sources. 
The data sources have two options at disposal: providing (i) either data following exactly the same schema defined in the standard schema, (ii) or the minimum set of required information along with a set of conversion information with which the platform will be able to convert the original schema to the standard one. In both cases, the platform makes use of a conversion schema that is described in the following.


Conversion Schema
-----------------

The *Conversion schema* is used to ingest both ordinary and standard datasets.

Every dataset in input needs to be associated with a conversion schema.

A conversion schema has a twofold purpose:

1. to provide basic information describing the dataset stored in the
   platform, at least at the level of ordinary dataset;
2. with respect to ordinary datasets, providing rules to map the related
   data schema to the standard schema.

The Conversion schema contains the following information:

-  specific information on the dataset that is not foreseen in DCAT-AP(_IT) metadata profile;
-  the reference to the associated standard schema in case the conversion
   schema is used to map the incoming dataset structure to a standard
   one. In this case, a list that maps each input field to the standard
   schema is provided.
-  the list of the so-called *custom fields* with the same information and
   structure of the required/optional fields described in the standard schema. This list has different purposes if the
   conversion schema is used to map to a standard one, or whether it is used to
   ingest an ordinary dataset. In the first case, the list contains
   fields that are not part of the standard schema, but they are still
   provided by the data source. In the case of ordinary dataset ingestion, it
   contains the full list of fields that describe the dataset itself.

... You can find the metadata of the `Conversion Schema
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/conv-prototype.json>`__,
and a `Conversion Schema example
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/mobility/examples_conv/it_palermo/conv-gtfs_fare_rules.json>`__.
