 
Install
============================================================

This installation is tested on Ubuntu. The main reason is the difficulties to
launch freeipa docker on mac and windows (Any help making official freeipa docker 
working on these platforms will be very usefull). For users with mac and windows 
that want to test the application faster I suggest to install freeipa in some cloud 
provider with a public ip and ldap ports opened.

For angry users it is possible to install directly this virtul box images (wo)

These are a series of docker recipes that are used in daf-dataportal for giving tools and 
instruments for analyzing and visualizing data. 

In not necessary to install all dockers in order but is important to install freeipa as 
first docker because is an identity manager system which all dockers connect to have access.

- Install freeipa following the instructions in freeipa section.

- Install ckan following the instructions in ckan section.

- Install superset following the instructions in superset section.

- Install metabase following the instructions in metabase section.

- Install jupyter (working progress)



