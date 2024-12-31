[Back To Main](/README.md)

# 2.1 Command Line Basics

**Shell:** a program that enables text based communication between the operating system and the user.

There are several different shells on Linux, these are just a few:
* Bourne-again shell(Bash)
* C shell (csh or tcsh, the enhanced csh)
* Korn shell (ksh)
* Z shell (zsh)

When using an interactive shell, the user inputs commands at a so-called prompt. For each Linux distribution, the default prompt may look a little different, but it usually follows this structure:

```bash
username@hostname current_directory shell_type
```

**username:** Name of the user that runs the shell

**hostname:** Name of the host on which the shell runs. There is also a command hostname, with which you can show or set the system's host name.

**current_directory:** The directory that the shell is currently in. A `~` means that the shell is in the current user's home directory.

**shell_type:**\
\$ indicates the shell is run on a regular user.

\# indicates the shell is run by the superuser root.

## Command Line Structure

Most commands at the command line follow the same basic structure:

```
command [option(s)/parameter(s)...] [argument(s)...]
```

Example:

```
$ls -l /home
```

**Command:** program that the user will run `-ls` in the above example

**Option(s)/Parameter(s):** A "Switch" that modifies the behavior of the command in some way, such as `-l` in the above example. Options can be accessed in a short and in a long form. For example, `-l` is identical to `--format=long`. Multiple options can be combined as well and for the short form, the letters can usually be typed together.

Example:

```
$ ls -al
$ ls -a -l
$ ls --all --format=long
```

**Argument(s):** additional data that is required by the program, like a filename or path, such as `/home` in the above example.

## Command Behavior Types

The shell supports two types of commands: 

**Internal:** these commands are part of the shell itself and are not separate programs. There are around 30 such commands. Their main purpose is executing tasks inside the shell (e.g. `cd`, `set`, `export`)

**External:** These commands reside in individual files. These files are usually binary programs or scripts. When a command which is not a shell builtin is run, the shell uses the `PATH` variable to search for an executable file with same name as the command. In addition to programs which are installed with the distribution's package manager, users can create their own external
commands as well.

The command `type` shows what type a specific command is:

```
$ type echo
echo is a shell builtin
$ type man
man is /usr/bin/man
```

## Quoting

In Linux, managing files and variables can become challenging when dealing with spaces, special characters, and variables. To handle this, shells offer a feature called quoting, which allows you to encapsulate such data using different types of quotes. In Bash, the three types of quotes used are:

* Double quotes (`" "`)
* Single quotes (`' '`)
* Escape characters (using a backslash `\`)

### Double Quotes

Double quotes tell the shell to take the text in between the quote marks ("...") as regular characters. All special characters lose their meaning, except the `$` (dollar sign), \ (backslash) and ` (backquote). This means that variables, command substitution and arithmetic functions can still be used.

For example, the substitution of the $USER variable is not affected by the double quotes:

```
$ echo I am $USER
I am tom
$ echo "I am $USER"
I am tom
```

A space character, on the other hand, loses its meaning as an argument separator:

```
$ touch new file
$ ls -l
-rw-rw-r-- 1 tom students 0 Oct 8 15:18 file
-rw-rw-r-- 1 tom students 0 Oct 8 15:18 new
$ touch "new file"
$ ls -l
-rw-rw-r-- 1 tom students 0 Oct 8 15:19 new file
```

In the first example, the touch command creates two separate files because it interprets the two strings as individual arguments. In the second example, both strings are treated as one argument, resulting in the creation of a single file. However, it's best practice to avoid spaces in filenames, and instead use underscores (_) or dots (.) for separation.

### Single Quotes

Single quotes don't have the exceptions of the double quotes. They revoke any special meaning from each character. Let's take one of the first examples from above:

```
$ echo I am $USER
I am tom
```

When applying the single quotes you see a different result:

```
$ echo 'I am $USER'
I am $USER
```

The command now displays the exact string without substituting the variable.

### Escape Characters

We can use escape characters to remove special meanings of characters from Bash. Going back to
the $USER environment variable:

```
$ echo $USER
carol
```

By default, the contents of a variable are displayed in the terminal when preceded by a dollar sign. However, if a backslash (`\`) is placed before the dollar sign, it negates the special meaning of the dollar sign, causing Bash to interpret the variable name literally instead of expanding it to its value.

```
$ echo $USER
$USER
```

If you recall, we can get similar results to this using the single quote, which prints the literal contents of whatever is between the single quotes. However the escape character works differently by instructing Bash to ignore whatever special meaning the character it precedes may
possess.

## Variables

In Linux shells, variables store data like text or numbers and are accessed by their names. There are two types of variables:

1. **Local Variables:** These are accessible only in the current shell process and are not inherited by sub-processes.
2. **Environment Variables:** These are available both in the shell session and in sub-processes. They are often used to pass configuration data to commands and are typically in uppercase (e.g., PATH, USER).

Variables are not persistent; once the shell is closed, the variables and their contents are lost. To make variables permanent, they need to be added to configuration files that load them each time a new shell starts.

## Manipulating Variables

### Working with Local Variables

You can set up a local variable by using the `=` (equal) operator. A simple assignment will create a local variable:

```
$ greeting=hello
```

Display the variable using the `echo` command. The command usually displays the text in the argument section:

```
$ echo greeting
greeting
```

In order to access the value of the variable you will need to use $ (dollar sign) in front of the variable's name.

```
$ echo greeting
hello
```

Now this variable only exist in the current shell. If you open up another shell and run the command above you will not get anything to appear.

```
$ echo $greeting world
hello world
$ bash -c 'echo $greeting world'
world
```

In order to remove a variable, you will need to use the command `unset`:

```
$ echo $greeting
hello
$ unset greeting
$ echo $greeting
```

>Note\
>`unset` requires the name of the variable as an argument. Therefore you may not add `$` to the name, as this would resolve the variable and pass the variable's value to `unset` instead of the variable's name.

### Working with Global Variables

To make a variable available to subprocesses, turn it from a local into an environment variable. This is done by the command `export`. When it is invoked with the variable name, this variable is added to the shell's environment:

```
$ greeting=hello
$ export greeting
```

>Note\
>Again, make sure to not use `$` when running `export` as you want to pass the name of the variable instead of its contents.

An easier way to create the environment variable is to combine both of the above methods, by assigning the variable value in the argument part of the command.

```
$ export greeting=hello
```

Another way to use environment variables is to use them in front of commands. We can test this with the environment variable `TZ` which holds the timezone. This variable is used by the command `date` to determine which timezone's time to display:

```
$ TZ=EST date
Thu 31 Jan 10:07:35 EST 2019
$ TZ=GMT date
Thu 31 Jan 15:07:35 GMT 2019
```

You can display all environment variables using the `env` command.

### The `PATH` Variable

The `PATH` variable is one of the most important environment variables in a Linux system. It stores a list of directories, separated by a colon, that contain executable programs eligible as commands from the Linux shell.

```
$ echo $PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

To append a new directory to the variable, you will need to use the colon sign (:).

```
$ PATH=$PATH:new_directory
```

To find out how the shell invokes a specific command, `which` can be run with the command's name as argument. We can, for example, try to find out where `nano` is stored:

```
$ which nano
/usr/bin/nano
```
107
# 2.2 using the Command Line to Get Help

## Getting Help on the Command Line

### Built-in Help

### Man Pages

### Info Pages

### The /usr/share/doc/ directory

## Locating files

### The `locate` command

### The `find` command

# 2.3 Using Directories and Listing Files

## Files and Directories

## File and Directory Names

## Navigating the Filesystem

### Getting Current Location

### Listing Directory contents

###
## Absolute and Relative Paths

## Home Directories

## The Special Relative Path for Home

## Relative-to-Home File Paths

## Hidden Files and Directories

## The Long List Option

## Additional Is Options

## Recursion in Bash

# 2.4 Creating, Moving and Deleting Files

## Case Sensitivity

## Creating Directories

## Creating Files

## Renaming Files

## Moving Files

## Deleting Files and Directories

## Copying Files and Directories

[Back To Main](/README.md)