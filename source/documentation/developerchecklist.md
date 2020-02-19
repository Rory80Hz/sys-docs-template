## Code Review checklist

This developer checklist is to help people when they are about to get their code in Code Review.

#### Added a new environment variable?

- Update the docker-compose file with the new variable(s)
- Update each of the terraform environments with the new variable(s)
- Update the relevant README's with the variable(s) and either a description or example
- Inform team members about the new variable(s) via slack
(or via keybase if it is a password or other secure piece of information)

#### Added new sass file?

- Add your newly generated css file to the head.html file
(which imports all the css files that are used within the project)
- Add to ./sass.sh file
- run `npm run sass`

#### Checked deployment on Azure?

- Check Jenkins has built
- Search logs for the random deployment string
(hint: search with the keyword 'imports-' and look for the 3 letter random deployment string)
- Test new functionality on Azure

#### Run code quality tools?

- Frontend linter as guidance (StandardJS)
- Services (google-java-format) as guidance
- Code quality tool (SonarQube)
- Test coverage tools (Istanbul (frontend) and Jacoco (Java services))

#### Other

- Check READMEs are up to date
- Rebase and squash commits into [one sensible commit message](https://chris.beams.io/posts/git-commit/)

#### After merging to master
- Delete environment from Azure (message web-ops team with random deployment string
  of environment to be deleted)
- Delete branch from Gitlab (via GitLab website)

#### Readme contents

Each project and subproject must have a readme file. Each Readme file should contains at least those sections :

* An introduction explaining what is the purpose of this project
* Pre-requisites : What is needed to use this project (configuration, 3rd party tools, ...)
* How to build and run the project
* How to build the docker image
* Directory Structure / Package Structure : An explanation of the structure of the project