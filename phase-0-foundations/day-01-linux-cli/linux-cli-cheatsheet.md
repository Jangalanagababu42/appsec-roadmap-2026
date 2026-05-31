pwd-print working directory
cd- change directory
`.` (current directory), `..` (parent directory), `~` (home directory),`-` (previous directory)
ls - will list the directories and files in your current directory, 
ls -a  -to view hidden files 
ls -l  - details list of files in long format
ls -r  -for reverse order
ls -la  ,ls -al, ls -lar are combing commands
touch - to create new file 
touch existingfilename - it will update file timestamps to current time
touch -r filename -allows to set files timestamp to match to another file .useful for synchronizing timestamps across related files .
 # Set file2.txt's timestamp to match file1.txt's timestamp
touch -r file1.txt file2.txt 
touch -d -to put specific date as timestamp for file
 touch -d "2023-01-01 12:30:00" mysuperduperfile
 file -It identifies the **type** of a file (e.g., "ASCII text", "gzip compressed data", "ELF 64-bit executable").
 file hello.txt - it shows content type of hello file
 cat -cat myfile.txt- display content of file 
 cat dogfile birdfile-concatnate multiple files and display combined output
 cat > newfile -create new file and write content in new file 
 less - The `less` utility displays text in a paged format, allowing you to navigate through a file page by page without loading the entire file into memory.
 history-to check history of all cmds
  `Ctrl-R`.One of the most powerful history shortcuts is `Ctrl-R`. This initiates a reverse search.
  cp - cmd for copying files cp source destination 
  cp mycoolfile /home/pete/Documents/cooldocs
  in the destination you can also give new file . it will automaticially create file and copy content
  For Bulk copying 
  - `*`: Matches any sequence of characters.
- `?`: Matches any single character.
- `[]`: Matches any one of the characters enclosed in the brackets.
- ### Copying Directories Recursively
- cp -r Pumpkin/ /home/pete/Documents here r means recursive fetching into the folders and copying.
- `cp` will overwrite a file at the destination if it has the same name. To prevent accidental data loss, use the `-i` (interactive) flag, which prompts for confirmation before overwriting.
- cp -i mycoolfile /home/pete/Pictures
-  if you want to force an overwrite without any prompts
   cp -f mycoolfile /home/pete/Pictures
   The `cp -p flag` is particularly useful for backups or when migrating files where preserving timestamps is critical.
mv - It serves two primary purposes: renaming files or directories and moving them to a different location
To rename a file:

```bash
mv oldfile newfile
```

  To move a single file into a different directory:

```bash
mv file2 /home/pete/Documents
```
 linux mv -t
 mv -t /somedirectory file_1 file_2
**-i (interactive)**: **-b (backup)**: **-v (verbose)**:
mkdir "Make Directory"
mkdir -p books/hemmingway/favorites - for nested directories here p for parent

rm- remove
|`rm -f`|Force delete file|
|`rm -rf`|Force recursive delete folders/files|
`-r` = recursive  
`-f` = force
The `rmdir` command will only succeed if the directory is completely empty, making it a safer choice than `rm -r` for cleanup tasks.
rm -i interactive it asks confirmation before deleting
find  - used to search a file or dir even in nested dirs.
find /home -name puppies.jpg
find /home -type d -name MyFolder
To use the **Linux help command**, simply type `help` followed by the name of the built-in command.
help echo and ls --help
man cmd - manual for that cmd
man followed by cmd name
man ls
whatis cmd - to know about cmd in one line 
whatis echo
alias - used to create custom shortcut cmds 
alias ll='ls -la' 
alias update='sudo apt update && sudo apt upgrade'
For the changes to take effect, you must either close and reopen your terminal or tell the shell to reload the configuration file using the `source` command:
unalias ll - to remove the shortcut if no lonnger needed.
The most common way to end a shell session is with the `exit` command.
Another command you can use for a terminal exit is `logout`. This command is specifically designed to terminate a login shell.

echo Hello World > peanuts.txt -> it creates a new file and write the content in file .
if the file already exits then it overwrites the existing content with new ones .
What if you want to add to a file without erasing its contents? For that, we use the `>>` operator.

```bash
echo Hello World >> peanuts.txt
```

cat < peanuts.txt > banana.txt
 it reads contents from peanuts.txt and writes to banana,txt
stderr
A **file descriptor** is a non-negative number that the kernel uses to identify an open file or stream. The default file descriptors are:

- `0`: stdin (standard input)
- `1`: stdout (standard output)
- `2`: stderr (standard error)
- To redirect `stderr` to a file, you use the file descriptor `2` followed by the `>` operator. ls /fake/directory 2> peanuts.txt
- ### Combining stdout and stderr
- ls /fake/directory /etc/passwd > peanuts.txt 2>&1 (order is imp . if 1st one is fake dir 2 should be first ) but 
- ls /fake/directory /etc/passwd &> peanuts.txt modern method
- ls /fake/directory 2> /dev/null -> to completely ignore and discard error msgs .
- ### Pipe and Tee
- ls -la /etc | tee etc_listing.txt | grep "conf"
- allows you to save an intermediate result while continuing to process the data.
- This command does three things:

1. It lists the contents of the `/etc` directory.
2. It pipes that output to `tee`, which saves a copy to `etc_listing.txt` and also passes it along.
3. The output from `tee` is then piped to `grep`, which filters for lines containing "conf".
4
ENV Variables
echo $HOME -display the path to your home directory,
echo $USER -output your current username
env- output a list of key-value pairs
echo $PATH -returns a colon-separated list of directories.
echo 'The quick brown; fox jumps over the lazy dog' > sample.txt
cut -c 5 sample.txt it returns 5th letter
cut -f 2 sample.txt returns 2nd field 
paste -s sample2.txt- combine all lines to a single line 
the `head` command displays the first 10 lines of any given file
head /var/log/syslog
head -n 15 /var/log/syslog
tail /var/log/syslog
tail -f /var/log/syslog
the `-f` (follow) flag. When you use `tail -f`, the command doesn't exit after displaying the last few lines. Instead, it waits for new data to be appended to the file and prints it to the screen as it arrives.
expand sample.txt -By default, the `expand command` converts each tab into 8 spaces
unexpand -a result.txt -  `unexpand` only converts leading spaces on each line. The `-a` option tells the `unexpand command` to convert all instances of 8 spaces into a tab, not just those at the beginning of a line,
join file1.txt file2.txt
join -1 2 -2 1 file1.txt file2.txt
split somefile
sort file1.txt sort -r file1.txt sort -n file1.txt
tr Transalation 
$ echo "hello world" | tr a-z A-Z 
HELLO WORLD
### Deleting Characters with -d

$ echo "My address is 123 Main Street" | tr -d '0-9' 
My address is Main Street
### Squeezing Repeated Characters
$ echo "Hello World, how are you?" | tr -s ' ' 
Hello World, how are you?
`uniq` command is to remove duplicate adjacent lines
uniq reading.txt -To remove the repeated lines
uniq -c reading.txt - To count the occurrences of each line
uniq -u reading.txt - To display only the lines that are not repeated
uniq -d reading.txt -to display only the lines that are repeated
sort reading.txt | uniq- we need to sort first then uniq because uniq ignores duplicates if they are not adjacent

$ wc /etc/passwd 96 265 5925 /etc/passwd
The output displays three numbers followed by the filename. From left to right, these numbers represent:

1. The number of lines.
2. The number of words (the Linux word count).
3. The number of bytes.
4.- `-l`: Shows only the line count.
- `-w`: Shows only the word count.
- `-c`: Shows only the byte count.
- nl file1.txt - Using the `nl` command, you can easily add Linux line numbers
- grep - `grep` searches for a pattern within a file
- grep fox sample.txt
- grep -e "-v" /path/to/some/file.conf 
- The `-e` flag explicitly tells `grep` that the next argument is the pattern. This is particularly helpful when searching for patterns that start with a hyphen (`-`),
- grep -i somepattern somefile -**Case-Insensitive Search**
- grep -c fox sample.txt -**Count Matching Lines**
- grep -o fox sample.txt -**Show Only the Match**
- grep -f patterns.txt sample.txt - **Search for Patterns from a File**
- env | grep -i User - you can filter environment variables to find ones related to the user
- ls /somedir | grep '.txt$' -  to find all files ending with `.txt` in a directory

File Permissions
$ ls -l Desktop/ drwxr-xr-x 2 pete penguins 4096 Dec 1 11:45 .
The permission string has four main parts.
the first char indicates file type  d -> means directory , " -" for regulat files
next 9 chars are actual file permissions.
d          | rwx | r-x   | r-x
filetype|user|group|other 
user or owner has all permissions .group has only read and execute no write permissions
others have same permissions similar to group.
- **r**: Read permission.
- **w**: Write permission.
- **x**: Execute permission. ( permission on a directory allows you to enter it, while on a file, it allows you to run it as a program.)
- **-**: No permission granted.
-modify permissions
 The `chmod` command offers two main methods for this task: symbolic and numerical mode.
 ### Symbolic Mode
 first specify which permission set you want to change (user, group, or other), then use a `+` to add a permission or a `-` to remove it.

- `u` (user/owner)
- `g` (group)
- `o` (others)
- `a` (all: user, group, and others)
- chmod u+x myfile
-This command adds (`+`) the executable (`x`) permission for the user (`u`) on `myfile`.
chmod g-w myfile - to remove written permsiion for group
chmod ug+w myfile to add written permission for user and group
### Numerical (Octal) Mode
The permissions are represented by the following values:

- `4`: read (r)
- `2`: write (w)
- `1`: execute (x)
-chmod 755 myfile
- **7 (User):** `4 + 2 + 1` -> The user gets read, write, and execute permissions (`rwx`).
- **5 (Group):** `4 + 0 + 1` -> The group gets read and execute permissions (`r-x`).
- **5 (Others):** `4 + 0 + 1` -> All other users get read and execute permissions (`r-x`).
-# Ownership Permissions
sudo chown patty myfile -changing user ownership
sudo chgrp whales myfile -changing group ownership
sudo chown patty:whales myfile - changing both user and group

#  Umask
Every file that gets created comes with a default set of permissions.
umask 021- umask uses 3 bit permission set 
When you run the `umask` command, it will apply that default set of permissions to any new file you create.
The Permission Breakdown

- **0 (First digit):** Applies to the **Owner**. Subtracts nothing(6-0=6). The owner gets full access.
- **2 (Second digit):** Applies to the **Group**(6-2=4). Subtracts write permissions (\(2\)).
- **1 (Third digit):** Applies to **Others**.(6-1=5) Subtracts execute permissions (\(1\)).

The Set User ID (SUID) allows a user to run a program as the owner of the program file rather than as themselves.Commonly used for programs that need temporary **root access**.
-rwsr-xr-x 1 root root ... /usr/bin/passwd
- The `s` in `rws` means **SUID is enabled**.
- So when a normal user runs `passwd`, it runs with **root privileges**, allowing modification of `/etc/shadow`.

### Commands to set SUID

Symbolic:

```
sudo chmod u+s myfile
```

Numeric:

```
sudo chmod 4755 myfile
```

- `4` at the beginning represents the **SUID bit**.
- Capital `S` means SUID exists but **execute permission is missing**.
- **SGID** allows a program to run with the **permissions of the file’s group** instead of the user’s group.
- Useful when multiple users need shared group access.

Example:

```
-rwxr-sr-x 1 root tty ... /usr/bin/wall
```

- The `s` in the **group permissions** (`r-s`) means **SGID is enabled**.
- Programs run as members of the file’s group (`tty` here).

### Commands to set SGID

Symbolic:

```
sudo chmod g+s myfile
```

Numeric:

```
sudo chmod 2555 myfile
```

- `2` at the beginning represents the **SGID bit**.
# Process Permissions
Joy (root, UID 0): I set SUID on `passwd`. That means when it runs, the program can use the file owner’s privileges, which are root’s.

Bob (user, UID 500): So what happens to my IDs when I run it?

Joy: Your Real UID stays 500, because you started the process. The Effective UID becomes 0 while `passwd` runs, so it can access protected files. The Saved UID stores that elevated identity so the program can safely switch between your normal and elevated permissions when needed.

Bob: Can I change Sally’s password?

Joy: No. The program knows your Real UID is 500, so it only allows changes to your own account. Even with an Effective UID of 0, it won’t let you modify other users unless you’re truly acting as a superuser.

Bob: Got it—Real ID tracks me, Effective controls current access, and Saved helps safe switching.
# The Sticky Bit
The sticky bit is a permission setting that can be applied to a directory.
when a dir has sticky bit , only file or directory owners,or root users can delete or rename them .
-it is mainly useful for shared directories .

$ ls -ld /tmp drwxrwxrwt 17 root root 4096 Dec 15 11:45 /tmp
`t` at the end of the permission string .Because of this, while any user can create files in `/tmp`, they cannot delete or move files created by other users.
To add the sticky bit using symbolic mode:

```bash
chmod +t my_shared_dir
```
To set permissions using octal mode, you prepend a `1` to the standard three-digit permission code.

```bash
# This sets permissions to rwxr-xr-x with the sticky bit
chmod 1755 my_shared_dir
```

Processes

Processes are the programs currently running on your machine. each process is assigned a unique number called the **process ID (PID)**.

```
$ ps PID TTY STAT TIME CMD 41230 pts/4 Ss 00:00:00 bash 51224 pts/4 R+ 00:00:00 ps
```

This output shows a few key details:

- **PID**: The unique Process ID.
- **TTY**: The controlling terminal for the process.
- **STAT**: The current status of the process.
- **TIME**: The total CPU time the process has used.
- **CMD**: The command that started the process.
### BSD-Style
```
ps aux
```

- **a**: Displays all processes for all users.
- **u**: Provides a detailed, user-oriented format.
- **x**: Includes processes not attached to any terminal. These often include system daemons that start at boot and show a `?` in the TTY column.

This command gives a much richer output with additional columns like `USER`, `%CPU`, `%MEM`, `VSZ`, and `RSS`

### System V style
```
ps -ef
```
The **ps -ef linux** command provides a full listing of all processes.

- **-e**: Selects every process on the system.
- **-f**: Displays a "full-format" listing, which includes details like UID, PPID (Parent Process ID), C (CPU utilization), and STIME (start time).
Many users prefer `ps -ef` over `ps aux` for its clear, hierarchical view and detailed information.
A simpler variation, `ps -e linux`, will also list all processes but in a less detailed format.
While `ps` gives you a snapshot, the `top` command provides a real-time, dynamic view of the processes on your system.

# Controlling Terminal
- In Linux, TTY means the **terminal connected to a process**.
- The `TTY` column in `ps` output shows which terminal started the process.
### Controlling Terminal

- Most processes are attached to the terminal that started them.
- If the terminal closes, those processes usually stop too.

Example:

```
find /
```

If you close the terminal, the `find` process may terminate.

### Daemons

- Background system service processes.
- Start during boot and run independently.( untill shutdown).
- Not attached to any terminal.

In `ps` output:

```
TTY = ?
```

means:

- No controlling terminal.
- Process runs independently in background.



A process is a running instance of a program.  
Each process has a unique PID.  
The kernel loads it, allocates resources, and tracks it.  
The scheduler shares CPU time by priority and need.  
When it exits, the kernel reclaims its resources.

Process Creation 
Process creation in Linux uses fork to clone a process and create a child with a new PID.  
The parent’s PID appears as the child’s PPID.  
After fork, execve can replace the child’s program with a new one.  
You can see parent-child links with `ps l` by checking the PPID column.  
`init` with PID 1 (mostly root user ) is the first user-space process and the ancestor of all processes.
# Process Termination – Short Notes

- Process ends using `_exit()`.
    
- `0` → success, non-zero → error.
    
- Parent uses `wait()` to collect child status.
    
- Cleanup using `wait()` is called **reaping**.
    

## Orphan Process

- Parent dies before child.
    
- Child becomes orphan.
    
- Adopted by `init` (PID 1).
    
- Orphan is alive.
    

## Zombie Process

- Child ends before parent calls `wait()`.
    
- Zombie is dead but still in process table.
    
- Uses no CPU.
    
- Removed after reaping.
    

## Difference

- Orphan → alive, no parent.
    
- Zombie → dead, not cleaned yet.

  ###Signal = software interrupt to a process.
    
- Used for IPC and process management.
    
- Signals can be:
    
    - Ignored
        
    - Caught (signal handler)
        
    - Blocked
        
    - Default action executed
        
- Pending signal = waiting for delivery.
    

## Common Signals

- `SIGINT` → Ctrl-C interrupt
    
- `SIGTERM` → normal terminate request
    
- `SIGKILL` → force kill
    
- `SIGSTOP` → pause process
    
- `SIGSEGV` → invalid memory access
    
- `SIGHUP` → reload configuration
    

## Key Difference

- `SIGTERM` → graceful termination
    
- `SIGKILL` → immediate termination (cannot catch/block)
# kill Command – Important Notes

- `kill` command sends signals to processes.
    
- Default signal = `SIGTERM (15)`.
    

## Common Commands

- `kill PID` → sends `SIGTERM`
    
- `kill -15 PID` → graceful termination
    
- `kill -9 PID` → force kill using `SIGKILL`
    
- `kill -0 PID` → check if process exists
    

## Important Signals

- `SIGTERM (15)` → polite terminate request
    
- `SIGKILL (9)` → immediate force termination
    
- `SIGHUP (1)` → reload configuration
    
- `SIGINT (2)` → Ctrl-C interrupt
    
- `SIGSTOP (19)` → pause process
    
- `SIGCONT` → resume stopped process
    

## Key Difference

- `SIGTERM` → cleanup possible
    
- `SIGKILL` → no cleanup, immediate stop
# Niceness – Important Notes

- CPU gives each process a small time slice.
    
- Linux scheduler manages CPU sharing.
    

## Niceness

- Niceness controls process priority.
    
- Range: `-20` to `19`
    

### Priority

- `-20` → highest priority
    
- `19` → lowest priority
    

## Meaning

- High niceness = process is “nice” → less CPU usage
    
- Low/negative niceness = higher CPU priority
    

## Commands

- `top` → view NI (niceness) value
    
- `nice -n 5 command` → start process with niceness 5
    
- `renice 10 -p PID` → change niceness of running process
# Process States – Important Notes

- `ps aux` → shows process states in `STAT` column.
    
- Process state = current activity of process.
    

## Common States

- `R` → Running/Runnable
    
    - Executing or ready for CPU
        
- `S` → Interruptible Sleep
    
    - Waiting for event/input
        
    - Can wake by signal
        
- `D` → Uninterruptible Sleep
    
    - Waiting for I/O operation
        
    - Cannot be interrupted
        
- `Z` → Zombie
    
    - Process finished but not reaped
        
- `T` → Stopped
    
    - Suspended using Ctrl+Z or debugger
        

## Important

- Many `Z` states → possible parent process issue
    
- Long `D` state → possible hardware/driver problem
    
- `SIGCONT` → resumes stopped process
# /proc Filesystem – Important Notes

- `/proc` = virtual filesystem created by kernel.
    
- Stores process and system information.
    
- Not stored on hard disk.
    

## Important Points

- Each PID has a directory in `/proc`.
    
- `/proc/PID/` → contains process details.
    
- Example:
    
    - `cat /proc/12345/status`
        
    - Shows process state, memory, user ID, etc.
        

## Useful Commands

- `ls /proc` → list process/system files
    
- `cat /proc/cpuinfo` → CPU details
    
- `cat /proc/meminfo` → memory details
    

## Important

- Tools like `ps`, `top`, `htop` read data from `/proc`.
    
- Used for system monitoring and custom scripts.
# Job Control – Important Notes

- Job control manages background and foreground processes.
    
- `&` → run command in background.
    
    - Example: `sleep 1000 &`
        

## Important Commands

- `jobs` → list background jobs
    
- `Ctrl+Z` → suspend foreground process
    
- `bg` → resume suspended job in background
    
- `fg` → bring background job to foreground
    
- `fg %1` → bring specific job to foreground
    
- `kill %1` → terminate specific job
    

## Symbols in jobs

- `+` → most recent job
    
- `-` → second recent job
    

## Important

- Background jobs allow multitasking in terminal.
    
- Job IDs are referenced using `%`.
