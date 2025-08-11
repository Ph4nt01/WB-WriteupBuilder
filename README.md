# WB-WriteupBuilder

**WriteupBuilder** is a command-line tool for creating clean, organized CTF write-ups in Markdown — interactively or using a ready-to-fill advanced template.

Whether you want to quickly document your hacking process or prepare a professional post-CTF report, `wb` guides you through each section and saves your work in a well-structured `.md` file.

---

## ✨ Features

- **Interactive mode** – Answer prompts to build a Markdown write-up step by step  
- **Pre-written template** – Generate a detailed, advanced CTF template with `--template`  
- **Color-coded prompts** for better readability    
- **Multi-line input support**
- **Markdown formatting**


---

## 📦 Installation

### Using `pipx` (recommended):

```bash
pipx install wb-writeupbuilder
````

### Using `pip`:

```bash
pip install wb-writeupbuilder
```

### After installation, you can run:

```bash
wb
```

---

## 🚀 Usage

### **1️⃣ Interactive Mode**

Fill in each section via guided prompts.

```bash
wb
```

You’ll be asked for:

- Challenge overview (name, platform, category, etc.)
    
- Initial info
    
- Initial analysis
    
- Exploitation steps
    
- Flags
    
- Takeaways
    

The result is saved as:

```
<challenge_name>-<platform>.md
```

---

### **2️⃣ Advanced Template Mode**

Generate a **pre-written detailed Markdown template** for manual filling.

```bash
wb -t -fn MyWriteup.md
```

**Options:**

|Flag|Description|
|---|---|
|`-fn`, `--filename`|Output file name (default: `WriteupTemplate.md`)|
|`-t`, `--template`|Use the advanced pre-written template|

---

## 🧪 Example Run

Below are **two** example sessions: one for the interactive flow and one for the template flow. This shows the prompts and sample user input.

### 1) Interactive session (full transcript)

```bash

$ wb

In The Name of God

Tips for a clean writeup:

- Screenshot as you go through the CTF, then return here to build the writeup.

- For multi-line sections, press Enter to add new lines, and type `END` on a new line to finish.

- To insert an image: `![image](imagename.jpg)` — the image file must be in the same directory as the .md file.

- Skipping: If you press Enter without typing anything, that question will be skipped.

- Sections with no answers will not be written to the file.

WritupBuilder --> Starting /
(Press Enter to continue)

[User presses Enter]

# Challenge Overview

Name of the challenge: ReverseMe

Platform / Event: picoCTF

Who are you (solver): alice

Category of the challenge: Reverse Engineering

Difficulty of the challenge: Medium

Points for solving: 200

Writing to file: reverseme-picoctf.md

# Initial Info

Paste the challenge description, any attached files, or screenshots here.

(Type `END` on a new line to finish. Press ENTER immediately (empty first line) to skip this question.)

> Small stripped binary that prints "Welcome"

> Includes hidden function that checks a password

> END

# Initial Analysis

What stood out during your first inspection? Mention suspicious URLs, strange files, unusual behavior, etc.

(Type `END` on a new line to finish. Press ENTER immediately (empty first line) to skip this question.)

> Binary is stripped; strings show "check_password"

> Running it prints "Try harder"

> END

# Exploitation

Describe the steps and tools/scripts used to exploit the challenge...

(Type `END` on a new line to finish. Press ENTER immediately (empty first line) to skip this question.)

> Used radare2 to locate main and the check_password function

> Identified hardcoded comparison against a signature

> Patched binary to bypass check and printed flag

> END

# Flag

Enter The Flag: picoCTF{r3v3rs1ng_is_fun}

# Takeaways

List the commands, tricks, or concepts you learned...

(Type `END` on a new line to finish. Press ENTER immediately (empty first line) to skip this question.)

> Use radare2 `afl` to list functions, `s` to seek, `px @` to view bytes

> Patched bytes with `wx` to flip the conditional jump

> END

Done. Saved reverseme-picoctf.md

```

**Notes about the transcript**

* Filenames are sanitized to lowercase and spaces/special characters are replaced with underscores.

* For multi-line answers the tool expects you to type `END` on a new line to finish. Pressing Enter immediately at the first prompt of a multiline field skips that section.

---

### 2) Template mode (quick)

```bash

$ wb -t -fn MyWriteup.md

In The Name of God

WritupBuilder -> Writing the Advanced Writeup Template to MyWriteup.md /
(Press Enter to continue)

[User presses Enter]

Template saved as MyWriteup.md

```
---

## 📂 Output Example

```markdown
# 📌 Challenge Overview

| 🧩 Platform / Event | picoCTF |
| ------------------- | -------- |
| 📅 Date             | 2025-08-11 |
| 🔰 Category         | Reverse Engineering |
| ⭐ Difficulty        | Medium |
| 🎯 Points           | 200 |

---

# 📋 Initial Info:
Challenge description...

---

# 🔍 Initial Analysis:
First thoughts...

---

# ⚙️ Exploitation
Steps taken...

---

# 🚩 Flag -> picoCTF{example_flag}

---

# 📚 Takeaways
Things learned...
```

---

## 🛠 Development

Clone the repo:

```bash
git clone https://github.com/yourusername/writeupbuilder.git
cd writeupbuilder
pip install -e .
```

---
## 📂 Project Structure

```
WB-WriteupBuilder/
├── wb/
│   ├── __init__.py
│   └── cli.py
├── README.md
├── LICENSE
├── setup.py
├── pyproject.toml
├── .gitignore
```

---

## 📜 Author

[Ph4nt01](https://github.com/Ph4nt01)
