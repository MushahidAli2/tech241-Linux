# Research: Changing File Permissions

## 1. What command changes file permissions?

The command used to change file permissions is `chmod` (short for "change mode").

## 2. To change permissions on a file, what must the end user be? (2 answers)

To change permissions on a file, the end user must meet either of the following conditions:

- Be the owner of the file.
- Have appropriate superuser/administrator privileges.

## 3. Examples of different ways/syntaxes to set permissions on a new file (named testfile.txt):

a. Set User to read, Group to read + write + execute, and Other to read and write only:

```shell
chmod u=r,g=rwx,o=rw testfile.txt
```
b. Add execute permissions (to all entities):

chmod +x testfile.txt

c. Take write permissions away from Group:

chmod g-w testfile.txt

d. Use numeric values to give read + write access to User, read access to Group, and no access to Other:

chmod 640 testfile.txt

In this case, the numeric value 640 represents the permissions as follows:

User: Read + Write (6)
Group: Read (4)
Other: No access (0)
