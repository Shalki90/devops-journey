# Environment Variables

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains environment variables in Linux, how they are created, inherited, modified, and used by applications. It covers shell variables, environment variables, login and non-login shells, configuration files, the `PATH` variable, and best practices.

Understanding environment variables is essential for Linux administration, software development, DevOps, containers, CI/CD pipelines, and cloud infrastructure.

---

# What are Environment Variables?

Environment variables are **name-value pairs** that store configuration information for processes.

They allow applications and the operating system to share configuration without modifying source code.

Example:

```text
USER=ubuntu
HOME=/home/ubuntu
PATH=/usr/local/bin:/usr/bin:/bin
```

---

# Why Environment Variables Matter

Environment variables allow applications to:

* Locate executables
* Store configuration
* Pass runtime settings
* Store credentials (temporarily)
* Configure development environments
* Control application behavior

---

# Architecture

```text
Login
   │
Shell Starts
   │
Read Configuration Files
   │
Environment Variables Loaded
   │
Applications Started
   │
Child Processes Inherit Variables
```

---

# Variable Types

| Type                 | Description                          |
| -------------------- | ------------------------------------ |
| Shell Variable       | Exists only within the current shell |
| Environment Variable | Inherited by child processes         |
| System Variable      | Available system-wide                |
| User Variable        | Specific to one user                 |

---

# Shell Variables vs Environment Variables

| Shell Variable         | Environment Variable         |
| ---------------------- | ---------------------------- |
| Local to current shell | Available to child processes |
| Not exported           | Exported using `export`      |
| Temporary              | Can be made persistent       |

---

# Viewing Variables

Display all environment variables:

```bash
printenv
```

or

```bash
env
```

Display a specific variable:

```bash
echo $HOME
```

---

# Creating Variables

Create a shell variable:

```bash
EDITOR=vim
```

Create an environment variable:

```bash
export EDITOR=vim
```

---

# Removing Variables

```bash
unset EDITOR
```

---

# Variable Inheritance

```text
Parent Shell
     │
export VAR=value
     │
───────────────
│             │
Child A     Child B
│             │
VAR=value   VAR=value
```

Only exported variables are inherited by child processes.

---

# Common Environment Variables

| Variable   | Purpose                   |
| ---------- | ------------------------- |
| `HOME`     | User's home directory     |
| `USER`     | Current username          |
| `PWD`      | Current working directory |
| `PATH`     | Executable search path    |
| `SHELL`    | Current shell             |
| `HOSTNAME` | System hostname           |
| `LANG`     | Language and locale       |
| `TERM`     | Terminal type             |

---

# The PATH Variable

`PATH` tells Linux where to search for executable programs.

Example:

```text
/usr/local/bin:/usr/bin:/bin
```

When a command is executed:

```bash
git
```

Linux searches each directory in `PATH` until it finds the executable.

---

# Viewing PATH

```bash
echo $PATH
```

---

# Adding to PATH (Current Session)

```bash
export PATH=$PATH:/opt/tools/bin
```

---

# Persistent Environment Variables

Configuration files are read when a shell starts.

| File               | Purpose                               |
| ------------------ | ------------------------------------- |
| `/etc/environment` | System-wide environment variables     |
| `/etc/profile`     | System-wide login shell configuration |
| `~/.profile`       | User login shell                      |
| `~/.bash_profile`  | Bash login shell                      |
| `~/.bashrc`        | Interactive Bash shell                |
| `~/.zshrc`         | Zsh configuration                     |

---

# Login vs Non-Login Shells

| Login Shell               | Non-Login Shell                |
| ------------------------- | ------------------------------ |
| Started after user login  | Started from an existing shell |
| Reads login configuration | Reads shell configuration      |
| Loads user profile        | Loads `.bashrc` or equivalent  |

---

# Environment Variables in Scripts

Example:

```bash
#!/bin/bash

echo "Current User: $USER"
echo "Home Directory: $HOME"
```

---

# Temporary Variables

Assign a variable for a single command:

```bash
EDITOR=nano crontab -e
```

The variable exists only for that command.

---

# Viewing Process Environment

View the environment of a running process:

```bash
cat /proc/<PID>/environ
```

---

# Common Commands

| Command     | Purpose                       |
| ----------- | ----------------------------- |
| `env`       | Display environment variables |
| `printenv`  | Display environment variables |
| `echo $VAR` | Display a variable            |
| `export`    | Export a variable             |
| `unset`     | Remove a variable             |
| `which`     | Locate executable in `PATH`   |

---

# Environment Variables in DevOps

Environment variables are widely used for:

* Docker containers
* Kubernetes ConfigMaps
* Kubernetes Secrets
* Terraform variables
* AWS CLI credentials
* Azure CLI configuration
* Google Cloud SDK
* CI/CD pipelines
* Jenkins
* GitHub Actions
* GitLab CI

Examples:

```text
AWS_REGION
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY

JAVA_HOME

KUBECONFIG

DOCKER_HOST

TF_VAR_region
```

---

# Common Troubleshooting

| Problem                    | Investigation        | Resolution                 |
| -------------------------- | -------------------- | -------------------------- |
| Command not found          | Check `PATH`         | Add correct directory      |
| Variable missing           | `printenv`           | Export the variable        |
| Script behaves differently | Compare environments | Verify shell configuration |
| Configuration not loaded   | Check startup files  | Reload or restart shell    |
| Wrong executable used      | `which command`      | Correct `PATH` order       |

---

# Best Practices

| Practice                                                  | Benefit                     |
| --------------------------------------------------------- | --------------------------- |
| Use descriptive variable names                            | Improve readability         |
| Store user-specific variables in user configuration files | Avoid affecting other users |
| Keep `PATH` organized                                     | Prevent conflicts           |
| Use environment variables for configuration               | Avoid hardcoding values     |
| Use secrets managers for production credentials           | Improve security            |

---

# Common Mistakes

| Mistake                                               | Better Practice                                  |
| ----------------------------------------------------- | ------------------------------------------------ |
| Hardcoding credentials in scripts                     | Use environment variables or secrets managers    |
| Overwriting `PATH` accidentally                       | Append to `PATH` instead of replacing it         |
| Forgetting `export`                                   | Export variables needed by child processes       |
| Storing sensitive values in shared shell files        | Limit access and use dedicated secret management |
| Assuming all shells load the same configuration files | Understand login vs non-login shell behavior     |

---

# Interview Highlights

| Question                                                                     | Answer                                                                                                               |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| What is an environment variable?                                             | A name-value pair that provides configuration to processes.                                                          |
| What is the difference between a shell variable and an environment variable? | Environment variables are exported and inherited by child processes; shell variables are local to the current shell. |
| What is `PATH`?                                                              | An environment variable that specifies where Linux searches for executable programs.                                 |
| How do you make an environment variable persistent?                          | Define it in the appropriate shell or system configuration file.                                                     |
| How do child processes receive environment variables?                        | Through inheritance from the parent process when variables are exported.                                             |

---

# Key Takeaways

| Concept              | Summary                                      |
| -------------------- | -------------------------------------------- |
| Environment Variable | Configuration available to processes         |
| Shell Variable       | Local variable within a shell                |
| `export`             | Makes variables available to child processes |
| `PATH`               | Search path for executables                  |
| Login Shell          | Reads login configuration                    |
| Non-Login Shell      | Reads interactive shell configuration        |
| `printenv`           | Displays environment variables               |
| `unset`              | Removes a variable                           |

---

# Related Documents

| Document              | Purpose                                                         |
| --------------------- | --------------------------------------------------------------- |
| Shell.md              | Shell behavior and command execution                            |
| Bash Scripting.md     | Using variables in scripts                                      |
| Users and Groups.md   | User-specific environments                                      |
| Package Management.md | Executable locations and `PATH`                                 |
| Linux for DevOps.md   | Environment variables in containers, CI/CD, and cloud platforms |
