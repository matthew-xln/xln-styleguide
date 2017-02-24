# [XLN Code Style Guide](../README.md) - Git Repository

> Guide for our Git repository workflow

## Table of Contents
  1. [Feature Branch Workflow](#feature-branch-workflow)
  1. [Why Not Git-flow?](#why-not-git-flow)
  1. [Git Commits](#git-commits)
  1. [Code Reviews](#code-reviews)
  1. [The Git Commandments](#the-git-commandments)

---

### Feature Branch Workflow
All feature development should be done in a dedicated branch, never in the master branch. This will ensure that the master branch never contains partial or non-functional code and that hotfixes can always quickly be pushed and deployed.

As a team we should strive towards making many smaller releases, where functionality goes live as soon as it's been completed and tested.

Branches must have a descriptive name for the feature or functionality being worked on. Local commits should be pushed to the central repository, creating a backup. Branch names begin with branch type followed by a slash and the branch description. All characters should be lowercase with dashes for word separation.

Branch types:
* **feature/**... _(new features and functionality)_
* **refactor/**... _(code cleanup and restructuring)_
* **bug/**... _(bugfixes too complex to do directly as hotfixes on master)_
* **test/**... _(testing and proof of concept)_

> Example: feature/adyen-payment-integration

**[⬆ back to top](#table-of-contents)**

---

### Why not Git-flow?

Git-flow is centered around planning and deploying larger product releases. Compared to the feature branch workflow this requires additional branches and steps to perform deployments.

We're a small team following the _"release early, release often"_ philosophy. We want new features in the hands of our users as quickly as possible. The Git-flow workflow adds unnecessary complexity that we feel risks delaying the deployment of new functionality.

**[⬆ back to top](#table-of-contents)**

---

### Git Commits
Commits should only contain single sets of functionality. If a developer has made bugfixes and addressed requested quickfixes while working on a new set of features, these should be split into separate commits. This will help keep commit history clear and make it easier to cherry pick general fixes from feature branches.

Capitalize the first letter, limit subject to 50 characters and don't use period sign at the end. Separate subject from body with two line breaks. Clients like Tower will guide you by having separate subject and body fields with character counters. Note that subjects are mandatory while a body text is optional. Commit comments are very valuable, a diff can tell you what has changed, but not why it's been changed.

The subject line should be written in imperative, meaning descriptions should be written as if they are in present tense versus past tense. As an example, write “Fix typo in page footer” instead of writing “Fixed typo...”. This is in line with Git's own commit messages. Note that this does not need to be enforced on the body.

> Quick tip, write the subjects thinking: This commit will …...

**[⬆ back to top](#table-of-contents)**

---

### Code Reviews
When a feature branch has been completed any changes done to the master branch should be merged into the current feature branch. The developer should then request a Code Review session.

During code review sessions we should primarily look for bugs or logic flaws as well as code that's badly structured and difficult to follow. We should also look for typos and code that doesn't follow our internal guidelines. Once the code has been approved it should be merged back into the master branch and deployed.

**[⬆ back to top](#table-of-contents)**

---

### The Git Commandments
* Master should never contain broken or non-functional code
* Only push to master if you're ready to deploy within a couple of hours
* All new feature development is done in separate branches
* Feature branches must have descriptive names
* Quick/hot fixes can be done directly on master
* Commits should contain single sets of functionality
* Always write descriptive comments for commits
* Request a code review when branched off functionality is completed
* Avoid unnecessary merge commits, rebase on merge when possible
* Squashing commits is optional, avoid long squash messages

**[⬆ back to top](#table-of-contents)**