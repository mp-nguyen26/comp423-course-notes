# Setting up a dev container for Rust

* Primary author: [Minh Nguyen](https://github.com/mp-nguyen26)
* Reviewer: [Christina Do](https://github.com/chrxstyxdo)

## Prerequisites
Before we get started, make sure you have the following:

1. **A GitHub account**
2. **Git installed**
3. **Visual Studio Code**
4. **Docker**
5. **Some knowledge of command-lind basics**

## Git Setup

### Step 1: Create a local directory and initialize git.

* Open terminal/command prompt.
* Change into a parent directory in which you would like to house this project, or by default, it will be in your user's home directory.
* Create a new directory for your project:
```
mkdir rust-project
cd rust-project
```
* Initialize as a new Git repository:
```
git init
```
!!! question "What does `git init` do?"
    This command turns a regular directory into a git repository. After it is configured this way, all git commands can now work.
* Create a README file:
```
echo "# Rust Project" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Create a remote repository on GitHub.

* Log into your GitHub account and navigate to the "Create a New Repository" page.
* Fill in the following details:
    1. **Repository Name:** rust-project
    2. **Description:** "A remote repo for running a simple Rust program."
    3. **Visibility:** Public
* Do not initialize the repository with a README, .gitignore, or license.
* Click **Create Repository**.

### Step 3: Link your local repository to GitHub.

* Add the GitHub repository as a remote:
```
git remote add origin https://github.com/<your-username>/comp423-course-notes.git
```
* Replace `<your-username>` with your GitHub username.
* Push your local commits to your GitHub repository:
```
git push --set-upstream origin main
```
!!! question "What does `--set-upstream` do?"
    This command sets up the main branch to track the remote branch so that future pushes and pulls can be done without specifying the branch name.

## Development Container Setup

### Step 1: Configuring development container

* In VS Code, open your `rust-project` directory using File > Open Folder.
* Install the **Dev Containers** extension for VS Code.
* Create a `.devcontainer` directory in the root of your project. Inside, place the following file: `devcontainer.json`. The filepath should be as follows: `.devcontainer/devcontainer.json`.
* Specify the following
    1. `name`: A descriptive name for your dev container.
    2. `image`: We will use the latest version of a Rust environment from Microsoft.
    3. `customizations`: We will install the official `rust-lang.rust-analyzer` extension.

```
{
    "name": "Rust Development Environment",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "extensions": ["rust-lang.rust-analyzer"]
        }
    }
}
```
!!! info "More about `devcontainer.json"
    The `devcontainer.json` file specifies configuration for a consistent development environment using a Docker image.