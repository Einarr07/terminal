# 🐧 Linux Terminal & Commands Study Guide

This repository is a collection of essential Linux commands. It serves as a personal cheat sheet for navigating the file system and managing data via the CLI (Command Line Interface).

---

## 1. Identity & Location 📍
Before executing commands, it is important to know which user you are and where you are located.

| Command | Description |
| :--- | :--- |
| `whoami` | Displays the current logged-in username. |
| `pwd` | **Print Working Directory**: Shows the path of the folder you are currently in. |
| `clear` | Cleans the terminal screen (Shortcut: `Ctrl + L`). |

---

## 2. Navigation & Movement 🚀
Moving between folders is one of the most common tasks in the terminal.

| Command | Action |
| :--- | :--- |
| `cd [folder]` | **Change Directory**: Move into a specific folder. |
| `cd ..` | Move **up** one level (to the parent directory). |
| `cd ~` | Move to your **Home** directory. |
| `cd ./path` | Find a **relative** position from your current folder. |
| `TAB` key | **Auto-complete**: Press Tab while typing a path to see your options. |

### The "Teleport" Stack (`pushd` & `popd`) 🌀
* **`pushd .`**: Saves your current location and "pushes" it onto a stack.
* **`popd`**: The "Teleport" command. It takes you back to the last location you saved.

---

## 3. File & Directory Management 📂

### Creating Files and Folders
| Command | Description |
| :--- | :--- |
| `touch file.txt` | Creates an empty file. |
| `mkdir Documents` | Creates a new directory (folder). |
| `mkdir -p ./A/B` | Creates nested directories (subfolders) all at once. |

### Viewing and Editing Content
* **Display Text:**
  ```bash
  echo "Hello World!!"
  ```
* **Write to a file (Overwrite):**
  ```bash
  echo "Hello world" > greet.txt
  ```
* **Read file content:**
  ```bash
  cat greet.txt
  ```

### Moving and Renaming (`mv`)
The `mv` command is used for both moving files and renaming them.
* **Move:** `mv ./School/Physical/ .` (Moves 'Physical' to your current location).
* **Rename:** `mv School University` (Renames the folder 'School' to 'University').

### Copying (`cp`)
* **Copy a file:** `cp greet.txt farewell.txt`
* **Copy a folder (Recursive):** `cp -r University CopyUniversity`

### Deleting (`rm`) ⚠️ (rm -i)
> **Note:** Be very careful with these! There is no "Trash Can" in the terminal.
* **Delete a file:** `rm file.txt`
* **Delete a folder and its contents:** `rm -r 'University copy'`
* **Force delete (no questions asked):** `rm -rf 'folder_name'`

---

## 4. Listing Files (`ls`) 🔍
| Flag | Description |
| :--- | :--- |
| `ls` | Basic list of files and folders. |
| `ls -a` | Show **all** files (including hidden ones starting with `.`). |
| `ls -l` | **Long format**: Shows permissions, owner, size, and date. |
| `ls -la` | Shows **all** files in **long** format. |

---

## 💡 Pro Tips
* **Spaces in names:** If a folder name has a space, use quotes: `cd 'University copy'`.
* **Tab Completion:** Always use the `Tab` key to avoid typos!
* **Stop a Process:** Press `Ctrl + C` if you need to cancel a command.