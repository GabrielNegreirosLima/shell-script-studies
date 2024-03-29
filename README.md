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
  - `touch [args] [file]`: creates a empty file, or update the timestamp of a existing file;;
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

## Running scripts and useful Commands
  - `bash -x script.sh`: Runs `script.sh` step-by-step showing the command and it's output for debugging purposes

## Output redirectors 
  The words between the `{}` means to choose one of the words as options for the command.
  - `{command,script} > file`: Standart Output - STDOUT. Create or overwrite the file with the command/script output;
  - `{command,script} >> file`: Sets STDOUT. Create or append the file with the command/script output;
  - `{command, script} 2> file`: Sets STDERR. Create or overwrite the file with the command/script error output;
  - `> /dev/null 2>&1`: Sets the STDOUT to the `/dev/null` (the standard device for sanitize output in UNIX) and the STDERR to the STDOUT defined (the /dev/null);
  - `{command,script} 1> /dev/null 2>/dev/null`: 
  - `command1 | command2`: Redirects the first command output to the next command;
  - `command1 <<< {command2, variable}`: Receives a entry (command, output, variable) as command1 entry. It eliminates the need of `echo` and `cat` commands;
    - Example: `COLUMN_HOSTNAME=$(cut -d, -f1 <<< $LINEVARIABLE)`
  - `EOF`: End Of File. It ends a file or input for command. Can be used for aggregate commands for some other as the example. Can used to write a config file as the example2 or edit some other file, using `cat`;
    - Example:
    
          $ ssh localhost << EOF
          > ls -l
          > echo $PATH
          > EOF

    - Example2: 
    
		  $ cat << EOF > file.conf
		  > someconfiguration
		  > otherconfigurations
		  > EOF

  - `command | tee file`: Copy shell command output for the file, keeping the output for the shell;

## Regex - Regular Expressions
  _Curiosity_: There is a env var called LC_ALL in some UNIX systems that stands for [_locale_](https://wiki.archlinux.org/index.php/Locale). These LC_* prefixes sets the local values for locale in the UNIX current session, so with LC_ALL you can set your standart output for any language that you want. Other of these variables is LC_COLLATE that sets the locale value for collate in the session - that means you can change the Lower Case and Upper Case settings, set bit-wise sorting as the below example, and some other stuff. At last but not least, to change these to the default value, use the letter `C` as `LC_ALL`. Examples from [Unix Stack Exchange](https://unix.stackexchange.com/questions/87745/what-does-lc-all-c-do)

	```
	$ LC_ALL=es_ES man
	¿Qué página de manual desea?

	$ LC_ALL=C man
	What manual page do you want?

	$ LC_ALL=en_US sort <<< $'a\nb\nA\nB'
	a
	A
	b
	B

	$ LC_ALL=C sort <<< $'a\nb\nA\nB'
	A
	B
	a
	b
	```
  - `*`: Match with anything in the current expression, from 0 to any chars;
  - `?`: Match with any unique character in the current expression;
  - `[0123456789]`: Match with any character that is within the interval - from 0 to 9;
  - `[0-9]: Same as above with shorter representation;
  - `[012]?`: Example that matches a string of two characters beggining with 0 or 1, or 2 or 3 and end with any character;
  - `[0-46-9a-eg-z]`: Example that matches from 0 to 9 excepting 5 or all letters excepting f;
  - ``
