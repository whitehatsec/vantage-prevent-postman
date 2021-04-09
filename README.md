# API Security Tester

WhiteHat’s [API Security Tester](https://www.postman.com/whitehatsec-innovations/workspace/api-security-tester/overview) is a collection enabling you to automatically test your API's for security vulnerabilities directly within your Postman IDE using WhiteHat Security's Intelligence-Directed DAST (ID-DAST). ID-DAST tests for the [OWASP Top 10 for APIs](https://owasp.org/www-project-api-security/) as well as the [OWASP Top 10 for Web Applications](https://owasp.org/www-project-top-ten/). Use of this collection and associated works are subject to the terms and conditions of the [End User License Agreement](https://www.whitehatsec.com/terms-conditions/eula-postman/).

## System requirements  
1) Postman IDE and Docker is installed, up, and running
2) The API/application that you wish to test against is live (e.g.: JuiceShop or TiredfulAPI)
3) And the associated API collection you wish to test  
4) Watch Postman [Hackathon demo](https://youtu.be/9wQRr1lMdTU)

## Initialize with Docker
ID-DAST utilizes a Docker container to perform the vulnerability scanning. Running this container requires you to accept the [End User License Agreement](https://www.whitehatsec.com/terms-conditions/eula-postman/) by setting the _WHITEHAT_ACCEPT_EULA_ environment variable to 'y'. Pull and run the container with accepted EULA by executing the following commands:

`$> docker pull whsinnovations/dast-attacker-api:latest`

`$> docker run -p 27374:27374 -e WHITEHAT_ACCEPT_EULA=y whsinnovations/dast-attacker-api:latest`

_Note_: Windows users need to enable support for Linux containers by following the official [Ubuntu documentation](https://ubuntu.com/tutorials/windows-ubuntu-hyperv-containers).

## Usage
Perform the following steps to run a WhiteHat Security dynamic vulnerability test on your API:

## Export Your Collection
Export the collection you wish to test by right clicking on the collection and selecting "Export". Choose "Collection v2.1" and save it to Postman's working directory. For more information on Postman directory settings, [CLICK HERE](https://learning.postman.com/docs/getting-started/settings/#working-directory). 

## Configure Your Test in 3 Easy Steps
Within the "Submit Scan Job" POST request of the WHS "API Security Tester" collection: 
1)	Select the "Body" tab. Make sure the "allowedHosts" parameter is set correctly. And for the predefined "inputFiles" key parameter, click "Select Files" value and browse to the exported collection. Click "Open".
2)	Now select the "Headers" tab and set the value of the "X-WhiteHat-License-Key" to that of your license key. 
3)	And finally, the most important step, click "Save" to ensure your changes are applied.

_Note_: The “allowedHosts” parameter specifies the hosts that are allowed to be scanned, e.g.: localhost, https://www.example.com, www.example.com.
Review this parameter to ensure you do not scan an endpoint that is not intended to be attacked.

## Run the WHS Tester Collection
Run the API Security Tester collection by using a "Collection Runner". This can easily be done with the blue “Run” button at the top of the Tester collection leaflet. It should open a new "Collection Runner" window. Click "Run" button again. This will kick off the scan and poll the status until complete. You will know the scan is complete when the Collection Runner is finished with all tests passing. For more information on Collection Runners, please follow the [official Postman documentation](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/). 

## View the Results
Close the Connection Runner. Go back to the WHS Tester collection and click the "Display Scan Results" GET request. Now click the "Send" button to request the latest test results. From the response bottom section, select the "Body" tab and click the gray "Visualize" button to view discovered vulnerabilities within your API. For more details about specific vulnerabilities, click the eyeball icon under the “Actions” column.
