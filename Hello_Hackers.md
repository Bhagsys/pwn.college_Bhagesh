#Hello Hackers
##Intro to Commands

This challenge introduces the concept of invoking commands in a Linux shell. The goal is to familiarize the user with entering a command, executing it, and understanding the output. Commands in Linux are case-sensitive, which means `hello`, `HELLO`, and `Hello` are all treated as different commands.

###Solve
**flag:**pwn.college{YYez-0QZW5-V-_m5Jdt_B67VScx.QX3YjM1wyM4kjNzEzW}

  ```bash
  hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{YYez-0QZW5-V-_m5Jdt_B67VScx.QX3YjM1wyM4kjNzEzW}
hacker@hello~intro-to-commands:~$ 

### New learnings
Learned how to use the whoami command and that linux is case sensitive 

##Intro to Arguments

a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments.
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal
###Solve 
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{cstEZG0OZ2STS9whH4LlWxmPR0o.QX4YjM1wyM4kjNzEzW}
hacker@hello~intro-to-arguments:~$ 
###New learnings
Learned echo command and that It is used to repeat all of its arguments back
##Command History
You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In other challenges, the history will contain the log of the commands you've run, so if you need to run a similar command again, you can use the arrow keys to scroll through and find it
###Solve
hacker@hello~command-history:~$ the flag is pwn.college{I2hFsijLYOgk9fWQSSWPzpUMV9E.0lNzEzNxwyM4kjNzEzW}
###New Learnings
I learned how you can use the up and down arrows to go through your command history and how its easier to execute an earlier command without typing It again.