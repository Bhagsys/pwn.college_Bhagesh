#Perceiving Permissions

## Using sudo
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{AN72FnNcYLSrz4xMwWwP8M8k66W.QXxEjN0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{AN72FnNcYLSrz4xMwWwP8M8k66W.QXxEjN0wyM4kjNzEzW}
hacker@permissions~changing-file-ownership:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Groups and Files
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{IKoK5digDVLeTJBwwE-DNnHMcVc.QXxcjM1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{IKoK5digDVLeTJBwwE-DNnHMcVc.QXxcjM1wyM4kjNzEzW}
hacker@permissions~groups-and-files:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Fun with Groups Names
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{48PVTTZIYyL50fHAxlmvb2s9mS_.QXycjM1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~fun-with-groups-names:~$ chgrp grp11474 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{48PVTTZIYyL50fHAxlmvb2s9mS_.QXycjM1wyM4kjNzEzW}
hacker@permissions~fun-with-groups-names:~$  
```

### New Learnings
Su is used to switch user, usually used to switch to the root user





## Changing Permissions
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{M88VPtrW_uXCpIqfxKsCghHcKFP.QXzcjM1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~changing-permissions:~$ chmod a-rwx /flag
hacker@permissions~changing-permissions:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-permissions:~$ chmod u+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~changing-permissions:~$ chmod a+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{M88VPtrW_uXCpIqfxKsCghHcKFP.QXzcjM1wyM4kjNzEzW}  
```

### New Learnings
Su is used to switch user, usually used to switch to the root user





## Executable files
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{8lCnJQIySNOrZ78osoQYC-Khsxr.QXyEjN0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~executable-files:~$ chmod o-x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{8lCnJQIySNOrZ78osoQYC-Khsxr.QXyEjN0wyM4kjNzEzW}
hacker@permissions~executable-files:~$  
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Permission Tweaking Practices
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{MVmNELZjPZSlXR1sJkuXXxYI8cg.QXwEjN0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{MVmNELZjPZSlXR1sJkuXXxYI8cg.QXwEjN0wyM4kjNzEzW}
hacker@permissions~permission-tweaking-practice:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Permission Setting Practices
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{wq7RJY84YDoa4DCgJ1DYBRCOxfM.QXzETO0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=-,o=rwx /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": --x---rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r----x---
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=x,o=- /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": r----x---
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw--wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=rw,o=wx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": rw-rw--wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxr-x-w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=rx,o=w /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rwxr-x-w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr-x--x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ 
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=rx,o=x /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r-xr-x--x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw---x-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=x,o=w /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rw---x-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r---wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=r,o=wx /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": -w-r---wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-xr--r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=r,o=r /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod a+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{wq7RJY84YDoa4DCgJ1DYBRCOxfM.QXzETO0wyM4kjNzEzW}
hacker@permissions~permissions-setting-practice:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## The SUID Bit
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{Ec_YBjQye4jQXR7EFgnZ_MtmpFb.QXzEjN0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# 
root@permissions~the-suid-bit:~# cat /flag
pwn.college{Ec_YBjQye4jQXR7EFgnZ_MtmpFb.QXzEjN0wyM4kjNzEzW}
root@permissions~the-suid-bit:~#  
```

### New Learnings
Su is used to switch user, usually used to switch to the root user
