Big data platform
=================

The DAF Big Data platform is an environment offering capabilities for:

-  *storing and managing datasets*: users can register and load datasets on the platform,
   specifying the ingestion model (e.g batch, streaming), the serialization formats (e.g. Avro, Parquet),
   the desired serving layers (e.g. HBase, Impala), metadata, etc;
-  *processing and analysing datasets*: the platform supports several Hadoop-based technologies.
   Users can not directly use these technologies, since they are mediated by user-friendly applications
   provided by the `Dataportal <../dataportal>`_ (e.g. Superset, Jupyter);
-  *managing of access rights for each dataset*: the adopted security approach allows
   the platform administrators to set the proper access rights for each dataset.

The DAF Big Data platform also enable *redistributing datasets, developing data application, publishing insights*
by mean of the above mentioned tools provided by the `Dataportal <../dataportal>`_: by these tools, data scientists and analysts can perform analysis on data, run statistical and machine learning models, and produce data
visualizazions and reports.

For more information, continue your tour looking at:

.. toctree::
   :maxdepth: 1

    Big Data Architecture <architecture/index>
    Security & Privacy issues <security/index>
