# Shell

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains the Linux Shell, how commands are executed, different shell types, shell environments, command syntax, pipes, redirection, and why the shell is the primary interface for Linux system administration.

---

# What is a Shell?

A **Shell** is a command-line interpreter that acts as an interface between the user and the Linux kernel.

It accepts user commands, interprets them, and requests the kernel to perform the required operations.

---

# Shell Architecture

```text
User
   │
Terminal
   │
Shell (Bash)
   │
System Calls
   │
Linux Kernel
   │
Hardware
```

---

# Responsibilities of the Shell

| Responsibility           | Description                         |
| ------------------------ | ----------------------------------- |
| Command Interpretation   | Reads and interprets user commands  |
| Program Execution        | Launches applications and utilities |
| Process Creation         | Starts and manages processes        |
| Environment Management   | Maintains environment variables     |
| Input/Output Redirection | Redirects command input and output  |
| Pipelines                | Connects multiple commands together |
| Scripting                | Automates repetitive tasks          |

---

# Terminal vs Shell

| Terminal                                   | Shell               |
| ------------------------------------------ | ------------------- |
| User interface application                 | Command interpreter |
| Displays text                              | Executes commands   |
| Examples: GNOME Terminal, Windows Terminal | Bash, Zsh, Fish     |

---

# Popular Linux Shells

| Shell | Description                    | Common Usage                        |
| ----- | ------------------------------ | ----------------------------------- |
| Bash  | Bourne Again Shell             | Default on most Linux distributions |
| Zsh   | Extended Bash-compatible shell | Developers and power users          |
| Fish  | Friendly Interactive Shell     | Beginner-friendly interactive shell |
| Dash  | Lightweight POSIX shell        | System scripts                      |
| Ksh   | Korn Shell                     | Enterprise Unix systems             |

---

# Basic Command Syntax

General format:

```text
command [options] [arguments]
```

Example:

```bash
ls -la /home
```

| Part    | Meaning  |
| ------- | -------- |
| `ls`    | Command  |
| `-la`   | Options  |
| `/home` | Argument |

---

# Shell Prompt

Example:

```text
alice@server:~/projects$
```

| Component    | Meaning             |
| ------------ | ------------------- |
| `alice`      | Current user        |
| `server`     | Hostname            |
| `~/projects` | Current directory   |
| `$`          | Regular user prompt |
| `#`          | Root user prompt    |

---

# Command Execution Flow

```text
User enters command
        │
Shell parses command
        │
Searches executable using PATH
        │
Creates process
        │
Kernel executes process
        │
Returns output to terminal
```

---

# PATH Environment Variable

The shell searches for executable programs using the `PATH` environment variable.

Example:

```bash
echo $PATH
```

Typical directories:

| Directory        | Purpose                    |
| ---------------- | -------------------------- |
| `/bin`           | Essential commands         |
| `/usr/bin`       | User applications          |
| `/usr/local/bin` | Locally installed software |

---

# Command Types

| Type             | Example              |
| ---------------- | -------------------- |
| Built-in         | `cd`, `pwd`, `echo`  |
| External Command | `ls`, `grep`, `find` |
| Script           | `backup.sh`          |
| Alias            | `ll`                 |

---

# Aliases

Aliases provide shortcuts for frequently used commands.

Example:

```bash
alias ll="ls -lah"
```

View aliases:

```bash
alias
```

Remove an alias:

```bash
unalias ll
```

---

# Environment Variables

| Variable    | Purpose                |
| ----------- | ---------------------- |
| `$HOME`     | User's home directory  |
| `$USER`     | Current user           |
| `$PATH`     | Executable search path |
| `$PWD`      | Current directory      |
| `$SHELL`    | Current shell          |
| `$HOSTNAME` | System hostname        |

Display a variable:

```bash
echo $HOME
```

---

# Command History

| Command    | Purpose                   |
| ---------- | ------------------------- |
| `history`  | Display previous commands |
| `!!`       | Repeat previous command   |
| `!25`      | Execute command number 25 |
| `Ctrl + R` | Search command history    |

---

# Pipes

Pipes pass the output of one command as the input to another.

Syntax:

```bash
command1 | command2
```

Example:

```bash
ps -ef | grep nginx
```

---

# Redirection

## Output Redirection

| Symbol | Purpose          |
| ------ | ---------------- |
| `>`    | Overwrite output |
| `>>`   | Append output    |

Example:

```bash
ls > files.txt
```

---

## Input Redirection

```bash
command < input.txt
```

---

## Error Redirection

| Symbol | Purpose                 |
| ------ | ----------------------- |
| `2>`   | Redirect standard error |
| `2>>`  | Append standard error   |

Example:

```bash
find /root 2> errors.log
```

---

# Wildcards

| Wildcard | Meaning                          |
| -------- | -------------------------------- |
| `*`      | Zero or more characters          |
| `?`      | Single character                 |
| `[abc]`  | Match one character from the set |
| `[0-9]`  | Match any digit                  |

---

# Command Substitution

Execute one command inside another.

Example:

```bash
echo $(date)
```

---

# Exit Status

Every command returns an exit code.

| Exit Code | Meaning |
| --------- | ------- |
| 0         | Success |
| Non-zero  | Failure |

Check the last exit code:

```bash
echo $?
```

---

# Useful Keyboard Shortcuts

| Shortcut   | Action                            |
| ---------- | --------------------------------- |
| `Ctrl + C` | Stop running command              |
| `Ctrl + D` | End input / logout                |
| `Ctrl + L` | Clear terminal                    |
| `Ctrl + A` | Move to beginning of line         |
| `Ctrl + E` | Move to end of line               |
| `Ctrl + R` | Search history                    |
| `Tab`      | Auto-complete command or filename |

---

# Best Practices

| Practice                               | Benefit                              |
| -------------------------------------- | ------------------------------------ |
| Use tab completion                     | Faster and fewer typing errors       |
| Use pipes instead of temporary files   | Cleaner and more efficient workflows |
| Verify commands before execution       | Prevent accidental changes           |
| Use command history for repeated tasks | Improve productivity                 |
| Learn shell shortcuts                  | Increase command-line efficiency     |

---

# Common Mistakes

| Mistake                                                    | Better Practice                                  |
| ---------------------------------------------------------- | ------------------------------------------------ |
| Running commands without understanding them                | Read the manual (`man`) first                    |
| Ignoring exit codes                                        | Check `echo $?` when troubleshooting             |
| Using absolute paths unnecessarily in interactive sessions | Relative paths can improve efficiency            |
| Forgetting quotes around paths with spaces                 | Quote file and directory names containing spaces |

---

# Interview Highlights

| Question                                   | Answer                                                                         |
| ------------------------------------------ | ------------------------------------------------------------------------------ |
| What is a shell?                           | A command interpreter between the user and the Linux kernel.                   |
| Difference between a terminal and a shell? | A terminal provides the interface; the shell interprets and executes commands. |
| What is the `PATH` variable?               | An environment variable listing directories searched for executable programs.  |
| What is a pipe?                            | A mechanism that passes the output of one command to another.                  |
| How do you check if a command succeeded?   | Inspect the exit status using `echo $?`.                                       |

---

# Key Takeaways

| Concept              | Summary                              |
| -------------------- | ------------------------------------ |
| Shell                | Command interpreter                  |
| Terminal             | Interface to the shell               |
| PATH                 | Executable search path               |
| Pipe                 | Connects commands                    |
| Redirection          | Controls input and output            |
| Environment Variable | Stores shell configuration           |
| Exit Status          | Indicates command success or failure |

---

# Related Documents

| Document                 | Purpose                        |
| ------------------------ | ------------------------------ |
| Linux Overview.md        | Linux architecture             |
| File System.md           | Filesystem navigation          |
| Processes.md             | Process creation and execution |
| Bash Scripting.md        | Shell automation               |
| Environment Variables.md | Shell environment              |
| Cheatsheet.md            | Common shell commands          |
