# Bash Suggested user guide

## Table of contents

* [Bash Suggested user guide](#bash-suggested-user-guide)
  * [Table of contents](#table-of-contents)
  * [Commands and Interactions](#commands-and-interactions)
    * [Environment variables [env,WSLENV]](#environment-variables-envwslenv)
    * [System Information](#system-information)
      * [date](#date)
    * [File Managment](#file-managment)
      * [Navigation, Viewing, Searching [pwd,ls (ll,la,l aliases),cat,less/more,head,tail,grep] - Immutable](#navigation-viewing-searching-pwdls-lllal-aliasescatlessmoreheadtailgrep---immutable)
        * [ls - List Directories](#ls---list-directories)
      * [Creating and Editing, Deleting [mkdir,rmdir,touch,mv,rm,unlink] - Mutable](#creating-and-editing-deleting-mkdirrmdirtouchmvrmunlink---mutable)
      * [Listing Directories](#listing-directories)

## Commands and Interactions

----------

### Environment variables [env,WSLENV]

```bash
env
```
<!-- #region(collapsed) output-->
<details>
<summary>output</summary>

```text
SHELL=/bin/bash
WSL_DISTRO_NAME=Ubuntu-20.04
WT_SESSION=bfc4c582-a408-4667-a7d5-5802cd0f178d
NAME=DESKTOP-TDGP3CU
PWD=/mnt/c/Users/user
LOGNAME=user
MOTD_SHOWN=update-motd
HOME=/home/user
LANG=C.UTF-8
WSL_INTEROP=/run/WSL/8_interop
```

</details>
<!-- #endregion -->

----------

### System Information

#### date

calculates dates and provides current date/time information

```bash
#current time
date
# future date
date -u --date="next thur"
# with formatting
date -u --date="next thur" "+%dd"
```

<!-- #region(collapsed) output-->
<details open>
<summary>output</summary>

```text
Sun Oct 11 13:56:24 IDT 2020
Thu Oct 15 00:00:00 UTC 2020
15
```

</details>
<!-- #endregion -->

----------

### File Managment

#### Navigation, Viewing, Searching [pwd,ls (ll,la,l aliases),cat,less/more,head,tail,grep] - Immutable

##### ls - List Directories

```bash
ls
```

ls has useful flags such as `-all` and `list`
Ubuntu 20.04 by default comes with a few useful aliases shortening flag usage.

```bash
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
```

#### Creating and Editing, Deleting [mkdir,rmdir,touch,mv,rm,unlink] - Mutable

```diff
-todo the commands listed above in file managment
print current directory - pwd
```

#### Listing Directories

```bash
date > file.txt
cat file.txt
```

```text
Sat Oct 10 22:31:12 IDT 2020

```

```bash
mv file renamedfile
```

```diff
! if dir exists, move will move because it's move not rename
```

```diff
-todo unlink(remove hard link) vs rm
```

```bash
rmdir specific_directory
```

```diff
! needs folder to be empty. use rm -R to recursively remove
```
