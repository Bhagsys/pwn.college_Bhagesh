#Citadel CTF

## The Path Variable
In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you

### Solve
**Flag:** `pwn.college{Qg3vL8bHh5AFAqPUpV-ffVwT-1b.QX2cDM1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Qg3vL8bHh5AFAqPUpV-ffVwT-1b.QX2cDM1wyM4kjNzEzW}
hacker@path~the-path-variable:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user