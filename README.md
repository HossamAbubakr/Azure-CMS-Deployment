# CMS, Azure Full Stack App Deployment


## Table of Contents

* [Summary](#Summary)

* [Technologies](#Technologies)

* [Features](#Features)

* [Case Study](#Case-Study)

* [Structure](#Structure)

* [Usage](#usage)

## Summary

This full stack content management system was deployed to Azure as part of my **Cloud Developer using Microsoft Azure Nanodegree from Udacity**.

It demonstrates my understanding and ability to configure the following services:  
Azure Resource Groups  
Azure SQL Server  
Azure SQL Database  
Azure Blob Storage  
Azure App Service  
Azure Active Directory  

As well as my ability to configure my app to connect to the aforementioned services and set up my application to authenticate users using Azure's Active Directory for oAuth using Microsoft Authentication Library (MSAL).

## Technologies

SQLAlchemy as the ORM of choice.  
JQuery was used for DOM manipulation.  
WTForms for forms validation/rendering.  
Bootstrap was used for the user interface.  
Flask was used as a backend using python.  
Microsoft Azure was used for deployment.

## Features

1. Create new posts.

2. Edit your existing posts.

3. Embed images in your social posts. 

4. Login using an existing Microsoft account (Including Xbox etc.) using Azure Active Directory oAuth.

## Features

1. Create new posts.

2. Edit your existing posts.

3. Embed images in your social posts. 

4. Login using an existing Microsoft account (Including Xbox etc.) using Azure Active Directory oAuth.

## Case Study

### Azure Analysis, Choice and Justification for the resource option for deploying the app.

My report was made based on Azure Tiers [current pricing](https://azure.microsoft.com/en-us/pricing/) as of 02/05/2021

#### General Comparison

| Service  | Cost | Scalability | Availability | Workflow |
| ------------- |:-------------:|:-------------:|:-------------:|:-------------:|
|App Service|Cheaper but always paying, even if service/application isn’t running|Highly Scalable, has a hardware limit per instance|High availability|IaaS, Complete control over deployment and the technology stack of the operating system|
|VM Service|More expensive, but can be de-allocated when not needed|Highly Scalable|High availability|PaaS, Allows the developer to focus on development, receiving less control over the deployment pipeline|

#### App Service and VM Tiers Considered
| Service  | Tier | Cost | RAM |Storage |CPU |
| ------------- |:-------------:|:-------------:|:-------------:|:-------------:|:-------------:|
|App Service|F1|Free|1GB|1GB|Shared (60 CPU minutes / day)|
|VM Service|B1LS|$4~ a month|0.5GB|4GB|1 vCPU|

#### My Choice :
I chose **App Service** to deploy our project for the following reasons: 
1. It suits the computational  requirements of our lightweight application.
2. For our small app the cost of App Service being lower than that of an Azure VM.
3. We will not be hitting the upper limit of the hardware configuration of the App Service
4. The programming language used for our application **(Python)** is natively supported by App Service.

### Changes to our application that can warrant me to change my choice

If the requirements of our application needs more hardware allocation than the upper limit of the App Service   
Which are **14GB of memory and 4 vCPU cores per instance** then a switch to VM service would be needed.  

## Structure 
```
|   application.py
|   config.py
|   requirements.txt
|
+---FlaskWebProject
|   |   forms.py
|   |   models.py
|   |   views.py
|   |   __init__.py
|   |
+---sql_scripts
|   |   posts-table-init.sql
|   |   users-table-init.sql
|   |
|   +---static
|   |   +---content
|   |   |       bootstrap.css
|   |   |       bootstrap.min.css
|   |   |       site.css
|   |   |
|   |   +---fonts
|   |   |       glyphicons-halflings-regular.eot
|   |   |       glyphicons-halflings-regular.svg
|   |   |       glyphicons-halflings-regular.ttf
|   |   |       glyphicons-halflings-regular.woff
|   |   |
|   |   +---images
|   |   |       sign-in-with-ms.svg
|   |   |
|   |   \---scripts
|   |           bootstrap.js
|   |           bootstrap.min.js
|   |           jquery-1.10.2.intellisense.js
|   |           jquery-1.10.2.js
|   |           jquery-1.10.2.min.js
|   |           jquery-1.10.2.min.map
|   |           jquery.validate-vsdoc.js
|   |           jquery.validate.js
|   |           jquery.validate.min.js
|   |           jquery.validate.unobtrusive.js
|   |           jquery.validate.unobtrusive.min.js
|   |           modernizr-2.6.2.js
|   |           respond.js
|   |           respond.min.js
|   |           _references.js
|   |
|   \---templates
|           auth_error.html
|           index.html
|           layout.html
|           login.html
|           post.html
|
\---tests
        test_hello_world.py
```

## Usage and Installation

The app has these default credentials beside oAuth.
```
Username : admin
Password : pass
```

You will have to configure the following services to deploy the blog.  

Azure Resource Groups  
Azure SQL Server  
Azure SQL Database  
Azure Blob Storage  
Azure App Service  
Azure Active Directory  

All the models for the database are already included and ready for use.   
You can 

1. Use the following command to install the required packages
```
pip install -r requirements.txt
```
2.populate your Azure SQL Database with initial data using the files in the sql_scripts folder.  
3. Supply your own configuration string at config.py
```python
    CLIENT_ID = "ENTER_CLIENT_ID_HERE"
```
```python
    CLIENT_SECRET = "ENTER_CLIENT_SECRET_HERE"
```
```python
    SQL_DATABASE = os.environ.get('SQL_DATABASE') or 'ENTER_SQL_DB_NAME'
```
```python
    SQL_PASSWORD = os.environ.get('SQL_PASSWORD') or 'ENTER_SQL_SERVER_PASSWORD'
```
```python
    BLOB_ACCOUNT = os.environ.get('BLOB_ACCOUNT') or 'ENTER_STORAGE_ACCOUNT_NAME'
```
```python
    SQL_USER_NAME = os.environ.get('SQL_USER_NAME') or 'ENTER_SQL_SERVER_USERNAME'
```
```python
    BLOB_STORAGE_KEY = os.environ.get('BLOB_STORAGE_KEY') or 'ENTER_BLOB_STORAGE_KEY'
```
```python
    BLOB_CONTAINER = os.environ.get('BLOB_CONTAINER') or 'ENTER_IMAGES_CONTAINER_NAME'
```
```python
    SQL_SERVER = os.environ.get('SQL_SERVER') or 'ENTER_SQL_SERVER_NAME.database.windows.net'
```
4. Deploy Using Azure App Service Deployment Through Github!

5. Optional : Run App Locally! 
```Batchfile
set FLASK_APP=application.py
flask run
```



