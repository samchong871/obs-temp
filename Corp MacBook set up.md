---
Created at: Friday 02-10-2026 – 08:39
Modified at: Thursday 08-10-2026 – 16:15
---
## Available info/guidance

### General
[Build instructions](https://officenationalstatistics.sharepoint.com/:w:/r/sites/sps_usen/User%20Guides/Corporate%20MacBook/Build%20Instructions/ONS_Corporate_MacBook_build_guide_JUNE2026_v0.4.docx?d=wcf00947a3c6c4a438e85ca2731071d87&csf=1&web=1&e=c4OH2e)
[Corp MB FAQs](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions/AllItems.aspx)
[Software list](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Software%20List/AllItems.aspx)
[Corporate MacBook wiki](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/SitePages/Corporate-MacBook-wiki.aspx)

### Dev-specific info
[Dev toolchains FAQ](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions/DispForm.aspx?ID=38&e=nKnGUW)
	**Q**: Is there a either some documentation on or a good method for distributing a series of packages. Say we get a new team member start; we want to make sure they have everything they need?
	**A**: CITS do not produce documentation explaining how development teams should manage their tool chains. This should be the responsibility of development teams, as they know their tool chains best.
	The default package manager on the managed MacBook, Conda, provides some guidance on bootstrapping environments that teams can opt to adopt. https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

#### Other ONS dev teams
Some info on set up from trawling Confluence

[Hippo](https://officefornationalstatistics.atlassian.net/wiki/x/YgC3H)
- Using [conda-global](https://github.com/conda-incubator/conda-global) to make tools (e.g. poetry, CLIs like gh, gcloud) available across system
- Notes workaround for node/npm with conda

[Census RM (draft)]([https://officefornationalstatistics.atlassian.net/wiki/x/IwJFF](https://officefornationalstatistics.atlassian.net/wiki/x/IwJFF)
- Tools like tflint, gh, gcloud CLIs installed as default packages into all new conda envs (`.condarc`)
- pyenv, nmv/node, tfenv outside conda [via shell scripts](https://officefornationalstatistics.atlassian.net/wiki/spaces/DSC/pages/340066851/DRAFT+Census+RM+-+Corporate+MacBook+Setup+Guide#Helpful-scripts)
- Also updated using shell scripts

[Dissemination](https://officefornationalstatistics.atlassian.net/wiki/x/EQDvGQ)
- Significant overlap with Blaise 5 tools
- Various tools [outside conda](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#Manual-Installs%2FHacks)
	- Download binaries to run from `~/bin`
	- Specific notes related to [pyenv + pipx + poetry](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#Python-(pyenv-%2B-pipx-%2B-poetry)) and also [fly](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#fly-(Concourse-CI))

Tom
- Single reusable conda env with tools installed

## Initial build
Following [Build instructions](https://officenationalstatistics.sharepoint.com/:w:/r/sites/sps_usen/User%20Guides/Corporate%20MacBook/Build%20Instructions/ONS_Corporate_MacBook_build_guide_JUNE2026_v0.4.docx?d=wcf00947a3c6c4a438e85ca2731071d87&csf=1&web=1&e=c4OH2e)
- MB should be in wiped state
	- As instructed in build document, raise incident on ServiceNow if a user account is set up
	- Corp MB team/support can guide through erase, recovery process
- Issue connecting to office WiFi (GovWifi, ONS-guest) during initial build (network is required for activation, enrolment)
	- Some info in build instructions for connecting to WiFi and troubleshooting - did not work for me
	- Fine on home broadband via wifi - did not try ethernet connection
    - Phone tethering seems to work, but can use a lot of data depending on updates required, etc.
- After enrolment, connecting to ONS WiFi and wired connection ask for certificate and/or authentication details
	- Various combinations tried, so far without success
    - Question asked on Corp MB Teams - will update if there is a response - or raise ticket
## Development set up
### Software availability
[Corp MB Software list](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Software%20List/AllItems.aspx)
[FAQs](https://officenationalstatistics.sharepoint.com/:l:/r/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions?e=YxcBhk)

#### Notes
- No VPN access
- Homebrew is not approved as a package manager (PM)
- `pyenv` is approved; can install on command line
- MS Edge is the approved browser
	- Chrome has to be requested

#### Approved sources
- **Self Service+** is the ONS "app store" app.
- Conda is the approved package manager
    - `conda-forge` channel installation into a user conda environment
    - `base` env is read-only
- Some approved packages/tools can be installed via shell, including pyenv, nvm/node

#### Other software
- Can be requested/installed via JustInTime (JIT) elevation (access via SelfService+)
- Requires business justification
- Check software list for approved/not approved or no status
- If not listed as approved, installing from, e.g. downloaded .dmg etc., will need to get JIT Admin Access and then the JIT Wrapper
![[Pasted image 20261006142951.png|744]]


### Set up so far...

| Software/tool           | Source       | Notes                                                                                                 |
| ----------------------- | ------------ | ----------------------------------------------------------------------------------------------------- |
| VSCode                  | Self Service |                                                                                                       |
| Add `code` to PATH      | Self Service |                                                                                                       |
| XCode CLI Tools         | Self Service |                                                                                                       |
| miniconda               | Self Service |                                                                                                       |
| Git Crediential Manager | Self Service |                                                                                                       |
| GPGSuite                | Self Service |                                                                                                       |
| fly                     | Self Service | Installs latest version; options for earlier. <br>May not be ideal - not sure if `fly sync` will work |
| pyenv                   | terminal     |                                                                                                       |
| nvm                     | terminal     |                                                                                                       |
| node                    | terminal     |                                                                                                       |
- VSCode extensions seem to be uncontrolled, as far as I can see
    - There is a specific document on the [approach to VS Code extensions](https://officenationalstatistics.sharepoint.com/:w:/r/sites/DS_CorporateMacBooks/Shared%20Documents/ONS%20VS%20Code%20Extension%20Approach.docx?d=wecc73cc5a7284c2a94c07072dba37f75&csf=1&web=1&e=7CJdSR)



/[draft thoughts/]
### Should be OK

Available on SS+

- Yarn

### ???
Only available via conda (conda-forge)

- GCP cli
- Azure cli
- tflint
- ...

### Possible approach

#### System-wide tools: CLIs, pipx, etc.
- Manage with conda
- Use conda-global
	- Accessible across projects
	- Benefit of package management for updates, etc.

#### Python version management
- pyenv (independent install approved)
- Fits with existing Blaise5 stack of pyenv/pip(x)/poetry

#### Python packages/venv
- poetry (recommended to install via pipx)
- Existing approach for Blaise5

