# Torch 7 'Hands-On Hunting' Capstone Scenario


## Objective

The purpose of the capstone 'hands-on hunting' scenario is to provide an end-to-end, interactive exercise that applies the concepts, workflow, and technical skills discussed during the threat hunting workshop.

Previous capstone exercises were delivered through written prompts (in slides) that instructed the participants to complete particular tasks. In order to better simulate the overall threat hunting workflow described in the workshop, we created a mock Github/Gitlab containing a variety of hunting tasks. These tasks may be completed in any order, but should be prioritized in order to complete as many as possible within the time frame of the exercise.


## Logistics

Participants may work individually or in groups. Participants are encouraged to use the issue tracker and Kanban boards to delegate specific tasks to individuals. If participants do not have access to the exercise repository workflow management features (ie, the ability to create/modify issues), the facilitator can perform these actions on their behalf.  

Facilitators are available for support during the session, and are happy to answer any questions via email between session times.


## Scenario Description

This demo Gitlab repository has been pre-populated with a small backlog of hunting tasks and playbooks.

**Backlog Grooming**

Please review the issue backlog and prioritize which hunting tasks you would like to perform. Some of the tasks in the backlog may be time-consuming or require additional data and thus are not feasible to complete during the alloted time. _This is intentional_.

> Hint: Putting issues in a `blocked` state does not mean you failed the challenge.

**Exploratory Data Analysis**

For issues labeled `EDA`, it is expected that participants will use ELK or other tools to profile an unfamiliar data source. Follow the guidance in the issue to complete these tasks.

**Create Playbook**

For issues labeled `Create Playbook`, it is expected that participants will try to create a playbook using the provided template for the threats described in the issue. It may not be possible to create a playbook for some threats given the available data (and that's OK).

**Execute Playbook**

For issues labeled `Hunt`, it is expected that participants will try to follow the data collection and analysis steps described in a provided playbook. Please document your findings, as well as open new issues to track any suggested improvements to the playbooks.

**Detector Creation**

Upon completion of the hunting playbooks, it is expected that participants will try to create detectors that would help identify relevant threats. Detectors may be created in either EDR or SIEM systems.

**(Optional) Learning Git**

A copy of this repository will be shared with participants via OneDrive and (optionally, upon client approval) in GitHub. While not explicitly part of the hunting capstone exercise, participants are encouraged to use `git` to perform some of the following tasks:

* Cloning the repository (`git clone`)
* Creating a branch (ie, when creating or updating a playbook) (`git checkout`)
* Adding changes to your branch (`git add`)
* Committing changes (`git commit`)
* Opening a pull request/merge request (`git push --set-upstream`)
* Keeping up-to-date with the master branch (`git pull`)
