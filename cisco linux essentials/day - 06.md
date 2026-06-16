# Day 6

## Overview

Today I learned how the Linux Command Line Interface (CLI) works behind the scenes. I explored the Bash shell, command structure, command history, variables, aliases, functions, quoting methods, and control operators that help automate and simplify tasks.

---

## Why Learn the Command Line?

The Linux CLI provides:

* Faster system interaction
* Greater control over the operating system
* Automation through scripting
* Consistent experience across Linux distributions

Learning the CLI allows users to work efficiently on almost any Linux system.

---

## The Bash Shell

The shell acts as an interpreter between the user and the operating system.

### Responsibilities

* Accept user commands
* Interpret instructions
* Execute commands
* Display output and errors

### Bash Features

* Command history
* Aliases
* Variables
* Scripting support
* Functions

Example Prompt:

```bash
sysadmin@localhost:~$
```

Components:

* Username: `sysadmin`
* Hostname: `localhost`
* Current Directory: `~` (Home Directory)

---

## Linux Command Structure

General format:

```bash
command [options] [arguments]
```

Example:

```bash
ls -lh Documents
```

Where:

* `ls` → command
* `-lh` → options
* `Documents` → argument

---

## Arguments

Arguments specify what the command should act upon.

Example:

```bash
ls /etc
```

The directory `/etc` is the argument.

---

## Options

Options modify command behavior.

Examples:

```bash
ls -l
ls -r
ls -lh
```

Common Option Types:

* Short options: `-l`
* Long options: `--human-readable`

---

## Command History

Linux stores previously executed commands.

Useful Commands:

```bash
history
```

Execute previous commands:

```bash
!!
```

Run a command from history:

```bash
!5
```

Benefits:

* Saves time
* Reduces repetitive typing
* Improves productivity

---

## Variables

Variables store information temporarily.

### Local Variables

Available only in the current shell.

```bash
name="Angad"
echo $name
```

### Environment Variables

Available system-wide.

Examples:

```bash
HOME
PATH
HISTSIZE
```

Display a variable:

```bash
echo $PATH
```

Export a variable:

```bash
export variable=value
```

Remove a variable:

```bash
unset variable
```

---

## PATH Variable

The PATH variable tells Bash where to search for executable commands.

Display PATH:

```bash
echo $PATH
```

Example:

```bash
/usr/bin
/bin
/usr/local/bin
```

If a command is not found inside PATH directories, Linux returns:

```bash
command not found
```

---

## Command Types

### Internal Commands

Built directly into Bash.

Examples:

```bash
cd
echo
history
```

Check type:

```bash
type cd
```

---

### External Commands

Stored as executable files.

Examples:

```bash
ls
cal
ping
```

Find location:

```bash
which ls
```

---

## Aliases

Aliases create shortcuts for longer commands.

Example:

```bash
alias ll="ls -alF"
```

Usage:

```bash
ll
```

Benefits:

* Faster typing
* Improved productivity

---

## Functions

Functions combine multiple commands into a reusable block.

Example:

```bash
my_report() {
    date
    ls
}
```

Run:

```bash
my_report
```

Benefits:

* Automation
* Reusability
* Simplified workflows

---

## Quoting in Bash

### Double Quotes

Allow variable expansion.

```bash
echo "Home is $HOME"
```

---

### Single Quotes

Treat everything literally.

```bash
echo '$HOME'
```

---

### Backslash

Escapes special characters.

```bash
echo \$100
```

Output:

```bash
$100
```

---

### Backticks (Command Substitution)

Execute commands inside commands.

```bash
echo Today is `date`
```

---

## Control Operators

### Semicolon (;)

Runs commands sequentially.

```bash
command1; command2
```

---

### Double Ampersand (&&)

Runs second command only if first succeeds.

```bash
command1 && command2
```

---

### Double Pipe (||)

Runs second command only if first fails.

```bash
command1 || command2
```

---

## Key Takeaways

* Learned how Bash interprets commands.
* Understood command structure using commands, options, and arguments.
* Used command history to improve efficiency.
* Worked with local and environment variables.
* Learned the importance of the PATH variable.
* Explored aliases and functions for automation.
* Practiced different quoting methods.
* Used control operators to combine commands logically.

---

## Conclusion

This chapter introduced the core concepts of Bash and the Linux command line environment. Understanding shells, variables, aliases, functions, and command execution is essential for Linux administration, scripting, automation, and cybersecurity workflows.
