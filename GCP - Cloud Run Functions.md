---
tags:
  - cloud
  - technical
  - GCP
  - learning
---
[Cloud Run](https://docs.cloud.google.com/run/docs/overview/what-is-cloud-run)
## Cloud Run functions
- Code that runs on some trigger event, e.g. HTTP request, file upload
	- **Cloud events** happen in the cloud environment, e.g. change to DB contents, files uploaded in storage, new VM instance
- Cloud Run functions used for tasks that need to be performed quickly and/or don't need to be long-running
- Examples
	- Generate thumbnails of images uploaded to bucket
	- Push notification to phone when message receive in Pub/Sub
	- Process data and generate report from database
- Can use any language that supports Node.js


### Create, deploy, test and monitor Cloud Run function in Cloud Console

student-03-1af5a75b027c@qwiklabs.net
oACDaZYJ5T5a
qwiklabs-gcp-02-2594bfa05d83

#### Create and deploy
Qwik Start course creates the function via
Cloud Run > Services ... Write a function
- You can configure the resource
- Then write some code in Source
- Then Save and redeploy

#### Testing
- In Service Details page, click Test button
- Allows you to specify
	- Payload (e.g. body in json)
	- Query parameters
	- Headers
- Shows the CLI command
	- `curl ...`
	- Copy and run in Cloud Shell (or there's a link to do it)

#### View logs
- In Service Details page, Observability tab, select Logs
- Can see stuff like the function being triggers, request and response details if relevant.


### CLI for Cloud Run functions
student-02-54bc19ec5ecf@qwiklabs.net
07mDSJlt6P7I
qwiklabs-gcp-01-12c1d78bbc3b

Tutorial creates a directory with an `index.js` and `package.json` and creates a node project using `npm install`

To deploy a new Cloud Function, it needs trigger to be specified
- `--trigger-topic`, `--trigger-bucket`, or `--trigger-http` are common trigger types
- updating the function retains the trigger unless specified otherwise

```js
// index.js
const functions = require('@google-cloud/functions-framework');  
  
	// Register a CloudEvent callback with the Functions Framework that will  
	// be executed when the Pub/Sub trigger topic receives a message.  
	functions.cloudEvent('helloPubSub', cloudEvent => {  // The Pub/Sub message is passed as the CloudEvent's data payload.  
	const base64name = cloudEvent.data.message.data;  
	const name = base64name
	    ? Buffer.from(base64name, 'base64').toString()    
	    : 'World';  
	console.log(`Hello, ${name}!`);  
});
```

```json
// package.json
{  
  "name": "gcf_hello_world",  
  "version": "1.0.0",  
  "main": "index.js",  
  "scripts": {    
    "start": "node index.js",    
    "test": "echo \"Error: no test specified\" && exit 1"  
    },  
  "dependencies": {    
  "@google-cloud/functions-framework": "^3.0.0"  
  }  
}
```

To deploy gcf
```
gcloud functions deploy nodejs-pubsub-function \
  --gen2 \
  --runtime=nodejs22 \  
  --region=us-east1 \ 
  --source=. \  
  --entry-point=helloPubSub \  
  --trigger-topic cf-demo \  
  --stage-bucket qwiklabs-gcp-01-12c1d78bbc3b-bucket \  
  --service-account cloudfunctionsa@qwiklabs-gcp-01-12c1d78bbc3b.iam.gserviceaccount.com \  
  --allow-unauthenticated
```

Build takes a while...

To check CCF status
```
gcloud functions describe nodejs-pubsub-function --region=us-east1
```
expect output to include `State: ACTIVE`

Testing

```
gcloud pubsub topics publish cf-demo --message="Cloud Function Gen2"
gcloud pubsub topics publish cf-demo --message="Here we are"
```

Runs PubSub with data that includes the trigger topic `cf-demo`
Output:
```
messageIds:
- '11927162971409664'
```


Logs

```
gcloud functions logs read nodejs-pubsub-function --region=us-east1
```

Can take a while, but could also check Logs Explorer from console
```
{
  "textPayload": "Hello, Here we are!\n",
  "insertId": "6ab69af1000c7378b830ddcf",
  "resource": {
    "type": "cloud_run_revision",
    "labels": {
      "configuration_name": "nodejs-pubsub-function",
      "project_id": "qwiklabs-gcp-01-12c1d78bbc3b",
      "location": "us-east1",
      "revision_name": "nodejs-pubsub-function-00001-doh",
      "service_name": "nodejs-pubsub-function"
    }
  },
  "timestamp": "2026-09-25T16:01:53.815992Z",
  "labels": {
    "instanceId": "0010dd86070f93feaa048434fda549dbdc6448e86671d914bfe945355362b5a9761b25b10e0b114d2ba156ad300ff921aca66f1dc5f559c5509fd0745e17a9cae8026902417dcf1c426105707e",
    "goog-managed-by": "cloudfunctions",
    "run.googleapis.com/base_image_versions": "us-docker.pkg.dev/serverless-runtimes/google-22-full/runtimes/nodejs22:nodejs22_20260915_22_23_2_RC00",
    "execution_id": "h5f89j46kayj"
  },
  "logName": "projects/qwiklabs-gcp-01-12c1d78bbc3b/logs/run.googleapis.com%2Fstdout",
  "receiveTimestamp": "2026-09-25T16:01:53.824215949Z",
  "spanId": "620687462605207957"
}
```
