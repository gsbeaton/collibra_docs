# FTI Dataiku-Collibra Connector Documentation

**Contents**

- What is the connector?
- Requirements
- License Information
- Using the Connector
- Installing the Connector
- Getting Started
  - Dataiku Configuration
  - Collibra Configuration
  - Running the Connector
  - Overriding the Default Mappings
- Troubleshooting
- Command Reference

## **What is the Connector?**{#headin}

The Dataiku-Collibra connector is a tool built by [FTI Consulting](https://digitaldelivery.uk/) to push Dataiku artifacts/assets into Collibra for cataloguing purposes. Application code & unit tests originally written in NodeJS.

## **Requirements**

- Running instance of Dataiku DSS with Public REST API access ([Discover, Enterprise or Business license](https://www.dataiku.com/product/get-started/))
- Running instance of [Collibra](https://www.collibra.com/)

Technical requirements to install the connector:

- OS: Linux (Ubuntu)
- Network connections to Dataiku and Collibra instances
- Storage: the connector will create log files every time a data connection is made. The log file size will vary depending on amount of data and Dataiku instances.

## **License Information**

- The connector is designed to connect to a single Collibra instance and 1 or more DataIKU instances. For information on licensing, please contact your DataIKU account representative. 

## **Using the Connector**

Placeholder text  // may not be needed

## **Installing the Connector**

The connector does not require any installation beyond placing the connector in a folder. The folder structure should be as follows:

```
├── config
│   ├── assetTypes.json
│   ├── config.json
│   ├── dataiku.json
│   ├── relationTypes.json
├── fti-connector
```

## **Getting Started**

Placeholder text

### Dataiku Configuration

This connector can be configured to connect to one or more Dataiku instances. For each instance you will need to supply the following:

1. The URL of the instance's public API
2. An API key

You will need to enter this information in the `config/dataiku.json` file. For example, if you have 2 Dataiku instances you would like the connector to contactm specify them in `dataiku.json` as follows:

```
[
  {
    "url": "https://dataiku-url1.com:11000/public/api/",
    "apiKey": "apikey1"
  },
  {
    "url": "https://dataiku-url2.com:11000/public/api/",
    "apiKey": "apikey2"
  }
]
```

### Collibra Configuration

As with Dataiku, you must specify the following in `config/collibra.json`:

1. Collibra URL
2. Collibra credentials
3. Domain/Community

If you wish to view asset relationships on the "Overview" page of specific assets, then you will need to manually create the appropriate Assignments in the Collibra interface on the Asset Types. This is a one-time step that will retroactively apply to all the assets, so you may do this at any time.

### Running the connector

In order to start the connector simply run the executable with this command: `./ fti-connector`

If successful you should be greeted with execution logs, e.g.:

```
Process Start Time: xx:xx:xx xx/xx/xxxx
The next scheduled data connection will execute at xx:xx:xx xx/xx/xxxx, which is in x days, x hours, x minutes, x seconds
fti-connector> Successfully parsed config.json.
fti-connector> Successfully parsed dataiku.json (1 instance(s) found)
fti-connector>
```

### Overriding the Default Mappings

**Advanced users only:** You may, at your own risk, change the Asset Types and Relation Types used to represent the Dataiku objects. You can find these in `config/assetTypes.json` and `config/relationTypes.json` respectively. We recommend making backups of these files before making any changes.

Please note that if you have already previously used the connector to create Collibra assets and before changing the Asset Types or Relation Types, these Asset Types, Relation Types, and assets will all remain in Collibra.

### **Troubleshooting**

Placeholder text

### **Command Reference**

The connector offers a command line interface to help with configuration and management. The following commands are available:

`help`

This command displays the list of commands.

`info`

This command will display the next scheduled data connection time.

`updateconfig`

This command will re-read the config files and process any changes made.

`exit`

This command exits the connector.
