Dataset MetaCatalog: a deep dive into metadata for datasets
===========================================================

The MetaCatalog, managed by the Catalog Manager microservice (see Architecture Section), are detailed info describing a dataset. They are data about data, therefore metadata. Metadata are heavily used in DAF to help discoverability of dataset, allows for multi-system interoperability, perform internal automatic operations. According to their function, metadata are divided into 3 macro categories: dataset level (DCATAPIT), data structure level, operational level metadata.


Dataset level metadata (DCATAP_IT)
----------------------------------

These metadata are meant to describe the dataset's info such as its name, owner, category, etc. DAF implemented the mandatory fields of the DCATAP_IT profile, according to AGID regulations. Following a subset of the DCATAPIT metadata (see the link below for a complete list of required info)

* ``name``: dataset unique name
* ``title``: title of the dataset
* ``identifier``: dataset unique identifier
* ``alternate_identifier``:...
* ``author``: ...
* ``theme``: thematic domain that characterize the dataset
* ``license_id``:...
* ``resources``: a list of resources from where to download the dataset and other related data. Dataset managed in DAF will have here API endpoints to download and access the dataset.
* ``license_title``:
* ``frequency``:
* ``publisher_name``: name of the organization that publish the dataset
* ``publisher_identifier``....
* ``organization``:....
* ``owner_name``: name of the organization that owns the dataset
* ``holder_name``:...
* ``holder_identifier``:...
* ``tags``: tagging system connected to vocabulary.
* ``relationshiops_as_subject``:...
* ``notes``: additional information
* ``modified``: date of last modification to the dataset


Data structure level metadata
-----------------------------
Data scructure metadata contains information about the internal structure of a dataset, at column or field level. It manages info about format, content, semantics that are contained into a single column of a tabular dataset, for example. Here we store two datastructure metadata: an avro schema of the dataset, and a 'flatschema' where we store additional information than the one provided by the avro schema, specifically thought to enrich the information expressed about the content and the semantics of the columns. Below, you'll find the list of info contained in the 'flatschema' part, we'll skip the avro schema part as are using the standard avro schema definition.

* ``name``: name of the field/column. This name needs to obey to formatting rules that are necessary for it to be used as the name of a column in a database, therefore it may not be human readable.
* ``title``: [TBA] human readable name for the column.
* ``type``: data format of the column, such as 'string'.
* ``desc``: description of the content of the column.
* ``metadata.field_type``: it tells if the column is a dimension, a metric (numeric attribute) or a descriptive attribute.
* ``metadata.required``: it tells if the field is mandatory or optional.
* ``metadata.cat``: category that can better represent the content of the field. This is controlled by a vocabulary.
* ``metadata.tag``: list of tags that can better represent the content of the field. All tags are saved into an evolving vocabulary.
* ``metadata.constr``: a list of objects (made by ``type`` and ``param`` arguments) to set contraints on the content of the field.
* ``metadata.semantics``: an object containing semantic info to link hte column to related ontology and controlled vocabulary, if any. In particular:
  
  * ``id``: this is the semantic tag that links the column with a given attribute of a concept described into an ontology.
  * ``context``: (or Subject) it is used to give a better context to the info contained in the column. Technically, it is a tag for a concept described into an ontology. In most cases, it can be seen as the subject that makes an action, derived from the id attribute.
  * ``predicate``: [TBA] the action that the subject perform on the content of the column.
  * ``voc``: it is  a semantic tag associating the column to a given controlled vocabulary, if it exists. This tag contains also info about the hierarchy of the vocabulary used.

* ``metadata.uniq_dim``: checked if the column is part of the list of dimensions that make the row unique, such that there will not be two rows with the same values for the columns checked as ``uniq_dim``.
* ``metadata.personal``: this objects contains info whether the data are of personal kind. In particular:

  * ``ispersonal``: boolean, to tell whether or not the info contained in the column is a personaltype of information.
  * ``cat``: category of personal information

* ``metadata.format_std``: this is an object that gives info about a format standard the data follows when ingested in DAF. It is useful to help the system identify such standard and transform into the DAF choosen standard. The object has the following two attributes:
 
  * ``name``: name of the format standard, e.g. date, credit card, address, etc.
  * ``param``: depending on the type of format, it is a string giving the exact formatting order and composition of the information contained. E.g. for the date example, it may be 'YY/MM/DD'. This will help the normalization procedure to refactor in the right order and format the information, such to follow the DAF internal conventions. 


Operational level metadata
--------------------------

These metadata are used to manage the dataset within DAF logics and conventions, from input sources to storage options to ingesiton pipelines mechanics.

* ``group_access``: (name, role)
* ``group_own``:...
* ``input_src``: (url, srv_pull, srv_push, daf_dataset, sftp)
* ``logical_uri``:
* ``storage_info``: (hdfs, kudu, hbase, mongo, textdb)
* ``physical_uri``:..
* ``ingestion_pipeline``:..
* ``is_std``:..
* ``theme``:..
* ``subtheme``:...
* ``dataset_type``: batch vs stream
* ``georef``:..
* ``read_type``: update vs timeseries
* ``std_schema``
* ``opendata``: object that contains the information needed to build an opendata version of the dataset accordingly to transformation rules.

