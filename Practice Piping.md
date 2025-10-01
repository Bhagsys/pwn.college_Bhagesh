# Practice Piping

## Redirecting output
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Solve
**Flag:** `pwn.college{MkLxiopY97RuN02dIka-gV9McYw.QX0YTN0wyM4kjNzEzW}`

Redirect PWN word to file COLLEGE using >

```You may have created a PWN file instead of a COLLEGE file.
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{MkLxiopY97RuN02dIka-gV9McYw.QX0YTN0wyM4kjNzEzW}
hacker@piping~redirecting-output:~$ 
```

### New Learnings
'>' redirects a program’s standard output to a file, creating or overwriting it. echo is a simple way to emit strings.

### References



## Redirecting more output
In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file

### Solve
**Flag:** `pwn.college{Y7ocWdJzTJY_XTdL7PqUr4ySnez.QX1YTN0wyM4kjNzEzW}`

/challenge/run redirected to my flag then using cat the my flag file is read

```hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Y7ocWdJzTJY_XTdL7PqUr4ySnez.QX1YTN0wyM4kjNzEzW}

hacker@piping~redirecting-more-output:~$ 
```

### New Learnings
'>' redirects a program’s standard output to a file, creating or overwriting it. echo is a simple way to emit strings.

### References



## Redirecting more output
In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file

### Solve
**Flag:** `pwn.college{Y7ocWdJzTJY_XTdL7PqUr4ySnez.QX1YTN0wyM4kjNzEzW}`

/challenge/run redirected to my flag then using cat the my flag file is read

```hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Y7ocWdJzTJY_XTdL7PqUr4ySnez.QX1YTN0wyM4kjNzEzW}

hacker@piping~redirecting-more-output:~$ 
```

### New Learnings
'>' redirects a program’s standard output to a file, creating or overwriting it. echo is a simple way to emit strings.

### References



## Appending output
The challenge is about append-mode redirection using >>. The level writes the first half of the flag into /home/hacker/the-flag on its first invocation and prints the second half to stdout — if you append stdout to the same file the second half will be concatenated to the first and you'll get the full flag. If you instead use > on the second run you’ll truncate the file and lose the first half.

### Solve
**Flag:** `pwn.college{oNIhl9QZqvH7L_g0CYh1F73UKOZ.QX3ATO0wyM4kjNzEzW}`

/challenge/run redirected to my flag then using cat the my flag file is read

```hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /theflag
cat: /theflag: No such file or directory
hacker@piping~appending-output:~$ cat ~/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{oNIhl9QZqvH7L_g0CYh1F73UKOZ.QX3ATO0wyM4kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$ 
```

### New Learnings
write data to a file in append mode whereas > overwrites it

### References



## redirecting errors
The challenge is about redirecting both stdout and stderr to separate files using file descriptor numbers. You must capture the flaginto myflag. and capture the program’s instructions into instructions. Because you redirect both streams, nothing should appear on the terminal — the flag will be in myflag and the human-readable messages will be in instructions.

### Solve
**Flag:** `pwn.college{I_3cXiaEOTxUiyGu7rIPjgP_fa8.QX3YTN0wyM4kjNzEzW}`

/challenge/run redirected to my flag and errors to instruction then using cat the myflag file is read

```hacker@piping~redirecting-errors:~$ /challenge/run >myflag 2>instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{I_3cXiaEOTxUiyGu7rIPjgP_fa8.QX3YTN0wyM4kjNzEzW}

hacker@piping~redirecting-errors:~$ 
```

### New Learnings
You can redirect errors 

### References




## redirecting input
using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

### Solve
**Flag:** `pwn.college{k1G6AdfyNo8d0GddHfYcHImnM2c.QXwcTN0wyM4kjNzEzW}`

/challenge/run redirected to my flag and errors to instruction then using cat the myflag file is read

```hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{k1G6AdfyNo8d0GddHfYcHImnM2c.QXwcTN0wyM4kjNzEzW}
hacker@piping~redirecting-input:~$ 
```

### New Learnings
you can redirect input to programs! This is done using <

### References




## Grepping stored results
This level combines redirection and searching: you must capture a large program output into a file and then grep that file for the flag.

### Solve
**Flag:** `pwn.college{Yyrce2aV1iHBdYwSFrEWakbPPDp.QX4EDO0wyM4kjNzEzW}`

Redirected then used grep to get the flag

```hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn /tmp/data.txt
pwning
pwn
pwned
pwns
pwn.college{Yyrce2aV1iHBdYwSFrEWakbPPDp.QX4EDO0wyM4kjNzEzW}
hacker@piping~grepping-stored-results:~$  
```

### New Learnings
The pipe | feeds stdout of one command into stdin of another, enabling streaming workflows

### References



## Grepping live output
The challenge is about piping live program output into grep so you can search a stream without first writing it to disk. The | operator connects stdout of the left-hand command to stdin of the right-hand command, so you can run /challenge/run and immediately filter its output for the flag.

### Solve
**Flag:** `pwn.college{oZmzkXekUgEoCfLIAHdMCFljEiv.QX5EDO0wyM4kjNzEzW}`

I followed the instructions and ran the path followed by | grep pwn to get the flag 

```hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn
pwning
pwned
pwn.college{oZmzkXekUgEoCfLIAHdMCFljEiv.QX5EDO0wyM4kjNzEzW}
pwns
hacker@piping~grepping-live-output:~$ 

```

### New Learnings
The pipe | feeds stdout of one command into stdin of another, enabling streaming workflows

### References



## Grepping errors
This level teaches how to search (grep) text that a program writes to standard error (FD 2). Pipes (|) only connect stdout (FD 1) to the next command, so to grep stderr you first redirect stderr into stdout and then pipe the combined stream into grep.

### Solve
**Flag:** `pwn.college{4FqqDlJQJ9zzWb_35SgjgPr0dUL.QX1ATO0wyM4kjNzEzW}`



```hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwned
pwning
pwns
pwn
pwn.college{4FqqDlJQJ9zzWb_35SgjgPr0dUL.QX1ATO0wyM4kjNzEzW}
hacker@piping~grepping-errors:~$ 
```

### New Learnings
2>&1 makes stderr (fd 2) go to the same place as stdout (fd 1), so subsequent | pipes will see the former. |& is a bash (and some other shells) shorthand for 2>&1 |.


### References



## Filtering with Grep -v
The challenge is about removing unwanted lines from a stream using grep -v (invert match). /challenge/run prints the real flag and many decoy lines that include the literal DECOY. Use grep -v 'DECOY' to remove those decoys and reveal the true flag.

### Solve
**Flag:** `pwn.college{E99Gf_Jsg13RoQQ7wF-BUnyhzT0.0FOxEzNxwyM4kjNzEzW}`



```hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{E99Gf_Jsg13RoQQ7wF-BUnyhzT0.0FOxEzNxwyM4kjNzEzW}
hacker@piping~filtering-with-grep-v:~$  
```

### New Learnings
grep -v PATTERN prints lines that do not match PATTERN — useful to remove noisy or decoy lines. Combining grep -v with a second grep for the desired pattern is a common, efficient pipeline: remove the junk, then pick the useful content.

### References




## Duplicating Piped Data with tee
/challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you

### Solve
**Flag:** `pwn.college{YHdxbmImwXQRaP8L9sQ2XOoGBTl.QXxITO0wyM4kjNzEzW}`



```hacker@piping~duplicating-piped-data-with-tee:~$ echo /challenge/run tee /challenge/college
/challenge/run tee /challenge/college
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn
cat: pwn: No such file or directory
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn | /challe
nge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "YHdxbmIm"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret YHdxbmIm | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{YHdxbmImwXQRaP8L9sQ2XOoGBTl.QXxITO0wyM4kjNzEzW}
hacker@piping~duplicating-piped-data-with-tee:~$ 
```

### New Learnings
Tee can be used to for debugging and pipeline analysis

### References




## Process Substitution for input
The challenge is about process substitution — using <(command) to present a running command’s stdout as a file-like argument — and using it to compare outputs of two commands with diff without creating any temporary files on disk.

### Solve
**Flag:** `pwn.college{MC0N_PrDQulDjMaiT9X2WPMXYbz.0lNwMDOxwyM4kjNzEzW}`

Using diff function I found the flag from the decoys 

```hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
17a18
> pwn.college{MC0N_PrDQulDjMaiT9X2WPMXYbz.0lNwMDOxwyM4kjNzEzW}
hacker@piping~process-substitution-for-input:~$ 
```

### New Learnings
<(givenfile) is a placeholder for the output of the given file

### References




## Writing to Multiple Programs
The challenge demonstrates writing the same stream of data as input to multiple commands by combining tee and output process substitution (>(...)). The goal here was to run /challenge/hack and deliver its output simultaneously as stdin to both /challenge/the and /challenge/planet, so that one (or both) of those consumers prints the flag.

### Solve
**Flag:** `pwn.college{cOWaflPAt9t8nLXc_PYuNZbF8Oi.QXwgDN1wyM4kjNzEzW}`

Using tee the secret data is entered into /challenge/the and /challenge/planet from /challenge/hack

```hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
1289177722248730942
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{cOWaflPAt9t8nLXc_PYuNZbF8Oi.QXwgDN1wyM4kjNzEzW}
hacker@piping~writing-to-multiple-programs:~$ 
```

### New Learnings
<(command) redirects input to given command

### References



## Split Piping stderr and stdout
The challenge is to send one program’s stdout into one consumer and its stderr into a different consumer, without mixing the two streams. The pipe operator (|) only connects stdout to the next command, and 2>&1 merges stderr into stdout (which mixes them). The clean solution is to use output process substitution (>(command)) to give the producer two writeable “files” — one for stdout and one for stderr — each hooked to a separate consumer.


### Solve
**Flag:** `pwn.college{MC0N_PrDQulDjMaiT9X2WPMXYbz.0lNwMDOxwyM4kjNzEzW}`

Used diff learned previously to remove the decoy flags

```hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
1a2
> pwn.college{MC0N_PrDQulDjMaiT9X2WPMXYbz.0lNwMDOxwyM4kjNzEzW}
hacker@piping~process-substitution-for-input:~$ 
```

### New Learnings
Process substitutions are expanded by the shell before launching the pipeline; the shell launches the consumer processes and supplies file-like paths for the producer to write to.

### References




## Named Pipes
This challenge introduces FIFOs / named pipes. You create a persistent pipe with mkfifo, then one process writes into it and another reads from it. Writers/readers block until the other side opens the FIFO, which gives automatic synchronization (handy for coordinating two processes). In this level you must create /tmp/flag_fifo and redirect stdout of /challenge/run into it so the challenge writes the flag into the FIFO — but because FIFOs block, you also need a reader open on the other end to receive the flag.

### Solve
**Flag:** `pwn.college{cPGZM-Ckk_kW5DluxI70GYwUsSH.01MzMDOxwyM4kjNzEzW}`

Using VSS code I split the terminal into two where I wrote into the fifo in one and read from the fifo in the other to get the flag

```hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{cPGZM-Ckk_kW5DluxI70GYwUsSH.01MzMDOxwyM4kjNzEzW}
hacker@piping~named-pipes:~$ 

hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
hacker@piping~named-pipes:~$ 
```

### New Learnings
FIFOs only executes a command when both read and write operations are acting on them

### References