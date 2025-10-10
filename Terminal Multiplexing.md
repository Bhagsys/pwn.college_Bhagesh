#Terminal Multiplexing

##Launching Screen
For this challenge, we've hooked things up so that just launching screen will get you the flag.

### Solve
**Flag:** `pwn.college{I33ZaZ28yIgH1RssPnyokJTtVKR.0VN4IDOxwyM4kjNzEzW}`

enter screen command

```Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{I33ZaZ28yIgH1RssPnyokJTtVKR.0VN4IDOxwyM4kjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$ cat /flag 
```

### New Learnings
screen opens a new screen session


##Detaching and Attaching
For this challenge, you'll need to:

Launch screen
Detach from it.
Run /challenge/run (this will secretly send the flag to your detached session!)
Reattach to see your prize

### Solve
**Flag:** `pwn.college{4iv5COIj6UoPQi1SPnXWwUWEpvJ.0lN4IDOxwyM4kjNzEzW}`

enter screen then pressed crtl +a +d to detatch and then run /challenge/run and reenter screen by using screen -r and get the flag 

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
screen -r is used to reenter a detatched screen and ctrl +a +d is used to detatch screen


##Finding Sessions
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys.

### Solve
**Flag:** `pwn.college{08hbPK-9Svkf9Ii9aU3R94zOXNK.01N4IDOxwyM4kjNzEzW}`

use screen -ls to see all active screens and then go to one of the active screens using screen -r (screen name) 

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
screen -ls is used to see all active screens


## Switching Windows
For this challenge, we've set up a screen session with two windows:

Window 0 has... well, you'll have to switch there to find out!
Window 1 has a welcome message
Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag.

### Solve
**Flag:** `pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}`

use screen -r then enter ctrl +a +0 and ctrl +a +1 to swtitch windows and get the flag 

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
Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows



## Detaching and Attaching (tmux)
For this challenge:

Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize.

### Solve
**Flag:** `pwn.college{AanurIRGRmLzK4g5eAW0r8YrROY.0FO4IDOxwyM4kjNzEzW}`

run tmux then exit usinf ctrl +b +d then run /challenge run and tmux attatch to get the flag

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
tmux attach or tmux a is used to reattach to session



## Switching Windows (tmux)
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
We've created a tmux session with two windows:

Window 0 has the flag!
Window 1 has your warm welcome.
Go get that flag.

### Solve
**Flag:** `pwn.college{kx-OXDfQmaaC8vASCFl0IUioGLE.0FM5IDOxwyM4kjNzEzW}`

run tmux then ctrl +a +0/1 to switch windows 

```hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux

hacker@terminal-multiplexing~switching-windows-tmux:~$ Here is your flag: pwn.college{kx-OXDfQmaaC8vASCFl0IUioGLE.0FM5IDOxwyM4kjNzEzW}
```

### New Learnings
The * shows your current window, and each entry also shows the process that the window was created to run.
