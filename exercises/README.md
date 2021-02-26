# 'Hands-On Hunting' Exercises


## Objective

The purpose of the 'hands-on hunting' scenario is to provide an end-to-end, interactive exercise that applies the concepts, workflow, and technical skills discussed during the threat hunting workshop.

In order to better simulate the overall threat hunting workflow described in the workshop, we created a mock Github containing a variety of hunting tasks. These tasks may be completed in any order, but should be prioritized in order to complete as many as possible within the time frame of the exercise.


## Logistics

Participants may work individually or in groups. Participants are encouraged to use the issue tracker and Kanban boards to delegate specific tasks to individuals. If participants do not have access to the exercise repository workflow management features (ie, the ability to create/modify issues), the facilitator can perform these actions on their behalf.  

Facilitators are available for support during the session, and are happy to answer any questions via email between session times.


## Scenario Description

This demo repository has been pre-populated with a small backlog of threat hunting tasks (issues) and abstracts. The goal is to prioritize the backlog by rating the hunts based on a combination of the amount of effort required and the value, (severity of impact, likelihood of producing true positives, etc), each potential threat hunt might have. The backlog 

> Note: The discussion of whether you have the data comes later and should not play into the effort discussion.

**Backlog Grooming**

Please review the issue backlog and prioritize which hunting tasks you would like to perform. Some of the tasks in the backlog may be time-consuming or require additional data and thus are not feasible to complete during the alloted time. _This is intentional_.

> Hint: Putting issues in a `blocked` state does not mean you failed the challenge.

**Create Abstract**

Participants will try to create an abstract using the provided template for the threats described in the issue. It may not be possible to create an abstract for some threats given the available data (and that's OK).

**Execute Abstract**

Participants will try to follow the data collection and analysis steps described in a provided abstract. Please document your findings, as well as open new issues to track any suggested improvements to the abstracts.

**Detector Creation**

Upon completion of the hunting abstracts, it is expected that participants will try to create detectors that would help identify relevant threats. Detectors may be created in either EDR or SIEM systems.

**(Optional) Learning Git**

A copy of this repository will be shared with participants via OneDrive and (optionally, upon client approval) in GitHub. While not explicitly part of the hunting capstone exercise, participants are encouraged to use `git` to perform some of the following tasks:

* Cloning the repository (`git clone`)
* Creating a branch (ie, when creating or updating an abstract) (`git checkout`)
* Adding changes to your branch (`git add`)
* Committing changes (`git commit`)
* Opening a pull request/merge request (`git push --set-upstream`)
* Keeping up-to-date with the master branch (`git pull`)
