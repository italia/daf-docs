Publicdata

What is?

Publicdata is a web application that ...

Install Standalone.

The Publicdata has an integrated mock server. 
To install the Publicdata in a standalone environment you need to follow the next steps:
- download the code from https://github.com/italia/daf-publicdata
- go to the daf-publicdata directory and type 'npm run start-mock-server' in order to start the mock server (by default it runs on port 3001)
- type npm install in order to install all the dependencies needed
- type npm start in order to launch the application (by default it runs on port 3000)
- go to http://localhost:3000 

Install Integrated.

The Publicdata needs for the next docker container:
- ckan
- daf-datipubblici

