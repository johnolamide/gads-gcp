# Google Cloud Fundamentals: Getting Started with App Engine

## Overview
	
 In this lab, you create and deploy a simple App Engine application using a virtual environment in the Google Cloud Shell.

## Objectives

 In this lab, you learn how to perform the following tasks:

 - Initialize App Engine.

 - Preview an App Engine application running locally in Cloud Shell.

 - Deploy an App Engine application, so that others can reach it.

 - Disable an App Engine application, when you no longer want it to be visible.
 

### Initialize App Engine

#### Initialize your App Engine app with your project and choose its region
	
	gcloud app create --project=$DEVSHELL_PROJECT_ID
	
#### Clone the source code repository for a sample application in the hello_world directory

	git clone https://github.com/GoogleCloudPlatform/python-docs-samples
	
#### Navigate to the source directory

	cd python-docs-samples/appengine/standard_python3/hello_world
	

### Run the Hello World Application Locally

#### Download and Update the Package list

	sudo apt-get update
	
#### Install and Setup a Virtual Environment to run the Application (Enter 'Y' when prompted)
	
	sudo apt-get install virtualenv
	
	virtualenv -p python3 venv
	
#### Activate the virtual environment

	source venv/bin/activate
	
#### Install the application dependencies

	pip install  -r requirements.txt
	
#### Run the application

	python main.py
	
#### Preview your application on port 8080

#### Press CTRL+C to terminate the deployed service


### Deploy and Run Hello World Application on App Engine

- To deploy your application to the App Engine Standard environment

#### Navigate to the Source Directory

	cd ~/python-docs-samples/appengine/standard_python3/hello_world
	
#### Deploy your Helo World Application (Enter 'Y' when prompted)
	
	gcloud app deploy
	
#### Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com

	gcloud app browse
	

### Disable the Application

#### Go to the App Engine Settings Page

#### Click 'Disable Application'

#### Enter the Application ID and click 'DISABLE'