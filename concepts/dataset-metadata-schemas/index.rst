Datasets - Metadata & Schemas in DAF
====================================

`Dataset <../dataset/>`__ is the main concept of DAF. The two main types of datasets have different
required sets of rules and information, more stringent for the *standard
datasets*, less for *ordinary*.

Several *metadata* can be used to describe a dataset. Some metadata are
useful to implement search/discovery mechanisms, others provides
operational information.

Generally speaking, metadata are of three macro types:

-  **DCAT-AP(_IT)**: this kind of metadata defines a standard way to specify descriptive information of the datasets. It defines metadata about theme, geographic location, who
   produced the dataset, who is responsible of the dataset, title and description of the dataset, and so on. DCAT-AP_IT is the Italian extension of the European metadata profile DCAT-AP `Data Catalogue Application
   Profile <https://joinup.ec.europa.eu/asset/dcat_application_profile/description>`__.
-  **DataSchema**: this type of metadata involves the data content. Thus, it regards features and the associated
   type, optional constraints on the values that the features can take,
   as well as semantic information, optional theme and categories of
   each features.
   .. You'll find the `DataSchema schema here <md-dataschema.json>`__ and an `example application here <example/metadata/data-dataschema.json>`__
-  **Operational**: this type of metadata is related to the operational back-end, such as:
   dataset uri, physical storage url, standard schema conversion,
   transformation pipeline, associated API for retrieval and ingestion,
   etc.
   .. You'll find the `Operational schema here <md-operational.json>`__ and an `example application here <example/metadata/data-operational.json>`__

In practice, the Big Data platform relies on a schema and metadata framework based on three concepts:

-  standard schema
-  conversion schema
-  dataset metadata

Standard Schema
---------------

A *standard schema* defines a *standard dataset*.

A standard schema declares the existence of a specific standard dataset
and contains a set of information describing its structure and content.

More precisely, a standard schema defines all the rules and details that
a data source must oblige to if it wants to belong to a specific
standard dataset.

For example, let's imagine we want to build a standard dataset
describing the phenomena "Bike Sharing" and let's suppose that we have
multiple data sources each of which collecting bike sharing data for a
specific geographic area (e.g. a town). In order to be eligible to insert
their data into the "Bike Sharing" standard dataset, each data source
must provide data according to the rules defined in the related standard
schema defined by the DAF owner. The resulting dataset will then be able
to describe a unique phenomena in a consistent way across multiple data
sources. The latter have two options: either providing data following
exactly the same schema defined in the standard schema or providing
the minimum set of required information and a set conversion information with which
the platform will be able to convert the original schema to the standard
one. In both cases, the tool to do so uses the conversion schema described
in the next section.

Summarizing, a standard schema provides the following information:

-  specific information on the dataset that is not contained in
   DCAT-AP_IT.
-  the list of required fields, with information, among the other, about
   their format, constraints if any, nature (e.g. measure or a
   dimension), domain specific info that will help the programmatic use
   of the data in specific contexts.
-  The list of optional fields, with the same info listed for the
   required ones.
-  The associated DCAT\_AP metadata id.
-  Information about where the data set is stored and how.
-  Information about the owner of the data and the group (list of users)
   that has the right to access the data.

You can find the metadata of the `standard schema
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/schema-prototype.json>`__,
and a `Standard Schema example
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/mobility/shema-gtfs_fare_attributes.json>`__.

Conversion Schema
-----------------

**THIS SECTION NEEDS IMPROVEMENTS**

*Conversion schema* is the basic tool to ingest both ordinary and
standard dataset in the platform.

Every dataset in input needs to have an associated conversion schema.

A conversion schema has a twofold purpose:

1. to provide basic information describing the dataset stored in the
   platform, at least at the level of ordinary dataset;
2. with respect to ordinary datasets, providing rules to map the related
   data schema to the standard one.

Conversion schema contains the following info:

-  specific information of the dataset not contained in DCAP\_AP.
-  the reference to the associated standard schema in case conversion
   schema is used to map the incoming dataset structure to a standard
   one. In this case, a list mapping each input field to the standard
   schema one is provided.
-  the list of the so-called *custom fields* with the same info and
   structure of the required/optional fields described in the section
   about standard schema. It has a different purpose in case the
   conversion schema is used to map to a standard one, or it is used to
   ingest an ordinary dataset. In the first case, this list contains
   fields that are not part of the standard schema, but are still
   provided by the data source. In the ordinary dataset case, it
   contains the full list of fields that describe the dataset itself.

You can find the metadata of the `Conversion Schema
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/conv-prototype.json>`__,
and a `Conversion Schema example
here <https://github.com/lilloraffa/daf-datamgmt/blob/master/dataschema/mobility/examples_conv/it_palermo/conv-gtfs_fare_rules.json>`__.

Dataset Metadata
----------------

**THIS SECTION NEEDS IMPROVEMENTS**

This is the minimum set of metadata required to register a dataset in
the DAF Platform.

This is the lowest level of details the platform need to classify, build
a catalogue and expose datasets. Here the level of description is the
dataset itself, no info on the internal structure/fields are provided.
This is the minimum required info to build the catalogue like the well
known Open Data catalogue, and uses CKAN as internal backend.

*NOTE: TO BE DECIDED IF WE IMPOSE THE DCAT\_AP AS MINIMUM REQUIREMENT
FOR ACCEPTING DATA*

You can find the metadata of the `Metadata schema here <???>`__, and an
`example here <???>`__ [coming soon...].
