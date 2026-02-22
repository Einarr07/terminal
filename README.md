# 🐧 Linux Terminal & Commands Study Guide

A personal, practical cheat sheet of essential Linux terminal commands for navigating the filesystem and working with files from the CLI.

---

## 1. Identity & Location 📍
Before running commands, it helps to know **who you are** and **where you are**.

| Command | Description |
| :--- | :--- |
| `whoami` | Shows the current logged-in username. |
| `pwd` | **Print Working Directory**: displays the full path of your current directory. |
| `clear` | Clears the terminal screen (`Ctrl + L` also works in most terminals). |

---

## 2. Navigation & Movement 🚀
Moving between directories is one of the most common CLI tasks.

| Command | Action |
| :--- | :--- |
| `cd [folder]` | **Change Directory**: enter a folder. |
| `cd ..` | Go **up** one level (parent directory). |
| `cd ~` | Go to your **Home** directory. |
| `cd ./path` | Move using a **relative** path from your current directory. |
| `Tab` | Auto-complete paths/commands or show suggestions. |

### Directory “Teleport” Stack (`pushd` & `popd`) 🌀
These commands let you jump between directories using a stack.

- `pushd .` → saves your current directory on the stack  
- `popd` → returns to the last saved directory  

> Tip: Use `dirs -v` to see the stack content.

---

## 3. File & Directory Management 📂

### Create files and folders
| Command | Description |
| :--- | :--- |
| `touch file.txt` | Creates an empty file (or updates timestamp if it exists). |
| `mkdir Documents` | Creates a new directory. |
| `mkdir -p ./A/B` | Creates nested directories in one go. |

### Display, write, and read content
**Print text to the terminal:**
```bash
echo "Hello World!!"
```

**Write to a file (overwrite):**
```bash
echo "Hello world" > greet.txt
```

**Append to a file (do not overwrite):**
```bash
echo "Another line" >> greet.txt
```

**Read file content:**
```bash
cat greet.txt
```

### Move and rename (`mv`)
`mv` is used for both **moving** and **renaming**.

**Move:**
```bash
mv ./School/Physical/ .
```
(Moves `Physical` into your current directory)

**Rename:**
```bash
mv School University
```
(Renames `School` to `University`)

### Copy (`cp`)
**Copy a file:**
```bash
cp greet.txt farewell.txt
```

**Copy a directory (recursive):**
```bash
cp -r University CopyUniversity
```

### Delete (`rm`) ⚠️
> **Warning:** There is no “Trash Bin” by default. Deleting is immediate.

**Delete a file:**
```bash
rm file.txt
```

**Delete a directory and its contents:**
```bash
rm -r "University copy"
```

**Interactive delete (asks before deleting):**
```bash
rm -i file.txt
```

**Force delete (no prompts):**
```bash
rm -rf folder_name
```

---

## 4. Listing Files (`ls`) 🔍

| Command / Flag | Description |
| :--- | :--- |
| `ls` | Basic list of files and folders. |
| `ls -a` | Show **all** files, including hidden ones (`.` prefix). |
| `ls -l` | Long format: permissions, owner, size, date. |
| `ls -la` | All files + long format. |

---

## 5. Exploring & Inspecting Files (Text / CSV) 🧪

### Quick preview with `less`
Use `less` to open files and scroll/search (great for large files).

```bash
less file.csv
```

**Useful keys inside `less`:**
- Quit: `q`
- Search: `/text` then Enter
- Next match: `n`
- Previous match: `N`
- End of file: `G`
- Start of file: `gg`

### First / last lines (`head`, `tail`)
**First 10 lines:**
```bash
head file.csv
```

**Last 10 lines:**
```bash
tail file.csv
```

**Custom number of lines (example: 25):**
```bash
head -n 25 file.csv
tail -n 25 file.csv
```

### Number lines (`nl`)
```bash
nl file.txt
```

### Count lines / words (`wc`)
**Count lines (useful for CSV row count):**
```bash
wc -l file.csv
```

**Count words:**
```bash
wc -w file.txt
```

### Extract columns (`awk`)
**Print first column (space/tab separated):**
```bash
awk '{print $1}' file.txt
```

**CSV: use comma as separator, print columns 1 and 3:**
```bash
awk -F ',' '{print $1, $3}' file.csv
```

**If you want a comma between them:**
```bash
awk -F ',' '{print $1 "," $3}' file.csv
```

---

## 6. Wildcards (Batch matching) ✨

### `*` (any characters)
Match many files:
```bash
ls *.txt
```

Match files starting with `file`:
```bash
ls file*.txt
```

### `?` (exactly one character)
Example files:
- `file1.txt`
- `file2.txt`
- `fileExtension.txt`

Match only files with **one character** after `file`:
```bash
ls -la file?.txt
```

### `[]` (one character from a set)
Example files:
- `fileB.md`
- `fileExtension.md`
- `fileA.txt`
- `fileC.log`

Match files ending with A, B, or C (case-sensitive):
```bash
ls -la *[ABC].*
```

> Note: `[ABC]` is not the same as `[abc]`.

### `{}` (brace expansion: multiple patterns)
Show files that end with specific extensions:
```bash
ls -la *.{md,log,txt}
```

---

## 7. Search: `grep` and `find` 🔎

### `grep` (search inside files)
Case-insensitive search for "thanos" in a CSV:
```bash
grep -i "thanos" marvel_wiki.csv
```

Useful flags:
- `-i` → case-insensitive
- `-n` → show line number
- `-c` → count matches
- `-v` → invert match (show lines that DO NOT match)
- `-r` → recursive search (inside folders)

Examples:
```bash
grep -in "thanos" marvel_wiki.csv
grep -ic "thanos" marvel_wiki.csv
grep -iv "thanos" marvel_wiki.csv
```

### `find` (search files/directories by name, type, size, etc.)
Find **directories**:
```bash
find . -type d -name "*"
```

Find **files larger than 1MB**:
```bash
find /home/marvel_rivals/ -type f -size +1M
```

More common examples:
```bash
find . -type f -name "*.log"
find . -type f -iname "readme*"
```

---

## 💡 Pro Tips
- **Spaces in names:** use quotes → `cd "University copy"`
- **Stop a command:** `Ctrl + C`
- **Command history:** use ↑ / ↓ arrows
- **Man pages:** `man ls`, `man grep`, `man find`
