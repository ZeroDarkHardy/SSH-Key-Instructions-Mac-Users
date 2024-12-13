Generating and Registering an SSH Key on macOS

This guide will walk you through the steps to generate an SSH key using the macOS Terminal and register it with your GitHub account. It will also explain how to use the same SSH key for GitLab.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Step 1: Install Homebrew (if not already installed)](#step-1-install-homebrew-if-not-already-installed)
3. [Step 2: Install Git](#step-2-install-git)
4. [Step 3: Generate an SSH Key](#step-3-generate-an-ssh-key)
5. [Step 4: Start the SSH Agent](#step-4-start-the-ssh-agent)
6. [Step 5: Copy Your SSH Key to Clipboard](#step-5-copy-your-ssh-key-to-clipboard)
7. [Step 6: Add SSH Key to GitHub](#step-6-add-ssh-key-to-github)
8. [Step 7: Test the SSH Connection](#step-7-test-the-ssh-connection)
9. [Step 8: Create a New Repository on GitHub](#step-8-create-a-new-repository-on-github)
10. [Step 9: Clone the Repository to Your Computer](#step-9-clone-the-repository-to-your-computer)
11. [Step 10: Use the Same SSH Key for GitLab](#step-10-use-the-same-ssh-key-for-gitlab)
12. [Troubleshooting](#troubleshooting)
13. [Useful Links](#useful-links)

---

## Prerequisites

1. **macOS Terminal**  
   The Terminal app comes pre-installed on macOS. You can find it by searching for "Terminal" in Spotlight (Cmd + Space).

2. **A GitHub Account**  
   If you do not already have a GitHub account, create one at [GitHub Signup](https://github.com/signup).

---

## Step 1: Install Homebrew (if not already installed)

Homebrew is a package manager for macOS. To check if Homebrew is installed, run the following command in Terminal:

```bash
brew --version
```

If Homebrew is not installed, install it by running:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions to complete the installation.

---

## Step 2: Install Git

Verify if Git is installed by typing:

```bash
git --version
```

If Git is not installed, use Homebrew to install it:

```bash
brew install git
```

---

## Step 3: Generate an SSH Key

1. In Terminal, type the following command to generate a new SSH key:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   Replace `your_email@example.com` with the email address associated with your GitHub account.

2. When prompted to "Enter a file in which to save the key," press `Enter` to accept the default file location.

3. When asked for a passphrase, press `Enter` to skip creating a passphrase. **Do not set a passphrase** to avoid potential issues with forgetting it.

   Once completed, your SSH key will be generated and saved to your computer.

---

## Step 4: Start the SSH Agent

To use your SSH key, you need to ensure the SSH agent is running. In Terminal, enter the following commands:

1. Start the SSH agent:

   ```bash
   eval $(ssh-agent -s)
   ```

2. Add your SSH key to the agent:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

---

## Step 5: Copy Your SSH Key to Clipboard

To register the key with GitHub, you need to copy it to your clipboard. Use the following command:

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

This copies the public key to your clipboard.

---

## Step 6: Add SSH Key to GitHub

1. Open [GitHub](https://github.com) and log into your account.

2. Navigate to **Settings** (found in the top-right dropdown menu).

3. In the settings menu, go to **SSH and GPG Keys**.

4. Click the **New SSH Key** button.

5. Give the key a descriptive title (e.g., `My Mac SSH Key`).

6. Paste your public key into the "Key" field. Use `Cmd+V` to paste if necessary.

7. Click **Add SSH Key**.

8. Confirm your GitHub password if prompted.

---

## Step 7: Test the SSH Connection

Verify that your key was added successfully by typing the following command in Terminal:

```bash
ssh -T git@github.com
```

You should see a message like this:

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## Step 8: Create a New Repository on GitHub

1. Log into your GitHub account and navigate to your profile.
2. Click the **Repositories** tab and then click **New**.
3. Provide a name for your repository (e.g., `my-first-repo`).
4. Ensure the repository is set to **Public**. This is required so that graders can access your homework.
5. Check the box to **Initialize this repository with a README**.
6. Select a `.gitignore` template: Choose **Python** from the dropdown menu.
7. Click **Create Repository**.

---

## Step 9: Clone the Repository to Your Computer

1. On the repository page, click the green **Code** button.
2. Select the **SSH** option and copy the SSH URL.
3. In Terminal, navigate to the directory where you want to clone the repository. For example:

   ```bash
   cd ~/Documents/Projects
   ```

4. Clone the repository using the SSH URL:

   ```bash
   git clone git@github.com:username/repository-name.git
   ```

   Replace `username` and `repository-name` with your GitHub username and the repository name.

5. Navigate into the cloned repository:

   ```bash
   cd repository-name
   ```

You can now start working on your project locally.

---

## Step 10: Use the Same SSH Key for GitLab

Your SSH key can also be used to authenticate with your class GitLab page. Follow these steps:

1. Open your class GitLab page and log in.
2. Navigate to **Preferences** (usually accessible from your profile dropdown).
3. In the preferences menu, go to **SSH Keys**.
4. Paste the same public key you copied earlier into the "Key" field.
   - If the key is no longer in your clipboard, re-copy it using the following command in Terminal:

     ```bash
     pbcopy < ~/.ssh/id_ed25519.pub
     ```

5. Give the key a descriptive title (e.g., `My Mac SSH Key`).
6. Click **Add Key** to save it.

Once added, you can use the same SSH key to interact with your repositories on GitLab.

---

## Troubleshooting

### 1. SSH Key Not Found
   - Ensure the file path for your key is correct. Use the `ls ~/.ssh` command to list your SSH keys.

### 2. Permission Denied
   - Make sure the SSH agent is running and the correct key has been added using `ssh-add`.

---

## Useful Links

- **Homebrew**: [https://brew.sh/](https://brew.sh/)
- **GitHub SSH Key Documentation**: [https://docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- **GitLab SSH Key Documentation**: [https://docs.gitlab.com/ee/user/ssh.html](https://docs.gitlab.com/ee/user/ssh.html)

---

This concludes the setup process for generating and registering an SSH key on macOS, creating a new repository on GitHub, and cloning it to your computer. If you encounter any issues, refer to the troubleshooting section or ask for assistance.

