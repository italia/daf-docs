Interoperability, Standardization and Semantics
===============================================

One of the biggest issues DAF wants to solve is interoperability/integrability between datasets. This is achieved by a combined use of a deep metadata architecture together with semantic tagging, controlled vocabularies and ingestion transformation procedures.
At the ingestion time, every dataset get transformed and enriched so that the output can be easily "linked" to other datasets.

At the moment, we are working to cover the following standardization use cases:

* **Data format & conventions**: incoming data are treated to follow coherent internal conventions, e.g. date, url format, address format, text reformatted to account for normalization vocabularies, etc.
* **Data enrichment**: adding new information to the incoming dataset in order to improve the informative value of the dataset and ensure internal interoperability, e.g. terms standardization using controlled vocabularies, addresses components, global unique id for rows, etc.


Metadata, Semantic Tagging and Controlled Vocabularies
------------------------------------------------------

Datasets are associated to concepts and attributes described into domain ontologies via semantic tagging (done during the ingestion step). This mechanism consists in linking columns/features of the datasets to corresponding ontologies. This is done to specify the concepts and the attributes the datasets contains.

  For example, let's consider a dataset containing the list of Italian companies and their headquarters. Here all the columns related to anagraphic information (e.g. name, year of establishment, etc.) will be tagged with the corresponding semantig tag contained in the "Organizations ontology".
  Furthermore, the information related to the address of the headquarter will be tagged with the semantig tag of *the address of* from the "Places Ontology", and also associated to the concept of "company".
  In this way the address is the one of a company (as opposed, for example, to the address of a citizen).
  Finally, by having linked the address to the related concepts contained in the "Places ontology", we will be able to use all info contained in the mentioned ontology, included the existence of controlled vocabularies for the properties used.

The advantage of using ontologies and linking them to the ingested dataset are as follows:

* easier establishment and implementation of standard dataset at national level;
* possibility to logically link datasets based on their content and concepts. This feature is specifically useful in exploratory analysis and model munging;
* usage of the controlled vocabulary information so to provide standardization procedure to ensure the correct usage of the vocabulary in the dataset, and therefore, improve interoperability;
* possibility to build meaningful and rich knowledge graphs to be exploited for further analysis.
