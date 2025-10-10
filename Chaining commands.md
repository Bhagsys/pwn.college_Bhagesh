#Chaining commands

## Chaning with Semicolons
In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

### Solve
**Flag:** `pwn.college{cPN5YW43IHwhUXq1A9U6H1UAcKD.QX1UDO0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{cPN5YW43IHwhUXq1A9U6H1UAcKD.QX1UDO0wyM4kjNzEzW}
hacker@chaining~chaining-with-semicolons:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Building on Success
In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator. Try running each command separately first to see what happens (which is that you will not get the flag). But if you chain them with &&, the flag will appear!

### Solve
**Flag:** `pwn.college{YSN4iXipJ4z1HlMOpoN5s8OQHlj.0lM0MDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{YSN4iXipJ4z1HlMOpoN5s8OQHlj.0lM0MDOxwyM4kjNzEzW}
hacker@chaining~building-on-success:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Handling Failure
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator. Go for it!

### Solve
**Flag:** `pwn.college{QRDjfmABsRlsS25cnt0X45dUIYL.01M0MDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{QRDjfmABsRlsS25cnt0X45dUIYL.01M0MDOxwyM4kjNzEzW}
hacker@chaining~handling-failure:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Your First Shell Script
 Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

### Solve
**Flag:** `pwn.college{cfuX1KzU4PpChy0My5gZZM3u7Oi.QXxcDO0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{cfuX1KzU4PpChy0My5gZZM3u7Oi.QXxcDO0wyM4kjNzEzW}
hacker@chaining~your-first-shell-script:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Redirecting Script Output
In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command.

### Solve
**Flag:** `pwn.college{g2a9oLjaZZN5kXZdf3T2afLq8ou.QX4ETO0wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~redirecting-script-output:~$ bash run_challenges.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{g2a9oLjaZZN5kXZdf3T2afLq8ou.QX4ETO0wyM4kjNzEzW}
hacker@chaining~redirecting-script-output:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user



## Executable Shell Scripts
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

### Solve
**Flag:** `pwn.college{02y4qC7YdtTrSRPnKjAZ7mUcfJN.QX0cjM1wyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~executable-shell-scripts:~$ chmod +x run_solve.sh
hacker@chaining~executable-shell-scripts:~$ ./run_solve.sh
Congratulations on your shell script execution! Your flag:
pwn.college{02y4qC7YdtTrSRPnKjAZ7mUcfJN.QX0cjM1wyM4kjNzEzW}
hacker@chaining~executable-shell-scripts:~$ 
```

### New Learnings
Su is used to switch user, usually used to switch to the root user




## Understanding Shebangs
For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!

### Solve
**Flag:** `pwn.college{k6IjLa7EGNwRaRZ5FSyUnNjYv5i.0VOzMDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ echo 'echo "hack the planet"' >> /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{k6IjLa7EGNwRaRZ5FSyUnNjYv5i.0VOzMDOxwyM4kjNzEzW}

hacker@chaining~understanding-shebangs:~$  
```

### New Learnings
We can use echo "string" > to input lines into files and >> to input a second line



## Scripting with Arguments
For this challenge, you need to write a script at /home/hacker/solve.sh that:
Takes two arguments
Outputs them in REVERSE order (second argument first, then the first argument)

### Solve
**Flag:** `pwn.college{csjlvtld08DU_yYDh2g6bO1Hk8-.0VNzMDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ 
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{csjlvtld08DU_yYDh2g6bO1Hk8-.0VNzMDOxwyM4kjNzEzW}
hacker@chaining~scripting-with-arguments:~$ 
```

### New Learnings
$1 - first argument $2- second argument and so on.



## Scripting with Conditionals
For this challenge, write a script at /home/hacker/solve.sh that:
Takes one argument
If the argument is "pwn", output "college"
For any other input, output nothing

### Solve
**Flag:** `pwn.college{csjlvtld08DU_yYDh2g6bO1Hk8-.0VNzMDOxwyM4kjNzEzW}`

Su to Zardus then enter password and run /challenge/run 

```hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ 
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{csjlvtld08DU_yYDh2g6bO1Hk8-.0VNzMDOxwyM4kjNzEzW}
hacker@chaining~scripting-with-arguments:~$ 
```

### New Learnings
$1 - first argument $2- second argument and so on.







