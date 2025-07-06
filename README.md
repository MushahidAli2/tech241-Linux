# Basic Command Line Commands

## Introduction
The command line interface (CLI) is a powerful tool for interacting with your computer.

## Commands

### `cd`
The `cd` command is used to change the current working directory. For example:
'''python
cd
'''

### `cd Documents`
This command will navigate to the "Documents" directory.

### `ls`
The `ls` command lists the contents of a directory. 

This will display all the files and directories in the current directory.

### `mkdir`
The `mkdir` command is used to create a new directory. 

### `mkdir new_directory`
This will create a new directory named "new_directory".

### `rm`
The `rm` command is used to remove files and directories. 
For example: rm file.txt

This will delete the file named "file.txt".

### `cp`
The `cp` command is used to copy files and directories. For example: cp file.txt new_location/

This will copy the file "file.txt" to the "new_location" directory.

### `mv`
The `mv` command is used to move or rename files and directories. For example:mv file.txt new_location/

This will move the file "file.txt" to the "new_location" directory.

### `cat`
The `cat` command is used to display the contents of a file. For example:cat file.txt

This will print the contents of "file.txt" to the console.

### `chmod`

The `chmod` command is used to change the permissions of files and directories. It allows you to control who can read, write, and execute files. Here are some commonly used `chmod` commands:

- `chmod +r file.txt`: Adds read permission to "file.txt" for the owner, group, and others.
- `chmod +w file.txt`: Adds write permission to "file.txt" for the owner, group, and others.
- `chmod +x script.sh`: Adds execute permission to "script.sh" for the owner, group, and others.
- `chmod u-x file.txt`: Removes execute permission from "file.txt" for the owner.
- `chmod go-rw file.txt`: Removes read and write permissions from "file.txt" for the group and others.
- `chmod 755 script.sh`: Sets read, write, and execute permissions for the owner, and read and execute permissions for the group and others.

The numeric mode in `chmod` uses a three-digit code, where the digits represent permissions for the owner, group, and others, respectively. Each digit can range from 0 to 7, with the following meanings:
- 0: No permission
- 1: Execute permission
- 2: Write permission
- 3: Write and execute permissions
- 4: Read permission
- 5: Read and execute permissions
- 6: Read and write permissions
- 7: Read, write, and execute permissions


### `history`
The `history` command displays a list of previously executed commands. For example: history
This will show a numbered list of the commands you have previously entered.

### `uname`
The `uname` command provides information about the system. Here are some useful options:
- `uname -r`: Displays the kernel release.
- `uname -l`: Shows the operating system name.
- `uname -a`: Provides detailed system information.

### `ps`
The `ps` command lists currently running processes. Here are some useful options:
- `ps`: Lists the processes running in the current terminal session.
- `ps -p $$`: Shows information about the current process.

### `curl`
The `curl` command is used to transfer data to or from a server. For example:
curl https://example.com

This will retrieve the content of the specified URL.

### `file`
The `file` command determines the type of a file.
For example: file file.txt

This will display information about the file "file.txt".

### `nano`
The `nano` command is a simple text editor for the command line.

For example:nano file.txt


This will open the file "file.txt" in the nano editor.

### `head` and `tail`
The `head` and `tail` commands display the first or last few lines of a file, respectively. For example:

head -2 file.txt 

tail -2 file.txt

These commands will show the first two or last two lines of "file.txt", respectively.

### `nl`
The `nl` command adds line numbers to a file. For example:

nl file.txt

This will display the contents of "file.txt" with line numbers.





