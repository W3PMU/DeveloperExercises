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
        - [Configuring ssh](#configuring-ssh)
        - [Cloning Your Project from GitHub to Your Local Machine](#cloning-your-project-from-github-to-your-local-machine)
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

The following procedure configures **ssh** to enable *git* to efficiently communicate between GitHub and your local machine. **ssh** client comes standard in most Linux distributions.  If you have a Windows machine and installed the [Git Software](#git-software) client as described in the beginning of this exercise, the *MINGW bash* terminal provides an **ssh** client. 

1. On your local machine, open a *bash* compatible terminal. In Windows, run the Git client: `git-bash.exe`.
2. Review the directory listinf for the folder `~/.ssh` using the command: `ls -al ~/.ssh`
    - screenshot: [typical .ssh directory listing](Exercise_GitHub_Fork.files/ssh_01.png)
3. If your directory listing for the `~/.ssh` folder contains the files: `id_rsa` and `id_rsa.pub` then you can probably skip the **ssh-keygen** step.  If the directory does not have those files the run the **ssh-keygen** utility.
    - When running **ssh-keygen** accept all of the defaults by pressing the *Enter* key. A passphrase is not needed for this exercise.
        - screenshot: [ssh-keygen](Exercise_GitHub_Fork.files/ssh_02.png)
4. Copy the *ssh-rsa* contents from the `~/.ssh/id_rsa.pub` file to your machine *clipboard*
    - screenshot: [ssh-rsa key in id_rsa.pub](Exercise_GitHub_Fork.files/ssh_03.png)
5. Open a web browser and sign in to your [GitHub.com](https://github.com) account
6. Drop down your Profile menu and select *Settings*
    - screenshot: [Profile menu Settings](Exercise_GitHub_Fork.files/GitHub_Settings_01.png)
7. Select the *SSH and GPG keys* item from left side Personal settings menu
8. Click the *New SSH key* button in the upper right
9. Paste the *ssh-rsa* key from the id_rsa.pub file into the *Key* text box. If paste does not work, repeat step 4 above and try again.
10. Enter a *Title* for the key. This is typically set to the username@machinename found at the end of the key.
    - screenshot: [New SSH Key](Exercise_GitHub_Fork.files/GitHub_Settings_02.png)
10. Click the *Add SSH key*
    - screenshot: [Added SSH Key](Exercise_GitHub_Fork.files/GitHub_Settings_03.png)

#### Cloning Your Project from GitHub to Your Local Machine

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