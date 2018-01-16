DAF - Data Ingestion
====================

Regardless of the nature of the dataset to be ingested in the platform,
the input dataset get stored into a landing area in HDFS.

Once there, the platform activates the following pipeline:

-  it reads all files contained in a configurable folder. Here, data
   should be organized into subfolders corresponding to each data owner
   (the entity that sends the data into the platform).

-  Once the dataset has been read, the module looks for the conversion
   schema associated with it. If it is found, the module verifies
   if there is an associated standard schema.

-  If the standard schema is found, then the module does coherence
   checks to make sure that the input schema is made according to the
   predefined standard schema.

-  Afterwards, the actual dataset is checked with respect to the resulting schema. If all
   the checks are positive, then the dataset gets saved into DAF. The saving
   methodology depends on the fact that the dataset belongs to the
   standard dataset or not.

-  In case there is no conversion schema associated with the dataset,
   the platform considers it as a ordinary dataset, so it tries to find a
   corresponding basic metadata, and if found, it saves the data
   accordingly.
