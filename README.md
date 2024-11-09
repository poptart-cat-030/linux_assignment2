# README
Assignment 2 for ACIT 2420 (Linux System Administration)
Created by: Hillary Lam

## Introduction
Hi, welcome to my linux_assignment2 repository! This repository contains scripts to download packages, create symbolic links, and add users to your system. These programs were written to work with the Arch Linux distro.

## Repository Contents

### Project 1

The project1 directory contains three scripts:
- packageDownloader
- symbolicLinkCreator
- main

See the [Usage](#Usage) section for details on how to run these scripts

**packageDownloader** <br>
The packageDownloader script downloads packages from a plain text file provided by the user when this script is called in the main script. Alternatively, it can also download 2 packages (kakoune and tmux by default) when the script is run using the correct flag.

**symbolicLinkCreator** <br>
The symbolicLinkCreator script creates symbolic links to configuration files in the 2420-as2-starting-files cloned repository for a given user. The 2420-as2-starting-files repository can be found [here.](https://gitlab.com/cit2420/2420-as2-starting-files)

**main** <br>
The main script runs the packageDownloader and the symbolicLinkCreator scripts. You can run them separately or at the same time.

---

### Project 2

The project2 directory contains 1 script called userAdd.

See the [Usage](#Usage) section for details on how to run this script

**userAdd** <br>
The userAdd script adds a user onto the system without using utilities other than passwd and chown. You can specify the name of the user, set their password, choose their default shell, and add the user to any existing groups. Moreover, when this script creates the user's home directory, the contents of /etc/skel are also copied into it.

## Usage

> [!important]
> You have to run each script with root user privileges

### Project 1

#### packageDownloader

To use the packageDownloader script, you have two options:
1. Create a file in the project1 directory containing the names of packages you want to install and run the following command in the project1 directory:
```bash
./main -p [filename]
```
- Where `-p` is the option that takes a `filename` argument to download packages from that file
	- If the file does not exist or the file cannot be found, then the program will terminate

 > [!Note]
 > Add an extra line at the end of your file to ensure that the last package you provided will be installed

2. Download default packages, kakoune and tmux, by running the following command in the project1 directory:
```bash
./main -d
```
- Where `-d` is the option to install default packages, kakoune and tmux

#### symbolicLinkCreator

To use the symbolicLinkCreator script, run the following command in the project1 directory:
```bash
./main -c [user]
```
Where `-c` is the option that takes a `username` argument to create symbolic links to the 2420-as2-starting-files cloned repository for that user
- If the user does not exist, then an error message will be printed

---

### Project 2

#### userAdd

To use the userAdd script, run the following command in the project2 directory:
```bash
./userAdd -u [username] -s [shell] -g ['group1 group2 ...']
```
Where:
- `-u` is the option that takes a `username` argument to set the user's name to
  - If the user already exists, then the program will terminate
- `-s` is the option that takes a `shell` argument to set the user's default shell to
  - If the shell path is invalid, then the program will terminate
- `-g` is the option that takes 1 or more `groups` as an argument to add to user to
  - If the group(s) do not exist, then the program will terminate

> [!Note]
> When using option `-g`,  wrap the argument in quotation marks if you are adding multiple groups and separate the groups with a space. If you are only adding one group, you can provide the argument without quotation marks.


