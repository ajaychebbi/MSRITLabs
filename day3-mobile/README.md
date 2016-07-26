# MSRITLabs

## Creating MobileFirst Foundation Service on Bluemix 

- Load [bluemix.net](https://bluemix.net) and visit the Catalog page (Classic Experience).
- From the left sidebar, tick the Mobile checkbox under Services. Then, click on the Mobile Foundation tile to begin the service creation process.
- Select a space to use and optionally set a Service name.
- Select the 'Developer' Plan, then click Create.
- Start the MobileFirst Server by clicking on 'Start Basic Server'.

## Let's go Cognitive with Watson Classifier 

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
  - Authorization: Basic Auth. Username and Password from the Credentials

 Copy Credentials
  - Go back to Bluemix dashboard. On the left side of the page, click Service Credentials to view your service credentials
  - Copy Username and Password from these service credentials.
 
 - Body: form-data . Add the following
<table>
    <tr>
        <td>Name</td>
        <td>type</td>
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
