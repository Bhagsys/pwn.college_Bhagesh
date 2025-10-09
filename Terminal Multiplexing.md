#Terminal Multiplexing

##Launching Screen
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{I33ZaZ28yIgH1RssPnyokJTtVKR.0VN4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{I33ZaZ28yIgH1RssPnyokJTtVKR.0VN4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$ cat /flag 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



##Detaching and Attaching
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{4iv5COIj6UoPQi1SPnXWwUWEpvJ.0lN4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 148.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 148.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 148.pts-0.terminal-multiplexing~detaching-and-attaching]

Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{I33ZaZ28yIgH1RssPnyokJTtVKR.0VN4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$ cat /flag 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



##Finding Sessions
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{08hbPK-9Svkf9Ii9aU3R94zOXNK.01N4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~finding-sessions:~$ screem -ls
bash: screem: command not found
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        156.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        144.session_8cee30a9ff5ef6af    (Detached)
        147.session_c36667701debc910    (Detached)
        150.session_1760878f2f80ffed    (Detached)
4 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_8cee30a9ff5ef6af
[detached from 144.session_8cee30a9ff5ef6af]

hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{08hbPK-9Svkf9Ii9aU3R94zOXNK.01N4IDOxwyM4kjNzEzW}
pwn.college{08hbPK-9Svkf9Ii9aU3R94zOXNK.01N4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~finding-sessions:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Switching Windows
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~switching-windows:~$ screen -r
[screen is terminating]

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~switching-windows:~$
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Detaching and Attaching (tmux)
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[exited]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach

<atulations, here is your flag: pwn.college{wYx14D0a9k8BVbjTv30LY69KWJE.0VO4IDOxwyM4kjNzEzW}
Congratulations, here is your flag: pwn.college{wYx14D0a9k8BVbjTv30LY69KWJE.0VO4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Detaching and Attaching (tmux)
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{wYx14D0a9k8BVbjTv30LY69KWJE.0VO4IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[exited]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach

<atulations, here is your flag: pwn.college{wYx14D0a9k8BVbjTv30LY69KWJE.0VO4IDOxwyM4kjNzEzW}
Congratulations, here is your flag: pwn.college{wYx14D0a9k8BVbjTv30LY69KWJE.0VO4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Switching Windows(tmux)
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{kx-OXDfQmaaC8vASCFl0IUioGLE.0FM5IDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux

hacker@terminal-multiplexing~switching-windows-tmux:~$ Here is your flag: pwn.college{kx-OXDfQmaaC8vASCFl0IUioGLE.0FM5IDOxwyM4kjNzEzW}
```

### New Learnings
Su is used to switch user, usually used to switch to the root user