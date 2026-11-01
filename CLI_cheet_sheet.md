# Command Line Interface (CLI)
CLI is the language we use in our terminal to interact with our system.
## What is shell?
• The shell is a user program or it is an environment provided for user interaction.  
• The shell accepts human-readable commands and translates them into something the kernel can read and process.
### Navigation commands
Print the current working directory.
```
pwd
```
List all files and directories in the current directory.
```
ls
```
Long list, with permission, owner, size, and date.
```
ls -l
```
List all, including hidden files.
```
ls -a
```
Long listing including hidden files
```
ls -la
```
Sort files by time.
```
ls -t
```
Reverse sort.
```
ls -r
```
Get files in human readable size.
```
ls -h
```
Change directory.
```
cd directory_name
```
Move up to the parent directory.
```
cd ..
```
Return to home directory.
```
cd ~
```
Return to the previous directory.
```
cd -
```
### Absolute path and Relative path
**Absolute path** - An absolute path starts from the root directory.  
**Relative path** - A relative path is interpreted from current working directory.
### Working with filesystem
Create a new directory.
```
mkdir dir_name
```
Remove an empty directory.
```
rmdir dir_name
```
Display directory structure as a tree.
```
tree
```
### Working with files
Create a new file.
```
touch file_name
```
Copy a file from its source to new destination.
```
cp src_name des_name
```
Copy a directory recursively, preserving permissions.
```
cp -a src_name des_name
```
Rename a file or directory.
```
mv old_name new_name
```
Move a file to other directory.
```
mv file_name dir_name
```
Remove a file.
```
rm file_name
```
Remove a directory.
```
rmdir dir_name
```
Remove a non-empty directory and all its contents.
```
rm -r dir_name
```
Print the contents of file to the screen.
```
cat file_name
```
View file contents one page at a time.
```
less file_name
```
Add content within file.
```
nano file_name
```
Print the first 20 lines of a file.
```
head -n 20 file_name
```
Print the last 20 lines of a file.
```
tail -n 20 file_name
```
Count the number of lines in a file.
```
wc -l
```
### Users, groups, and permissions
**Numeric permissions**  
1. Read - 4
2. Write - 2
3. Execute - 1
4. No permission - 0.  
**u** - User.  
**g** - Group.  
**o** - Other.  
Changing file permissions (symbolic or numeric notation).
```
chmod changing_mode file_name
```
Change ownership.
```
chown user_name file_name
```
Change file owner and group.
```
chown user_name:group_name file_name
```
Check user name.
```
whoami
```
Check Groups name.
```
groups
```
### Searching
Search for lines matching a pattern in a file.
```
grep "pattern" file_name
grep -in "pattern" file_name
```
Count how many lines contain a word.
```
grep - ic "word" file_name
```
Count total ocurrence of a word.
```
grep -o "word" file_name | wc -l
```
Show the full path to an executable command.
```
which command
```
Determine the type of a file.
```
file file_name
```
### find command and its flags
**find** - Search for files and folders based on different conditions.  
Finds the exact filename.
```
find .-name file_name
```
Find files
```
find .-type f
```
Find directories.
```
find .-type d
```
Find .txt files
```
find .-name "*.txt"
```
Matches the extension regardless of case.
```
find .-iname "*.TxT"
```

### Pipes and Command chaining
Pipes and command chaining are foundational techniques in the Command Line Interface (CLI) that allow you to combine small, single-purpose utilities to perform complex data processing and automation.  
**Commands**  
Pipe stdout (1) of cmd1 to stdin (0) of cmd2.
```
cmd1 | cmd2
```
Run commands in sequence regardless of exit status.
```
cmd1; cmd2
```
Run cmd2 only if cmd1 succeeds (exit code 0).
```
cmd1 && cmd2
```
Run cmd2 only if cmd1 fails (non-zero exit code).
```
cmd1 || cmd2
```
Run a command in the background.
```
cmd &
```
Group commands and redirect their combined output.
```
{ cmd1; cmd2; } > file
```
Run commands in a subshell (side effects don’t affect the current shell).
```
(cmd1; cmd2)
```
Continue a long command on the next line.
```
cmd1 \
```
### Process
Process is a running instance of a program.  
**Process Id (PID)** - PID is the unique identifier assigned to a running process.
List all processes in computer.
```
ps -ef
ps aux
```
Find process by it's name.
```
ps -ef | grep "name"
```
Find the most senior parent process.
```
ps -o pid,ppid,comm -p $$
```
### Commands to find Computer architecture
Prints all system information.
```
uname -a
```
Prints the Operating System kernel name.
```
uname -s
```
Prints the network node hostname of the machine.
```
uname -n
```
Prints the current kernel release version.
```
uname -r
```
Prints the specific kernel build date and timestamp.
```
uname -v
```
Prints the physical hardware architecture.
```
uname -m
```
Prints the processor type.
```
uname -p
```
Prints the hardware platform.
```
uname -i
```
Prints the generic operating system distribution name.
```
uname -o
```
Find audio driver (mac).
```
system_profiler SPAudioDataType
```
### Kill
The kill command is a built-in shell utility used to send specific operational signals to active processes.   
Kill the process with it's name.
```
pkill "process_name"
```
Kill the process with it's ID.
```
kill PId
```
Kill the process forcibly.
```
kill -9 PId
```
Requests graceful termination.
```
kill -TERM PID
```
Sends an interrupt signal.
```
kill -INT PID
```
Suspends a process.
```
kill -STOP PID
```
Resumes a stopped process.
```
kill -CONT PID
```
### Find the location of node and code
```
which node
which code
```
### Basic of sed and awk

