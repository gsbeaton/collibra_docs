Configuration and Running
=========================
To allow the Connector to interact with both your Dataiku and Collibra instances, as a 
minimum requirement you must edit your ``config/dataiku.json`` and ``config/collibra.json`` 
configuration files before you can run the connector.

Customising your Dataiku Configuration
######################################

To add your Dataiku connection details, open the ``config/dataiku.json`` file in your favourite editor.

Your file should look something like this

.. code-block:: json

    [
      {
        "url": "",
        "apiKey": "",
        "instanceNickname": "DSS instance 1"
      }
    ]

Edit the following parameters
-----------------------------
    * ``url`` The URL of the instance's public API
    * ``apiKey`` Generate a Dataiku API key
    * ``instanceNickname`` Optionally, add a unique name for this instance
   

Connecting to Multiple Dataiku instances
----------------------------------------
This connector can be configured to connect to one or more Dataiku instances. For each instance you will need to supply the following:

You will need to enter this information in the ``config/dataiku.json`` file. For example, if you have 2 Dataiku instances you would like the connector to contactm specify them in ``dataiku.json`` as follows

.. code-block:: json
    :caption: An example code block connecting to two Dataiku instances.

    [
      {
        "url": "https://dataiku-url1.com:11000/public/api/",
        "apiKey": "apikey1",
        "instanceNickname": "DSS instance 1"
      },
      {
        "url": "https://dataiku-url1.com:11000/public/api/",
        "apiKey": "apikey2",
        "instanceNickname": "DSS instance 2"
      }
    ]

Bypassing Invalid Certificates
------------------------------
.. Caution:: Setting the connector to bypass invalid certificates leaves you vulnerable to MITM (Man In The Middle) attacks. We recommend this setting is only used in a controlled secure zone such as a private network.

To set the connector to ignore an invalid certificate eg one that has expired, is invalid or has a broken chain, you will need to change the ``validCertificate`` parameter in the ``config.json`` file to ``true``.

.. code-block:: json
    :caption: An example code block connecting to two Dataiku instances.

    [
      {
        "runTimeInterval": "40m"
        "validCertificate": true
      }
    ]

Customising your Collibra Configuration
#######################################

To add your Collibra credentials, open ``config/collibra.json``. Using your favourite text editor. Update the following parameters.

 * ``prefix``:  this can be set to a string that will prefix all asset types, attribute types and relationship types that are created in Collibra by this connector
 * ``limitProjectLoad``: default is 1 so during install and testing not all projects are processed
 * ``url`` Collibra URL
 * ``pwd`` and ``uid`` Eneter your Collibra login credentials. Note it is recommended that you create a specific Dataiku user for Collibra.
 * ``defaultStatus`` all assets will be created with this status.  Collibra recommends this connector should create with status a status of ``Accepted``.  This is a default status, but you can type in any valid string and the connector will create if it does not exist.
 * ``Domain`` The connector will create items unders the existing domain types in your Collibra setup.  See ``Your_Collibra_Server -> Settings -> Domain Types``.  
  
.. Note:: Collibra recommends that you add Dataiku assets under the default Data Asset Domain. 

Adding the ``projectDomainType`` and ``connectionDomainType``
--------------------------------------------------------------

The connector needs some further information from your Collibra server to complete setup. Currently you need to get the Collibra Id for that domain type. The easiest way to do this is to use the Collibra API online document that is found on the Collibra Help Menu. 
To edit this, follow these steps:
#. In your Collibra instance, open **Api documentation** then expand **Domain Types**
#. Click on **GET** then type *Data Asset Domain* into the name input. Click **Execute**
#. Scroll down to **response** and copy the long GUID-like ID.
  
This value can then be pasted into the ``projectDomainType -> parentId`` and ``connectionDomainType -> parentId`` in your ``config/collibra.json`` file.

Adding the ``parentCommunityId``
--------------------------------

The ``parentCommunityId`` is slightly easier to find. Go to the Collibra Dashboard amd navigate to the Community you would like all Dataiku projects to reside.  After selecting the Community copy the last part of the url (the id) and use that for the ``community -> parentCommunityId`` setting.

.. Caution:: If settings are changed in this config the next connector run may re-create assets in Collibra with the new config.

Configuring the Log Directory and Run Time Interval
###################################################

The connector can be customised to run at pre-determined intervals depending on business requirements. When the connector is first started, it performs an immidiate syncronisation.
The customisable parameters are as follows:

* ``logDirectory``: Default is ``"./logs"`` but can be directory on the server of your choice,
* ``apiResponseTimeoutSeconds``: Default is ``5`` seconds. Determines how long the connector waits for a response from Dataiku or Collibra before returning a __timeout__ error and moving on.
* ``firstRunTime``: This parameter is currently unsupported and should be left at the default value of ``"00:00``,
* ``runTimeInterval``: The time interval in minutes that the connector should wait between synconisations. The default value is ``"40m"``.