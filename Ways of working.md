---
Created at: Thursday 17-09-2026 – 12:13
Modified at: Thursday 08-10-2026 – 14:28
---

[Stand-up](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50312609 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50312609")
[Retrospective](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329891 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329891")
[Jira](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50333301 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50333301")
[Definition of ready and done](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50314565 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50314565")
[Cherry-picking](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329785 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50329785")
[Team charter](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50325167 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50325167")
[Managing support calls and prod alerts](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50300931 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50300931")
[Large Language Models (LLMs) and Artificial Intelligence (AI)](https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50334529 "https://officefornationalstatistics.atlassian.net/wiki/spaces/QSS/pages/50334529")

### General principle
Work right-to-left on the kanban
- If something is waiting to be promoted, do that first
- Then peer review, etc.

#### Peer review
- As dev, make sure there's enough info for someone to easily review
	- Link to PR on github
	- How to test
	- [Info on raising peer review](https://officefornationalstatistics.atlassian.net/wiki/x/B-n-Ag)
- If reviewing, reassign to yourself while reviewing
	- Assign back to dev when done/asking for changes

#### In progress
- Current max of four
- Might change some time in future with bigger team
- Keep ticket up to date via comments as you are working
	- Enough detail that someone can see where you are, pick up if needed

#### Backlog
- Weekly refinement
- Consider a bit more
- Move priority to To Do
- Story points - use Fibonacci

#### Spikes
- When issue is not well-defined
- Spike used to investigate
- Points used to estimate time until review what has been found, rather
  
#### Requirements
 Come from from BAs in the form of Gherkin syntax
- Given
- When
- Then
-> Behaviour driven development

e.g. look in integration tests
- `xx.xx.Tests.Behaviour/Features`
- `xxx.feature` has the  gherkins


Requests from users (should) come via Service Now
Alerts from GCP env get raised to Slack channels
- Important one is `prod`

