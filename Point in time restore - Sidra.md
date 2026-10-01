---
tags:
  - Blaise
  - technical
  - demo_example
---
https://github.com/ONSdigital/blaise-questionnaire-point-in-time-restore.git
https://officefornationalstatistics.atlassian.net/wiki/x/I4AmH
BLAIS5-4963



Data delivery service for stuff like questionnaires run on a scheduled basis
- Usually every day moved from Blaise to Data Delivery
- Provides some level of data backup
- This adds another more fine-grained option to restore data

Repo: [blaise-questionnaire-point-in-time-restore](https://github.com/ONSdigital/blaise-questionnaire-point-in-time-restore/tree/main)
Contains a `Makefile`
- when `make run <questionnaire_name> <timestamp>` is run, has the effect of restoring the MySQL table for the given questionnaire to its state at the point in time specified by the timestamp
- The command does some checking of the arguments passed and then runs an existing script `scripts/run_restore.sh`

Look at Cloud SQL Studio

Actually more than just questionnaires
- Will be renamed one day

Point-in-time-restore
- GCP
- limited to last 7 days on dev/pre-prod
- 35 days for production env

Script lives in blaise-terraform/ci/tasks/deploy-point-in-time-restore
`task.sh` runs

Concourse group `pitr`
- runs cloud function restore-cloud-point-in-time (Cloud Run)


Backup function in terraform does not have access to temp bucket
- bucket contains clone of Cloud SQL from point in time
- but has its own service account
- Although terraform has access to the normal Cloud SQL service account, it does not to the new one see `blaise-terraform/modules/dataprotection/iam.tf`
- See iam-admin on GCP or backups bucket permissions
	- Clone has Storage Object User (also has Storage Object Admin, but possibly shouldn't have)