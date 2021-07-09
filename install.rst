=============
Installation
=============
The connector is a `Node.js` service to syncronise your `Dataiku <https://www.dataiku.com>`_ Meta Data into `Collibra <https://www.collibra.com>`_.


License Information
###################

- The connector is designed to connect to a single Collibra instance and 1 or more DataIKU instances. For information on licensing, please contact your DataIKU account representative. 

Preparing to Install the Connector
##################################

The connector is supplied as a pre-packaged executable service. It does not require any installation beyond placing the connector in a folder.
Copy the files to a suitable folder in your environment and ensure the following file and folder structure is maintained::

 ├── config
 │   ├── assetTypes.json
 │   ├── config.json
 │   ├── dataiku.json
 │   ├── relationTypes.json
 ├── fti-connector