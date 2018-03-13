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
* ``type``: data format of the column, such as 'string'.
* ``metadata.title``: human readable name for the column.
* ``metadata.desc``: description of the content of the column.
* ``metadata.field_type``: it tells if the column is a dimension, a metric (numeric attribute) or a descriptive attribute.
* ``metadata.required``: it tells if the field is mandatory or optional.
* ``metadata.uniq_dim``: checked if the column is part of the list of dimensions that make the row unique, such that there will not be two rows with the same values for the columns checked as ``uniq_dim``.
* ``metadata.is_createdate``: boolean, checked if the column contains the date when the row was created.
* ``metadata.is_updatedate``: boolean, checked if the column contains the date when the row was updated.
* ``metadata.cat``: category that can better represent the content of the field. This is controlled by a vocabulary.
* ``metadata.tag``: list of tags that can better represent the content of the field. All tags are saved into an evolving vocabulary.
* ``metadata.constr``: a list of objects (made by ``type`` and ``param`` arguments) to set contraints on the content of the field.
* ``metadata.semantics``: an object containing semantic info to link hte column to related ontology and controlled vocabulary, if any. In particular:

  * ``id``: this is the semantic tag that links the column with a given attribute of a concept described into an ontology.
  * ``context``: this info gives context info on the semantic tag.
  * ``rdf_subject``: it is used to give a better context to the info contained in the column. Technically, it is a tag for a concept described into an ontology. In most cases, it can be seen as the subject that makes an action, derived from the id attribute.
  * ``rdf_predicate``: the action that the subject perform on the content of the column.
  * ``rdf_object``: the target of the action performed by the subject. 
  * ``uri_voc``: It is a unique identifier for the vocabulary. It matches with the ``dsname`` field of the dataset in DAF.
  * ``uri_property``: it is the uri associated to the element epressed in the column. It is used, among other things, to link the column of the dataset to the column of the vocabulary which controls it, if any.
  * ``property_hierarchy``: it is of type array, and it gives info about the hierarchy, if any, to which the property/column belongs to.  

* ``metadata.personal``: this objects contains info whether the data are of personal kind. In particular:

  * ``ispersonal``: boolean, to tell whether or not the info contained in the column is a personaltype of information.
  * ``cat``: category of personal information

* ``metadata.format_std``: this is an object that gives info about a format standard the data follows when ingested in DAF. It is useful to help the system identify such standard and transform into the DAF choosen standard. The object has the following two attributes:
 
  * ``name``: name of the format standard, e.g. date, credit card, address, etc.
  * ``param``: depending on the type of format, it is a string giving the exact formatting order and composition of the information contained. E.g. for the date example, it may be 'YY/MM/DD'. This will help the normalization procedure to refactor in the right order and format the information, such to follow the DAF internal conventions. 

* ``metadata.field``: it has info on indexing in SearchEngine and profiling of the field, plus other Kylo specific information on standard and validation.

  * ``is_index``: it tells to create an index based on this field in the SearchEngine.
  * ``is_profile``: it tells to create a profile for the field that will be displayed as result of the SearchEngine.
  * ``validation``: contains info on the validation rules to be used for the field.
  * ``standardization``: contains info on the standardization procedure to be performed on the field.

  Operational level metadata
--------------------------

These metadata are used to manage the dataset within DAF logics and conventions, from input sources to storage options to ingesiton pipelines mechanics.

* ``inactive``: optional boolean, true if the dataset entry has been created as inactive (that is, no effects on the system has been created, e.g. no ingestion pipeline has been started for the dataset yet). 
* ``theme``:..
* ``subtheme``:...
* ``logical_uri``:
* ``physical_uri``:..
* ``is_std``:..
* ``group_own``:...
* ``group_access``: (name, role)
* ``std_schema``:...
* ``georef``:..
* ``input_src``: It is an object containing information about input feeds, which can be of the following types: 
  
  * ``sftp``: it contains info on how to access the sftp plus specific info on the feed characteristics (i.e. data format and related options)
    * ``name``
    * ``url``
    * ``username``
    * ``password``
    * ``param``: this is a json string containing info related to the specific input type not already codified. An important info contained here is the type of file to be ingested (e.g. csv, json, xml) and option related to the file format.
  * ``srv_pull``: , srv_push, daf_dataset. Each of them, 

* ``ingestion_pipeline``:..
* ``storage_info``: (hdfs, kudu, hbase, mongo, textdb)
* ``dataset_proc``: It has info about how to process and store internally the dataset. Such info includes partitioning, merge strategy, etc.
  
  * ``read_type``: update vs timeseries
  * ``dataset_type``: batch vs stream
  * ``partitions``: It contains info on how the dataset is partitioned in DAF.

    * ``name``: name of the partition, given by the user.
    * ``field``: name of the field to be used for partitioning. It must correspond to one of the 'name' of the dataschema.
    * ``formula``: the formula to be applied to the field to get the partition value.
  
  * ``merge_strategy``: It tells how new data should be ingested into the existing dataset. User must choose among the following options. 'SYNC' to replace the existing content with      the new one; 'MERGE' to append the data into the target partitions; 'DEDUPE_AND_MERGE' to insert into the target partition but ensure no duplicate rows are remaining; 'PK_MERGE'      to insert or update existing rows matching the  same primary key; 'ROLLING_SYNC' to overwrite target partitions only when present in source.

* ``opendata``: it is used to tell the system to create an open data version of the dataset. If valued, it will create a new derived dataset entry, precompiled with info taken from the original dataset, and put into 'inactive' state so it can be valued and confirmed by the user. It is an object with the following info:
  * ``create_opendata``: boolean, valued as true if user wants to create a derived open data dataset.
  * ``sql``: SQL query with the final data structure of the open data dataset.
* ``service_layer``: it is used to put the dataset (or its transformation) into the service layer (Kudu?)
  * ``transfer_mode``: it tells whether the dataset will be put as is in the service layer or it needs to be transformed via derived dataset. It takes two values: ``direct``, ``derived``.
  * ``sql``: optional, used in case ``transfer_mode`` is valued at ``derived`` and user wants to specify ex-ante the transformation query.
