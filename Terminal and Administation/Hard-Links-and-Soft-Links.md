
# The File System, managing files

## Table of contents

* [The File System, managing files](#the-file-system-managing-files)
  * [Table of contents](#table-of-contents)
  * [Windows](#windows)
    * [Referencing files and folders](#referencing-files-and-folders)
      * [Shell Links (aka Shortcut)](#shell-links-aka-shortcut)
      * [Hard Links](#hard-links)
        * [How to create](#how-to-create)
        * [Editing and Overwriting behaviors](#editing-and-overwriting-behaviors)
      * [Soft Links](#soft-links)
        * [(NTFS) Junction Link](#ntfs-junction-link)
          * [How to create](#how-to-create-1)
          * [Editing and Overwriting behaviors](#editing-and-overwriting-behaviors-1)
        * [(NTFS) Symbolic Link](#ntfs-symbolic-link)
        * [How to create](#how-to-create-2)
          * [Editing and Overwriting behaviors](#editing-and-overwriting-behaviors-2)
      * [Useful tools](#useful-tools)
  * [Unix \ Linux](#unix--linux)

## Windows

### Referencing files and folders

In windows there are multiple ways to access and reference files and folders. each unique with different capabilities.  
see also:  

* [Overview to Understanding Hard links, Junction Points and Symbolic links in Windows](https://cects.com/overview-to-understanding-hard-links-junction-points-and-symbolic-links-in-windows/)  

#### [Shell Links (aka Shortcut)](https://docs.microsoft.com/en-us/windows/win32/shell/links)

[(The .lnk file specification)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-shllink/99e8d0e5-5bc6-4aed-af37-da7f584f832a)

* These are actual files. they take additional space on disk
* Use the .lnk file extension
* They do not act as a substitute or a place holder to their target unless processed specifically.
* Can refer to commands with arguments, action, urls. etc.

#### [Hard Links](https://docs.microsoft.com/en-us/windows/win32/fileio/hard-links-and-junctions#hard-links)

"A hard link is the file system representation of a file by which more than one path references a single file in the same volume."

* Apply to files only. not to directories.
* A file that acts like a representation of a target file on the same drive
* Has the same size as the target without duplicating it (doesn’t use any space)
* Interpreted at the operating system level (SW apps act upon the target through the link)
* Deleting the Hard Link does not remove the target file
* If the target is deleted, its content is still available through the hard link
* Changing the contents through the Hard Link changes the target contents*
* Must reside on the same partition as the target file
Compatible with Win2k and above in Windows

##### How to create

```cmd
fsutil hardlink create new_filename existing_filename
mklink /H new_filename existing_filename
```

```powershell

```

##### Editing and Overwriting behaviors

#### Soft Links

* Soft link can reference folders

##### (NTFS) [Junction Link](https://docs.microsoft.com/en-us/windows/win32/fileio/hard-links-and-junctions#junctions)

* Can refer to local paths only
* Requires absolute paths

###### How to create

###### Editing and Overwriting behaviors

##### (NTFS) [Symbolic Link](https://docs.microsoft.com/en-us/windows/win32/fileio/symbolic-links)

* Symbolic links can refer to network locations too
* Works with relative paths too.
* Similar and compatible to UNIX symbolic link.
* ```Creation of symbolic links requires the SeCreateSymbolicLinkPrivilege (“Create symbolic links”), which is granted only to administrators by default (but you can change that using security policy).``` [see more](https://superuser.com/a/125981)

##### How to create

###### Editing and Overwriting behaviors

#### Useful tools

* [Link Shell Extension](https://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html) - Create links from `file explorer` with right click and drag intuitively rather than a cli.

## Unix \ Linux
