# Untangling Users

## Becoming root with su
THIS challenge does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag

### Solve
**Flag:** `pwn.college{o-Qs1emmOs1Z7iE3YOGBKcfk9Lh.QX1UDN1wyM4kjNzEzW}`

Use su then entered password to cat flag 

```hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat/flag
bash: cat/flag: No such file or directory
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{o-Qs1emmOs1Z7iE3YOGBKcfk9Lh.QX1UDN1wyM4kjNzEzW}
root@users~becoming-root-with-su:/home/hacker# 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Other users with su
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

### Solve
**Flag:** `pwn.college{ExKmYZAYdwRjh5CRQ7Q6TEXH0iX.QX2UDN1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{ExKmYZAYdwRjh5CRQ7Q6TEXH0iX.QX2UDN1wyM4kjNzEzW}
zardus@users~other-users-with-su:/home/hacker$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Cracking passwords
This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag

### Solve
**Flag:** `pwn.college{8pV3rYNpSYIjX4rP0O76JJs-fCI.QX3UDN1wyM4kjNzEzW}`

using john as the user go to /challenge/shadow-leak optain zardus's password then using su loginto zardus's account and run challenge to get flag 

```hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:02 28% 1/3 0g/s 266.6p/s 266.6c/s 266.6C/s sudraz!..bzardus
0g 0:00:00:10 96% 1/3 0g/s 264.3p/s 264.3c/s 264.3C/s zardus999991963..zardus1939
0g 0:00:00:13 0% 2/3 0g/s 267.4p/s 267.4c/s 267.4C/s kelly..snickers
0g 0:00:00:20 1% 2/3 0g/s 274.9p/s 274.9c/s 274.9C/s 10sne1..nermal
aardvark         (zardus)
1g 0:00:00:21 100% 2/3 0.04725g/s 275.1p/s 275.1c/s 275.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ 
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{8pV3rYNpSYIjX4rP0O76JJs-fCI.QX3UDN1wyM4kjNzEzW}
zardus@users~cracking-passwords:/home/hacker$ 
```

### New Learnings
If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords



## Using sudo
In this level, we will give you sudo access, and you will use it to read the flag. Nice and easy.

### Solve
**Flag:** `pwn.college{Ibo8WyoNSNWajiV2ve8wDNRHs-a.QX4UDN1wyM4kjNzEzW}`

sudo cat the flag file 

```hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{Ibo8WyoNSNWajiV2ve8wDNRHs-a.QX4UDN1wyM4kjNzEzW}
hacker@users~using-sudo:~$ 
```

### New Learnings
sudo checks policies to determine whether the user is authorized to run commands as root.
