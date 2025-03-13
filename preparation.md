# Welcome to the Preparation for our Git Workshop!

In this workshop, we'll explore the fundamentals of modern version control and collaboration in research using Git, along with the platform GitHub. For the applied parts of the course we we would like to ask you to go through the preparations in this document independently before the course so that we can directly start using Git in the course. 

First, you need a Git installation, configure Git and setup an SSH key. Second, you need a GitHub account and you must authorize your computer to interact with GitHub using SSH. If you already have a working Git environment and a GitHub account, feel free to skip to the verification of your setup in Section 3. Otherwise, please follow Sections 1-3.

# 1. Setup Your Git Environment

## 1.1 Install Git

Install the latest version of Git (2.48.1 or newer) on your machine to ensure you have the most recent security patches and feature updates. If you already have Git installed, make sure you are using at least version 2.45.1, as earlier versions contain critical vulnerabilities. To check your installed Git version, open any terminal or command prompt and run: git --version.
Downloads and instructions can be found at [git-scm.com/downloads](https://git-scm.com/downloads).
Please follow the instructions depending on your operating system.
After successful installation you should have "Git CMD", "Git Bash" and some other tools on your Windows machine. We will now refer to Git Bash as "bash".

## 1.2 Configure Git

Before using Git, you need to set your name and email. 
Git records this information with every change you save (commit) to track who made each update. Without setting this, Git may not allow you to save changes. This step is essential for working alone and when collaborating with others.

### Step 1: Check the Git configuration for name and mail

First, check if you have set this in the past or if you already had Git installed. Type the following into your bash:

```bash
git config --get user.name
git config --get user.email
```

### Step 2: Set your name and email
If the answer is blank, provide Git your name and email address.
To do this, type the following commands, replacing the name and email address with your data:

```bash
git config --global user.name "Firstname Surname"
git config --global user.email "mail@example.com" 
```

Then check the output again using the commands from "Configure Git - Step 1".

You should get a response like this:
```bash
$ git config --get user.name
Firstname Surname

$ git config --get user.email
your-email@example.com
```

## 1.3 Setup SSH key

To use GitHub conveniently, you need an SSH key. We will briefly discuss what this is in the workshop.
If you don't have a private and public SSH key yet, please create one.

### Step 1: Check for an existing SSH key
Open your bash and enter this command

```bash
ls -al ~/.ssh
```

This command lists all files in the .ssh directory, including hidden files. 
If you already have SSH keys, the output may look something like this:

```bash
$ ls -al ~/.ssh
total 16
drwxr-xr-x 1 user 197120 0 Mar 13 10:15 ./
drwxr-xr-x 1 user 197120 0 Mar 13 09:45 ../
-r--r--r-- 1 user 197120 2602 Mar 13 10:15 id_rsa
-rw-r--r-- 1 user 197120 567 Mar 13 10:15 id_rsa.pub
-rw-r--r-- 1 user 197120 789 Mar 12 14:20 known_hosts
```

If there are any files called:
- `id_rsa`/`id_rsa.pub`
- `id_dsa`/`id_dsa.pub`
- `id_ecdsa`/`id_ecdsa.pub`
- `id_ed25519`/`id_ed25519.pub`
- or two files, one with and one without the `.pub` extension.

Then you already have an ssh key and should proceed with "Github Setup".
If the directory contains only the `known_hosts` file and perhaps a `config` file, or you receive an
error that `~/.ssh` does not exist, proceed to "Step 2".

### Step 2: Generate an SSH Key

To create a new SSH key run (in bash):

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Note: Git Bash does not show an error if you mistype something.

Why this command?
- ssh-keygen: Creates a new SSH key pair.
- -t ed25519: Uses the Ed25519 algorithm.
- -C "your-email@example.com": Adds your email as a label to identify your key.

Follow these steps when prompted:
1. Choose a file name and location. Press Enter to use the default location (~/.ssh/id_ed25519), or type a custom file name.
2. Set a password (optional but recommended). If you want to use the key without a password, just press Enter.
3. Confirm the password.
4. SSH key is generated! You’ll see a confirmation message with a random ASCII art that visually represents your key.

This is an example output:
```bash
$ ssh-keygen -t ed25519 -C "your-email@example.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (~/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in ~/.ssh/id_ed25519
Your public key has been saved in ~/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:eQI862Q7Nk6HoUrImp+22uWxUrXDIXeXhPaYAeQwlFQ your-email@example.com
The key's randomart image is:
+--[ED25519 256]--+
|   o=+E. .       |
|    .=  + .      |
|      =. * .     |
|    . +++.+      |
|     ==+S..      |
|..  .=++ o       |
|....+ O..        |
|.+o= * +         |
|++*oo .          |
+----[SHA256]-----+
```

# 2. GitHub Setup

We will use Git in combination with GitHub. You will need an account and some Basic configurations on your computer.

### Step 1: Create a GitHub Account

If you don't have a GitHub account yet, go to the [github.com sign up Page](https://github.com/signup?ref_cta=Sign+up) and create onw. Otherwise, login to your GitHub account and proceed with "Step 2".

### Step 2: Add Your SSH Key to GitHub

SSH keys allow you to securely connect to GitHub without entering your password every time.

Copy the contents of your `.pub` file which is the public part of your SSH key.

Run the following command to display your public key:

```bash
$ cat ~/.ssh/id_ed25519.pub
```

It will look something like this:

```bash
ssh-ed25519 AAAAC3NzaC1lHJK3FMAsmesoIAOk3xSVgqmS1bGhfBUn8rpIDgIYb8i8vNMfEU/2s1Ru your-email@example.com
```
Next, add your SSH key to GitHub:
1. Go to your [SSH and GPG keys](https://github.com/settings/keys) settings in github.com.
2. Click "New SSH Key".
3. Enter a title (e.g., "My Laptop SSH Key").
4. Paste the output from the previous command inside the bash into the Key field. (You need to copy and paste everything from ssh-ed25519 to the end of the email address).
3. Click "Add SSH Key".

For more detailed instructions, Wir verwenden das von uns aufgesetzte repositorium mit dem wir in diesem Workshop arbeiten wollen.see the [official GitHub documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

# 3. Verify Your Setup

Now that you've set up SSH authentication with GitHub, we need to test if everything is working correctly. The following step will a) confirm that your SSH key is properly linked to your GitHub Account; b) check if you can securely access repositories without entering a password; c) ensure that Git is using the correct email and name when you do something in Git.

What are we doing in the verification exactly? You will learn about the keywords "branch", "commit", and "commit log" during the workshop.

We will:
- Clone a repository (download it from GitHub). We will use the repository with which we want to work in this workshop.
- Create a new branch using your email as the name.
- Add your name to a file to check if Git recognizes your identity.
- Commit your changes to see if everything is recorded correctly.
- View the commit log to verify your setup.

Run the following:

```bash
git clone git@github.com/anolte-DSC/Git_Workshop_2025_PenguInc.git
cd git-course-test
git switch -c $(git config --get user.email)
echo $(git config --get user.name) >> participants.md
git add participants.md
git commit -m "I, $(git config --get user.name), completed the setup"
git log
```

The last command should get you a response like:

```bash
commit 018ce0ba29fab3413f0e3207159ec9bf8e383d24 (HEAD -> your.email@example.com)
Author: Your Name <your.email@example.com>
Date:   Wed May 29 12:23:51 2024 +0200

    I, Your Name, completed the setup
```

If your output is not similar, there seems to be a problem with the setup.
Take a look at the error message you received.
If you can't fix this issue yourself, please arrive at the workshop one hour ealier (at 9 am), but please bear in mind that we cannot help all participants within one hour.
