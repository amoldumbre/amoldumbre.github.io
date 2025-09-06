---
layout: post
title: "Setting up Multiple GitHub Accounts on the Same Machine"
date: 2022-05-15
categories: GitHub
---

# Setting up Multiple GitHub Accounts on the Same Machine

You may already have a personal GitHub account set up and working seamlessly. However, after starting a new job, you might also need to manage work-related repositories from a separate account—on the same laptop.  

So, how can you efficiently push and pull from multiple GitHub accounts on a single machine? Let’s walk through the process step by step.  

---

## Step 1: Create a New SSH Key

We need to generate a unique SSH key for the second GitHub account.  

Navigate to the `~/.ssh` directory and run the following commands:

```bash
cd ~/.ssh
ssh-keygen -t rsa -C "amol.dumbre@example.com"
````

When prompted:

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/crystal/.ssh/id_rsa): id_rsa_mycompany
```

> **Tip:** Press `Enter` twice if you don’t want to set a passphrase.

---

## Step 2: Add the SSH Key to GitHub

1. Log in to your second GitHub account.

2. Go to **Settings → SSH and GPG Keys → New SSH Key**.

3. Retrieve the public key you created:

   ```bash
   cat ~/.ssh/id_rsa_mycompany.pub
   ```

4. Copy the output and paste it into GitHub’s SSH Key field.

5. Optionally, give the key a descriptive title.

Now, add the key to your local SSH agent:

```bash
ssh-add ~/.ssh/id_rsa_mycompany
```

If successful, you’ll see:

```
Identity added.
```

---

## Step 3: Configure SSH for Multiple Accounts

To differentiate between accounts, create or edit an SSH config file:

```bash
touch ~/.ssh/config
vim ~/.ssh/config
```

Paste the following configuration:

```bash
# Personal GitHub
Host mygithub
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

# Company GitHub
Host github-mycompany
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_mycompany
```

Here:

* `mygithub` is the alias for your personal account.
* `github-mycompany` is the alias for your work account.

Save and exit the editor.

---

## Step 4: Test the Setup

Let’s verify that everything works:

```bash
mkdir test-repo && cd test-repo
git init
echo "# Test Repo" >> README.md
git add .
git commit -m "Initial commit"
```

On your company GitHub account, create a new repository (e.g., `Test`).
Then, push your local repo to GitHub using the custom host:

```bash
git remote add origin github-mycompany:Company/testing.git
git push origin master
```

Notice that we used `github-mycompany` (the alias defined in `~/.ssh/config`) instead of the default `github.com`.

---

## Example with a Custom Git Server

For reference, if you’re connecting to a custom Git server, your config might look like:

```bash
Host github-mycompany
  HostName mydomain.mygitsite.com
  User mygit
  IdentityFile ~/.ssh/id_rsa_company
```

Then your remote would be added as:

```bash
git remote add origin mygit@mydomain.mygitsite.com:testproject-automation/testrepo.git
```

---

## Step 5: Configure Git Username and Email per Repository

Instead of setting a global Git identity, configure it per repository:

```bash
git config user.name "Amol Dumbre"
git config user.email "amol.dumbre@example.com"
```

This ensures that commits from your personal and company repositories are properly attributed.

### Summary
<a href="https://github.com/user-attachments/assets/1507c8a4-0591-4d45-8091-765ac77468cd" target="_blank">
 <img width="768" height="130" alt="github_multiple_accounts" src="https://github.com/user-attachments/assets/1507c8a4-0591-4d45-8091-765ac77468cd" />
</a>
