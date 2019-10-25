# Mongoose App Deployment Study

<br>

## What is Mongoose App Deployment Study
The Mongoose App deployment study is an examination and simplified workflow process for deploying Mongo-backed Express applications. In this study, we use the PaaS (Platform as a Service) Heroku to deploy our app to the web.

Here's some of the questions covered in the study:

* [What is Heroku?](#What-is-Heroku)
* [How do you deploy a Mongoose app to Heroku?](#How-do-you-deploy-a-Mongoose-app-to-Heroku)
* [](#)

<br>

## What is Heroku?
Heroku is a container-based cloud platform as a servive (PaaS) that developers use to deploy, manage, and scale modern applications. In other words, it is a deployment tool meant to make life easier for developers.

Heroku runs apps in *dynos*, which are essentially virtual computers that can scale the power required to run those apps. This means that as your demand for your app grows, you can scale horizontally or vertically (for a price of course). Important to note that Heroku does not host your app as it is deployed to Amazon Web Services (AWS). 

<br>

## How do you deploy a Mongoose app to Heroku?

<dl>
<dd>

### STEP 1: Provision a new database in Atlas.
------
To provision a new database in Atlas:
1. Click **Collections**.
2. Click **Create Database**.
3. Name your database (e.g. *my-app*).
4. Add you database.

### STEP 2: Create your Heroku app.
------
To create your Heroku app, you simply need to run "heroku create" at the command line in your project folder:
```
    heroku create
```
Then, push your app to Heroku:
```
    git push heroku master
```



### STEP 3: 






</dl>
</dl>
