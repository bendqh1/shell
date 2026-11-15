## Unix File Permissions are not shell file permissions (there is no such thing as shell file permissions)

In Unix and virtually all Unix-like operating systems, we have files of different types and their permissions.

```
TRWX
```

In the above:

`R`=Read
`W`=Write
`X`=Execute

`T` in the above is a file type indicator that describes the type of file (regular file, directory, symbolic link, etc. so it is not a permission (it's useful when we study a directory as with `ls`).
`T` is not a standard notation for this feature, it's just my own wording here.

Each one of the first three letters RWX can be comprised of `4||0`+`2||0`+`1||0`.

Given that typically a system has more than one user, we repeat the above data structure this way:

`TRWXRWXRWX`

Where `T` is, the character `-` can mean "regular file".

Where `RWXRWXRWX` is, The character `-` can mean `0` (no permission).

Each RWX refers to:

* **Owner** (for example "kenthompson"
    * The file's owning user, not necessarily the currently logged-in user.
* **Group** (for example "developers"
    * The file's owning group, not necessarily the user's primary group.
        * A file's owning group can contain multiple users, and membership is determined by the system's group memberships.
* **Others**
    * Anyone who is neither the owning user nor a member of the owning group.

`chown` changes file ownership.

`chgrp` changes file group.

`chmod` changes file permissions for the file's owning-user, the file's owning group, and any other user.

A file can have only one owner and only one owning group.

---

## In my opinion, why this architecture is confusing

* `X` for execute, should have been `E` for execute.
* There is no unique single character for the above `T`.
* The term "group" can make people mistake that there is a "group of owners" but actually there is only one owner.
* `-` can stand both for `regular file` and `0` but if there were two different unique computer characters for this, lots of confusion between `-` contextual meaning would have been spared.

## Clarification: File permissions are not shell-specific

Unix file permissions are fundamentally an **operating-system and filesystem feature** and therefore not shell-specific.

This means that the permission model is essentially the same regardless of whether we use Bash, Zsh, Ksh, Fish, Elvish, Nushell, or another Unix-compatible shell.

In particular:

* The permission model (Owner, Group, Others; Read, Write, Execute) is defined by the operating system.
* The permission representation (`rwxr-xr-x`) is independent of the shell.
* Numeric permissions (`755`, `644`, etc.) are also independent of the shell.
* Commands such as `chmod`, `chown`, and `chgrp` are system utilities, not shell-specific commands.
* Shells simply provide an environment in which we can invoke these utilities and interact with the filesystem.

Therefore, learning Unix file permissions is essentially a one-time learning investment that applies across different Unix shells.

There are some differences between Unix and Unix-like operating systems, and between filesystems. 
For example, ACLs (Access Control Lists), special permission bits, and filesystem capabilities introduce additional features and nuances.
However, the fundamental Owner/Group/Others and Read/Write/Execute model remains remarkably consistent across Unix-like systems.

Regardless, `TRWXRWXRWX` is just the first layer of *basic permissions*, as beyond these, there are also *Special permission bits* such as `setuid`, `setgid`, `sticky bit`.
However, ordinary users rarely need to change them.

## Notes

* `chown`, `chgrp`, and `chmod` are commonly available system utilities, but their implementations and exact options can vary between Unix-like systems.
