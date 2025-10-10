#Perceiving Permissions

## Changing File ownership
In this level, we will practice changing the owner of the /flag file to the hacker user, and then read the flag. For this challenge only, I made it so that you can use chown to your heart's content as the hacker user (again, typically, this requires you to be root).

### Solve
**Flag:** `pwn.college{AN72FnNcYLSrz4xMwWwP8M8k66W.QXxEjN0wyM4kjNzEzW}`

chown using hacker as the user and run /flag to get the flag

```hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{AN72FnNcYLSrz4xMwWwP8M8k66W.QXxEjN0wyM4kjNzEzW}
hacker@permissions~changing-file-ownership:~$ 
```

### New Learnings
Chown is used to change the ownership of a file to another user 




## Groups and Files
In this level, I have made the flag readable by whatever group owns it, but this group is currently root. Luckily, I have also made it possible for you to invoke chgrp as the hacker user! Change the group ownership of the flag file, and read the flag.

### Solve
**Flag:** `pwn.college{IKoK5digDVLeTJBwwE-DNnHMcVc.QXxcjM1wyM4kjNzEzW}`

use chgrp to change the group to hacker then run flag file

```hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{IKoK5digDVLeTJBwwE-DNnHMcVc.QXxcjM1wyM4kjNzEzW}
hacker@permissions~groups-and-files:~$ 
```

### New Learnings
group ownership can be changed with the chgrp command



## Fun with Groups Names
 in this level, that is not going to work. I'll still allow you to use chgrp, but I have randomized the name of the group that your user is in. You will need to use the id command to figure that name out, then chgrp to victory.
 
### Solve
**Flag:** `pwn.college{48PVTTZIYyL50fHAxlmvb2s9mS_.QXycjM1wyM4kjNzEzW}`

use id command to see all groups anf then use chgrp to run /flag 

```hacker@permissions~fun-with-groups-names:~$ chgrp grp11474 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{48PVTTZIYyL50fHAxlmvb2s9mS_.QXycjM1wyM4kjNzEzW}
hacker@permissions~fun-with-groups-names:~$  
```

### New Learnings
id command is used to display user and group information





## Changing Permissions
In this challenge, you must change the permissions of the /flag file to read it! Typically, you need to have write access to the file in order to change its permissions, but I have made the chmod command all-powerful for this level, and you can chmod anything you want even though you are the hacker user. This is an ultimate power. The /flag file is owned by root, and you can't change that, but you can make it readable.

### Solve
**Flag:** `pwn.college{M88VPtrW_uXCpIqfxKsCghHcKFP.QXzcjM1wyM4kjNzEzW}`

use chmod to change permissions to get the flag

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
r - user/group/other can read the file (or list the directory)
w - user/group/other can modify the files (or create/delete files in the directory)
x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- - nothing 



## Executable files
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable! Remember your chmod, and get /challenge/run to tell you the flag!

### Solve
**Flag:** `pwn.college{8lCnJQIySNOrZ78osoQYC-Khsxr.QXyEjN0wyM4kjNzEzW}`

set permissions to other permissions (o-x) 

```hacker@permissions~executable-files:~$ chmod o-x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{8lCnJQIySNOrZ78osoQYC-Khsxr.QXyEjN0wyM4kjNzEzW}
hacker@permissions~executable-files:~$  
```

### New Learnings
the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions.




## Permission Tweaking Practices
This challenge will ask you to change the permissions of the /challenge/pwn file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you chmod /flag to make it readable for yourself :-) Launch /challenge/run to get started!

### Solve
**Flag:** `pwn.college{MVmNELZjPZSlXR1sJkuXXxYI8cg.QXwEjN0wyM4kjNzEzW}`

complete using chmod according to the permissions required to get the flag  

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





## Permission Setting Practices
This level extends the previous level by requesting more radical permission changes, which you will need = and ,-chaining to achieve. 

### Solve
**Flag:** `pwn.college{wq7RJY84YDoa4DCgJ1DYBRCOxfM.QXzETO0wyM4kjNzEzW}`

similar approach using the question as refrence use chmod to get the flag

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
u=rw sets read and write permissions for the user, and wipes the execute permission
o=x sets only executable permissions for the world, wiping read and write
a=rwx sets read, write, and executable permissions for the user, group,and world.
chmod u=rw,g=r /challenge/pwn will set the user permissions to read and write, and the group permissions to read-only
chmod a=r,u=rw /challenge/pwn will set the user permissions to read and write, and the group and world permissions to read-only
chmod u=rw,g=r,o=- /challenge/pwn will set the user permissions to read and write, the group permissions to read-only, and the world permissions to nothing at all



## The SUID Bit
add the SUID bit to the /challenge/getroot program in order to spawn a root shell for you to cat the flag yourself

### Solve
**Flag:** `pwn.college{Ec_YBjQye4jQXR7EFgnZ_MtmpFb.QXzEjN0wyM4kjNzEzW}`

use chmod u+s /challenge/getroot then run /challenge/getroot, cat to get the flag

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
As the owner of a file, you can set a file's SUID bit by using chmod u+s [program]
