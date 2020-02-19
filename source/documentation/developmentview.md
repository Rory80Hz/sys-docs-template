# Development View
This section outlines the approach to development for the system as defined by the development princinples, chosen technology stack and definition of done.

## Development Principles
### Applications will follow the 12 Factor approach to development

#### Rationale

* In order to meet our stated architectural principle of making applications portable, they must be engineered to be stateless, scalable etc.  [https://12factor.net/](https://12factor.net/)

#### Implications

* Code review must check that the 12 factor approach is being followed.

* Developers will need to understand this approach.

#### Applicability
All deployable units of code that will be used in production.

### All code is peer reviewed

#### Rationale

* In order to meet the quality, reliability, scale, performance and security requirements applications must produce appropriate logging and telemetry data.

#### Implications

* All schema changes must be captured in code, versioned and deployed automatically via the deployment pipeline.

* This must be checked as part of any code review, and tested appropriately.

#### Applicability
All deployable units of code that will be used in production.

### Applications must be observable.

#### Rationale

* To meet the quality, reliability, scale, performance and security requirements applications must produce appropriate logging and telemetry data.

#### Implications

* A standard logging format must be followed for all notable system events.

* All applications will provide a health check endpoint.

* All applications will have defined metrics that are useful to generate alerts.

* The above will be identified as part of open design proposals for applications, and verified during code review.

#### Applicability
All services that will be used in production.

## Definition of Done

The following tasks are completed on the feature branch:

* Code
* Liquibase database changes
* Unit tests
* Integration tests
* Selenium tests
* JMeter tests
* Infrastructure as Code

The change impact for each of those tasks should be reviewed during sprint planning.

Furthermore, we should have all the following:

* Merge request created and code review is done
* All tests (unit tests, integration, selenium, jmeter) passed in Jenkins
* Application have been successfully deployed by Jenkins for the feature branch
* Swagger documentation for endpoints is done
* Terraform plan output is attached to the JIRA ticket (if applicable)
* Story is signed off by the Product Owner
* Feature branch is merged into master

Whenever a branch is merged into master developers are encouraged to rebase and squash with
master at this point in order to minimize conflicts later on in the development phase. The
following tasks should be completed as part of this rebase:

* All intermediate commits are squashed in a single commit for the story
* Feature branch is rebased with master
* Commit comments include the JIRA Ticket ID and are relevant to the current state of the
branch
* Check all tests pass and the application is successfully deployed by Jenkins

After the story have been accepted by the Product Owner, and for each affected repo full
process to merge a feature branch would be:

* If not already done, squash commits, rebase with master and check the application is
succesfully deployed and tested by Jenkins.
* Check on slack that nobody is in the middle of their own merge to master
* Announce to slack channel “merging <rebased commit hash> to X”
* Merge to master (there will be an automatic announcement of the merge on slack)
* Check Jenkins successfully deploys to test
* Check that things are working as expected on test
* If all has not gone well, checkout the last good commit and push to HEAD (don't roll
back)

## Technology Stack

### Example: Front end

Tool | Target Version | Status | URL | Description
---- | ---------------| ------ | --- | -----------
NodeJs | 8.9.1 | Adopted | [https://nodejs.org/en/](https://nodejs.org/en/) |  Main Platform
NPM |   5.5.1  | Adopted | [https://www.npmjs.com/](https://www.npmjs.com/) | Packaging tool
MOCHA | 4.0.1 | Adopted | Test suite

### Example: Services

Tool | Target Version | Status | URL | Description
---- | ---------------| ------ | --- | -----------
Java |  1.8 (to be defined) | Adopted | | Main development language
MVN  | 3.5.2 | Adopted | [https://maven.apache.org/](https://maven.apache.org/) | Build tool
Dropwizard | 1.2.0 | Adopted | [http://www.dropwizard.io/](http://www.dropwizard.io/) | Main Framework
JDBI | 2.78 | Adopted | [http://jdbi.org/](http://jdbi.org/) | SQL connectivity
Junit | 5.0.1 | Adopted | [http://junit.org](http://junit.org) | Test Suite
Mockito | 2.12.0 | Adopted | [http://site.mockito.org/](http://site.mockito.org/) | Mocking framework for tests

### Example: Database

Tool | Target Version | Status | URL | Description
---- | ---------------| ------ | --- | -----------
Azure SQL Database | * | Adopted | [https://azure.microsoft.com/en-gb/services/sql-database/](https://azure.microsoft.com/en-gb/services/sql-database/) | Database server

### Example: Infrastructure as code

Tool | Target Version | Status | URL | Description
---- | ---------------| ------ | --- | -----------
Terraform | 0.10.5 | Adopted | [https://www.terraform.io/](https://www.terraform.io/) | Define a cloud infrastructure in a high-level configuration language
Ansible | 2.3.2 | Adopted | [https://www.ansible.com/](https://www.ansible.com/)| Automates software provisioning, configuration management, and application deployment