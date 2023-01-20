# What is Railway? 

[Railway](https://railway.app) is a deployment platform where you can provision infrastructure, develop with that infrastructure locally, and then deploy to the cloud. For those familiar with Heroku, it enables us to do many of the same things as that platform. 

# Setting up

You will need to make a Railway account first; you can choose either to login using your email address or GitHub account. We recommend using your GitHub account as this will allow Railway to seemlessly bring in your repos from GitHub. Once you have logged in you should see the [railway dashboard](https://railway.app/dashboard).

![dashboard](/app/assets/images/railwaydashboard.png)

First we need to make a new project. When we click the 'new project' button we will be presented with a series of options. These options include the ability to link a GitHub repo to Railway, as well as allow us to provision services such as PostgreSQL and Redis to our project. 

If you have linked your GitHub account to Railway you should be able to see all your repos, it is recommended you select a repo **based on this template** as it will save you some time when it comes to the initial configuration of your app.  

# The Project dashboard

Once the project is created you will land on your project dashboard. Your project's infrastructure, environments, and deployments are all controlled from here.

![projectdashboard](/app/assets/images/projectdashboard.png)

You should see a box relating to your GitHub repo as well as any plugins you have provisioned in your app. Railway projects allow you to provision additional infrastructure on top of your existing services in the form of database services. You can add a plugin in the Command + K menu or by clicking the New Service button on the Project Canvas.

# Connecting to services 

Railway provides connection strings and project variables that let your application connect to the database service. You can access your plugin's connection strings under the Connect tab in the service view.

![connecttab](/app/assets/images/serviceconnect.png)

This template already has environment variables for [PostgreSQL](https://github.com/gclssvglx/ab-tool-tester/blob/7a66c1a3145d42196580f7fd90926eff6662ff04/config/database.yml) and [Redis](https://github.com/gclssvglx/ab-tool-tester/blob/7a66c1a3145d42196580f7fd90926eff6662ff04/config/redis.yml) setup.

# Making your app public

Assuming your GitHub repo's initial deployment finalizes your next step will be to expose your service to the public internet. To do this you will need to generate a domain in the settings tab of your repo. 

![generatedomain](/app/assets/images/reposettings.png)

After your deployment completes, you will be able to see your new deployment live at the deployment's URL that you just generated. 
# Additional credentials

As well as the environment variables for Postgres and Redis you will also have to account for the basic auth that is enabled in this template. To do this you can env vars to Railway for USERNAME and PASSWORD. You will be then prompted for these values when you navigate to your app's URL. 

You will also need to create a 'master.key' credential for you app, to do this you can 

* First have a copy of the project locally
* In the project run bin/rails credentials:edit to generate a new set of credentials and a master.key file.
* The master.key file is automatically ignored in .gitignore - DO NOT COMMIT THIS FILE
* Add an environment variable for SECRET_KEY_BASE with the value that is the content of your config/master.key file.

Once this variable is added the site will redeploy.