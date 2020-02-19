# Deployment View
Overview of build pipeline, quality gates etc. will be outlined here, these will be standard across the programme.


## CI/CD Principles
The intention is to embed in the development approach and delivery toolchain good practice as early as possible. This allows us to “bake in” risk reduction, efficiency and visibility offered by good Continuous Integration/Continuous Delivery practice. Below are a few of the most widely acknowledged CI best practices.

* Commit frequently.
* Don’t commit broken code
* Fix forward broken builds
* Write unit tests for code
* All test and inspections must pass (Unit Test, Static/Code quality/Automated tests suites), both for the product and for its deployment scripts
* Run local builds before committing to SCM
* Don’t pull code if build is broken – help fix it

It is recommended that developers write unit tests using the [red, green, refactor method](http://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html) to ensure that tests are correct. In order to check that we have good quality tests it is important to check that tests fail when we expect them to, for example when the code that should ensure they pass is absent we expect the tests to fail. Without this step it is very easy to write tests that don't assert things correctly or even at all but give good code coverage statistics yet actually test nothing. The red, gree, refactor method suggested should prevent this from happening.

The above practices will help speed the delivery of quality code and artefacts into the delivery pipeline. In addition, the following CD principles will ensure that the pipeline is able to deliver reliable and robust “no-surprises” releases consistently throughout all environments, up to and including production, and also provide some response and recovery in the event of failure.

* A repeatable and reliable process for release (single deployable artefact & process)
* Automate everything that can be automated
* Store and version everything required for release in SCM (Infra as code, config, database scripts etc.)
* If a step is problematic do it earlier and more often
* Build quality in
* Everyone is responsible for the whole delivery process
* Continuous Improvement is the goal

## Branching Strategy

### Branch Toplogy

![Workflow Diagram](/images/deployment_branch_diagram.png)

The approach for the code repository is to have a centralised hub repo as the origin from which the developers will draw local repositories. Stories should be as far as practicable independently releasable and the feature branches supporting them should merge to Master for release.

* The topology of the commit graph should be as simple as possible whilst enabling multiple teams to work swiftly without impacting each other.
* The topology of the commit graph should enable a clean and consistent delivery releases.
* The code workflow should be flexible enough to support a variety of releases cadences.
* The naming of feature branches will be the same as the JIRA story name.
* Feature branches are continually baselined from main before commit for local testing.
* Only merges from a completed feature branch are allowed onto the Master.
* Feature branch creation should be through a jenkins automation job.
* Fixes are treated as Feature branches allowing prioritisation of merge and release

### Core workflow

Working in Feature Branches with commit squashing provides the flexibility to release features on merge to master.

* Developers work on feature branches until their work is fully tested and is signed off by the product owner.
* Feature branches must be rebased from the latest version of Master before merging.
* They produce a squashed commit that combines all the changes on that branch.
* Merging to master signifies intention to release.
* Merging a feature to master means that other features that are in-flight will have to rebase their code.
* Fixes are treated as urgent features. That is, other in-flight features should wait on branch for the fix to be merged to master so that the rebasing overhead falls on them rather than on the urgent fix.
* Merge conflicts are offloaded to the feature branches by the rebasing from master.
* Merge activity should be coordinated through a realtime channel such as slack

Rebasing before merge means that the subsequent merge will be fast forward. That is, it results in no additional merge commit; rather the master pointer moves forward to the last commit on the feature branch. Fast forward merge has the additional benefit of simplifying the commit topology. If a project only fixed forward, this is the only branch topology the project would ever need. This topology is sufficient whether the project uses cadence releases (release per sprint) or moves to feature-based releases.

### Fix workflow

The fix workflow is handled as though it was a normal feature with its own branch. The only difference is that the fix is prioritised over all other feature releases (depending on urgency). This allows the reuse of the normal workflow and preserves consistency.

### Maintenance Workflow

While this document focuses mainly on the development needs of the repositories and build/test pipeline it should be noted that maintaining releases can be accomplished by taking a maintenance branch at the point of release and replacing it with each subsequent release to live. In this case a hotfix would be developed as a feature branch against the current live branch. With changes merged to main when the fix is applied to live.

![Workflow Details](/images/deployment_workflow_details.png)

### Constraints

Master should comprise merges, but not direct commits by developers. Assuming we are committed to rebasing so that merges are fast forward, we can add a commit hook that checks the parentage of the commit that the user is trying to merge and rejects everything that is not the result of a rebase. Rebase-before-merge only works if long-running branch does not move on, in between the start of the rebase and the end of the fast forward merge. Coordination and good comms are required to ensure cross team visibility of activities and status.