---
tags:
  - cloud
  - GCP
  - learning
  - technical
Created at: Thursday 24-09-2026 – 16:39
Modified at: Thursday 08-10-2026 – 14:27
---
### gcloud
[`gcloud`CLI overview](https://docs.cloud.google.com/sdk/gcloud)

Open [Cloud Shell](https://docs.cloud.google.com/shell/docs) ![[Pasted image 20260924170026.png|30]] from Cloud Console

> [!note] Cloud Shell
> A VM with dev tools installed
> Runs on Google Cloud and has 5 GB persistent storage in `home` dir

Sets the project
`gcloud config set project [PROJECT_ID]`

List current account
`gcloud auth list`

Change active account
`gcloud config set account <ACCOUNT>` 

List project ID
`gcloud config list project`

Set region (europe-west1 here)
`gcloud config set compute/region europe-west1`

Set zone
`gcloud config set compute/zone "us-east5-a"`
`export ZONE=$(gcloud config get compute/zone)` (assuming this sets an env var)


### Creating bucket

`buckets create` command

`gcloud storage buckets create gs://<YOUR-BUCKET-NAME>`
e.g.
`gcloud storage buckets create gs://qwiklabs-gcp-02-ca69391b8b38`
- creates a bucket with default settings
	- multi-region, us
	- default storage class: standard
	- public access: subject to object access control lists (ACLs)
	- fine-grained access control
	- soft delete protection
	- flat namespace
	- no bucket retention rules, lifecycle rules
	- tagged: **gcp-environment** : prod
	- encryption Google-managed

> [!warning] Bucket name must be unique
> `Creating gs://YOUR-BUCKET-NAME/...`  
`ServiceException: 409 Bucket YOUR-BUCKET-NAME already exists`


Can use `curl` in google shell to download to pwd
`curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output ada.jpg`

Then copy to a bucket:
`gcloud storage cp ada.jpg gs://YOUR-BUCKET-NAME`
- `tab` works to autocomplete bucket name (not sure it does, actually)


To download from bucket into pwd:
`gcloud storage cp -r gs://YOUR-BUCKET-NAME/ada.jpg .`


List buckets
`gcloud storage ls`

List bucket contents
`gcloud storage ls gs://YOUR-BUCKET-NAME`

Get some more details (size, creation time) using `-l` flag
`gcloud storage ls -l gs://YOUR-BUCKET-NAME/ada.jpg`


Update properties of object in bucket
`gcloud storage objects update`

e.g. permissions
`gcloud storage objects update gs://YOUR-BUCKET-NAME/ada.jpg --add-acl-grant=entity=allUsers,role=READER`
- adds read access to allUsers


`gcloud storage objects update gs://qwiklabs-gcp-02-ca69391b8b38/ada.jpg --add-acl-grant=entity=allUsers,role=READER`


To delete object from bucket
`gcloud storage rm gs://qwiklabs-gcp-02-ca69391b8b38/ada.jpg`
