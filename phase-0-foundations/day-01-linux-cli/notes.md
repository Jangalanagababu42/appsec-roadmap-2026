---
day: 1
date: 2026-05-25
phase: 0
hours: 6
tags:
  - day/001
  - phase/0
aliases:
  - "Day 1"
  - "Linux CLI Essentials"
---

# Day 001 — Linux CLI Essentials

**Mon 25 May 2026** · ~6h · Stage 0 — Programming & Engineering Foundations



— Start — · [[00-Dashboard|🏠 Dashboard]] · [[00-Calendar|📅 Calendar]] · [[Day-002-Git-and-GitHub-Workflow|Day 2 →]]

---

## 📘 Learn (~2h)

Filesystem, permissions (chmod/chown), grep/find/sed/awk, pipes/redirection, environment variables, processes, ssh basics. Why a CLI-fluent person reads code, logs, and config 3× faster.

## 🛠️ Do (~4h)

Set up Ubuntu VM or WSL. Do Linux Journey through file system + processes. Practice 20 grep/find combos on a real codebase.

## 🎯 Deliverable

`linux-cli-cheatsheet.md`

- [ ] Deliverable committed to GitHub
- [ ] Verbal explain-aloud done (15 min)

## 📚 Resources

- 🧪 Lab [Linux Journey](https://linuxjourney.com/)
- 🧪 Lab [OverTheWire Bandit (levels 0–15)](https://overthewire.org/wargames/bandit/)
- 📖 Read [The Missing Semester (MIT)](https://missing.csail.mit.edu/)
- 🎥 Video [NetworkChuck: Linux basics](https://www.youtube.com/watch?v=BMGixkvJ-6w)

## 📝 Notes

> Write your own learnings, gotchas, code snippets, and questions here.
   


> ## Dashed Filenames Summary

- The Problem: Linux treats leading dashes (e.g., `-file.txt`) as command flags, breaking tools like `rm` or `cat`.
- Fix 1 (Path Prefix): Add `./` before the name to hide the dash.
    
    - _Example:_ `cat ./-file.txt`
    
- Fix 2 (Double Dash): Use `--` to stop the command from looking for flags.
    
    - _Example:_ `cat -- -file.txt`
    
- Single Dash (`-`): Represents standard input. You must use `./-` to reference it as a file

- Spaces (`file name.txt`): Wrap in quotes (`rm "file name.txt"`) or escape the space (`rm file\ name.txt`).
- Leading Tilde (`~file.txt`): Linux expands `~` to your home directory. Wrap in quotes (`rm "~file.txt"`) to target the local file.
- Wildcards (`*file.txt`): The `*` expands to match all files. Escape it (`rm \*file.txt`) to protect the actual filename.
- Control Characters (`\n` or tabs): Use interactive mode (`rm -i *`) to delete by confirmation without typing the name.
example : file name:   --spaces in the filename--
cat ./"--spaces in the filename"

to find human readable file out of many files and the file starts with - ?
use file * - it fetches all the files in a dir along with file data type.
here * means wildcard meaning everything
then do ./
ans file ./* 
. ->current dir
/ ->path separator
** ->wildcard meaning everything
When you combine them into `./*`, the shell expands it into a list of absolute paths for every file in your folder (e.g., `./-file01`, `./-file02`). This safely forces the `file` command to see them as paths, preventing it from mistaking filenames starting with a dash (`-`) for command

to find a file that has 1033 bytes ,readable, not executable in a nested directories

find -type f -size 1033c -readable ! -executable
find - to find into nested directors 
-type -for what we are searching for , d -> directory , f-file 
-size- file size
-readable - check for file that has  readable permission
! - which is not 
-executable - check for file that has  executable permission

to find file stored **somewhere on the server**  - owned by user bandit7
- owned by group bandit6
- 33 bytes in size
ans :- find / -type f -size 33c -user bandit7 -group bandit6 2> /dev/null
 if we execute till bandit6 we will get permission error.to completely ignore and discard error msgs we use 2(stderror code) > /dev/null.
 
Two things to lock in from levels 5 + 6 — write these in your cheatsheet:

1. `find` combines filters by AND by default — stack as many `-flag value` as you need
2. `2>/dev/null` discards errors (stderr = 2). You'll use this constantly in real AppSec work — running scans, recon, log parsing.
to find password next to a word in a file with lot of data 
grep  "word" filename 

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once
sort a.txt | uniq -u 
unique only checks adjacent duplicates . so if we do sort first then all randomly placed duplicates will become adjacent then unique cmd will make duplicates to single cmd .
-u - to find only lines  that occured only once .
diff b/w sort filename.txt | uniq sort filename.txt | uniq -u ?
- **`sort filename.txt | uniq`** removes duplicates but **keeps one copy** of every single line.
- **`sort filename.txt | uniq -u`** deletes the duplicates completely and **only prints lines that were unique from the start**.
example : apple apple banana cherry cherry
sort filename.txt | uniq 
This condenses the list. If a line repeats, it shrinks it down to just one occurrence.
apple banana cherry
sort filename.txt | uniq -u
The `-u` flag stands for **"unique only"**. It tells the system: _"If a line appears more than once, wipe it out completely. I only want to see the lines that never repeated."_  
**Output:**
banana

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

ans :- strings data.txt | grep "== "
about syntax order first we need to extract strings from binary file ->strings data.txt next | pipe the extracted data and find words preceded by == .

**`grep` argument order.** It's `grep PATTERN [FILE]`. When grep reads from a pipe, you don't pass a file at all — just the pattern. So `grep "===="` (no file) when it's downstream of a pipe.

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data
base64 -d data.txt -d for decoding the encoded base64 data

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

ans 
mkdir /tmp/kushu
then copy file to kush dir
cd to tmp/kushu
LOOP:
  1. file <current_file>           # what is it?
  2. rename so extension matches   # e.g., mv X X.bz2
  3. decompress with the right tool # gunzip / bunzip2 / tar -xf / etc and do ls 
  4. file <new_file>
  5. if ASCII text → STOP, cat it, find password
     else → GOTO step 2
  decompression cmds
  unzip filename.zip
  gunzip filename.gz
  bunzip2 filename.bz2
  unxz filename.xz
  tar -xf <file>  

## 🔗 Related

- [[00-Dashboard|Dashboard]]

## ✅ Completion

- [ ] Marked complete in v4.5 HTML roadmap
- [ ] Notes synced
- [ ] Anki cards added (if applicable)

---

— Start — · [[Day-002-Git-and-GitHub-Workflow|Day 2 →]]
