# Kentix-MultiSensorTI-Template-PRTG
How-to and template to use the Kentix Multisensor TI in PRTG using the API

Based on the Official Kentix documentation: https://docs.kentix.com/display/FAQ/Kentix+Integration+in+PRTG

## Creating HTTP-Header
1)  Copy the API authentication key in the Kentix Web Interface (Configuration | General | Security | API Authentication Key)
2)  Add a ":" to the API key and convert it to the BASE64 format. Use the following tool for example: https://www.base64encode.org/
3)  The HTTP header has the following syntax: Authorization: Basic <credentials> The credentials consist of username:password (The username is the API key, followed by the ":", the password remains empty)
4)  An example HTTP header with the communication key "Kentix" looks like this: 
> Authorization: Basic ZjlhNzY2Yjg4NDBmNTMxMmExNGYwYTE5YzUzOWMzN2I2ZDJmMWQ0YjY4ZTI4OTQ5YmQ3MGQ2OTI2NGI4MzdiNTo=

## Preparations in PRTG

1)  Copy the official ovl and template file OR use my altered versions in this project
    Official download:  https://docs.kentix.com/download/attachments/21004622/MultiSensor_json.zip?version=2&modificationDate=1591447707843&api=v2
2)  Place the template file Kentix.multisensor.template in the rest (Custom Sensors) subfolder of your PRTG installation. (C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\rest)
3)  Place the lookup file(s) with the extension .ovl in the custom lookup files folder (C:\Program Files (x86)\PRTG Network Monitor\lookups\custom)
4)  Load the lookup files in PRTG's Web Interface (Setup | System Administration | Administrative Tools | Load Lookups and File Lists)

## Add custom REST sensor in PRTG

![This is an image](https://docs.kentix.com/download/attachments/21004622/Bildschirmfoto%202020-05-12%20um%2022.19.15.png)

## Add extra value in the template file

1) Download and install Postman: https://www.postman.com/downloads/
2) Create a new collection
3) Choose Basic Auth and use the API Authentication Key as username
4) Add a request to the collection
5) Use following URL as GET request: https://KENTIX-IP-ADDRESS/api/devices/multisensor/values
6) Click send (and Disable SSL Verification if neccesary)
7) Copy the returned body and paste the body in a tool like https://jsonpath.com/ as input
8) Enable Output Paths
9) Examples of JSONPaths: 
> $.data.temperature.has_alarm<br />
> $.data.digital_inputs[0].input.has_alarm
10) Use the Evaluation Result in the Kentix.multisensor.template file



