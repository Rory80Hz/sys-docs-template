# Developer Guide

## Software and Services
The following software and services are used by the delivery teams.

### Example: Slack

Slack is main communication tool used in this project. 

#### Kainos Slack workspace : kainos.slack.com

This workspace contains all Kainos related channels, and some specific channels for the program :
 
- 

Use your kainos email address to join the workspace. Ask your scrum master to be added to the relevant groups.


### Example: JIRA / Confluence

JIRA is used to manage our user stories. 

To get access to JIRA, send an email to person@example.org, with your Kainos email address. 

Put your scrum master in cc of this mail.

JIRA URL : https://eaflood.atlassian.net/secure/Dashboard.jspa

Ensure you have access to the project : **International Trade - Accelerated Imports Prototyping**

### Example: Keybase

Keybase is used to exchange passwords and secrets. Create an account on Keybase.

### Example: Github

We're using GitHub to maintain the Traces-X documentation (documentation you're currently reading)

You should have a github account and ask your scrum master to add you to the relevant projects.


## Example: Set up your local machine

Here are the minimal tools needed to start developing

* Install homebrew - https://brew.sh/

```text
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* Install GIT

```text
$ brew install git
```

* Install npm and node

```text
$ brew install npm
```

* Install Java (version 8)

```text
$ brew tap caskroom/versions
$ brew cask install java8
```

* Install Docker

```text
$ brew cask install docker
```

* Install maven

```text
$ brew install maven
```

* Install Browsers

```text
$ brew cask install firefox
$ brew cask install chrome
```

* Install IDE (IntelliJ is the recommendation, Log a request to Kainos Assistance to get a licence key)

```text
$ brew cask install intellij-idea
```

On the Systems request (assistance.kainos.com), please add your Delivery Manager as CC : 
![System Request for IntelliJ](/images/newdev-systems-intellij.png)

* Install Keybase

Keybase must be used to share any password or secret. 
It must be used by everyone on the project

```text
$ brew cask install keybase
```

* Install Slack

Slack is the communication tool used in Kainos. There is also a DEFRA Slack workspace for the EU Exit program.

```text
$ brew cask install slack
```


## Example: Set up your development environment
Document steps required to run a local development setup. Instructions on running services locally _must_ also be availble in any README in the source code control repositories. If it is more convenient just link to them.

### Java code formatting

Use Google Java Format for all Java code.

For IntelliJ IDEA there is the google-java-format (1.5.0.172) plugin for Java code formatting.

To use it you will need to:

- Install it via Preferences --> Plugins --> Browse repositories…
- Enable it via Preferences --> Other Settings --> google-java-format Settings (use Default Google Java style)
- Use CTRL+ALT+O and ALT-CMD-L for each Java change to format the code and remove unused imports

### Install Docker

Go to [Docker Downloads](https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac) and download the appropriate platform package for your system.
Next, Install these packages according to the instructions for your operating system.