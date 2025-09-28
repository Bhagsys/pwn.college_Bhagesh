# Pondering Paths

## The Roots
The filesystem root (/) contains a program named pwn. Your goal is to run that program using its absolute path to obtain the flag.

### Solve
**Flag:** `pwn.college{ocMkOoZ1-jaWEvq0w5RZ4JVjZGS.QX4cTO0wyM4kjNzEzW}`

An absolute path begins with /, so invoking /pwn runs that exact file regardless of your current directory or PATH

```hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{ocMkOoZ1-jaWEvq0w5RZ4JVjZGS.QX4cTO0wyM4kjNzEzW}
```

### New Learnings
The “/“ lets you change directories, configuration files and programs 



## Program and absolute paths
A challenge program named run is located in the challenge directory which sits at the filesystem root. Your goal is to run that program using its absolute path to receive the flag.

### Solve
**Flag:** `pwn.college{4wWwmTVgAcR0yD7EeQ1znuqgwS6.QX1QTN0wyM4kjNzEzW}`

This is similar to the first program except we are going into a sub directory to run the challenge 

```hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{4wWwmTVgAcR0yD7EeQ1znuqgwS6.QX1QTN0wyM4kjNzEzW}
```

### New Learnings
earned how to navigate one level deeper into the filesystem hierarchy and still use the absolute path correctly.


## position thy self
A challenge program named run is located in the challenge directory which sits at the filesystem root. Your goal is to run that program using its absolute path to receive the flag.

### Solve
**Flag:** `pwn.college{UNiVZo4M40us52HxXNJEiw4AoRp.QX3QTN0wyM4kjNzEzW}`

Entering the challenge I found out that the sys directory isn’t set as the directory after changing it using the cd function allows me to use the “/“ to run the challenge from its directory

```/hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/138 directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/138
hacker@paths~position-elsewhere:/proc/138$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UNiVZo4M40us52HxXNJEiw4AoRp.QX3QTN0wyM4kjNzEzW}
```

### New Learnings
Use “pwd” to check current directory before running cd function.


## position elsewhere
A challenge program named run is located in the challenge directory which sits at the filesystem root. Your goal is to run that program using its absolute path to receive the flag.

### Solve
**Flag:** `pwn.college{AESX_oDpxcfDMrQ_z_6w7TDYKqW.QX2QTN0wyM4kjNzEzW}`

Similar thought process to the last one where entering the directory as the previous challenge

```/challenge/run
Incorrect...
You are not currently in the /sys directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /sys
hacker@paths~position-thy-self:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{AESX_oDpxcfDMrQ_z_6w7TDYKqW.QX2QTN0wyM4kjNzEzW}
```



## position yet elsewhere
A challenge program named run is located in the challenge directory which sits at the filesystem root. Your goal is to run that program using its absolute path to receive the flag.

### Solve
**Flag:** `pwn.college{At22ofo4N7eW0RD_YHBaYnWYS9v.QX4QTN0wyM4kjNzEzW}`

Similar thought process to the last one where entering the directory as the previous challenge

```hacker@paths~position-yet-elsewhere:/home$ cd /usr/share/build-essential
hacker@paths~position-yet-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{At22ofo4N7eW0RD_YHBaYnWYS9v.QX4QTN0wyM4kjNzEzW}
```


## implicit relative paths, from /
A challenge program named run is located in the challenge directory which sits at the filesystem root. Your goal is to run that program using its absolute path to receive the flag.

### Solve
**Flag:** `pwn.college{Qem5ph8sktyOJKzK10YCAVfBgI3.QX5QTN0wyM4kjNzEzW}`

Since we are using a relative path it doesn’t need to have a / in front of the path

```hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Qem5ph8sktyOJKzK10YCAVfBgI3.QX5QTN0wyM4kjNzEzW}
```
###New Learnings
Difference between absolute and relative paths



## explicit relative paths, from /
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.This challenge will get you using . in your relative paths. Get ready!

### Solve
**Flag:** `pwn.college{0WUyo5TSa3QRZbW5BmL-O4PvBGs.QXwUTN0wyM4kjNzEzW}`


```hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/./run
Correct!!!
./challenge/./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0WUyo5TSa3QRZbW5BmL-O4PvBGs.QXwUTN0wyM4kjNzEzW}
```
###New Learnings
Use of . In relative path


## implicit relative path
in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. 
### Solve
**Flag:** `pwn.college{Y7fdWBJRmQwiHIzgzoVYnArhf_x.QXxUTN0wyM4kjNzEzW}`


```hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./././run
Correct!!!
./././run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Y7fdWBJRmQwiHIzgzoVYnArhf_x.QXxUTN0wyM4kjNzEzW}
```
###New Learnings
Linux explicitly avoids looking in automatically looking in cd when a naked path is provided



## home sweet home
In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:
	1	Your argument must be an absolute path.
	2	The path must be inside your home directory.
	3	Before expansion, your argument must be three characters or less.

### Solve
**Flag:** `pwn.college{Y7fdWBJRmQwiHIzgzoVYnArhf_x.QXxUTN0wyM4kjNzEzW}`

First tried to execute /challenge/run /hacker/home/s then was limited by the argument being less than 3 characters or less which led to me using ~ which then worked.

```hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./././run
Correct!!!
./././run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Y7fdWBJRmQwiHIzgzoVYnArhf_x.QXxUTN0wyM4kjNzEzW}
```
###New Learnings
~ is an absolute path that expands to /home/hacker
And ~/~ will be expanded to /home/hacker/~ and not /home/hacker/home/hacker 










