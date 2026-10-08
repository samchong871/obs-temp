
## Available info/guidance

### General
[Build instructions](https://officenationalstatistics.sharepoint.com/:w:/r/sites/sps_usen/User%20Guides/Corporate%20MacBook/Build%20Instructions/ONS_Corporate_MacBook_build_guide_JUNE2026_v0.4.docx?d=wcf00947a3c6c4a438e85ca2731071d87&csf=1&web=1&e=c4OH2e)
[Corp MB FAQs](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions/AllItems.aspx)
[Software list](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Software%20List/AllItems.aspx)
[Corporate MacBook wiki](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/SitePages/Corporate-MacBook-wiki.aspx)

### Dev-specific
[Dev toolchains FAQ](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions/DispForm.aspx?ID=38&e=nKnGUW)
	Is there a either some documentation on or a good method for distributing a series of packages. Say we get a new team member start; we want to make sure they have everything they need?
	CITS do not produce documentation explaining how development teams should manage their tool chains. This should be the responsibility of development teams, as they know their tool chains best.
	The default package manager on the managed MacBook, Conda, provides some guidance on bootstrapping environments that teams can opt to adopt. https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

#### Other ONS dev teams
Some info from trawling Confuence

[Hippo](https://officefornationalstatistics.atlassian.net/wiki/x/YgC3H)
- Using [conda-global](https://github.com/conda-incubator/conda-global) to make tools (e.g. poetry, gh, gcloud CLIs) available across system
- Notes workaround for node/npm with conda

[Census RM (draft)]([https://officefornationalstatistics.atlassian.net/wiki/x/IwJFF](https://officefornationalstatistics.atlassian.net/wiki/x/IwJFF)
- Tools like tflint, gh, gcloud CLIs installed into all new conda env (`.condarc`)
- pyenv, nmv/node, tfenv outside conda [via shell scripts](https://officefornationalstatistics.atlassian.net/wiki/spaces/DSC/pages/340066851/DRAFT+Census+RM+-+Corporate+MacBook+Setup+Guide#Helpful-scripts)
- Also updated using shell scripts

[Dissemination](https://officefornationalstatistics.atlassian.net/wiki/x/EQDvGQ)
- Significant overlap with Blaise 5 tools
- Various tools [outside conda](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#Manual-Installs%2FHacks)
	- Download binaries to run from `~/bin`
	- Specific notes related to [pyenv + pipx + poetry](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#Python-(pyenv-%2B-pipx-%2B-poetry)) and also [fly](https://officefornationalstatistics.atlassian.net/wiki/spaces/DIS/pages/435093521/Corporate+macbook+setup+-+Notes#fly-(Concourse-CI))

## Basic stuff

- Issue connecting to office WiFi during initial build (activation, enrolment)
    - Had to use phone tethering
- After enrolment, connecting to ONS WiFi or wired connection asks for certificate to be selected
    - Not sure which one (yet)

## Dev set up

### Software availability
[Corp MB Software list](https://officenationalstatistics.sharepoint.com/sites/DS_CorporateMacBooks/Lists/Software%20List/AllItems.aspx)
[FAQs](https://officenationalstatistics.sharepoint.com/:l:/r/sites/DS_CorporateMacBooks/Lists/Frequently%20Asked%20Questions?e=YxcBhk)

#### Notes

- Homebrew is not approved as package manager

- Conda is the approved PM
    - `base` env is read-only

- `pyenv` is approved

- No VPN access


#### Approved sources

- **Self Service+** is the ONS "app store" app.

- Conda is the approved package manager
    - `conda-forge` channel installation into a user conda environment

- Some approved packages/tools can be installed, e.g. in shell


### Set up so far...

| Software/tool           | Source       | Notes                                                                                                 |
| ----------------------- | ------------ | ----------------------------------------------------------------------------------------------------- |
| VSCode                  | Self Service |                                                                                                       |
| Add `code` to PATH      | Self Service |                                                                                                       |
| XCode CLI Tools         | Self Service |                                                                                                       |
| miniconda               | Self Service |                                                                                                       |
| Git Crediential Manager | Self Service |                                                                                                       |
| fly                     | Self Service | Installs latest version; options for earlier. <br>May not be ideal - not sure if `fly sync` will work |
| pyenv                   | terminal     |                                                                                                       |
| nvm                     | terminal     |                                                                                                       |
| node                    | terminal     |                                                                                                       |

### Should be OK

Available on SS+

- Yarn
- GPG


### So many questions

Only available via conda (conda-forge)

- GCP cli
- Azure cli
- tflint
- 