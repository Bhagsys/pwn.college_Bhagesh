# Module Name


## cat:not the pet, but the command!
One of the most critical Linux commands is cat. cat is most often used for reading out files

### Solve
**Flag:** `pwn.college{s_5pGRCdSfjJ4q9Z7_dAguoXGQR.QXxcTN0wyM4kjNzEzW}`

In this challenge cat is a command that will concatenate multiple files and used to read out files 

```hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{s_5pGRCdSfjJ4q9Z7_dAguoXGQR.QXxcTN0wyM4kjNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$ 
```

### New Learnings
Leant the use of the cat command: used to read out and concatenate files



## catting absolute paths
The challenge shows that cat accepts absolute paths and that some files can be read directly

### Solve
**Flag:** `pwn.college{04rE0oGTpUBGiYa98w6IbarIxL1.QX5ETO0wyM4kjNzEzW}`

I read the flag by specifying its absolute path to cat:

```hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{04rE0oGTpUBGiYa98w6IbarIxL1.QX5ETO0wyM4kjNzEzW}
hacker@commands~catting-absolute-paths:~$ 
```

### New Learnings
cat accepts absolute paths as arguments.



## more catting practice
The challenge shows that cat accepts absolute paths and that some files can be read directly

### Solve
**Flag:** `pwn.college{g4BpXBKizFlwD21SCsE820bSH-9.QXwITO0wyM4kjNzEzW}`

Using the given path directory using cat I obtained the flag

```You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/python3.8/concurrent/flag. Go cat it out **without** cding 
into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/python3.8/concurrent/flag
pwn.college{g4BpXBKizFlwD21SCsE820bSH-9.QXwITO0wyM4kjNzEzW}
hacker@commands~more-catting-practice:~$ 
```

### New Learnings
You can always pass an absolute path to cat and it will read that file regardless of your current working directory. When you cannot 'cd' use tools like 'find'


## grepping for a needle in a haystack
One of the most critical Linux commands is cat. cat is most often used for reading out files

### Solve
**Flag:** `pwn.college{cIQnwub_gkHuFm3OjAmlBD8WUBd.QX3EDO0wyM4kjNzEzW}`

In this challenge first grep should be used before the spring ti be searched and the data type must be mentioned

```
grep: /challenge/pwn.college: No such file or directory
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challe
nge/
grep: /challenge/: Is a directory
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{cIQnwub_gkHuFm3OjAmlBD8WUBd.QX3EDO0wyM4kjNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ 
```

### New Learnings
'grep pattern' searches a file for lines containing pattern and prints matching lines.


### New Learnings
You can always pass an absolute path to cat and it will read that file regardless of your current working directory. When you cannot 'cd' use tools like 'find'




## comparing files
The challenge is about using diff to find the single real flag hidden among many decoys. Two files are provided: /challenge/decoys_only.txt — 100 fake flags /challenge/decoys_and_real.txt — the same 100 fake flags plus the one real flag Use diff to compare the files line-by-line and see what was added.

### Solve
**Flag:** `pwn.college{0UNw655wvlhXMGSa4-988xUwX0w.01MwMDOxwyM4kjNzEzW}`

First change directory to challenge in order to compare the two files present in it

```hacker@commands~comparing-files:~$ cd /challenge
hacker@commands~comparing-files:/challenge$ diff decoys_only.txt decoys_and_real.txt
55a56
> pwn.college{0UNw655wvlhXMGSa4-988xUwX0w.01MwMDOxwyM4kjNzEzW}
hacker@commands~comparing-files:/challenge$ 

```

### New Learnings
diff compares two files line by line and shows you exactly what's different between them




## listing files
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.

### Solve
**Flag:** `pwn.college{wX1Xv9qFutXFfBKGvBMQ4l_fNQT.QX4IDO0wyM4kjNzEzW}`

Ls command lists all files in the directory where the renamed run file led to the flag

```hacker@commands~listing-files:~$ ls /challenge
218-renamed-run-3442  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/210-renamed-run-3442
bash: /challenge/210-renamed-run-3442: No such file or directory
hacker@commands~listing-files:~$ /challenge/218-renamed-run-3442
Yahaha, you found me! Here is your flag:
pwn.college{wX1Xv9qFutXFfBKGvBMQ4l_fNQT.QX4IDO0wyM4kjNzEzW}
hacker@commands~listing-files:~$ 

```

### New Learnings
ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. 




## touching files
 In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{EI2fy8USCFzvzpLMN6OFqx4haAK.QXwMDO0wyM4kjNzEzW}`

Touch command creates a file in the current directory

```hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{EI2fy8USCFzvzpLMN6OFqx4haAK.QXwMDO0wyM4kjNzEzW}
hacker@commands~touching-files:~$ 
```

### New Learnings
Touch lets you create new files



## removing files
This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!

### Solve
**Flag:** `pwn.college{APAt-4moWOCqGcJUbGjqxZXS-0_.QX2kDM1wyM4kjNzEzW}`

Rm command is used to remove the file from the directory and then I checked to make sure I've deleted it 

```hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{APAt-4moWOCqGcJUbGjqxZXS-0_.QX2kDM1wyM4kjNzEzW}
hacker@commands~removing-files:~$ 
```

### New Learnings
Rm is used to remove a file from the directory



## moving files
The challenge is about using mv to move files. You must move the /flag file into /tmp/hack-the-planet, then run the checker to confirm and get the flag.

### Solve
**Flag:** `pwn.college{wJY2N4b_rOmJ737LPgWeU44mrl1.0VOxEzNxwyM4kjNzEzW}`

Mv command is used to move a file, first the file thats moved is mentioned then the place where the file is being moved to is mentioned.

```hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{APAt-4moWOCqGcJUbGjqxZXS-0_.QX2kDM1wyM4kjNzEzW}
hacker@commands~removing-files:~$ 
```

### New Learnings
Mv is used to move files it can also be used to rename files.




## hidden files
 find the flag, hidden as a dot-prepended file in /.

### Solve
**Flag:** `pwn.college{UzqGQgNooJhzwdR5lLbVz0DMeWl.QXwUDO0wyM4kjNzEzW}`
First switch the directory to / then use the ls -a command to reveal all hidden files then use the cat command to open the flag file

```hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.           .flag-289102218820999  challenge  home   lib64   mnt  proc  sbin  tmp
..          bin                    dev        lib    libx32  nix  root  srv   usr
.dockerenv  boot                   etc        lib32  media   opt  run   sys   var
hacker@commands~hidden-files:/$ cat /.flag-28910221882099
cat: /.flag-28910221882099: No such file or directory
hacker@commands~hidden-files:/$ cat /.flag-289102218820999
pwn.college{UzqGQgNooJhzwdR5lLbVz0DMeWl.QXwUDO0wyM4kjNzEzW}
hacker@commands~hidden-files:/$ 
```

### New Learnings
Files can be hidden using .before the file name this won't show when using the ls command



## An epic filesystem quest
The challenge is a small scavenger-hunt through the filesystem using ls, cd, and cat. A clue file in / points to another file/directory, and following the breadcrumbs eventually leads to the hidden flag.


### Solve
**Flag:** `pwn.college{4Pw19Dlsbqkk0Mfcms6R__eSA0s.QX5IDO0wyM4kjNzEzW}`

I followed the breadcrumb clues from /, using ls to discover clue files and cat to read them, moving from one location to the next until I reached the final file containing the flag.

```hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
INFO  challenge  flag  lib32   media  opt   run   sys  var
bin   dev        home  lib64   mnt    proc  sbin  tmp
boot  etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat /INFO
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__$ ls
README  __init__.cpython-38.pyc  tids.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__$ cat /README
cat: /README: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__$ cat README
Lucky listing!
The next clue is in: /usr/share/javascript/three/examples/js/nodes/accessors

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/scapy/contrib/automotive/obd/tid/__pycache__$ cd /usr/share/javascript/three/examples/js/nodes/accessors
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/three/examples/js/nodes/accessors$ ls
CameraNode.js  LightNode.js     ReflectNode.js     UVNode.js
ColorsNode.js  NormalNode.js    ResolutionNode.js
INSIGHT        PositionNode.js  ScreenUVNode.js
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/three/examples/js/nodes/accessors$ cat INSIGHT
Lucky listing!
The next clue is in: /usr/lib/jvm/java-11-openjdk-amd64/legal/java.naming
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/three/examples/js/nodes/accessors$ cd /usr/lib/jvm/java-11-openjdk-amd64/legal/java.naming
hacker@commands~an-epic-filesystem-quest:/usr/lib/jvm/java-11-openjdk-amd64/legal/java.naming$ ls
ASSEMBLY_EXCEPTION  MESSAGE
hacker@commands~an-epic-filesystem-quest:/usr/lib/jvm/java-11-openjdk-amd64/legal/java.naming$ cat MESSAGE
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/tools/perf/ui/browsers
hacker@commands~an-epic-filesystem-quest:/usr/lib/jvm/java-11-openjdk-amd64/legal/java.naming$ cd /opt/linux/linux-5.4/tools/perf/ui/browsers
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/ui/browsers$ ls
Build   annotate.c  hists.c  map.c  res_sample.c
NUGGET  header.c    hists.h  map.h  scripts.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/ui/browsers$ cat NUGGET
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/sage/structure/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/ui/browsers$ cd /usr/lib/python3/dist-packages/sage/structure/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/structure/__pycache__$ ls -a
.                                     global_options.cpython-38.pyc
..                                    graphics_file.cpython-38.pyc
.MEMO                                 indexed_generators.cpython-38.pyc
__init__.cpython-38.pyc               list_clone_timings.cpython-38.pyc
all.cpython-38.pyc                    nonexact.cpython-38.pyc
coerce_exceptions.cpython-38.pyc      sequence.cpython-38.pyc
dynamic_class.cpython-38.pyc          set_factories.cpython-38.pyc
factorization.cpython-38.pyc          set_factories_example.cpython-38.pyc
factorization_integer.cpython-38.pyc  test_factory.cpython-38.pyc
formal_sum.cpython-38.pyc             unique_representation.cpython-38.pyc
gens_py.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/structure/__pycache__$ cat .MEMO
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/sound/hda

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/structure/__pycache__$ cd /opt/linux/linux-5.4/sound/hda
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ ls
Kconfig         hda_bus_type.o     hdac_device.c  hdac_stream.o  local.h
Makefile        hdac_bus.c         hdac_device.o  hdac_sysfs.c   trace.c
array.c         hdac_bus.o         hdac_i915.c    hdac_sysfs.o   trace.h
array.o         hdac_component.c   hdac_i915.o    hdmi_chmap.c   trace.o
built-in.a      hdac_component.o   hdac_regmap.c  hdmi_chmap.o
ext             hdac_controller.c  hdac_regmap.o  intel-nhlt.c
hda_bus_type.c  hdac_controller.o  hdac_stream.c  intel-nhlt.o
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ ls -a
.                       .hdac_sysfs.o.cmd  hdac_bus.o         hdac_sysfs.c
..                      .hdmi_chmap.o.cmd  hdac_component.c   hdac_sysfs.o
.NOTE                   .intel-nhlt.o.cmd  hdac_component.o   hdmi_chmap.c
.array.o.cmd            .trace.o.cmd       hdac_controller.c  hdmi_chmap.o
.built-in.a.cmd         Kconfig            hdac_controller.o  intel-nhlt.c
.hda_bus_type.o.cmd     Makefile           hdac_device.c      intel-nhlt.o
.hdac_bus.o.cmd         array.c            hdac_device.o      local.h
.hdac_component.o.cmd   array.o            hdac_i915.c        trace.c
.hdac_controller.o.cmd  built-in.a         hdac_i915.o        trace.h
.hdac_device.o.cmd      ext                hdac_regmap.c      trace.o
.hdac_i915.o.cmd        hda_bus_type.c     hdac_regmap.o
.hdac_regmap.o.cmd      hda_bus_type.o     hdac_stream.c
.hdac_stream.o.cmd      hdac_bus.c         hdac_stream.o
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ cat .NOTE
Tubular find!
The next clue is in: /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/Neo-Euler/Size3/Regular

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ ls /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/Neo-Euler/Size3/Regular
CLUE-TRAPPED  Main.js
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ cat /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/Neo-Euler/Size3/Regular/CLUE-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/tools/testing/selftests/locking

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ ls /opt/linux/linux-5.4/tools/testing/selftests/locking
Makefile  WHISPER-TRAPPED  ww_mutex.sh
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ ls /opt/linux/linux-5.4/tools/testing/selftests/locking/WHISPER-TRAPPED
/opt/linux/linux-5.4/tools/testing/selftests/locking/WHISPER-TRAPPED
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ cat /opt/linux/linux-5.4/tools/testing/selftests/locking/WHISPER-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{4Pw19Dlsbqkk0Mfcms6R__eSA0s.QX5IDO0wyM4kjNzEzW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/hda$ 
```

### New Learnings
How to proceed step-by-step with ls, cd, and cat to follow clues in the filesystem. ls helps discover filenames; cat reads clue files. Combining them lets you follow breadcrumbs without guessing. dotfiles may contain clues — use ls -a Absolute paths are handy for reading a file from anywhere (cat /challenge/secret/flag) once you know its location. Always be deliberate when moving around root (/) — use ls and cat rather than blind cd into random system dirs.


## making directories
The challenge is about creating directories with mkdir and placing files inside them. You must create /tmp/pwn and then create a file named college inside that directory. After that, run /challenge/run which will check your work and reveal the flag.

### Solve
**Flag:** `pwn.college{MuO41SFhleRAQiCF4PCMuQbdc3z.QXxMDO0wyM4kjNzEzW}`

Use mkdir to create a /tmp/pwn directory then run 

```hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{MuO41SFhleRAQiCF4PCMuQbdc3z.QXxMDO0wyM4kjNzEzW}
hacker@commands~making-directories:~$ 
```

### New Learnings
mkdir creates the directory and any missing parent directories. touch creates an empty file.




## finding files
The challenge is about using the find command to locate files anywhere on the filesystem. The flag file is named flag and is hidden somewhere under /. Some other flag files exist, and many locations are permission‑restricted (ignore the permission errors). Use find to locate the correct file and cat it.


### Solve
**Flag:** `pwn.college{MS8pWP4KyZsmxy7GzrIGOl2fh2R.QXyMDO0wyM4kjNzEzW}`



```hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.4mK6TfTSUV’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/lib/debug/.build-id/af/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ /usr/local/lib/python3.8/dist-packages/pwnlib/flag
bash: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/lib/debug/.build-id/af/flag
pwn.college{MS8pWP4KyZsmxy7GzrIGOl2fh2R.QXyMDO0wyM4kjNzEzW}hacker@commands~finding-files:~$ 
```

### New Learnings
The challenge is about using symbolic links to make one pathname resolve to another. The level gives you a program /challenge/catflag that will read /home/hacker/not-the-flag — but the real flag lives at /flag. Create a symlink named /home/hacker/not-the-flag that points to /flag, and the program will read the flag through the symlink.



## linking files
One of the most critical Linux commands is cat. cat is most often used for reading out files

### Solve
**Flag:** `pwn.college{wdYftgepDD5mHmvRAICleiP2few.QX5ETN1wyM4kjNzEzW}`


```hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{wdYftgepDD5mHmvRAICleiP2few.QX5ETN1wyM4kjNzEzW}
hacker@commands~linking-files:~$ 
```

### New Learnings
ln -s creates a symbolic link named that points to . Accessing a symlink transparently resolves to the target file (so programs reading /home/hacker/not-the-flag will actually read /flag).

