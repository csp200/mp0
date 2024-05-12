# CSP 200 MP0: Logistics

## Goals

After successfully completing this machine problem (MP), you should understand
how to:

- accept GitHub Classroom MP invitations
- clone and work on machine problem repositories
- complete the MP report
- add files and commit changes to your local repository
- submit your work by pushing changes to GitHub
- confirm that your submissions are successful

## 1. Overview

This MP is designed to help guide you through the steps you must follow to
accept, access, and submit your work on MPs. You will follow the same steps for
each subsequent MP, so it's important that you understand them well --- be sure
to ask for help if you're unclear on how to perform any step, or _why_ you're
doing it!

We'll walk you through all the steps below in class, but they are documented
here for reference.

## 2. Accepting MPs

Prior to accessing this writeup, you must have already created a GitHub account
and accepted the invitation to create your copy of the MP repository. At this
point, GitHub Classroom "knows" who you are (i.e., it has saved the mapping from
your GitHub account username to the Hawk ID you selected). You will accept
future MP invitations in the same manner.

After the repository is created, you'll be given a link to its homepage on
GitHub -- a URL that looks something like
`https://github.com/csp200/mpXX-USERNAME` (where `XX` is the MP number and
`USERNAME` is your GitHub username). Note this URL, as you'll need it to access
the repository in the future.

At the top of the repository homepage is a list of its files/directories, and
the contents of the "README.md" file (this writeup) will be displayed under that
listing. The GitHub web interface allows you to edit files directly in the
browser, but we _strongly recommend_ that you do not do so. Instead, you will
_clone_ the repository to the class server and work on it there.

## 3. Registering a public key with GitHub

In order to authenticate with GitHub and access your repository, you'll first
need to create a _public encryption key_ on the server and register it with
GitHub. This will be used to secure communications and allow you to clone your
private repositories without typing in a password each time. You'll only need to
perform this step once this semester!

To create a public key, enter the command `ssh-keygen`. This will prompt you for
a few pieces of information -- you should just accept the defaults by hitting
the enter/return key at each prompt, until the command completes and creates a
key. The output upon successful completion should look something like this:

    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/home/lee/.ssh/id_ed25519):
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /home/lee/.ssh/id_ed25519
    Your public key has been saved in /home/lee/.ssh/id_ed25519.pub
    The key fingerprint is:
    SHA256:BBUGjcRLSch9ifAfYjAvKqTVj1QDusF3a7iFPQBYk5k lee@csp200
    The key's randomart image is:
    +--[ED25519 256]--+
    | o+==OBB+o       |
    |..E=o*B++        |
    | .= *.*oo        |
    |o. u @.= .       |
    |o o + B S        |
    | .   + .         |
    |    .            |
    |                 |
    |                 |
    +----[SHA256]-----+

The next step is to copy the generated public key onto your clipboard. Print the
public key with the command `cat ~/.ssh/id_ed25519.pub`. This should produce
output that looks like this:

    ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBB5XjiH7UDnlkehsu25Yk8BxXK83eqU6IwUFuxknGQ9 lee@csp200

Copy this entire line to your clipboard.

Next, go to your GitHub Settings page. You can access this by clicking on your
profile photo in the top-right corner after logging into GitHub then clicking on
"Settings". Then, click on the "SSH and GPG keys" tab, then click on the "New
SSH key" button. Finally, paste your public key into the "Key" field, while
typing "csp200" into the "Title" field, and click "Add SSH key". If this is
successful, you should have a new authentication key listed on your settings
page. If there is an error, make sure you copied the entire key (and don't have
any leading spaces).

## 4. Cloning the repository

Finally, you're ready to clone the repository. On the server, type the following
command, replacing USERNAME with your own GitHub username (note, _not_ your IIT
username)!

    git clone git@github.com:csp200/mp00-USERNAME.git

This should clone the contents of your repository into a directory with a
matching name. The command may prompt you to verify the authenticity of the
GitHub service -- if so, just type `yes` and hit enter. When successful, you
should see output like the following.

    Cloning into 'mp00-USERNAME'...
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 5 (delta 0), reused 4 (delta 0), pack-reused 0 (from 0)
    Receiving objects: 100% (5/5), 5.62 KiB | 5.63 MiB/s, done.

You should now have a directory named "mp00-USERNAME" where you ran the
`git clone` command, and within it you will find all the files provided for this
machine problem. `cd` into that directory now.

## 5. Working on MPs

Most MPs will ask you to edit and/or create files in the repository in order to
implement specified functionality. We will typically provide you with starter
code and other resources to help you.

For this MP, however, there's no implementation component. Instead, we'll show
you how to add a file to the repository, edit the MP report, and submit our
work.

### 5.1. Adding files to the repository

Create an empty file in the MP directory named "foo". When you are done, run the
following command, which will _stage_ the new file to be added to the
repository:

    git add foo

Repeat the process for another file named "bar" (i.e., create the file and
`git add` it).

Next, we will need to _commit_ all our staged changes. Because this is our first
time doing this, we need to tell Git how we wish to sign our commits. Run the
following commands with your own name and e-mail address:

    git config --global user.name "John Doe"
    git config --global user.email "jdoe@iit.edu"

Now perform the commit with the following command. The quoted part is known as
the _commit message_, and will be recorded by Git alongside the changes you're
making to the repository. You will customize these messages for future commits.

    git commit -m "Adding required files"

This should produce output like the following, which tells us the files have
been added to and are now being tracked by the repository:

    [main c6f2484] Adding required files
     2 files changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 bar
     create mode 100644 foo

### 5.2. Completing the MP Report

Every MP will come with a file named "REPORT.md", which is the template for your
MP report. You will enter your information (name and ID) and mark the boxes in
the self-evaluation checklist that apply to your submission, then edit the
"Summary and Reflection" section.

Edit the report file now. When you are done and have saved your changes, run
`git add REPORT.md` to stage it, then `git commit -m "Editing report"` to commit
the change.

You can now run the command `git log` to view a record of commits to the
repository. It should look like this:

    commit 1665fe9a5c41dc4cb15e57e58fbff4983f01995a (HEAD -> main)
    Author: Michael Lee <lee@iit.edu>
    Date:   Tue Jan 28 16:36:15 2025 +0000

        Editing report

    commit 1472974c7a1fc6f206407bef336c0b377948a971
    Author: Michael Lee <lee@iit.edu>
    Date:   Tue Jan 28 16:35:25 2025 +0000

        Adding required files

    commit aa8d346bf759943643c0c93b2cbdf18893afd716 (origin/main, origin/HEAD)
    Author: github-classroom[bot] <66690702+github-classroom[bot]@users.noreply.github.com>
    Date:   Tue Jan 28 16:31:59 2025 +0000

        Initial commit

### 5.3. Submitting your work

Committing your changes updates your local repository (on the server), but in
order to submit your work, you must also _push_ your changes to the repository
maintained by GitHub.

To push your work, run the following command:

    git push

You should see output like the following:

    Enumerating objects: 8, done.
    Counting objects: 100% (8/8), done.
    Compressing objects: 100% (5/5), done.
    Writing objects: 100% (6/6), 602 bytes | 301.00 KiB/s, done.
    Total 6 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (2/2), completed with 1 local object.
    To github.com:csp200/mp00-michaelee.git
       aa8d346..1665fe9  main -> main

### 5.4. Confirming Your Submission

After you have pushed your changes to GitHub, you should go to the repository
homepage on GitHub and confirm that your changes are visible there. You should
see the updated "REPORT.md" file with the information you added, and other
changes you made in the commit history.

Once you have confirmed that your changes are visible on GitHub, you have
successfully submitted your work. You can commit and push as many times as you
like before the deadline, and we will grade the most recent version of your work
that was submitted before the deadline.

## 6. Summary

Here's a recap of the steps you need to follow to complete an MP:

1. Accept the MP invitation link
2. Clone the repository
3. View the "README.md" file for MP details
4. Add/Edit files to implement required functionality
5. Edit the "REPORT.md" file to include all requisite information
6. Stage and commit your changes (repeat steps 4-6 as needed)
7. Push your commits to GitHub
