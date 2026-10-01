
[Stand-up](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50312609 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50312609")
[Retrospective](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329891 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329891")
[Jira](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50333301 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50333301")
[Definition of ready and done](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50314565 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50314565")
[Cherry-picking](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329785 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329785")
[Team charter](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50325167 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50325167")
[Managing support calls and prod alerts](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50300931 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50300931")
[Large Language Models (LLMs) and Artificial Intelligence (AI)](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50334529 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50334529")

Work right-to-left on the kanban
- If something is waiting to be promoted, do that first
- Then peer review, etc.

Peer review
- As dev, make sure there's enough info for someone to easily review
	- Link to PR
	- How to test
	- [Info on raising peer review](https://officefornationalstatistics.atlassian.net/wiki/x/B-n-Ag)

In progress
- Current max of four
- Might change some time in future with bigger team

  
Requirements from BAs in the form of
Gherkin syntax
- Given
- When
- Then
-> Behaviour driven development


e.g. look in integration tests
- `xx.xx.Tests.Behaviour/Features`
- `xxx.feature` has the  gherkins


DDM dashboard
- shows status 
- no actual management

Prod dashboards only accessible on on-net
Dev accessible on off-net

Requests from users (should) come via Service Now
Alerts from GCP env get raised to Slack channels
- Important one is `prod`

