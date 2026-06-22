# Day 14

## 📖 Overview

In this lab, I explored how Linux handles text processing through **redirection, pipes, pagers, and regular expressions**. These concepts are fundamental for Linux administration, scripting, log analysis, and cybersecurity.

### 🎯 Objectives

* Learn how to redirect standard input, output, and error streams
* Understand and use pipes (`|`)
* View large files efficiently with `more` and `less`
* Use `head` and `tail` to extract specific portions of files
* Search and filter text using `grep` and regular expressions

---

# 🔄 Understanding Linux Streams

Linux commands communicate using three standard streams:

| Stream | Description     | File Descriptor |
| ------ | --------------- | --------------- |
| stdin  | Standard Input  | 0               |
| stdout | Standard Output | 1               |
| stderr | Standard Error  | 2               |

---

# ➡️ Redirecting Output

### Display output normally

```bash
echo "Hello World"
```

### Redirect output to a file

```bash
echo "Hello World" > mymessage
cat mymessage
```

Output:

```text
Hello World
```

⚠️ Using `>` overwrites the existing contents of a file.

---

# ➕ Appending to a File

Instead of overwriting:

```bash
echo "How are you?" >> mymessage
cat mymessage
```

Output:

```text
Greetings
How are you?
```

✅ `>>` appends data while preserving existing content.

---

# ⚠️ Redirecting Errors (stderr)

Example:

```bash
find /etc -name hosts
```

Output:

```text
/etc/hosts
Permission denied
```

Save error messages separately:

```bash
find /etc -name hosts 2> err.txt
cat err.txt
```

Output:

```text
Permission denied
```

---

# 📂 Separate stdout and stderr

```bash
find /etc -name hosts > std.out 2> std.err
```

View results:

```bash
cat std.out
cat std.err
```

---

# 🔗 Redirect Both stdout and stderr

```bash
find /etc -name hosts > find.out 2>&1
cat find.out
```

The `2>&1` syntax sends stderr to the same destination as stdout.

---

# ⌨️ Working with Standard Input (stdin)

Convert typed text to uppercase:

```bash
tr a-z A-Z
```

Example:

```text
hello linux
HELLO LINUX
```

Stop input with:

```text
Ctrl + D
```

---

# 📄 Redirect stdin from a File

```bash
tr a-z A-Z < myfile
```

This uses file contents as input instead of the keyboard.

---

# 🚰 Pipes ( | )

Pipes send the output of one command directly into another.

### Syntax

```bash
command1 | command2
```

### Example

```bash
ls -l /etc | more
```

Display large output page by page.

---

# 🔥 Chaining Multiple Commands

```bash
cut -d: -f1 /etc/passwd | sort | more
```

### Breakdown

```text
cut   → Extract usernames
sort  → Sort alphabetically
more  → Display page by page
```

---

# 📚 Viewing Large Files

## Using cat

```bash
cat /etc/passwd
```

Displays the entire file.

---

## Using more

```bash
more /etc/passwd
```

Useful controls:

```text
Space → Next page
q     → Quit
h     → Help
```

---

## Using less

```bash
less /etc/passwd
```

Search:

```text
/bin
```

Navigation:

```text
n → Next match
N → Previous match
q → Quit
```

💡 `less` provides more advanced navigation than `more`.

---

# 📌 Using head

Display first 10 lines:

```bash
head /etc/passwd
```

Display first 2 lines:

```bash
head -2 /etc/passwd
```

Exclude the last 20 lines:

```bash
head -n -20 /etc/passwd
```

---

# 📌 Using tail

Display last 10 lines:

```bash
tail /etc/passwd
```

Display last 5 entries:

```bash
ls /etc | tail -5
```

---

# 🔎 Introduction to Regular Expressions

Regular Expressions (Regex) are patterns used to search text efficiently.

Commands used:

```bash
grep
grep -E
egrep
```

---

# 🔍 Basic grep Searches

Search for sshd:

```bash
grep sshd passwd
```

Output:

```text
sshd:x:106:65534::/run/sshd:/usr/sbin/nologin
```

---

Search for root:

```bash
grep root passwd
```

Returns every occurrence of the word root.

---

# 🎯 Match Beginning of Line (^)

```bash
grep '^root' passwd
```

Output:

```text
root:x:0:0:root:/root:/bin/bash
```

Only lines starting with `root` are matched.

---

# 🎯 Match End of Line ($)

```bash
grep 'sync$' passwd
```

Matches lines ending with `sync`.

---

# 🎯 Wildcard Character (.)

```bash
grep '.y' passwd
```

Matches:

```text
sys
proxy
nobody
syslog
```

`.` matches any single character.

---

# 🎯 Alternation Operator ( | )

Basic grep:

```bash
grep 'sshd|root|operator' passwd
```

❌ Does not work as expected.

Use extended regex:

```bash
grep -E 'sshd|root|operator' passwd
```

Output:

```text
root
sshd
operator
```

---

# 🎯 Grouping with Parentheses

```bash
egrep 'no(b|n)' passwd
```

Matches:

```text
nobody
nonexistent
```

---

# 🎯 Character Classes [ ]

Match any digit:

```bash
grep '[0-9]' passwd
```

---

Match a sequence of three digits:

```bash
grep -E '[0-9]{3}' passwd
```

Examples:

```text
100
101
102
103
1000
1001
```

---

# 🧠 Commands Learned

```bash
echo
cat
find
tr
more
less
head
tail
cut
sort
grep
grep -E
egrep
```

---

# 🚀 Key Takeaways

✅ Standard Input (stdin)

✅ Standard Output (stdout)

✅ Standard Error (stderr)

✅ Output Redirection (`>`)

✅ Append Redirection (`>>`)

✅ Error Redirection (`2>`)

✅ Combined Redirection (`2>&1`)

✅ Pipes (`|`)

✅ Paging Output (`more`, `less`)

✅ File Preview (`head`, `tail`)

✅ Text Filtering

✅ Regular Expressions

✅ Pattern Matching using `grep`

---

## 💡 Reflection

This lab showed me that Linux becomes truly powerful when commands are combined together.

A simple command like:

```bash
cut -d: -f1 /etc/passwd | sort | more
```

demonstrates how small tools can work together to process and organize data efficiently.

Understanding redirection, pipes, and regular expressions is an essential skill for Linux administration, automation, and cybersecurity.
