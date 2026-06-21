# Day 13

## 📅 Overview

Day 13 focused on one of the most important Linux administration skills: **archiving and compression**.

I learned how to create backups, combine multiple files into a single archive, compress large files to save storage space, and extract archived data when needed.

The lab covered several popular Linux utilities including:

- `tar`
- `gzip`
- `bzip2`
- `xz`
- `zip`
- `unzip`

These tools are commonly used by Linux administrators, developers, and cybersecurity professionals for backups, data transfer, and storage optimization.

---

# 🎯 Topics Covered

- Creating TAR archives
- Viewing archive contents
- Extracting archives
- Gzip Compression
- Bzip2 Compression
- XZ Compression
- ZIP Archives
- Recursive Directory Compression
- Backup Management

---

# 📦 TAR (Tape Archive)

The `tar` command combines multiple files and directories into a single archive file.

## Create a TAR Archive

```bash
mkdir mybackups

tar -cvf mybackups/udev.tar /etc/udev
```

### Options Used

| Option | Meaning |
|----------|----------|
| `-c` | Create archive |
| `-v` | Verbose output |
| `-f` | Specify archive filename |

---

## View Archive Contents

```bash
tar -tvf mybackups/udev.tar
```

This displays:

- Files
- Directories
- Permissions
- Ownership
- Timestamps

without extracting the archive.

---

## Add Files to Existing Archive

```bash
tar -rvf udev.tar /etc/hosts
```

The `-r` option appends new files to an existing archive.

---

# 🗜️ Compressed TAR Archives

TAR archives can be compressed using Gzip.

## Create Compressed TAR Archive

```bash
tar -zcvf mybackups/udev.tar.gz /etc/udev
```

### Additional Option

| Option | Meaning |
|----------|----------|
| `-z` | Compress using Gzip |

---

## Benefits

- Smaller file size
- Faster transfers
- Easier backup storage

Example:

```text
udev.tar      → 10 KB
udev.tar.gz   → 1.2 KB
```

---

# 📂 Extract TAR Archives

## Extract Archive

```bash
tar -xvf udev.tar.gz
```

### Option Used

| Option | Meaning |
|----------|----------|
| `-x` | Extract files |

Files are restored into the current working directory.

---

# 🗜️ Gzip Compression

Gzip compresses a single file and replaces the original.

## Compress File

```bash
cp /usr/share/dict/words .

gzip words
```

Result:

```bash
words.gz
```

---

## Decompress File

```bash
gunzip words.gz
```

Result:

```bash
words
```

---

## Key Observation

Example file sizes:

```text
Original: 971,578 bytes

Compressed: 259,983 bytes
```

Gzip significantly reduces storage usage.

---

# 🗜️ Bzip2 Compression

Bzip2 works similarly to Gzip but uses a different compression algorithm.

## Compress

```bash
bzip2 words
```

Result:

```bash
words.bz2
```

---

## Decompress

```bash
bunzip2 words.bz2
```

Result:

```bash
words
```

---

## Example Compression

```text
Original: 971,578 bytes

Compressed: 345,560 bytes
```

---

# 🗜️ XZ Compression

XZ generally provides stronger compression than Gzip and Bzip2.

## Compress

```bash
xz words
```

Result:

```bash
words.xz
```

---

## Decompress

```bash
unxz words.xz
```

Result:

```bash
words
```

---

## Example Compression

```text
Original: 971,578 bytes

Compressed: 198,756 bytes
```

Among all tested formats, XZ achieved the smallest file size.

---

# 📦 ZIP Archives

ZIP archives are widely supported across Linux, Windows, and macOS.

Unlike Gzip, ZIP preserves the original file.

---

## Compress a File

```bash
zip words.zip words
```

Result:

```bash
words.zip
```

---

## Compress a Directory

```bash
zip -r udev.zip /etc/udev
```

### Option Used

| Option | Meaning |
|----------|----------|
| `-r` | Recursive compression |

---

## View ZIP Contents

```bash
unzip -l udev.zip
```

Displays all files stored inside the archive.

---

## Extract ZIP Archive

```bash
unzip udev.zip
```

Files are restored to the current directory.

---

# 📊 Compression Comparison

| Format | Example Size |
|----------|------------|
| Original | 971,578 bytes |
| Gzip (.gz) | 259,983 bytes |
| Bzip2 (.bz2) | 345,560 bytes |
| XZ (.xz) | 198,756 bytes |
| ZIP (.zip) | 260,119 bytes |

### Best Compression in this Lab

🏆 **XZ Compression**

Produced the smallest archive size.

---

# 💻 Commands Practiced

```bash
mkdir mybackups

tar -cvf mybackups/udev.tar /etc/udev

tar -tvf mybackups/udev.tar

tar -zcvf mybackups/udev.tar.gz /etc/udev

tar -xvf udev.tar.gz

tar -rvf udev.tar /etc/hosts

cp /usr/share/dict/words .

gzip words

gunzip words.gz

bzip2 words

bunzip2 words.bz2

xz words

unxz words.xz

zip words.zip words

zip -r udev.zip /etc/udev

unzip -l udev.zip

unzip udev.zip
```

---

# 🎯 Key Takeaways

- Learned the difference between archiving and compression.
- Created TAR archives for backups.
- Compressed archives using Gzip.
- Used Gzip, Bzip2, and XZ to reduce file size.
- Compared compression efficiency between different formats.
- Learned how ZIP archives maintain compatibility across operating systems.
- Practiced extracting and restoring archived data.

---
