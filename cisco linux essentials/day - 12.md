# Day 12

## 📅 Overview

In Day 12 of Cisco Linux Essentials, I learned how Linux handles file and directory management through the command line. The lab focused on using **globbing (wildcards)**, copying files, moving files, renaming files, and creating or deleting directories.

These are fundamental Linux skills that every system administrator, developer, and cybersecurity professional should understand.

---

# 🎯 Topics Covered

- Globbing (Wildcards)
- Copying Files & Directories
- Moving & Renaming Files
- Creating Files
- Creating Directories
- Deleting Files & Directories
- Recursive Operations
- Preserving File Attributes

---

# 🌟 Globbing (Wildcards)

Globbing allows Linux users to match filenames using patterns instead of typing full names.

## Asterisk `*`

Matches **zero or more characters**.

### Examples

```bash
echo *
```

Displays all files and directories in the current location.

```bash
echo D*
```

Displays files beginning with **D**.

```bash
echo *s
```

Displays files ending with **s**.

```bash
echo D*n*s
```

Displays filenames beginning with **D**, containing **n**, and ending with **s**.

---

## Question Mark `?`

Matches **exactly one character**.

### Examples

```bash
echo ??????
```

Displays filenames that are exactly six characters long.

```bash
echo D????????
```

Displays filenames beginning with **D** and containing exactly nine characters.

```bash
echo ?????*s
```

Displays filenames with at least six characters and ending with **s**.

---

## Square Brackets `[ ]`

Used to match specific characters or character ranges.

### Examples

```bash
echo [DP]*
```

Matches filenames starting with **D** or **P**.

```bash
echo [!DP]*
```

Matches filenames that do **not** start with **D** or **P**.

```bash
echo [D-P]*
```

Matches filenames beginning with characters between **D** and **P**.

```bash
echo [!D-P]*
```

Matches filenames not beginning with letters between **D** and **P**.

---

# 📂 Copying Files

The `cp` command is used to create copies of files and directories.

## Basic Copy

```bash
cp /etc/hosts hosts
```

Creates a copy of the hosts file in the current directory.

---

## Verbose Copy

```bash
cp -v /etc/hosts hosts
```

Shows source and destination during the copy process.

Example:

```bash
'/etc/hosts' -> 'hosts'
```

---

## Copy to Current Directory

```bash
cp -v /etc/hosts .
```

The dot (`.`) represents the current directory.

---

## Preserve File Attributes

```bash
cp -p hosts /home/sysadmin
```

Preserves:

- Timestamps
- Permissions
- File attributes

---

## Copy with a Different Name

```bash
cp hosts newname
```

Creates a duplicate file with a new filename.

---

# 📁 Copying Directories

To copy an entire directory structure:

```bash
mkdir Myetc

cp -R /etc/udev Myetc
```

The `-R` option copies directories recursively.

### View Copied Contents

```bash
ls -lR Myetc
```

Displays all files and subdirectories.

---

# 🚚 Moving & Renaming Files

The `mv` command is used for both moving and renaming.

## Rename a File

```bash
touch premove

mv premove postmove
```

The file remains in the same location but receives a new name.

---

## Move a File

```bash
mv file.txt Documents/
```

Moves the file into another directory.

---

# 📄 Creating Files

Create an empty file using:

```bash
touch sample.txt
```

Commonly used for:

- Testing
- Placeholders
- Quick file creation

---

# 🗂️ Creating Directories

Create a new directory:

```bash
mkdir test
```

Verify:

```bash
ls
```

---

# 🗑️ Removing Files

Delete a file:

```bash
rm sample.txt
```

Delete multiple files:

```bash
rm file1.txt file2.txt
```

⚠️ Linux permanently deletes files using `rm`.

---

# 🗑️ Removing Directories

Delete a directory and all contents:

```bash
rm -r Myetc
```

The `-r` option removes files and subdirectories recursively.

---

## Remove Empty Directory

```bash
rmdir empty_directory
```

Works only if the directory contains no files.

---

# 📝 Commands Practiced

```bash
echo *

echo D*

echo *s

echo D*n*s

echo ??????

echo D????????

echo [DP]*

echo [!DP]*

echo [D-P]*

echo [!D-P]*

cp /etc/hosts hosts

cp -v /etc/hosts hosts

cp -v /etc/hosts .

cp -p hosts /home/sysadmin

cp hosts newname

mkdir Myetc

cp -R /etc/udev Myetc

ls -lR Myetc

rm -r Myetc

touch premove

mv premove postmove

mkdir test

rm sample.txt

rmdir empty_directory
```

---

# 🎯 Key Takeaways

- Learned how Linux uses globbing patterns to match filenames efficiently.
- Practiced copying files while preserving permissions and timestamps.
- Understood recursive directory copying using `cp -R`.
- Learned the difference between moving and renaming files.
- Created and removed files/directories using command-line tools.
- Gained confidence navigating and managing the Linux filesystem.

---
