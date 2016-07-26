# MSRITLabs
## Android
- Get the source code from github
https://github.com/VidyasagarMSC/mfp8-watsonclassifier-android/archive/master.zip
- Import the project in Android Studio 
  File -> Open -> Navigate to unzipped folder of the app.
- Proceed to the next steps while gradle does its thing.

## Creating MobileFirst Foundation Service on Bluemix 

- Load [bluemix.net](https://bluemix.net) and visit the Catalog page (Classic Experience).
- From the left sidebar, tick the Mobile checkbox under Services. Then, click on the Mobile Foundation tile to begin the service creation process.
- Select a space to use and optionally set a Service name.
- Select the 'Developer' Plan, then click Create.
- Start the MobileFirst Server by clicking on 'Start Basic Server'.

## Let's go Cognitive with Watson Classifier 
[Move to "Add the Sample training data" if you already have a service created]
- Go to the “CATALOG” in the top nav bar and select “Watson” Services.
- Click on “Natural Language Classifier”.
- Pick the defaults.
- Change the Service Name if you prefer.
- Click on “Create”.

    ### Add the sample training data
This is what teaches the service to classify weather related info v/s golf
related info.
Download the sample
  - Go to http://ibm.co/1n7ipKV
  - Save the file. (<em>If the file is shown on the browser, Right-click and Save the file with .csv extension.</em>)

  ### Upload the training data
Open Chrome extension <strong>Postman</strong> create a request as follows
  
  - Method: POST
  - URL: https://gateway.watsonplatform.net/natural-language-classifier/api/v1/classifiers
  - Authorization: Select <strong>Basic Auth</strong> from the dropdown. Username and Password from the Credentials.

 Copy Credentials
  - Go back to Bluemix dashboard. Under Watson Classifier service you just created, On the left side of the page, click Service Credentials to view your service credentials
  - Copy Username and Password from these service credentials.
 
 - Body: Select <strong>form-data</strong> . Add the following
<table>
    <tr>
        <td>Name</td>
        <td>Type</td>
        <td>Value</td>
    </tr> 
   <tr>
     <td>training_data</td>
      <td>File</td>
      <td>Choose the saved csv File</td>
  </tr>
  <tr>
     <td>training_metadata</td>
      <td>Text</td>
      <td>{"language":"en","name":"TutorialClassifier"}</td>
  </tr>
</table>
  - Hit “Send”
  - Note: If you are having trouble – talk to the lab owner
  
- Keep the Postman response open – you will need the info later. It would
look something like this:
<br><em>{ "classifier_id": "563C46x20-nlc-154", "name":
"TutorialClassifier", "language": "en", "created":
"2016-01-19T10:52:06.518Z", "url": "https://
gateway.watsonplatform.net/natural-language-classifier/api/v1/
classifiers/563C46x20-nlc-154", "status": "Training",
"status_description": "The classifier instance is in its training
phase, not yet ready to accept classify requests"}</em>
- Your Watson backend is ready to query via REST.

## Edit and Run via Android Studio
Go back to Android studio
- Edit the file app\java\HttpStuff.java
- Replace username and password from your bluemix service credentials
- classifierID from the Postman response
- Start the emulator and Run the app
- Try the app – ask something like “Do I need a jacket today?”
- This is your app talking to the Watson REST service!

## What's Next
Open Command Prompt
- Point to the folder where you downloaded the android code.
- Run this command "mfpdev server add" and enter the below details

<br>? Enter the name of the new server profile: MyBluemixServer
<br>? Enter the fully qualified URL of this server: https://[YOUR MOBILEFIRST FOUNDATION SERVICE URL]:443
<br>? Enter the MobileFirst Server administrator login ID: admin
<br>? Enter the MobileFirst Server administrator password: ***** (Click on the eye icon to see your password)
<br>? Save the administrator password for this server?: Yes
<br>? Enter the context root of the MobileFirst administration services: mfpadmin
<br>? Enter the MobileFirst Server connection timeout in seconds: 30
<br>? Make this server the default?: Yes
<br>Verifying server configuration...
<br>The following runtimes are currently installed on this server: mfp
<br>Server profile 'MyBluemixServer' added successfully. 
- Run this command "mfpdev app register".

## Final Step
- Go to IBM MobileFirst Foundation service page and Click on LAUNCH CONSOLE.
- Login with Username: admin and Password: Click on eye icon.
- Under Applications on the left tab you should see Weather Classifier.
