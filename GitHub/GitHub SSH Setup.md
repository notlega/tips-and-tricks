# GitHub SSH Setup

This document will cover a method of connecting your machine with GitHub

## Prerequisites

- A GitHub Account
- Git installed on the local machine

## Steps

Open Git Bash and run the following commands below in order

Check if a SSH token exists already

```bash
ls -al ~/.ssh
```

Generate SSH key with keygen command

```bash
ssh-keygen -t rsa -b 4096 -c "<github email>"
```

Currently a few options will appear

The first option allows for you to decide the name and file directory in where to save the SSH key file

If you wish to use the default filepath which is usually **```C:\Users\user\.ssh\id_rsa```**, press enter

The second option allows for the usage of a password for when GitHub has been communicated

If you wish to have no password set (which means convenience), press enter

Make sure SSH agent is running

```bash
eval$(ssh-agent -s)
```

Add SSH key to ssh-agent

```bash
ssh-add ~/.ssh/id_rsa
```

Open the filepath that contains the SSH key, it is usually **```C:\Users\user\.ssh```**

Open the file **using Notepad** with a **.pub** extension, it is also mistaken by Windows as a Microsoft Publisher Document

Copy the whole chunk of text, it should start with **ssh-rsa**

Open your GitHub Settings page and navigate to the **SSH and GPG keys section**

Add a new key and paste the copied chunk of text into the **Key** section

Name the key whatever you like and click **Add SSH key** to complete the adding

##### **THE FOLLOWING STEP IS IMPORTANT**

Verify the key works

```bash
ssh -T git@github.com
```

Confirm the warning with **yes**

Congrats, you have added an SSH key to GitHub!

## Example Usage

Instead of cloning a repository using the standard HTTPS link

```bash
git clone https://github.com/notlega/tips-and-tricks.git
```

You can now clone the repository using the SSH link

```bash
git clone git@github.com:notlega/tips-and-tricks.git
```

This is faster and much safer
