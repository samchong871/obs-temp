---
Created at: Thursday 08-10-2026 – 09:33
Modified at: Thursday 08-10-2026 – 14:14
tags: [cMB, tools]
---
uv

From Rich - DFTS Confluence page

This document outlines the tools and software a developer will need to work on DFTS

- [Bash Profile](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Bash-Profile)
  - [Opening the terminal](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Opening-the-terminal)
  - [Check your profile](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Check-your-profile)
    - [Creating .zshrc](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Creating-.zshrc)
- [Self Service](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Self-Service)
  - [Software we use](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Software-we-use)
- [CLI Tools](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#CLI-Tools)
  - [UV](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#UV)
  - [Google Cloud CLI](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Google-Cloud-CLI)
- [GitHub](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#GitHub)
  - [SSH keys](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#SSH-keys)
  - [GPG Keys](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#GPG-Keys)
    - [Generating the key](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Generating-the-key)
    - [Finding the key](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Finding-the-key)
    - [Registering the key](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Registering-the-key)
    - [🚨 Ensuring commits are signed](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#%F0%9F%9A%A8-Ensuring-commits-are-signed)
- [DEXTA](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#DEXTA)
  - [Clone DEXTA](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Clone-DEXTA)
  - [Shares directory](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Shares-directory)
  - [ENV Variables](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#ENV-Variables)
- [Bookmarks](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/343638045/Macbook+Setup#Bookmarks)

Bash Profile

Your bash profile is where environment variables are persisted on your machine, we mainly use `.zshrc` for our bash profile.
Opening the terminal

- Go to “Apps” and search for terminal

Check your profile

First check you have a `.zshrc` by running…



c`at ~/.zshrc`
If you see

- `No such file or directory` you will need to create this file

Creating .zshrc

This command will create you an empty `.zshrc` file…
`touch ~/.zshrc`

Self Service

The way to install software on the new ONS MacBooks is through the application called “Self Service” which is shown in the image below. This can be accessed by clicking “Apps” on the dock.

Software we use

Below is a list of software we use on DFTS that can be found in Self Service…
If you cannot see any of the items listed below in your self service, a service desk request may need to be raised to get you access
N**ame**


**Purpose**

**Icon**

GPG Suite
To install and mange GPG keys, which is used to code sign commits to GitHub


JetBrains GoLand
An IDE for working with GoLang


JetBrains PyCharm Professional
An IDE for working with Python

JetBrains WebStorm
An IDE for working with web based technology


Postman
An application for making HTTP calls to services


Podman Desktop
An application for managing docker containers and images


Podman Runtime
The runtime for Podman


Xcode CLI tools
Various tools such as Git etc




CLI Tools

These are tools you do not need Self Service to install, instead they an be installed using the terminal app…
UV

[UV](https://docs.astral.sh/uv/) is the package manager we use to manage our Python packages.
Execute the following command in the terminal and follow the instructions on screen



c`url -LsSf ``https://astral.sh/uv/install.sh`` | sh`
Google Cloud CLI

To interact with GCP from your machine, you will need the google sdk. Instructions on installing this can be found
[here](https://docs.cloud.google.com/sdk/docs/install-sdk)

GitHub

GitHub is where we store our code, to get started ensure…

1. You have a GitHub account that is associated with your ONS email
2. You have 2FA enabled on your account

SSH keys

In order to pull and push private code to GitHub you will need an SSH key on your device.


ss`h-keygen -t rsa`
Don’t select a passphrase for your key
You should then be presented with something like this when you have generated a SSH key...


Your` identification has been saved in /Users/myname/.ssh/id_rsa.`
`Your public key has been saved in /Users/myname/.ssh/id_rsa.pub.`
`The key fingerprint is:`
`ae:89:72:0b:85:da:5a:f4:7c:1f:c2:43:fd:c6:44:38 myname@mymac.local`
`The key's randomart image is:`
`+--[ RSA 2048]----+`
`|                 |`
`|         .       |`
`|        E .      |`
`|   .   . o       |`
`|  o . . S .      |`
`| + + o . +       |`
`|. + o = o +      |`
`| o...o * o       |`
`|.  oo.o .        |`
`+-----------------+`
To copy your new
Pub**lic**
 SSH key to clipboard enter the following in the terminal


pbco`py < ~/.ssh/id_rsa.pub`
ensuring you change the name of the .pub file
if
 you specified a different location during the generation process
You will now need to copy your public SSH key into your Github account, to do this
Go to Github and login

Click your picture in the top right corner and click

1. **Settings**
2. Navigate to **SSH and GPG keys**
3. Click **New SSH Key**
4. Enter a title such as "ONS Macbook"
5. Paste your **Public** ssh key you copied earlier
6. Click **Add SSH key**

GPG Keys

A GPG key ensures all commits you make to GitHub are signed and will give the green “Verified” badge \(as shown below\)

Ensure you have the `gpg` command on your terminal by typing `gpg --help`
If the command is not found, ensure you installed the GPG suite from self service, if you have already installed GPG suite from self service and the command is not found, seek help
Generating the key

Run the following command and follow the on screen options


gp`g --full-generate-key`
You will be asked a few options when generating this key, they are as follows


Plea`se select what kind of key you want:`
`   (1) RSA and RSA (default)`
`   (2) DSA and Elgamal`
`   (3) DSA (sign only)`
`   (4) RSA (sign only)`
Enter
1
 for RSA and RSA or simply click enter as this is the default


RSA `keys may be between 1024 and 4096 bits long.`
`What keysize do you want? (2048) 4096`
Enter
409**6**



Plea`se specify how long the key should be valid.`
`         0 = key does not expire`
`      <n>  = key expires in n days`
`      <n>w = key expires in n weeks`
`      <n>m = key expires in n months`
`      <n>y = key expires in n years`
Enter
0

You will then be asked to enter some details including
Your Full name

Your email \(use the same one as your GitHub\)

- 

After this, you will be prompted to enter a passphrase for your key, if you leave the box empty and click "**Ok"** it will allow you to skip this step, the dialog may also pop up again to ask for a password, simply click "**Ok**" again to continue. Follow the final steps and you should have a GPG key on your MacBook.
Finding the key

You will need to copy the generated key to the clipboard, to do this we need to export it, start by listing all the keys on your system


gp`g --list-secret-keys --keyid-format=long `
You should then see a list of keys and one of them should look a bit like this


sec `  rsa4096/BB6C3098C3FDECC0 2021-12-13 [SC]`
`      129F638750E5213374422391NA6CF098C6FEECC4`
`uid                 [ultimate] Your Name <``your.name@gmail.com``>`
In this case the string we need is
BB6**C3098C3FDECC0**
 we are then going to run another command to get the public key to add to Github...


gpg `--armor --export BB6C3098C3FDECC0`
Replacing the
BB6**C3098C3FDECC0 **
with your personal id.
This should then print out your public GPG key, select this \(including the
-**------END PGP PUBLIC KEY BLOCK --------**
 and **------- BEGIN PGP PUBLIC KEY BLOCK --------**\) and copy it to the clipboard
Registering the key

Like with the SSH key

1. Go to Github and login
2. Click your picture in the top right corner and click **Settings**
3. Navigate to **SSH and GPG keys**
4. Scroll down and click **New GPG key**
5. Paste the key
6. Click **Add GPG key**

:rotating_light: Ensuring commits are signed

In order for GitHub to mark the commits as "VERIFIED" you will need to configure git on your mac to sign commits.

1. Grab the ID of your GPG key from the previous step \(BB6C3098C3FDECC0\) in this example.
2. Run the following commands with the ID
3. 
4. 

g`it config --global user.signingkey BB6C3098C3FDECC0`

1. 
2. `git config --global commit.gpgsign true`

DEXTA

If you are working with [DEXTA](https://github.com/ONSdigital/dexta) you will need to set up a few things on your local machine
Clone DEXTA

If you haven’t already clone the DEXTA repository…


gi`t clone git@github.com:ONSdigital/dexta.git`
Shares directory

DEXTA requires a
s`hares`
 directory to be present on the machine it’s running on. Choose a location for this, a good place is `/Users/YOUR_NAME/shares`
• Create the `shares` folder in `/Users/YOUR_NAME`
• Populate the folder with the following folders…
inputs
outputs
working
quarantine


ENV Variables

To instruct DEXTA to look in the folder we just created you will need to add an ENV variable called `SHARES_DIR`…

1. Open the DEXTA codebase
2. Create a `.env` file at the project root and write…

S`HARES_DIR=/Users/YOUR_NAME/shares`
Bookmarks

Here are the useful bookmarks you might want to add to Microsoft Edge…
B**ookmark Name**


**Description**

**URL**

Google Meets
The main Google meets meeting room for developers
[Meet](https://meet.google.com/oan-cszs-dge)
DFTS Confluence Page
The homepage for the team confluence
[❤️DFTS - Data Facilitation and Transformation Service](https://officefornationalstatistics.atlassian.net/wiki/spaces/SDC/pages/48808638)
DFTS Jira Board
The Jira board for DFTS
[DFTS | Active sprints](https://officefornationalstatistics.atlassian.net/jira/software/c/projects/DFTS/boards/2226)


