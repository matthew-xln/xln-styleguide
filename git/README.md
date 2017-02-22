# [XLN Code Style Guide](../README.md) - Git Repository

> Guide for our Git repository workflow

## Table of Contents 
  1. [Feature Branch Workflow](#feature-branch-workflow)
  1. [Git Commits](#git-commits)
  1. [Code Reviews](#code-reviews)
  1. [The Git Commandments](#the-git-commandments)

---

### Feature Branch Workflow
All feature development should be done in a dedicated branch, never in the master branch. This will ensure that the master branch doesn’t contain partial or non-functional code and that hotfixes can always quickly be pushed and deployed.

Feature branches must have a descriptive name for the feature being worked on. Any local commits to the branch should also be pushed to the central repository, creating a backup.

As a team we should strive towards making many smaller releases, where functionality goes live as soon as it’s been completed and tested.

**[⬆ back to top](#table-of-contents)**

---

### Git Commits
Commits should only contain single sets of functionality. If a developer has made bugfixes and addressed requested quickfixes while working on a new set of features, these should be split into separate commits. This will help keep commit history clear and make it easier to cherry pick general fixes from feature branches.

Capitalize the first letter, limit subject to 50 characters and don’t use period sign at the end. Separate subject from body with two line breaks. Clients like Tower will guide you by having separate subject and body fields with character counters. Note that subjects are mandatory while a body text is optional. Commit comments are very valuable, a diff can tell you what has changed, but not why it’s been changed.

The subject line should be written in imperative, meaning descriptions should be written as if they are in present tense versus past tense. As an example, write “Fix typo in page footer” instead of writing “Fixed typo...”. This is in line with Git’s own commit messages. Note that this does not need to be enforced on the body.

> Quick tip, write the subjects thinking: This commit will …...

**[⬆ back to top](#table-of-contents)**

---

### Code Reviews
When a feature branch has been completed any changes done to the master branch should be merged into the current feature branch. The developer should then request a Code Review session.

During code review sessions we should primarily look for bugs or logic flaws as well as code that’s badly structured and difficult to follow. We should also look for typos and code that doesn’t follow our internal guidelines. Once the code has been approved it should be merged back into the master branch and deployed.

**[⬆ back to top](#table-of-contents)**

---

### The Git Commandments
* Master should never contain broken or non-functional code
* Only push to master if you’re ready to deploy within a couple of hours
* All new feature development is done in separate branches
* Feature branches must have descriptive names
* Hotfixes / quick fixes can be done directly on master
* Commits should contain single sets of functionality
* Always write descriptive comments for commits
* Request a code review when branched off functionality is completed
* Avoid unnecessary merge commits, rebase when possible
* Squashing commits is optional, avoid long squash messages

**[⬆ back to top](#table-of-contents)**