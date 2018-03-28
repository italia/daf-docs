*****************
Dataportal-public
*****************

===========
What is it?
===========

The `Dataportal-public <https://dataportal.daf.teamdigitale.it/>`__ is the web app that allows access to the open data catalog and other content that can be exposed publicly.


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

* `daf-dataportal-backend <../local/devVM.html#dataportal>`__


Installation Steps
------------------
First of all, clone the following GitHub repository:

.. code-block:: bash

 > $ git clone https://github.com/italia/daf-dataportal-backend
  
Start in Debug Mode:

.. code-block:: bash

  > npm install
  > npm start 

Start with mock server:

.. code-block:: bash

  > npm run mock

Start in Production Mode:

.. code-block:: bash

  > npm run build
  > npm install -g serve
  > serve -s build

