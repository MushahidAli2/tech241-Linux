# Research: Managing File Permissions

## 1. Does being the owner of a file mean you have full permissions on that file? Explain.

Being the owner of a file does not necessarily mean you have full permissions on that file. Ownership determines the control and management of the file, but permissions further define what actions can be performed on the file. The owner's permissions are just one aspect of the overall permission set.

## 2. If you give permissions to the User entity, what does this mean?

Giving permissions to the User entity means granting specific access rights to the user who owns the file. These permissions define what actions the owner can perform on the file, such as reading, writing, or executing it. The User entity corresponds to the owner of the file.

## 3. If you give permissions to the Group entity, what does this mean?

Giving permissions to the Group entity means granting specific access rights to the group that the file belongs to. Multiple users can belong to a group, and by assigning permissions to the Group entity, all users in that group receive the same access rights. Group permissions define what actions the group members can perform on the file.

## 4. If you give permissions to the Other entity, what does this mean?

Giving permissions to the Other entity means granting specific access rights to all users who are neither the owner nor part of the group associated with the file. Other permissions define what actions any user who falls into this category can perform on the file.

## 5. You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write, and execute. You are logged in as the user who is the owner of the file. What permissions will you have on this file? Explain.

As the user who is the owner of the file, you will have the User permissions applied to you. In this case, the User permissions are read-only. Therefore, you can read the content of the file but cannot modify or execute it. The User permissions take precedence over the Group and Other permissions.

## 6. Here is one line from the `ls -l` command: `-rwxr-xr-- 1 tcboony staff 123 Nov 25 18:36 keeprunning.sh`

This line provides information about the file or directory named `keeprunning.sh`. Here's what we can infer from the permissions part of the line (`-rwxr-xr--`):

- The first character, `-`, represents the file type. In this case, it is a regular file.

- The following nine characters represent the file permissions divided into three sets of three characters each. Each set corresponds to User, Group, and Other permissions, respectively.

- In this example, the User permissions are `rwx`, which means the owner has read, write, and execute permissions on the file.

- The Group permissions are `r-x`, indicating that the group members have read and execute permissions but not write permissions.

- The Other permissions are `r--`, meaning users who are neither the owner nor part of the group have only read permission.

- The number `1` indicates the link count of the file.

- `tcboony` represents the owner of the file.

- `staff` indicates the group to which the file belongs.

- `123` represents the file size.

- `Nov 25 18:36` indicates the date and time of the last modification.

