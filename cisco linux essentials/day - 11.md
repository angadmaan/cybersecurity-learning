# Day 11 – Linux Essentials (File Management & Globbing)

## Overview

Today I learned how Linux handles file management through the command line. The session covered wildcard patterns (globbing), copying files, moving files, creating files and directories, and safely removing files.

One important takeaway is that Linux is **case-sensitive**, meaning:

```bash
hello.txt
HELLO.txt
Hello.txt
```

are considered three different files.

---

# 1. Globbing (Wildcards)

Globbing allows us to work with multiple files using patterns.

## Asterisk (*)

Matches zero or more characters.

### Example

```bash
echo /etc/t*
```

Lists files beginning with **t**.

---

## Question Mark (?)

Matches exactly one character.

### Example

```bash
echo /etc/*.???
```

Lists files with a three-letter extension.

---

## Square Brackets ([])

Match specific characters or ranges.

### Example

```bash
echo /etc/[a-d]*
```

Lists files starting with letters from **a to d**.

---

## Negation (![ ])

Exclude characters from matching.

### Example

```bash
echo /etc/[!a-t]*
```

Lists files not starting with letters between **a and t**.

---

# 2. Listing Files with Globs

When using wildcards with `ls`, use the `-d` option to display directory names instead of their contents.

### Example

```bash
ls -d /etc/x*
```

Output:

```bash
/etc/xdg
```

---

# 3. Copying Files

The `cp` command copies files.

### Basic Copy

```bash
cp /etc/hosts ~
```

Copy hosts file to the home directory.

---

### Verbose Copy

```bash
cp -v /etc/hosts ~
```

Shows copy progress.

---

### Interactive Mode

```bash
cp -i source destination
```

Prompts before overwriting files.

---

### No Clobber

```bash
cp -n source destination
```

Prevents overwriting existing files.

---

### Copy Directories

```bash
cp -r source_directory destination_directory
```

Copies directories recursively.

---

# 4. Moving & Renaming Files

The `mv` command is used for both moving and renaming.

### Move File

```bash
mv hosts Videos
```

Move file into another directory.

---

### Rename File

```bash
mv oldfile.txt newfile.txt
```

Rename a file.

---

### Useful Options

```bash
mv -i
```

Interactive mode.

```bash
mv -n
```

Do not overwrite.

```bash
mv -v
```

Verbose output.

---

# 5. Creating Files

Create an empty file using:

```bash
touch sample.txt
```

Useful for creating placeholders or testing.

---

# 6. Removing Files

Delete a file:

```bash
rm filename
```

---

### Interactive Delete

```bash
rm -i *.txt
```

Prompts before deleting.

---

# 7. Removing Directories

Delete a directory and its contents:

```bash
rm -r directory_name
```

---

Delete an empty directory:

```bash
rmdir directory_name
```

---

# 8. Creating Directories

Create a new directory:

```bash
mkdir test
```

---

# Commands Learned Today

```bash
cp
mv
touch
rm
rmdir
mkdir
ls -d
cp -r
cp -i
cp -n
mv -i
mv -n
rm -i
```

---

# Key Takeaway

Today's lesson focused on practical Linux file management. I learned how to use wildcards (globbing) to work with multiple files efficiently and how to safely copy, move, create, and remove files and directories using the Linux command line.
