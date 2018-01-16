Data at rest
============

Once data arrives in the landing area, it is stored in HDFS
adopting the rules described in this documentation.

It is worth noting that data is always related to a dataset and it is
converted in AVRO format by-default. Furthermore, a copy of the
unaltered data sent by data-sources is always saved.

On the basis of the settings provided by the dataset owner during the
registration phase, data can be also stored as a Parquet file.

Data organization in HDFS
-------------------------

Data in HDFS is stored adopting the following folder structure. The
forder structure is designed to be as flexible as possible based on the
use cases of each dataset type (Standard and Ordinary).

Since the file format is derivable by the directory name, all files are
stored by using the following naming convention:

``YYYYMMDD_HHMMSS``

where:

-  ``YYYY`` stands for four-digit year date
-  ``MM`` stands for two-digit month date
-  ``DD`` stands for two-digit day date
-  ``HH`` stands for two-digit hour date
-  ``MM`` stands for two-digit minute date
-  ``SS`` stands for two-digit second date

Standard Dataset Directory Structure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All Standard datasets are stored in the following HDFS directory:

``/daf/standard/``

The content of this directory is organized following these rules:

``domain/subdomain/datasetName.datasetFormat/sourceOrg/``

where:

-  ``domain`` is the parent category to which the dataset belongs (e.g.
   "transport")
-  ``subdomain`` is the sub-category to which the dataset belongs (e.g.
   "traffic")
-  ``datasetName`` is the name of the dataset
-  ``datasetFormat`` specifies the serialization format. At the moment
   the allowed formats are: ``csv``, ``json``, ``avro``, ``parquet``.
-  ``sourceOrg`` is the name of the dataset owner. This name is
   specified as ``organizationType_organizationName``.

Ordinary Dataset Directory Structure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All Ordinary datasets are stored in the following HDFS directory:

``/daf/ordinary/``

The content of this directory is organized following these rules:

``sourceOrg/domain/subdomain/datasetName.stage.datasetFormat/``

where:

-  ``sourceOrg`` is the name of the organization owning the dataset.
   This name is specified as ``organizationType_organizationName``
-  ``domain`` is the parent category to which the dataset belongs (e.g.
   "transport")
-  ``subdomain`` is the sub-category to which the dataset belongs (e.g.
   "traffic")
-  ``datasetName`` is the name of the dataset
-  ``stage`` is the particular stage of the dataset in the
   transformation pipeline, ex. ``landing``, ``stage1``
-  ``datasetFormat`` specifies the serialization format. At the moment
   the allowed formats are: ``csv``, ``json``, ``avro``, ``parquet``

