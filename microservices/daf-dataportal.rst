Data Portal

What is?

Dataportal is a web application that has the purpose of manage a large number of public administration datasets; is the user interface of the Data & Analytics Framework. Specifically, it meets the following needs:

- Facilitates access to public administration data by citizens, businesses and public administrations  organizes content , searchability, "linkability" between data resources
- Facilitate and encourage the use of data → Provides data visualization and analysis tools for an easy use. Furnish REST API for machine-to-machine integration.
- Encourage the creation and dissemination of analysis and information-based content → data stories that can be created by public authorities (authoritative sources) and citizens / civic hackers (analysis, synthesis, and sharing).
- Facilitates access to "authoritative" and standardized sources: Controlled Vocabularies and Ontologies, Dataset Standard
- Provides public administrations with the ability to use Dataportal to serve / manage their data, avoiding the proliferation of open date catalogs.
- Facilitates the onboarding of public administrations through a digital platform that structures the data upload workflow and provides concrete benefits to individual administrations who decide to use the platform

Install Standalone.

The Dataportal has an integrated mock server. 
To install the dataportal in a standalone environment you need to follow the next steps:
- download the code from https://github.com/italia/daf-dataportal
- install node and npm 
- go to the daf-dataportal directory and type 'npm run start-mock-server' in order to start the mock server (by default it runs on port 3001)
- type npm install in order to install all the dependencies needed
- type npm start in order to launch the application (by default it runs on port 3000)
- go to http://localhost:3000
- to launch the application in mock-mode please ensure that the configuration in the file /src/config/serviceurl.js is calling the mock services (all address pint to http://localhost:3001)
- login with test/test credential

Install Integrated.

The dataportal needs for the next docker container:
- freeipa
- ckanlast
- catalog-manager
- security-manager
- daf-datipubblici
- ontonethub

