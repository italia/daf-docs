*****************
Dataportal-public
*****************

===========
What it is?
===========

The Dataportal-public [put link]  is the webapp to access the open data catalog and other content that can be exposed publicly


=======
Install
=======

Before proceeding with the installation steps, you need to install and run the following external components:

Basic Dependencies
------------------
There are no basic dependencies needed.


Features Enabling Dependencies
------------------------------
Connection with DataStories:

* `DAF Dataportal Backend <https://github.com/italia/daf-dataportal-backend>`_

Installation Steps
------------------
First of all, clone the DAF github repository(if you haven't already done):

.. code-block:: bash

 > $ git clone https://github.com/italia/daf
  
Then publish a local snapshot as follows:

.. code-block:: bash

  > cd daf
  > cd common
  > sbt publish-local
  > cd ..
 
  
clone the this dataportal-backend repository:

.. code-block:: bash

   > $ git clone https://github.com/italia/daf-dataportal-backend
   > sbt compile
   > sbt run
   Listening for HTTP on /0:0:0:0:0:0:0:0:9000
   


