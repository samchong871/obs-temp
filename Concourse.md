---
Created at: Monday 28-09-2026 – 13:50
Modified at: Thursday 08-10-2026 – 14:20
---

## Concourse CLI `fly` basics

The cli is called `fly`
[`fly` docs](https://concourse-ci.org/docs/fly/)

### Create a fly "target"

`fly login --target <target_name> --team-name <specific_team> --concourse-url <concourse_pipeline_url>`

Aliases for options
	`-t`  `target`
	`-n`  `team-name`
	`-c`  `concourse-url`

Example for Blaise pipelines
`fly login --target blaise --team-name blaise --concourse-url https://concourse.social-surveys.gcp.onsdigital.uk`

### List targets
`fly targets`

### Log into target
`fly login -t <target_name>`
e.g.
`fly login -t blaise`

### Check log in
`fly -t <target_name> status`

### Check user team membership
`fly -t example userinfo`

### Logout 
Clears auth tokens
#### Specific pipeline
`fly -t <target_name> logout`

#### All targets
`fly logout -a`


### Check and update API version
`fly -t <target_name> sync`



In Blaise concourse
For integration-tests
- Some tests cannot run at the same time
- Some are dependent on others having run before
- Uses lock files to avoid tasks running at the same time
	- See azure-lock task
- On `blaise-concourse-locks`
	- Dir for each env/sandbox
	- Contains `claimed` and `unclaimed` dirs
	- Concourse moves the relevant file for components being tested into claimed


Integration tests as they are are more like "smoke tests"
- just check it works as expected - happy path
- not what happens if, e.g. user does something stupid



ben2  
    >az7p;&R)JZ*@PD
    
