|   |   |
|---|---|
| **[Grid Protection Alliance](http://www.gridprotectionalliance.org "Grid Protection Alliance Home Page")** | **[Exercises](README.md)** |

***This document is an exercise procedure for illustrating workflow methods.***

---

# UNDER CONSTRUCTION

---

# GitHub Fork Exercise

This is a *cookbook recipe* style exercise that illustrates GitHub forked project workflow methods.

- [Platform](#platform)
    - [GitHub.com Account](#githubcom-account)
    - [Git Software](#git-software)
- [Forking a Project](#forking-a-project)
    - [Cloning Your Project Fork](#cloning-your-project-fork)
    - [Frequently Asked Questions (FAQ)](#cloning-frequently-asked-questions-faq)
        - [Configure Your Cloned Project Remotes](#configure-your-cloned-project-remotes)
- [Synchronizing Your GitHub Fork with the Upstream Master](#synchronizing-your-project-fork-with-the-upstream-master)
    - [Pulling Changes from Your GitHub Fork](#pulling-changes-from-your-github-fork)
    - [Pulling Changes from the Upstream Master](#pulling-changes-from-the-upstream-master)
    - [Pushing Changes to your GitHub Fork](#pushing-chagnes-to-your-gethub-fork)
- [Creating a Pull Request](#creating-a-pull-request)
- [Managing Merge Conflicts](#managing-merge-conflicts)

---

## Platform

This exercise uses a PC or virtual machine with Internet connection and Git command line software installed.  This exercise was tested in both Windows and Linux operating systems.  The GitHub website is designed to work with a modern web browser with a graphic user interface (GUI). 

### GitHub.com Account

You need a [GitHub.com](https://github.com) registered account with a verifiable email address to perform the tasks in this exercise.  A free GitHub account can be used for this exercise.

### Git Software

- *Windows* - Download and install Git from [https://git-scm.com](https://git-scm.com/). This exercised was tested using a *Portable* version.
- *Linux* - Install Git using your distro's package manager or build Git from source code. For example: [Git instructions in Exercise_openPDC_in_Debian_Jessie](Exercise_openPDC_in_Debian_Jessie.md#git)

---

## Forking a Project

The folllowing demonstrates how to create a *Fork* of this DeveloperExercises project.

1. Run a web browser and Sign in to [https://github.com](https://github.com)
2. Navigate to the [DeveloperExercises](https://github.com/GridProtectionAlliance/DeveloperExercises) repository
3. Click the *Fork* button
    - screenshot: [GitHub project page showing *Fork* button in upper right corner](Exercise_GitHub_Fork.files/Fork_01.png)
    - screenshot: [Project *Forking* progress page](Exercise_GitHub_Fork.files/Fork_02.png)
4. After the *Fork* process is completed, your browser will display a new *forked* project page in your GitHub account.
    - screenshot: [Your account's new *Forked* project page](Exercise_GitHub_Fork.files/Fork_03.png)
5. Optional Setting: To avoid possible confusion, click the *Settings* button and give your project *Fork's* repository a new name.  For example, after *forking* **DeveloperExercises**, rename its repository to **DeveloperExercises_fork**
6. Optional Setting: Set the *Restrict editing to collaborators only* option to checked
    - screenshot: [Your *Forked* project's *Settings* showing *Repository name* changed and *Restricted editing* checked](Exercise_GitHub_Fork.files/Fork_04.png)

### Cloning Your Project Fork

For simplicity in the scope of this exercise: *Forks* are on GitHub and *Clones* are on your local machine.

*Clone* a project's repository to work with the project's files on your local machine. 

#### Frequently Asked Questions (FAQ)

- What is a *clone*?

> A *clone*, in the scope of this exercise, is a copy of a *git* repository. *Cloning* a repository is the procedure for making a copy of the repository. Unlike a downloaded *zip* or *tar* file containing a copy of the repository's files, a clone includes git's content management metadata that enables you to pull updates and merge changes in your repository.

- What is a *fork*?

> A *fork*, in the scope of this exercise, is a *GitHub* repository that was *cloned* from another existing *GitHub* repository. *Forking* a repository is the procedure for cloning a GitHub repository from the main *upstream* source to your own GitHub repositories collection.

- Should I *clone* my *fork* or should I *clone* the mainstream or *upstream* repository?

> When you *clone* your *fork*, it is easier to push your local changes to your *fork* on GitHub. Using the GitHub *fork* and *pull request* workflow allows you and others to review your changes before committing them to the main *upstream* project.

- Can I *fork* my *clone*?

> No, not in the scope of this exercise.  GitHub cannot access your *clones* on your local machine; so GitHub cannot *fork* your *clones*.


#### Configuring **ssh**

The following procedure configures **ssh** to enable *git* to efficiently communicate between GitHub and your local machine. If you have a Windows machine, 




#### How to Clone Your Project from GitHub to Your Local Machine

1.


#### Configure Your Cloned Project Remotes

---

## Synchronizing Your GitHub Fork with the Upstream Master

### Pulling Changes from Your GitHub Fork

### Pulling Changes from the Upstream Master

### Pushing Changes to your GitHub Fork

---

## Creating a Pull Request

---

## Managing Merge Conflicts

---

Jan 7, 2017 - Under Construction

---

Copyright 2017 [Grid Protection Alliance](http://www.gridprotectionalliance.org)