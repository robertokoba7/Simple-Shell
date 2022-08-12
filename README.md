Simple_shell
---
This is a simple UNIX command interpreter based on bash and Sh.

Overview
---

hsh is a sh-compatible command language interpreter that executes commands read from the standard input or from a file.

Invocation
---

```gcc -Wall -Werror -Wextra -pedantic *.c -o hsh
./hsh
```
Environment
---
Upon invocation, hsh receives and copies the environment of the parent process in which it was executed. This environment is an array of name-value strings describing variables in the format NAME=VALUE. A few key environmental variables are:

**HOME**

The home directory of the current user and the default directory argument for the **cd** builtin command.

```
$ echo "echo $HOME" | ./hsh
/home/vagrant

```

**PWD**
The current working directory as set by the cd command.

```
$ echo "echo $PWD" | ./hsh
/home/vagrant/simple_shell

```

OLDPWD
The previous working directory as set by the cd command.

**Variable Replacement**
hsh nterprets the $ character for variable replacement.

Example:
```
$ echo "echo 'hello' ; echo 'world'" | ./hsh
'hello'
'world'
```

**&& - AND logical operator**

```command1 && command2:``` ```command2``` is executed if, and only if, command1 returns an exit status of zero.

Example:
```
$ echo "error! && echo 'holberton'" | ./hsh
./shellby: 1: error!: not found
$ echo "echo 'my name is' && echo 'Robert'" | ./hsh
'my name is'
'Robert'
```

**|| - OR logical operator**

```command1 || command2:``` ```command2``` is executed if, and only if, command1 returns a non-zero exit status.

Example:
```
$ echo "error! || echo 'wait for it'" | ./hsh
./hsh: 1: error!: not found
'wait for it'
```

The operators ```&&``` and ```||``` have equal precedence, followed by ;.

**Builtin Commands**
cd
Usage: ```cd [DIRECTORY]```
Changes the current directory of the process to ```DIRECTORY.```
If no argument is given, the command is interpreted as ```cd $HOME.```
If the argument ```-``` is given, the command is interpreted as ```cd $OLDPWD``` and the pathname of the new working directory is printed to standad output.
If the argument, ```--``` is given, the command is interpreted as cd $OLDPWD but the pathname of the new working directory is not printed.
The environment variables ```PWD``` and ```OLDPWD``` are updated after a change of directory.
Example:
```
$ ./hsh
^-^ pwd
/home/vagrant/holberton/simple_shell
$ cd ../
^-^ pwd
/home/vagrant/holberton
^-^ cd -
^-^ pwd
/home/vagrant/holberton/simple_shell
```

exit
Usage: exit [STATUS]
Exits the shell.
The STATUS argument is the integer used to exit the shell.
If no argument is given, the command is interpreted as exit 0.
Example:
```
$ ./hsh
$ exit
```

**env**
Usage: env
Prints the current environment.
Example:
```
$ ./hsh
$ env
NVM_DIR=/home/vagrant/.nvm
...
```

**setenv**
Usage: setenv ```[VARIABLE] [VALUE]```
Initializes a new environment variable, or modifies an existing one.
Upon failure, prints a message to stderr.
Example:
```
$ ./hsh
$ setenv NAME ALX
$ echo $NAME
ALX
```

**unsetenv**
Usage: ```unsetenv [VARIABLE]```
Removes an environmental variable.
Upon failure, prints a message to stderr.
Example:

```
$ ./hsh
$ setenv NAME ALX
$ unsetenv NAME
$ echo $NAME

$
```



Authors & Copyrights
---
* Robert okoba
* Marren Nyagaya

