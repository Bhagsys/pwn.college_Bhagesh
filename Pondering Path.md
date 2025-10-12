#Pondering Path

## The Path Variable
In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you

### Solve
**Flag:** `pwn.college{Qg3vL8bHh5AFAqPUpV-ffVwT-1b.QX2cDM1wyM4kjNzEzW}`

Declare path to "" and then run /challenge/run to get the flag

```hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Qg3vL8bHh5AFAqPUpV-ffVwT-1b.QX2cDM1wyM4kjNzEzW}
hacker@path~the-path-variable:~$ 
```

### New Learnings
If u blank out the PATH variable, it wouldn't be able to find a file or directory 



## Setting PATH
This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.

### Solve
**Flag:** `pwn.college{s3952X6cE1PFBKl1B3es_WzCj-W.QX1cjM1wyM4kjNzEzW}`

Set path to /challenge/,ore_commands and run /challenge/run 

```hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{s3952X6cE1PFBKl1B3es_WzCj-W.QX1cjM1wyM4kjNzEzW}
hacker@path~setting-path:~$ 
```

### New Learnings
By adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name.



## Finding Commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory.

### Solve
**Flag:** `pwn.college{8ELBRsTxDEIRRG6EGSoxtpeUT6H.01NzEzNxwyM4kjNzEzW}`

Use which command to find win directory and run flag file  

```hacker@path~finding-commands:~$ which win
/challenge/paths/22875/win
hacker@path~finding-commands:~$ ls /challenge/paths/22875
flag  win
hacker@path~finding-commands:~$ cat /challenge/paths/22875/flag
pwn.college{8ELBRsTxDEIRRG6EGSoxtpeUT6H.01NzEzNxwyM4kjNzEzW}
hacker@path~finding-commands:~$ 
```

### New Learnings
Which is used to find the directory of a command



## Adding Commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory.

### Solve
**Flag:** `pwn.college{8ELBRsTxDEIRRG6EGSoxtpeUT6H.01NzEzNxwyM4kjNzEzW}`

Use which command to find path of win then use ls to see other files then run flag file

```hacker@path~finding-commands:~$ which win
/challenge/paths/22875/win
hacker@path~finding-commands:~$ ls /challenge/paths/22875
flag  win
hacker@path~finding-commands:~$ cat /challenge/paths/22875/flag
pwn.college{8ELBRsTxDEIRRG6EGSoxtpeUT6H.01NzEzNxwyM4kjNzEzW}
hacker@path~finding-commands:~$ 
```

### New Learnings
Which command gives directory of program



## Adding Commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory.

### Solve
**Flag:** `pwn.college{gEzvigItQXSwh8VGN3xZuRd0C8F.QX2cjM1wyM4kjNzEzW}`

Assign cat /flag to ~/,y_bin/win then assign path to ~/my_bin/win and run /challenge/run

```hacker@path~adding-commands:~$ echo 'cat /flag' > ~/my_bin/win
bash: /home/hacker/my_bin/win: No such file or directory
hacker@path~adding-commands:~$ mkdir ~/my_bin
hacker@path~adding-commands:~$ echo 'cat /flag' > ~/my_bin/win
hacker@path~adding-commands:~$ chmod +x ~/my_bin/win
hacker@path~adding-commands:~$ PATH=~/my_bin:$PATH
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{gEzvigItQXSwh8VGN3xZuRd0C8F.QX2cjM1wyM4kjNzEzW}
hacker@path~adding-commands:~$ 
```

### New Learnings
Assign lines to path files using >



## Hijacking Commands
This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.
How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it. What else can you create?

### Solve
**Flag:** `pwn.college{wsFBcUbgytWTKWp7THReWDH9VA0.QX3cjM1wyM4kjNzEzW}`

Assign #!/bin/bash to /tmp/my_bins/rm then add second line cat /flag then set path to /tmp/my_bins:$PATH and run challenge tricking the system into writing the flag into a fake rm and get the flag

```hacker@path~hijacking-commands:~$ mkdir /tmp/my_bins
hacker@path~hijacking-commands:~$ echo '#!/bin/bash' > /tmp/my_bins/rm
hacker@path~hijacking-commands:~$ echo 'cat /flag' >> /tmp/my_bins/rm
hacker@path~hijacking-commands:~$ chmod +x /tmp/my_bins/rm
hacker@path~hijacking-commands:~$ export PATH="/tmp/my_bins:$PATH"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/my_bins/rm. Executing!
pwn.college{wsFBcUbgytWTKWp7THReWDH9VA0.QX3cjM1wyM4kjNzEzW}
hacker@path~hijacking-commands:~$ 
```

### New Learnings
