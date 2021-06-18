# API Security Tester

Providing a Collection powered by WhiteHat Security designed to enable the secure development of APIs throughout the Postman lifecycle.

## The Problem

Security testing is a cornerstone of API Lifecycle Management. Yet, traditional security testing technologies are struggling to adapt to the design and architectural characteristics of APIs. The result? Most API development teams are waiting days or weeks for results, perform their security testing manually, or perform no security testing at all.

## The Solution

With this workspace and its Collections, we seek to drastically improve this reality for the Postman community. Here you will find Collections allowing for the fast, automated and accurate testing of your APIs throughout the Postman lifecycle using WhiteHat Security's Intelligence Directed DAST (IDD). Not only will you be testing for vulnerabilities as you build and test your APIs locally using Postman IDE, you will also be empowered to automate API security testing within your CI/CD via our integration with Newman.

## The Difference

So how does IDD accomplish this while not disrupting your continuous innovation?

* It's Fast! - IDD scan times are measured in minutes, not hours or days. This enables security testing to be part of the CI/CD pipeline and deliver real time vulnerability findings.
* It's Accurate! - Focus on accuracy is incredibly important in todays DevOps world. False positives are as important as false negatives as noise in scan results can slow down the entire process. That’s why "Evidence" is included with IDD's vulnerability results.
* It's Easy! - No need to spend days with documentation or a product workshop. IDD is easy to use with no dependencies and minimal configuration. It also includes intelligence that automatically handles common challenges such as logins and complex session state.

# Product Overview
WhiteHat’s API Security Tester is a collection enabling you to automatically test your API's for security vulnerabilities directly within your Postman IDE using WhiteHat Security's Intelligence-Directed DAST (ID-DAST). ID-DAST tests for the OWASP Top 10 for APIs as well as the OWASP Top 10 for Web Applications. [Click here](https://youtu.be/k2GuK_mVboo) to watch a presentation and demonstration of how to use this collection in your Postman workspace.

### License
ID-DAST requires a license to perform security testing. [Click here](https://www.whitehatsec.com/idd-lap-reg/) and complete the form to obtain a free tiral license.

### System requirements
  1) Postman IDE and Docker is installed and running
  2) The API/application that you wish to test againist is live (e.g. JuiceShop or TiredfulAPI)
  3) And you have the associated API collection you wish to test for security

### Setup
Docker
ID-DAST utilizes a Docker container to perform the vulnerability scanning. Running this container requires you to accept the End User License Agreement by setting the WHITEHAT_ACCEPT_EULA environment variable equal to y. Pull and Run the container with the accepted EULA option by executing the following commands:
```
$> docker pull whsinnovations/dast-attacker-api:latest
$> docker run -it --rm -p 27374:27374 -e WHITEHAT_ACCEPT_EULA=y whsinnovations/dast-attacker-api:latest
```
Note: Windows users will need to enable support for Linux containers by following the [official documentation](https://docs.docker.com/docker-for-windows/wsl/).

### Import the Security Tester Collection
There are two options for importing the WhiteHat Security Tester Collection:
  1) Within Postman, fork the collection directly from our public [WhiteHat Workspace](https://www.postman.com/whitehatsec-innovations/workspace/api-security-tester/overview), however, you will need to enable a public profile.
  2) Alternatively, you can download the Security Tester collection from this GitHub repo and import it into Postman.

### Export Your Collection
Export the collection you wish to test by right clicking on the collection and selecting "Export". Choose "Collection v2.1" and save it to Postman's working directory. For more information on Postman directory settings, [click here](https://learning.postman.com/docs/getting-started/settings/#working-directory).

### Configure Your Test in 3 Easy Steps
Within the "Submit Scan Job" POST request of the WhiteHat Security Tester collection:
  1) Select the "Body" tab. Make sure the "allowedHosts" parameter is set correctly. And for the predefined "inputFiles" key parameter, click "Select Files" value and browse to the exported collection. Click "Open".
  2) Now select the "Headers" tab and set the value of the "X-WhiteHat-License-Key" to that of your license key.
  3) And finally, the most important step, click "Save" to ensure your changes are applied.

Note: The “allowedHosts” parameter specifies the hosts that are allowed to be scanned, e.g.: localhost, https://www.example.com, www.example.com. Review this parameter to ensure you do not scan an endpoint that is not intended to be attacked.
Run the WHS Tester Collection

### Run a Security Test
Run the API Security Tester collection by using a "Collection Runner". This can easily be done with the blue “Run” button at the top of the Tester collection leaflet. It should open a new "Collection Runner" window. Click "Run" button again. This will kick off the scan and poll the status until complete. You will know the scan is complete when the Collection Runner is finished with all tests passing. For more information on Collection Runners, please follow the official Postman documentation.
View the Results
Close the Connection Runner. Go back to the WHS Tester collection and click the "Display Scan Results" GET request. Now click the "Send" button to request the latest test results. From the response bottom section, select the "Body" tab and click the gray "Visualize" button to view discovered vulnerabilities within your API. For more details about specific vulnerabilities, click the eyeball icon under the “Actions” column.

## Related Projects

* [newman-reporter-har](https://www.npmjs.com/package/newman-reporter-har) - free and open source software that integrates with Newman to generate HTTP Archive (HAR) reports from the execution of Collections. We developed and released this reporter to the Postman community as a part of our work on API Security Tester.

## Reporting Issues

You can report any and all issues you encounter using [Issues on GitHub](https://github.com/whitehatsec-innovations/dast-postman-resources/issues).

## Past Events

### WEBINAR ON MAY 6, 2021: BLUEPRINT FOR GOVERNANCE: INTEGRATING SECURITY TESTING WITHIN POSTMAN

Join Eric Sheridan (Chief Scientist at WhiteHat Security) and Kin Lane (Chief Evangelist at Postman) in this live webinar on Thursday, May 6 and learn the “must-haves” of API security testing within your overall governance strategy. In addition, we will put theory into practice with a demonstration of how to achieve fast, easy, accurate and scalable security testing of your APIs. [Register today!](https://info.whitehatsec.com/0521-WebinarWH-IntegrateAPITestingPostman.html)


### POSTMAN GALAXY: FEB 4, 2021 10:30AM–10:45AM PST

We are pleased to announce that Eric Sheridan, Chief Scientist at WhiteHat Security, will be speaking at the upcoming "Postman Galaxy" conference. We will be delivering a presentation titled ["Partner Talk: Integrating API Security Testing into Postman Lifecycle"](https://www.postman.com/postman-galaxy/schedule/) wherein we will demonstrate API Security Testing from within Postman IDE and Newman. [Register now](https://www.postman.com/postman-galaxy/) and come join our talk.

### POSTMAN HACKATHON: JAN 25, 2021

We are pleased to announce the API Security Tester has been submitted to the [Postman Hackathon](https://www.postman.com/postman-galaxy/postman-api-hack/) as of January 25th.
