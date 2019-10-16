# Shell Script Studies
This repo is about my Shell Script studies, starting with the [Udemy course](https://www.udemy.com/course/shell-scripting-para-administradores-de-sistemas/) (pt-br only).

## [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) - FHS



The standard file systems and their meaning, created and maintained by Linux Foundation. 
  - `/` - root of the system;
  - `/bin` - binaries of the system open to single mode user;
  - `/sbin` - binaries of the system owned and restricted by super user (root);
  - `/boot` - kernel and operational system images;
  - `/dev` - devices of the computer;
  - `/etc` - static configuration files of the system and it softwares installed;
  - `/home` - the home directory of the users and their configuration;
  - `/lib` - stores the system libraries;
  - `/mnt` and `/media` - default file system where devices are mounted as pendrives, cd-roms;
  - `/opt` - stores the data of the softwares that are not from the linux/unix distribution;
  - `/proc` - stores information about the virtual files;
  - `/root` - the directory of the home directory of the super user;
  - `/tmp` - used to temporary operations
  - `/usr` - file system that has sub hierarchies to read-only user data;
  - `/var` - stores logs of operational system and other softwares;


## Commands Structure and Manipulation Commands

The `[something]` means that the `something` is optional.

  - `ls [args] [files/dirs]` - list files and directories. The args can by combined (e.g. -lash):
    - `-a`: all files including hidden files and dirs;
    - `-A`: all files including hidden files except the `./` and `../`;
    - `-l`: list the files in a ordered list by name with permissions, owner and group, bytes and modification date;
    - `-h`: show the size of the file in human readable notation (K, M, G, T);
    - `-r`: reverse the list, ordered by descending name;
    - `-t`: order the list by date, from newer to older;
    - `-l`: column list format;
    - `-R`: recursive list in directories in the actual directory;
  - `clear` - clear the terminal window;
  - `cd [dir]` - change dir;
    - `-`: get back to the previous directory (before using cd command to any directory);
    - `..`: get back to one level on the FHS;
  - `mkdir [dir]`: create a directory. It creates __only__ one directory, if the father directory doesn't exist, the directory will not be created;
    - `-p`: create recursively the directory (e.g. `mkdir father/dir` creates the father directory and the dir);
  - `rmdir [dir]`: remove a directory, if not empty;
    - `-p`: remove recursively the dir, if not empty;
  - `rm [args] [files/dirs]`: removes the files or diretories specified;
    - `-f`: force deletion;
    - `-r`: recursive deletion;
    - `-i`: interative deletion, asking for confirmation one by one;
  - `touch [args] [file]`: creates a empty file, or update the timestamp of a existing file;
  - `cat [path]`: prints file content;
  - `echo "[message]"`: prints the message to the standard output;
  - `cp [args] [source] [destination]`: copy a file/directory from a source to a destination;
    - `-i`: iterative copy;
    - `-p`: preserve timestamp and permissions (if you're the file/dir owner);
    - `-R`: recursively copy;
    - `-v`: verbose mode, printing all files copied;
  - `mv [source] [destination]`: move a file/dir from a source to a destination. If moving from some path to the same path with other file name it's  a rename;
    - `-i`: iterative copy;
    - `-v`: verbose mode, printing all files copied;