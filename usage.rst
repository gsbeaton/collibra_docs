Usage
#####

Starting the connector
======================

In order to start the connector, navigate to the folder fith your ``fti-connector`` file and type the following command

.. parsed-literal::

    #  ./fti-connector


If successful you should be greeted with execution logs, e.g.:

.. parsed-literal::

   # Process Start Time: xx:xx:xx xx/xx/xxxx
   # The next scheduled data connection will execute at xx:xx:xx xx/xx/xxxx, which is in x days, x hours, x minutes, x seconds
   # fti-connector> Successfully parsed config.json.
   # fti-connector> Successfully parsed dataiku.json (1 instance(s) found)
   # fti-connector>


Connector Commands
=====================
From the commnad line of the running connector the following commnads can be used to test your connector install. The connector supports the following commands.

``testDataiku``
---------------
tests connection and retrieves conections and projects

.. parsed-literal::

    #fti-connector> testDataiku

``testCollibra``
----------------
Tests authentication to the Collibra server

.. parsed-literal::

    #fti-connector> testCollibra

``setupCollibra``
-----------------
This command checks for the core data (asset types, relationship types, attribute types) in Collibra that is defined in `config/collibra.json`. 
This will create any that are not already existing and can be safely re-run.

.. parsed-literal::

    #fti-connector> setupCollibra

``testCollibraConnector``
-------------------------
This will copy assets from Dataiku to Collibra (this calls the same internal function that the normal schedule run calls)
You can pass an numeric index or project name to only proces that project (selecting by index position or name).

.. parsed-literal::

    #fti-connector> testCollibraConnector


Overriding Default Mappings
===========================

.. Caution:: You may, at your own risk, change the Asset Types and Relation Types used to represent your own specific setup of Dataiku objects. You can find these in ``config/assetTypes.json`` and ``config/relationTypes.json`` respectively. We recommend making backups of these files before making any changes.



Please note that if you have already previously used the connector to create Collibra assets and before changing the Asset Types or Relation Types, these Asset Types, Relation Types, and assets will all remain in Collibra.


Command Reference
=================

The connector offers a command line interface to help with configuration and management. The following commands are available:

``help``  This command displays the list of commands.
``info``  This command will display the next scheduled data connection time.
``updateconfig`` This command will re-read the config files and process any changes made.
``exit`` This command exits the connector.