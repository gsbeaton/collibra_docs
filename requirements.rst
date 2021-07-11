Requirements
************

Server
######
The Connector runs as ``Node.js`` service. It can be installed on your DSS server or a standalone Linux instance. The Connector has been tested on Ubuntu distributions.

Prerequisites
#############

* You need a running instance of Dataiku DSS with Public REST API access `Discover, Enterprise or Business license <https://www.dataiku.com/product/get-started/>`_
* A running instance of `Collibra <https://www.collibra.com/>`_


Server Minimum Recommended Requirements
#######################################

* OS: Linux (Ubuntu)
* Network connections to Dataiku and Collibra instances
* Storage: the connector will create log files every time a data connection is made. The log file size will vary depending on amount of data and Dataiku instances.
