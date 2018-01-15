More on Datasets: A Deep dive
=============================

Datasets are the center around which DAF architecture has been build. In fact, DAF provides advanced features for data governance, analysis and interoperability designed to solve typical problems faced by the public administrations and large companies. In this section we expands on what has been presented in the Overview section, to better describe how datasets are managed in DAF. What will follows is common to all datasets managed in DAF, except for some aspects related to stream of data, that will be covered into an ad hoc section.

In what follows, a dataset is defined as a combination of data and metadata. Data is the actual content of the dataset, and can be organized into tabular, json and text formats. Metadata are all the information about the dataset that describe and give context to its contect. Metadata will be treated in details in an appropriate section.


Ordinary Dataset
----------------

Every datasets that are ingested by an organization (PA) are treated as **ordinary dataset**. Ordinary dataset does not have a pre-defined structure they need to follow, they are ingested as they come, besides the standardization, normalization and enrichment processes defined in the ingestion pipeline. 

They will have the following data structure:

* standardized & normalized original columns
* raw original columns
* enrichment columns, among which (most of them will depend on the content of the original columns):
  * `__ROWID`: global unique row id
  * `__dtcreated`: date and time when the info has been added
  * `__dtupdated`: date and time when the info has been updated

Ordinary datasets can be created from data coming from outside DAF, or by transformations applied to already existing DAF datasets. For example, a public administration can decide to create an open data version of a private dataset, by indicating the columns that can be released publicly and an optional aggregation policy. In this way, everytime the private dataset receives updates, they will be automatically be reflected into its open data version (that will be another dataset in the DAF world).

Storage & other conventions
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Ordinary datasets are stored by default in HDFS in parquet format and exposed as Hive and Impala tables. Data will be physically stored in the following HDFS directory: 

``/daf/ordinary/{organization}/{domain}_{subdomain}/{dataset name}/{version}``

where:

* ``{organization}`` is the name of the organization owner of the dataset, e.g. 'Comune_Milano'
* ``{domain}`` and ``{subdomain}`` are the code of the categories used to group the data. They are mutuated from DCATAP_IT.
* ``{dataset name}`` is the unique identifier for the dataset
* ``{version}`` is the name of the version of the dataset that is stored into that folder. It can typically be ``landing`` for the raw data ingested, ``final`` for the output of the ingestion pipeline. The final version will be the one exposed via API by DAF.

As convention, DAF manages a system of logical uri by which a dataset can be uniquely identified. In the case of ordinary dataset, it is built as follows:

``daf://dataset/ordinary/{organization}/{domain}/{subdomain}/{dataset name}``


Standard Datasets
-----------------

Standard Datasets are those datasets that describe concepts and phenomena valid nationwide, following a strict data structure and semantics rules. In fact, standard datasets are said to follow 'standards' that are defined for all PAs to follow, so to guarantee that a given phenomena is described in the same way and following the same conventions nationwide. Data will be physically stored in the following HDFS directory:

They will typically have the following data structure:

* standardized and normalized mandatory columns, grouped under the ``mand.{colname}`` struct field
* standardized and normalized optional columns, grouped under the ``opt.{colname}`` struct field
* enrichment columns from the ingestion procedures, grouped under the ``enr.{colname}`` struct field
* operational enrichment columns, with info needed for internal DAF operations and grouped under the ``ops.{colname}`` struct fields. These fields are:
  * ``__dtcreated``: date time when the info has been ingested into the standard dataset
  * ``__dtupdated``: date time when the info has been updated
  * ``__srcorg``: the code name of the organization that originated the data (e.g. 'Comune_Milano')
  * ``__dsname``: the unique name of the ordinary dataset from which the data come from.

Dataset standards can be created directly by a PA, if it is the only contributor to the national standard, or by 2 or more PAs in cases when every PA contribute to the national standard with the piece of info it manages. In the latter case, the standard dataset is created starting from 2 or more ordinary datasets, and in this case can be considered a 'derived' dataset. In this case, the ordinary dataset will specify that they contribute to a standard and the mapping model needed to map the ordinary dataset into the standard one.

Storage & other conventions
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Standard datasets are stored by default in HDFS in parquet format and exposed as Hive and Impala tables. Data will be physically stored in the following HDFS directory: 

``/daf/standard/{domain}__{subdomain}/{dataset name}/{version}``

If not specified differently, it is partitioned based on ``__srcorg`` and, in case the dataset is of type 'last update' (meaning it is composed by append of snapshot updates, as opposed to 'time series' type), it is also partitioned by ``__dtcreated``


Raw Open Data
-------------
Finally, we collect and store raw open data coming from the national catalog. They are automatically metadated based on the info available (in 'at best' fashion), and stored in HDFS in the following path:

``//daf/opendata/{organization}/{dataset name}``

Once ingested, they can be used with all other tools managed by DAF.
