# MSRIT Labs
Reference code for the labs for the Faculty enablement session

In the lab, we will try to build a simple Node.js application connecting to a Cloudant DB backend and push it onto Bluemix. 
The application archive is attached in this folder. The application allows the user to input their Questions to create a Survey form. It also provide an option to show all the questions by reading it from the database. 

## Steps to run the application.

+ Download the archive to your local directory. 
+ Unzip the archive to a folder, say WorkDir 
+ From the command prompt on your local development environment, change to the above directory, WorkDir

      `cd WorkDir` 

+ Login to the Bluemix environment

        cf login -a <BLUEMIX_ENDPOINT> -u <YOUR_BLUEMIX_ID> -p <BLUEMIX_PASSWORD> 
    For eg: cf login -a https://api.eu-gb.bluemix.net // if you are working on Bluemix - UK Region
    
    Choose the right Org and Space in your Bluemix account. 
+ Create a Cloudant Service on Bluemix

        cf create-service cloudantNoSQLDB Shared <CLOUDANT_INSTANCE_NAME_OF_YOUR_CHOICE> 
+ Create a Bluemix app

  To familiarize with various options, use the various cf push options

        cf push <BLUEMIX_APP_NAME> -i 3 -m 256M -d eu-gb.mybluemix.net --hostname <HOSTNAME_OF_APP> --no-start --no-manifest -c "node app.js" 
        
+ The application will be created with the Node code and will be in Stopped mode. 
+ Bind the service with the Application

        cf bind-service <BLUEMIX_APP_NAME_TO_CREATE> <CLOUDANT_INSTANCE_NAME_OF_YOUR_CHOICE>
  Provide the Bluemix app name and Cloudant instance name created in previous steps. 
+ Start the Bluemix application

        cf start <BLUEMIX_APP_NAME> 
