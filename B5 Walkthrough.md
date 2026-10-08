---
Created at: Tuesday 06-10-2026 – 10:43
Modified at: Thursday 08-10-2026 – 16:14
---
Audio (voice memo) starts 10:43ish (look at time on participants video screen)
@TOBI

Blaise 4 has problems
- Online access 
- Retention of data

Blaise 5 will help to address those issues

LFS
- Labour Force Survey
- Running on B4

LMS
- Labour Market Survey
- Parallel to LFS on B4
	- Much shorter than LFS
	- Ascertain if LMS data is as good as LFS
	- Recent reviews raised general concerns for ONS over data quality
		- So a particular concern
- Running on B5
- Knock to nudge (aka WebNudged)
	- In person aspect, but not really CAPI
	- Ask respondents to CAWI
	- Interviewer has Totalmobile, access to UAC
	- If respondent says "no computer"
		- Get phone number 
		- Telephone interviewer to call them -> CATI

IPS (Internet Passenger Survey)
- Cases not known up front
- Just grab people in the airport
- Donor case used to spawn new cases

LCF
- Living Costs and Food

DIA
- Sister to LCF
- aka ROS (record of spend)
- Upload photos of receipts
- Processed to extract info from B5 and converted to B4 so it can be processed/analysed in B4
	- 🤪
- 

CAWI
- repsond.ons.gov.uk
- ONS Online Studies

TOBI
- This is what a telephone operator/interviewer sees as the landing page
- Overview of questionnaires available
	- Click through to allocated cases, etc.
- Link to CATI dashboard

CATI
- Blaise Dashboard
	- Can actually do other online stuff
- Set up questionnaire for telephone interview
	- Needs survey date
- Access cases in daybatch
	- Giant table of cases
	- Press play to access next case
- Individual cases (Blaise?)
	- Buttons to call
	- Set outcome and details
	- Go through questionnaire
- Moving away from CATI
	- Next questionnaire -> performance issues
		- DB search uses `LIKE` in queries -> inefficient
 
Questionnaire
- Naming
	- `QQQYYMM_CCC`
		- `Q` questionnaire (abbreviation)
		- `Y` year
		- `M` month
		- `C` cohort
- Daybatch
	- cases to be conducted in a day

CAPI
- Offline, in person collection
- On device, interviews stored as sqlite
	- Important for, e.g. IPS (Internet Passenger Survey)
	- Can run locally, without internet
	- Sync to mySQL later when back on the internet 
		- Pop up prompt when connection
- DepApp 
	- Client provided by native Blaise
	- Wrapper developed by B5 team
		- Deployed with connection details for prod
- Manipula
	- Language dev by Blaise to do stuff with data
- CMA
	- Case Management Application
	- Runs on top of DepApp
	- Prettier way for interviewer to view allocated cases
	- Select case, click through to open Blaise

DQS
- Upload questionnaire packages for deployment into CAPI, CATI, CAWI, etc.
- Questionnaire has TO start date
	- Captured by DQS
	- Needs to be after TO start date for questionnaire to appear in TOBI

UAC
- Allows access by only person questionnaire is allocated to (the intended respondent)

urls
- `cname` for public-facing to get nice url
- CAWI - respond.gov.uk

Blaise
- RDBS-based
- default is sqlite
- Blaise uses mySQL
- Can be postgres

