# Mongoose App Deployment Study

<br>

## What is Mongoose App Deployment Study
The Mongoose App deployment study is an examination and simplified workflow process for deploying Mongo-backed Express applications. In this study, we use the PaaS (Platform as a Service) Heroku to deploy our app to the web.

Here's some of the questions covered in the study:

* [What is Heroku?](#What-is-Heroku)
* [How do you deploy a Mongoose app to Heroku?](#How-do-you-deploy-a-Mongoose-app-to-Heroku)

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
Assuming you already have an Atlas account and you are logged in (), provision a new database. If you do not have an account, check out my [MongoDB Atlas Cloud Deployment](https://github.com/john-azzaro/Study-MongoDB-Atlas-Cloud-Deployment "Atlas configuration study") study that goes step-by-step through the process.

So to provision a new database in Atlas:

1. Click **Collections**.
2. Click **Create Database**.
3. Name your database (e.g. *my-app*).
4. Add you database.

<br>

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
And lastly, start up the dyno on your Atlas server:
```
    heroku ps:scale web=1
```

<br>

### STEP 3: Connect to your database to Heroku
------
In the cluster overview, when you click the "connect" button and select the "connect your application". Among the connection strings you wil see "standard connection string". Simply replace the ```<PASSWORD>``` with your password and ```DATABASE``` with your database name. Copy-Paste that string, replace those inputs, and keep it handy for the next step.
```
    mongodb://my-first-user:<PASSWORD>@this-is-the-name-of-my-database-shard-00-00-11uld.mongodb.net:27017,this-is-the-name-of-my-database-shard-00-01-11uld.mongodb.net:27017,this-is-the-name-of-my-database-shard-00-02-11uld.mongodb.net:27017/<DATABASE>?ssl=true&replicaSet=this-is-the-name-of-my-database-shard-0&authSource=admin&retryWrites=true
```
Then, in the Heroku dashboard, click on the newly created app, go to settings, click on "reveal config vars", and addan entry named ```DATABASE_URL``` and paster the value we just prepared earlier.


</dl>
</dl>
