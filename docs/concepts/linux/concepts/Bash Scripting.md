# Bash Scripting

**Document Version:** 1.0
**Sprint:** 3 — Linux Fundamentals

---

# Purpose

This document explains Bash scripting, the standard scripting language used on Linux systems. It covers script structure, variables, control flow, functions, input handling, file operations, process management, error handling, debugging, and scripting best practices.

Bash scripting is a core skill for Linux administration, DevOps, cloud automation, CI/CD pipelines, and infrastructure management.

---

# What is Bash Scripting?

A Bash script is a text file containing a sequence of shell commands that are executed automatically.

Instead of manually running commands one by one, a script allows repetitive tasks to be automated.

Typical use cases include:

* System administration
* Backups
* Deployments
* Monitoring
* Log analysis
* Automation
* CI/CD pipelines

---

# Why Bash Scripting Matters

Bash scripting enables:

* Automation of repetitive tasks
* Consistent execution
* Reduced human error
* Infrastructure management
* Faster troubleshooting
* Integration with Linux utilities

---

# Script Execution Flow

```text
User
 │
 ▼
Bash Script
 │
 ▼
Bash Interpreter
 │
 ▼
Linux Kernel
 │
 ▼
Commands Executed
```

---

# Script Structure

A typical Bash script consists of:

```bash
#!/bin/bash

echo "Hello World"
```

The first line is called the **shebang** and specifies the interpreter.

---

# Creating a Script

Create a file:

```bash
touch hello.sh
```

Edit the script:

```bash
nano hello.sh
```

Make it executable:

```bash
chmod +x hello.sh
```

Run the script:

```bash
./hello.sh
```

---

# Variables

Declare a variable:

```bash
NAME="Linux"
```

Use a variable:

```bash
echo $NAME
```

---

# Command Substitution

Capture command output:

```bash
DATE=$(date)
```

or

```bash
HOST=$(hostname)
```

---

# User Input

Read input:

```bash
read USERNAME
```

Prompt for input:

```bash
read -p "Enter your name: " NAME
```

---

# Positional Parameters

| Parameter | Meaning                         |
| --------- | ------------------------------- |
| `$0`      | Script name                     |
| `$1`      | First argument                  |
| `$2`      | Second argument                 |
| `$#`      | Number of arguments             |
| `$@`      | All arguments                   |
| `$?`      | Exit status of previous command |
| `$$`      | Current process ID              |

Example:

```bash
./backup.sh /home
```

Inside the script:

```bash
echo $1
```

Outputs:

```text
/home
```

---

# Exit Status

Linux commands return an exit status.

| Exit Code | Meaning            |
| --------- | ------------------ |
| 0         | Success            |
| Non-zero  | Failure or warning |

Example:

```bash
if [ $? -eq 0 ]
then
    echo "Success"
fi
```

---

# Conditional Statements

```bash
if [ -f file.txt ]
then
    echo "Exists"
fi
```

---

# if-else

```bash
if [ "$USER" = "root" ]
then
    echo "Administrator"
else
    echo "Standard User"
fi
```

---

# Case Statement

```bash
case $1 in
    start)
        echo "Starting"
        ;;
    stop)
        echo "Stopping"
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

---

# Loops

## for Loop

```bash
for FILE in *.txt
do
    echo $FILE
done
```

---

## while Loop

```bash
COUNT=1

while [ $COUNT -le 5 ]
do
    echo $COUNT
    COUNT=$((COUNT+1))
done
```

---

# Functions

```bash
greet() {
    echo "Hello $1"
}

greet Alice
```

Benefits:

* Reusability
* Readability
* Easier maintenance

---

# File Tests

| Test | Description       |
| ---- | ----------------- |
| `-f` | File exists       |
| `-d` | Directory exists  |
| `-r` | Readable          |
| `-w` | Writable          |
| `-x` | Executable        |
| `-s` | File is not empty |

---

# String Tests

| Test | Description      |
| ---- | ---------------- |
| `-z` | Empty string     |
| `-n` | Non-empty string |
| `=`  | Equal            |
| `!=` | Not equal        |

---

# Numeric Comparisons

| Operator | Meaning               |
| -------- | --------------------- |
| `-eq`    | Equal                 |
| `-ne`    | Not equal             |
| `-gt`    | Greater than          |
| `-lt`    | Less than             |
| `-ge`    | Greater than or equal |
| `-le`    | Less than or equal    |

---

# Useful Commands in Scripts

| Command | Purpose                 |
| ------- | ----------------------- |
| `grep`  | Search text             |
| `awk`   | Process structured text |
| `sed`   | Stream editing          |
| `cut`   | Extract columns         |
| `sort`  | Sort data               |
| `uniq`  | Remove duplicates       |
| `find`  | Locate files            |
| `xargs` | Build command arguments |

---

# Debugging

Run with debugging enabled:

```bash
bash -x script.sh
```

Enable tracing inside a script:

```bash
set -x
```

Disable tracing:

```bash
set +x
```

---

# Error Handling

Stop execution on the first error:

```bash
set -e
```

Treat unset variables as errors:

```bash
set -u
```

Fail pipelines if any command fails:

```bash
set -o pipefail
```

A common production combination:

```bash
set -euo pipefail
```

---

# Best Practices

| Practice                      | Benefit                        |
| ----------------------------- | ------------------------------ |
| Use meaningful variable names | Improve readability            |
| Quote variables               | Prevent word splitting         |
| Check command exit codes      | Handle failures gracefully     |
| Write reusable functions      | Reduce duplication             |
| Use comments where necessary  | Improve maintainability        |
| Validate user input           | Prevent unexpected behavior    |
| Use `shellcheck` for linting  | Detect common scripting issues |

---

# Common Mistakes

| Mistake                                    | Better Practice                    |
| ------------------------------------------ | ---------------------------------- |
| Forgetting to quote variables              | Use `"$VAR"`                       |
| Ignoring exit codes                        | Check `$?` or use `set -e`         |
| Hardcoding file paths                      | Use variables or arguments         |
| Running scripts without execute permission | Use `chmod +x`                     |
| Writing long scripts without functions     | Break code into reusable functions |

---

# Interview Highlights

| Question                                    | Answer                                                                |
| ------------------------------------------- | --------------------------------------------------------------------- |
| What is a Bash script?                      | A file containing shell commands executed by the Bash interpreter.    |
| What is a shebang?                          | The first line (`#!/bin/bash`) that specifies the script interpreter. |
| What does `$?` represent?                   | The exit status of the last executed command.                         |
| How do you pass arguments to a Bash script? | As positional parameters (`$1`, `$2`, etc.).                          |
| Why use `set -euo pipefail`?                | To make scripts fail fast and handle errors more reliably.            |

---

# Key Takeaways

| Concept             | Summary                                  |
| ------------------- | ---------------------------------------- |
| Bash Script         | Automates Linux commands                 |
| Shebang             | Specifies the interpreter                |
| Variables           | Store reusable values                    |
| Functions           | Organize reusable logic                  |
| Loops               | Repeat tasks                             |
| Conditionals        | Make decisions                           |
| Exit Status         | Indicates command success or failure     |
| `set -euo pipefail` | Recommended error-handling configuration |

---

# Related Documents

| Document                 | Purpose                             |
| ------------------------ | ----------------------------------- |
| Shell.md                 | Bash shell fundamentals             |
| Environment Variables.md | Variables used by scripts           |
| Scheduling.md            | Running scripts automatically       |
| Logging.md               | Logging script output               |
| Package Management.md    | Installing tools used in scripts    |
| Linux for DevOps.md      | Bash automation in DevOps workflows |
