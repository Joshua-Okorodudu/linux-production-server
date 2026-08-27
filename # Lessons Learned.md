# Lessons Learned

During this project I gained practical experience with Linux user administration and permission management.

## Key Lessons

- Linux evaluates permissions in the following order:
  1. Owner
  2. Group
  3. Others

- File ownership and permissions work together to control access.

- Directory execute (`x`) permission allows users to enter a directory.

- The `-a` option in `usermod -aG` preserves existing secondary group memberships.

- `ls -ld` displays information about a directory itself, while `ls -l` displays the contents of a directory.

- Absolute paths begin with `/` and reference locations from the root of the filesystem.

- Linux is case-sensitive.

- Wildcards (`*`) simplify operations on multiple files or directories.

- Password policies can be configured using the `chage` command.

- Account access can be temporarily disabled without deleting a user by locking the account.

- Permissions such as `777` should generally be avoided because they grant unrestricted access.

## Practical Skills Developed

- User Administration
- Group Administration
- File Ownership
- Linux Permissions
- Password Management
- Troubleshooting
- Access Control
