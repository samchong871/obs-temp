---
Created at: Wednesday 07-10-2026 – 16:34
Modified at: Thursday 08-10-2026 – 16:10
tags: [AzureDO, technical, ticket, troubleshooting]
link: https://dev.azure.com/blaise-gcp/csharp/_build/results?buildId=165154&view=results
---

Pipeline fail on Blaise Integration Tests 
	`run-blaise-integration-test` task

### Investigate

On Azure DevOps
- Look at failing task
- Look at tests tabs

![[Pasted image 20261008095521.png]]

- Click on a failed test.

![[Pasted image 20261008095620.png]]

- Look at error stacktrace and/or attachments for info, e.g.
	`System.Exception : Questionnaire DST2304Z on server park gusty is stuck in Installing state Install date: 2026-10-06T16:13:38.7117583+00:00 Restart Blaise and uninstall the questionnaire via Blaise Server Manager at Blaise.Tests.Helpers.Questionnaire.QuestionnaireHelper.HandleInstallingState(String questionnaireName, String serverParkName) in D:\a\1\s\Blaise.Tests.Helpers\Questionnaire\QuestionnaireHelper.cs:line 229 at Blaise.Tests.Helpers.Questionnaire.QuestionnaireHelper.EnsureQuestionnaireReadyForTest(String questionnaireName, String serverParkName) in D:\a\1\s\Blaise.Tests.Helpers\Questionnaire\QuestionnaireHelper.cs:line 141`

In this case
- Not installed questionnaire properly


Look at VM (ben2's management node)
- Always management node first
- Server manager app (usually on desktop)
- Need Blaise username/password 
	- stored as ENV VAR on the VM, so look for it and enter into app at start up
- Gusty > Surveys
	- Will see DST2304Z is stuck installing
	- Try to Remove
	- Sometimes doesn't work
		- Try restarting Blaise 5 service on VM
		
		
Try rerunning pipeline task on Concourse
- trigger new build
