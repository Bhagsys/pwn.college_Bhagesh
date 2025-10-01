# Shell Variables

## Printing Variables
You can also print out variables with echo, by prepending the variable name with a $

### Solve
**Flag:** `pwn.college{gJ8_ViPA2QxsmCslno1KtmizIZ-.QX3UTN0wyM4kjNzEzW}`

Typed echo $flag

```hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{gJ8_ViPA2QxsmCslno1KtmizIZ-.QX3UTN0wyM4kjNzEzW}
hacker@variables~printing-variables:~$ 
```

### New Learnings
You can also print out variables using echo

### References 



## setting Variables
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

### Solve
**Flag:** `pwn.college{IiOW4yTsZ2Hcw1dapY_BIlJWYCf.QX5UTN0wyM4kjNzEzW}`

Set variable PWN to COLLEGE 

```hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IiOW4yTsZ2Hcw1dapY_BIlJWYCf.QX5UTN0wyM4kjNzEzW}
```

### New Learnings
You can write values to variables and then read them out 

### References



## Multi-word Variables
Here, the shell reads 1337 SAUCE as a single token, and happily sets that value to VAR. In this level, you'll need to set the variable PWN to COLLEGE YEAH.

### Solve
**Flag:** `pwn.college{keYJ7YKbNjes2hVDkobvMmunB-M.QXwYTN0wyM4kjNzEzW}`

 Set variable PWN to COLLEGE YEAH, in quotes

```hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{keYJ7YKbNjes2hVDkobvMmunB-M.QXwYTN0wyM4kjNzEzW}
hacker@variables~multi-word-variables:~$ 
```

### New Learnings
When the shell sees a space, it ends the variable assignment and interprets the next word so you need to quote it

### References



## Exporting Variables
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run).

### Solve
**Flag:** `pwn.college{keYJ7YKbNjes2hVDkobvMmunB-M.QXwYTN0wyM4kjNzEzW}`

 Export PWN set to COLLEGE and set COLLEGE to PWN the run /challenge/run

```hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{oH17cUaHqKxDOJMmwhlOM_x88RE.QXyYTN0wyM4kjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ 
```

### New Learnings
understanding the crucial distinction between local shell variables and exported environment variables

### References



## Printing Exported Variables
the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable

### Solve
**Flag:** `pwn.college{cHWOkdfFzRc0qEZwvT-pX8i_Ujt.QX4UTN0wyM4kjNzEzW}`

Invoke the env command

```hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=a098fca184c5bf6b5670bd97b4eae99bc9eb37823062298e62c0e2e0a7c0c507
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{cHWOkdfFzRc0qEZwvT-pX8i_Ujt.QX4UTN0wyM4kjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
hacker@variables~printing-exported-variables:~$ 
```

### New Learnings
Env is another way to access variables in bash

### References



## Storing Command Output
Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

### Solve
**Flag:** `pwn.college{MKlNZ49SO4tBo8XdbkQ7V4kDO79.QX1cDN1wyM4kjNzEzW}`

Read the output of /challenge/run command into the variable PWN

```hacker@variables~storing-command-output:~$ PWN=$( /challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{MKlNZ49SO4tBo8XdbkQ7V4kDO79.QX1cDN1wyM4kjNzEzW}
hacker@variables~storing-command-output:~$ 
```

### New Learnings
You can also use backticks instead of brackets

### References



## Reading Input
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE.

### Solve
**Flag:** `pwn.college{g_JZ_MNZ3xsC4Zm96c4-jWuiler.QX4cTN0wyM4kjNzEzW}`

Read PWN and input value COLLEGE

```hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{g_JZ_MNZ3xsC4Zm96c4-jWuiler.QX4cTN0wyM4kjNzEzW}
hacker@variables~reading-input:~$ 
```

### New Learnings
read reads data from your standard input

### References


## Reading Files
read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

### Solve
**Flag:** `pwn.college{8VU93YjJfYBPk_IJkcz2b3XCMHy.QXwIDO0wyM4kjNzEzW}`

Read PWN then set /challenge/run to the variable and run it

```hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8VU93YjJfYBPk_IJkcz2b3XCMHy.QXwIDO0wyM4kjNzEzW}
hacker@variables~reading-files:~$ 
```

### New Learnings
learned to combine the read shell builtin with input redirection (<) to directly pipe a file's contents into a shell variable.

### References