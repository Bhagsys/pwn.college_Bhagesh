## learning from documentation
The challenge is about reading documentation to discover the correct command-line arguments a program expects. The program /challenge/challenge requires a specific argument (--giveflag) according to its documentation, so invoking it without that argument will not produce the flag.

### Solve
**Flag:** `pwn.college{wXTW7_m_XbHzCXYaM0IZ1AcrnDa.QX0ITO0wyM4kjNzEzW}`


```hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{wXTW7_m_XbHzCXYaM0IZ1AcrnDa.QX0ITO0wyM4kjNzEzW}
hacker@man~learning-from-documentation:~$ 
```

### New Learnings
The correct usage of programs depends, in a large part, on the proper specification of arguments to them




## Learning Complex Usage
The challenge is about reading documentation to discover the correct command-line arguments a program expects. The program /challenge/challenge requires a specific argument (--giveflag) according to its documentation, so invoking it without that argument will not produce the flag.

### Solve
**Flag:** `pwn.college{wXTW7_m_XbHzCXYaM0IZ1AcrnDa.QX0ITO0wyM4kjNzEzW}`


```hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](/linux-luminarium/commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{IU3CRuePg6VWnBnUma1YGFhLleT.QX1ITO0wyM4kjNzEzW}
hacker@man~learning-complex-usage:~$ 
```

### New Learnings
ability to read and apply program documentation to correctly construct complex command-line arguments.



## Reading Manuals
The challenge is about learning to use the man command to read a program's manual page and discover a secret option that causes the program to print the flag

### Solve
**Flag:** `pwn.college{o4QBpVIP-z1wq2Lv-Q-hS4lib_g.QX0EDO0wyM4kjNzEzW}`

Using the man command I see the description for the command where the arguments are listed which give out the flag


```hacker@man~reading-manuals:~$ man yes
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge - print the flag!
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:~$ /challenge/challenge - print the flag
Incorrect usage! Please read the challenge man page!
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --opzwqv 412
Correct usage! Your flag: pwn.college{o4QBpVIP-z1wq2Lv-Q-hS4lib_g.QX0EDO0wyM4kjNzEzW}
hacker@man~reading-manuals:~$ 

```

### New Learnings
Man command is used for manual for a command





## Reading Manuals
The challenge is about learning to use the man command to read a program's manual page and discover a secret option that causes the program to print the flag

### Solve
**Flag:** `pwn.college{sr49RhA4m-uKhQDWWpjJdXidcPG.QX1EDO0wyM4kjNzEzW}`

Using the man command I see the description for the command where the arguments are listed which gives out the flag


```hacker@man~searching-manuals:~$ man challenge

gzip: stdout: Broken pipe
hacker@man~searching-manuals:~$ /challenge/challenge --ettkdw
Initializing...
Correct usage! Your flag: pwn.college{sr49RhA4m-uKhQDWWpjJdXidcPG.QX1EDO0wyM4kjNzEzW}
hacker@man~searching-manuals:~$ 
```

### New Learnings
The manual page supports incremental searching: type /pattern to search forward and ?pattern to search backward. After a search, use n to jump to the next match and N to go to the previous match — this is much faster than manual scrolling for long pages.




## Searching For Manuals
The challenge is about learning to use the man command to read a program's manual page and discover a secret option that causes the program to print the flag

### Solve
**Flag:** `pwn.college{sIf5yRwsfL-m2OzGJNb-2CO8A_f.QX2EDO0wyM4kjNzEzW}`

I used the manpage for man to learn how to search the man database, found 'sfywsfmzbf' for the challenge, and then ran /challenge/challenge with the discovered option and obtained the flag


```hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
sfywsfmzbf (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man sfywsfmzbf
hacker@man~searching-for-manuals:~$ man sfywsfmzbf
hacker@man~searching-for-manuals:~$ /challenge/challenge --sfywsf 522
Correct usage! Your flag: pwn.college{sIf5yRwsfL-m2OzGJNb-2CO8A_f.QX2EDO0wyM4kjNzEzW}
hacker@man~searching-for-manuals:~$ 
```

### New Learnings
man man is the authoritative place to learn advanced man usage; it documents tools like -k to search the man database. 'man -k (keyword)' searches the manpage short descriptions and returns matching entries even if the filenames are randomized.




## Helping Programs
The challenge is about discovering quick program documentation using the common --help flags. Some programs do not ship a manpage, but will print usage information when invoked with --help, -h, or other help-style options.

### Solve
**Flag:** `pwn.college{kCnur_IBgWYRTzr_BjG3J68VsB7.QX3IDO0wyM4kjNzEzW}`



```hacker@man~helpful-programs:~$ --help
bash: --help: command not found
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give
                        you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 368
hacker@man~helpful-programs:~$ /challenge/challenge -368
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: unrecognized arguments: -368
hacker@man~helpful-programs:~$ /challenge/challenge -g 368
Correct usage! Your flag: pwn.college{kCnur_IBgWYRTzr_BjG3J68VsB7.QX3IDO0wyM4kjNzEzW}
hacker@man~helpful-programs:~$ 
```

### New Learnings
Many programs support a quick help option; the most common is --help, but -h, help, or -? are also used. Using --help is safe and non-destructive — it’s a good first step before trying unknown options.




## Help For Bulitins
The challenge is about shell builtins — commands implemented inside the shell itself — and using the shell's help builtin to read their documentation.

### Solve
**Flag:** `pwn.college{YXeqPiRpT58sS58-3Bvam9lf53d.QX0ETO0wyM4kjNzEzW}`

I used the shell help builtin to read the documentation for the challenge builtin, discovered the secret option, and invoked the builtin with that option to print the flag:

```hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "YXeqPiRp".
hacker@man~help-for-builtins:~$ challenge --secrect YXeqPiRp
Incorrect usage! Please read the help page for the challenge builtin!
hacker@man~help-for-builtins:~$ challenge --secret YXeqPiRp
Correct! Here is your flag!
pwn.college{YXeqPiRpT58sS58-3Bvam9lf53d.QX0ETO0wyM4kjNzEzW}
```

### New Learnings
Builtins are implemented inside the shell and are documented with the help builtin: help lists builtins and help shows the usage for a specific builtin.
