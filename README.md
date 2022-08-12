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

#Authors & Copyrights
---
* Robert okoba
* Marren Nyagaya

