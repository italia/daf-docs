Interoperability, Standardization and Semantics
===============================================

One of the biggest problems DAF wants to solve is interoperability/integrability between datasets. This is achieved by a combined use of a deep metadata architecture, semantic tagging, controlled vocabularies and ingestion transformation procedures. In fact, at the ingestion time, every dataset get transformed and enrichedso that the output can be more easily "linked"to other datasets.

At the moment, we are working to cover the following standardization use cases:

* **Data format & conventions**: incoming data are treated to follow coherent internal conventions, e.g. date, url format, address format, text reformatted to account for normalization vocabularies, etc.
* **Data enrichment**: adding new information to the incoming dataset so to improve the informative value of the dataset and ensure internal interoperability, e.g. terms standardization using controlled vocabularies, addresses components, global unique id for rows, etc.


Metadata, Semantic Tagging and Controlled Vocabularies
------------------------------------------------------

Datasets are associated to concepts and attributes described into domain ontologies via semantic tagging. This mechanism consists in linking columns/features of the datasets to corresponding ontologies to specify the concepts and attributed the datasets contains information about. For example, let's consider a dataset containing the list of Italian companies and their headquarters. Here all the columns related to anagrafic information of the company (e.g. name, year of establishment, etc.) will be tagged with the corresponding semantig tag contained in the "Organizations ontology". Furthermore, info related to the address of the headquarter will be tagged with the semantig tag of the address of the "Places Ontology", and also associated to the concept of "company" so to mean the address is the one of a company (as opposed, for example, to the address of a citizen). Finally, by having linked the address to the related concepts contained in the "Places ontology", we will be able to use all info contained in the mentioned ontology, included the existence of controlled vocabularies for the properties used. 
The advantage of using ontologies and linkind them to the ingested dataset are as follows:

* easier establishment and implementation of standard datased at national level
* possibility to logically link datasets based on their content and concepts. This feature is specifically useful in exploratory analysis and model muilding.
* usage of the controlled vocabulary information so to provide standardization procedure to ensure the correct usage of the vocabulary in the dataset, and therefore, improve interoperability.
* possibility to build meaningful and rich knowledge graphs to be exploited for further analysis.
