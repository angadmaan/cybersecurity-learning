# Day 15

## Overview

Today's lab introduced **Linux Shell Scripting** and the **Vi text editor**. I learned how to create and edit files using Vi, write basic Bash scripts, use variables, make scripts executable, and automate tasks using conditional statements and loops.

---

# Topics Covered

* Introduction to Vi Editor
* Vi Navigation & Editing Commands
* Creating Shell Scripts
* Shebang (`#!/bin/bash`)
* File Permissions with `chmod`
* Executing Shell Scripts
* Environment Variable (`$PATH`)
* Variables & User Input
* Conditional Statements (`if`)
* While Loops
* For Loops
* Basic Automation

---

# 1. Vi Editor Basics

The **Vi Editor** is one of the most powerful command-line text editors available in Linux.

It operates in two modes:

* **Insert Mode** → Used to type or edit text.
* **Command Mode** → Used for navigation, editing, searching, saving, and quitting.

---

## Common Vi Commands

### Navigation

```bash
h        # Move left
l        # Move right
j        # Move down
k        # Move up
w        # Next word
b        # Previous word
e        # End of word
0        # Beginning of line
$        # End of line
1G       # First line
3G       # Go to line 3
G        # Last line
```

---

### Editing

```bash
i        # Insert before cursor
a        # Append after cursor
o        # Open new line below
O        # Open new line above

x        # Delete character
dw       # Delete word
dd       # Delete line
2dd      # Delete two lines
D        # Delete till end of line

u        # Undo
J        # Join lines
p        # Paste below
P        # Paste above
yw       # Copy word
```

---

### Search & Replace

```bash
/word          # Search forward
?word          # Search backward
n              # Next match

:%s/text//g    # Replace all occurrences
```

---

### Saving & Exiting

```bash
:w      # Save
:q      # Quit
:wq     # Save & Quit
:x      # Save & Exit
:q!     # Quit without saving
```

---

# 2. Creating a Basic Shell Script

A shell script is simply a text file containing Linux commands that execute sequentially.

Example:

```bash
#!/bin/bash

echo "Hello there!"
cal
```

Run using:

```bash
bash sample.sh
```

or make it executable:

```bash
chmod a+x sample.sh
./sample.sh
```

---

# 3. Shebang (`#!/bin/bash`)

Every Bash script should begin with:

```bash
#!/bin/bash
```

This tells Linux to execute the script using the Bash shell.

---

# 4. Making Scripts Executable

View permissions:

```bash
ls -l sample.sh
```

Grant execute permission:

```bash
chmod a+x sample.sh
```

Execute:

```bash
./sample.sh
```

---

# 5. Command Substitution

The output of one command can be embedded inside another.

Example:

```bash
echo "Today is" `date +%A`
```

Output:

```
Today is Tuesday
```

---

# 6. PATH Variable

Linux searches for executable programs using the **PATH** environment variable.

View PATH:

```bash
echo $PATH
```

Move scripts into:

```bash
~/bin
```

Then execute them directly without using `./`.

---

# 7. Variables & User Input

Read input from the user:

```bash
echo "Enter your age"
read age
```

Display variable:

```bash
echo $age
```

---

# 8. Conditional Statements (if)

Example:

```bash
#!/bin/bash

echo "Please enter your age"
read age

if [ $age -lt 16 ]
then
    echo "You are not old enough to drive."
else
    echo "You can drive!"
fi
```

Concepts learned:

* `if`
* `then`
* `else`
* `fi`
* Numeric comparisons using `test`

---

# 9. Using Commands as Conditions

Scripts can execute commands and check whether they succeed or fail.

Example:

```bash
#!/bin/bash

echo "Enter a username:"
read name

if grep $name /etc/passwd > /dev/null
then
    echo "$name exists"
else
    echo "$name does not exist"
fi
```

---

# 10. While Loop

Repeat code until a condition becomes false.

Example:

```bash
while [ $num -le 100 ]
do
    echo "$num is NOT greater than 100."
    read num
done
```

Used for:

* Continuous user input
* Validation
* Repeating tasks

---

# 11. For Loop

Execute commands multiple times.

Example:

```bash
for name in /etc/passwd /etc/hosts /etc/group
do
    wc $name
done
```

---

Generate numbers using `seq`:

```bash
for num in `seq 1 12`
do
    touch test$num
done
```

Creates:

```
test1
test2
...
test12
```

---

# Important Commands Learned

```bash
vi filename
chmod a+x file.sh
bash file.sh
./file.sh

echo $PATH
mv sample.sh bin

read variable

if [ condition ]
then
...
else
...
fi

while [ condition ]
do
...
done

for item in list
do
...
done

grep
wc
touch
seq
```

---

# Key Takeaways

* Learned to use the **Vi Editor** efficiently for editing files.
* Understood the structure of a **Bash shell script**.
* Used **Shebang** to define the script interpreter.
* Made scripts executable using `chmod`.
* Accepted user input using `read`.
* Automated decisions using **if-else conditions**.
* Practiced **while loops** for repeated execution.
* Used **for loops** to automate repetitive tasks.
* Learned how Linux searches executable files using the **PATH** variable.

---
