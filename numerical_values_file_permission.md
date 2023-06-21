# Research: Managing File Permissions Using Numeric Values

## 1. What numeric values are assigned to each permission?

Each permission is assigned a numeric value:

- Read permission is represented by the value 4.
- Write permission is represented by the value 2.
- Execute permission is represented by the value 1.

## 2. What can you do with the values assigned to read + write permissions?

When you assign the values of read and write permissions, the numeric value would be 6. With read and write permissions, you can read and modify the content of the file. This means you can view the file's contents and make changes to it.

## 3. What value would assign read, write, and execute permissions?

To assign read, write, and execute permissions to a file, the numeric value would be 7. With these permissions, you can not only read and write the file but also execute it as a program or script.

## 4. What value would assign read and execute permissions?

To assign read and execute permissions to a file, the numeric value would be 5. With these permissions, you can read the file's content and execute it as a program or script, but you cannot modify it.

## 5. Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?

The value 644 represents the permissions for a file. It follows the convention where the first digit represents the owner's permissions, the second digit represents the group's permissions, and the third digit represents permissions for others (users not in the owner or group categories).

- In this case, the owner has read and write permissions (6).
- The group has read permissions (4).
- Others have read permissions (4).

Therefore, a file with the mode/permissions set to 644 allows the owner to read and write the file, while the group members and other users can only read the file.

