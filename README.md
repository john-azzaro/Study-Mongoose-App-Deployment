# Mongoose App Deployment Study

<br>

## What is Mongoose App Deployment Study
The Mongoose App deployment study is an examination and simplified workflow process for deploying Mongoose Express applications to Heroku (a PaaS, or Platform as a Service, that helps deploy and scale and app), using Atlas for creating database clusters for your application.

Here's some of the questions covered in the study:

* [How do Mongoose, Atlas, and Heroku fit together in app deployment?](#How-do-Mongoose-Atlas-and-Heroku-fit-together-in-app-deployment)
* [How do you deploy a Mongoose app to Heroku?](#How-do-you-deploy-a-Mongoose-app-to-Heroku)

<br>

## How do Mongoose, Atlas, and Heroku fit together in app deployment?

When you deploy a mongoose app to Heroku, you are essentially merging MongoDB cloud services (which uses mongoose in app and by extension Atlas as a means to access that data) with Heroku (a PaaS) that helps deploy and manage that application. 

**As a brief refresher, our express application uses Mongoose.** Mongoose is an Object Data Mapper (ODM) library (or Object Modeling Modeler) for MongoDB and Node.js, is used to simplify the writing of validation code, business logic boiler plate, and make the code shorter and easier to work with. 

**To deploy our app in the most efificent way possible, we use MongoDB Atlas.** MongoDB Atlas provides an easy alternative to installing, tuning for optimal performance and security a database on the cloud for your own project. With Atlas you can create a MongoDB cluster on any major cloud provider (AWS, Google Cloud, Azure, etc.) and use that cluster within minutes with a browser-based interface. Additionally, you can allocate cloud resources and have the database automatically set itself up with predefined rules and further monitor its performance.

**To make deployment easy and efficient, we use Heroku to deploy our app.** Heroku is a container-based cloud platform as a servive (PaaS) that developers use to deploy, manage, and scale modern applications. In other words, it is a deployment tool meant to make life easier for developers. Heroku runs apps in *dynos*, which are essentially virtual computers that can scale the power required to run those apps. This means that as your demand for your app grows, you can scale horizontally or vertically (for a price of course). Important to note that Heroku does not host your app as it is deployed to Amazon Web Services (AWS). 

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
4. Add your database.

<br>

### STEP 2: Create and name your Heroku app.
------
In the Heroku dashboard, click "New", then click "Create New App", then give your app a name.

<br>

### STEP 3: Click the "Github" connection.
------
This connection wil sync up with the corresponding Github repository your project currently resides in. W

<br>

### STEP 4: Find and connect to the correct Github repository.
------
When you click the connection button, the app should automatically update for you.

<br>

### STEP 5: Input your key into vars configuration.
------
Go to settings > config vars > reveal config vars and put the key. this is in the env file and is DATABASE_URL. The value for the key is going to come from Mongodb atlas.

<br>

### STEP 6: Build a new cluster in Atlas.
------
In mongodb Atlas, Either build a new cluster (and save the password) OR the password (i.e. mypassword123, abc123, etc... whatever you specify).

<br>

### STEP 7: Connect application in Atlas and get the connection string.
------
In mongodb atlas, select the "connect your application". When this is done, you will get a connection string. Copy this string into a document and replace the password with your own.

<br>

### STEP 8: Amend the config vars string with the connection string.
------
Paste in the connection string into the value of your config vars in mongodb and click "Add".







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
