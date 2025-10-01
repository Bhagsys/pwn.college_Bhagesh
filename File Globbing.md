# File Globbing

## Matching With
The challenge is about shell globbing with * (wildcard) and using it to change directories. The * matches any part of a filename (except a leading . or /), and the shell expands the pattern before the command runs. The level asks you, starting from your home directory, to cd into /challenge while passing at most four characters as the argument to cd.

### Solve
**Flag:** `pwn.college{ALN6-aRGUBg2gl7Q4_5fAsPC1fd.QXxIDO0wyM4kjNzEzW}`

Using *c as a path name for challenge to change directories much quicker then executing /challenge/run

```This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{ALN6-aRGUBg2gl7Q4_5fAsPC1fd.QXxIDO0wyM4kjNzEzW}
hacker@globbing~matching-with-:/challenge$ 
```

### New Learnings
is a filename wildcard: the shell expands patterns like /c* into matching filesystem names before running the command. The argument you type can be very short; the shell will expand it to the full pathname if a match exists.

### References 




## Matching With ?
The challenge is about the single-character wildcard ?. Unlike *, which matches any string (including empty), ? matches exactly one character. The task: starting from your home directory, cd into /challenge but use ? in place of the letters c and l in the argument you pass to cd. Then run /challenge/run for the flag.

### Solve
**Flag:** `pwn.college{0wkwLGYbeYX-aGY7zEJYfwtgDbW.QXyIDO0wyM4kjNzEzW}`

I used a pattern where each ? stands for a single character. Replacing c and both l characters in challenge with ? gives the pattern /?ha??enge, which the shell expanded to /challenge before cd ran:

```This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{0wkwLGYbeYX-aGY7zEJYfwtgDbW.QXyIDO0wyM4kjNzEzW}
hacker@globbing~matching-with-:/challenge$ 
```

### New Learnings
? matches exactly one character in shell globbing; multiple ?s match multiple single characters. You can replace specific letters in a known name with ? to build concise patterns that still uniquely identify the target. Use * when you want variable-length matches and ? when you need precise single-character substitution.

### References 



## Matching With []
The challenge is about bracket globs ([...]) — a single-character wildcard that matches one character from a specified set. The task was to change into /challenge/files and run /challenge/run with a single argument that expands (via bracket-globbing) into file_b, file_a, file_s, and file_h.

### Solve
**Flag:** `pwn.college{oMkkcd4itbA3z8y0kMkdCQCsYcG.QXzIDO0wyM4kjNzEzW}`

Entered each distinct letter a b h s as glob in the bracket

```hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run
Error: you did not use a square bracket glob...
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file[]
Your expansion did not expand to the requested files (file_a, file_b, file_h, 
and file_s). Instead, it expanded to:
file[]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file[abhs]
Your expansion did not expand to the requested files (file_a, file_b, file_h, 
and file_s). Instead, it expanded to:
file[abhs]
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[abhs]
You got it! Here is your flag!
pwn.college{oMkkcd4itbA3z8y0kMkdCQCsYcG.QXzIDO0wyM4kjNzEzW}
hacker@globbing~matching-with-:/challenge/files$
```

### New Learnings
The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets.

### References 





## Matching Paths With []
The challenge is about using bracket globs ([...]) to expand entire absolute paths. Globbing is performed per pathname component, so you can write a single argument that expands into several absolute file paths.

### Solve
**Flag:** `pwn.college{IattnSt1c0uI23Nk_hQDv2OsGDq.QX0IDO0wyM4kjNzEzW}`

Entered each distinct letter a b h s as glob in the bracket in an absolute path statement

```hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{IattnSt1c0uI23Nk_hQDv2OsGDq.QX0IDO0wyM4kjNzEzW}
hacker@globbing~matching-paths-with-:~$ 
```

### New Learnings
Bracket globs [...] can be used inside absolute paths '/challenge/files/file_[bash]' to expand into multiple full pathnames. Globbing happens before the command runs, so the program receives separate arguments for each matched file path.

### References 




## Multiple globs
The challenge is about using multiple glob metacharacters in a single word. Bash allows more than one * in the same argument; for example fl* matches any pathname that contains an f followed later by an l. In this level you must cd into /challenge/files and run /challenge/run with a single short (3 characters or less) globbed word that contains two * and matches every filename that contains the letter p.

### Solve
**Flag:** `pwn.college{4q0aWwEpZFpYTAeDVrUfshNcvjN.0lM3kjNxwyM4kjNzEzW}`

I used the three‑character pattern p (two * characters with p between them). From /challenge/files the shell expands p into every filename that contains p, and I passed that expanded list as the single argument to /challenge/run:

```hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run/*p*
bash: /challenge/run/*p*: Not a directory
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{4q0aWwEpZFpYTAeDVrUfshNcvjN.0lM3kjNxwyM4kjNzEzW}
hacker@globbing~multiple-globs:/challenge/files$ 
```

### New Learnings
You can include multiple * wildcards in a single argument (e.g., p), and the shell will expand that one word into all matching filenames before the command runs. p is three characters long and contains two * characters, satisfying the level’s constraints while matching any name that contains p.

### References 




## Mixing globs
The challenge is about combining the glob techniques you’ve learned to produce a single short glob (6 characters or less) that matches multiple differently-named files. The target files are challenging, educational, and pwning, and you must pass one globbed argument to /challenge/run that expands to those filenames.

### Solve
**Flag:** `pwn.college{M99IDtE3Dp3mtOGD3RIPodb35VG.QX1IDO0wyM4kjNzEzW}`

Change cd to /challenge/files ,then go to /challenge/run with glob with arguments from the 3 files (c,e,p)

```hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{M99IDtE3Dp3mtOGD3RIPodb35VG.QX1IDO0wyM4kjNzEzW}
hacker@globbing~mixing-globs:/challenge/files$ 
```

### New Learnings
File globs can be used anywhere in the statement

### References 



## Exclusionary glowing
The challenge is about using an inverted bracket glob ([!...] or [^...]) to select filenames that do not start with certain characters. You must pass a single globbed argument to /challenge/run that expands to all files in /challenge/files whose first character is not p, w, or n.

### Solve
**Flag:** `pwn.college{EgMQwtEhCCN5xqruuUKqsHK-f8V.QX2IDO0wyM4kjNzEzW}`

Change cd to /challenge/files ,then go to /challenge/run with glob with arguments with ! To exclude those files

```hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run/file_[!pwn]
bash: /challenge/run/file_[!pwn]: Not a directory
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run/file_[!pwn]*
bash: /challenge/run/file_[!pwn]*: Not a directory
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{EgMQwtEhCCN5xqruuUKqsHK-f8V.QX2IDO0wyM4kjNzEzW}
hacker@globbing~exclusionary-globbing:/challenge/files$
```

### New Learnings
! or ^ list files that are not under by the file globs.

### References 



## Tab completion
The challenge demonstrates using the shell’s tab completion to complete a filename you are unable (or discouraged) to type fully. The file /challenge/pwncollege is present but typing it directly fails; pressing lets the shell expand the partial name into the correct full filename so you can cat it.

### Solve
**Flag:** `pwn.college{Y_kOmxULPfqTE0Vg6czNyeu-grk.0FN0EzNxwyM4kjNzEzW}`

I listed /challenge to confirm the entry and then used tab-completion to expand the partial name before running cat:

```hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{Y_kOmxULPfqTE0Vg6czNyeu-grk.0FN0EzNxwyM4kjNzEzW}
```
### New Learnings
Tab can be used to complete the file path

### References 




## Multiple Options for Tab Completion
The challenge explores what happens when tab-completion has more than one possible match. Different shells/configurations handle this differently (bash usually completes up to the common prefix and a second TAB lists candidates; other shells may cycle). The level places many files starting with pwncollege under /challenge/files; you must use tab completion from a sensible prefix to reach the flag file and cat it.

### Solve
**Flag:** `pwn.college{YwS-OAfMjWlOLO7HC_TVuSsh-ET.0lN0EzNxwyM4kjNzEzW}`

I listed /challenge to confirm the entry and then used tab-completion to expand the partial name before running cat:

```hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ /challenge/files/
hack-the-planet        pwn-the-planet         pwncollege-flyswatter
pwn                    pwncollege-family      pwncollege-hacking
pwn-college            pwncollege-flamingo    
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat /challenge/files/
hack-the-planet        pwn-the-planet         pwncollege-flamingo
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat /challenge/files/
hack-the-planet        pwn-the-planet         pwncollege-flamingo
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking 
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat /challenge/files/pwncollege-
pwncollege-family      pwncollege-flamingo    pwncollege-hacking
pwncollege-flag        pwncollege-flyswatter   
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat /challenge/files/pwncollege-flag
pwn.college{YwS-OAfMjWlOLO7HC_TVuSsh-ET.0lN0EzNxwyM4kjNzEzW}
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ 
```
### New Learnings
if there are multiple files that match the text they are all displayed together Pressing TAB twice in bash is a quick way to see all completion candidates so you can choose a longer prefix.

### References





## Tab Completion on Command
The challenge demonstrates that tab completion works for commands as well as filenames. A command beginning with pwncollege is available in the environment; typing its prefix and pressing will complete the command name so you can run it and get the flag.

### Solve
**Flag:** `pwn.college{Ey78c5dAI2xBrwtiY0xlR7JqHDH.0VN0EzNxwyM4kjNzEzW}`

Type pwncollege, hit tab and run command

```hacker@globbing~tab-completion-on-commands:~$ pwncollege-26126 
Correct! Here is your flag:
pwn.college{Ey78c5dAI2xBrwtiY0xlR7JqHDH.0VN0EzNxwyM4kjNzEzW}
hacker@globbing~tab-completion-on-commands:~$ 
```
### New Learnings
Tab can be used to autocomplete commands Completion prevents typing errors and is faster than remembering full command names.

### References






