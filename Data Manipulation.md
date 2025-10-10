# Data manipulation

## Translating characters
In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag

### Solve
**Flag:** `pwn.college{4M2kCoMsk1t5Ek8NXIaPtn9XHnp.01MxEzNxwyM4kjNzEzW}`

Using tr I swap all uppercase letters with lowecase letters but I didn't know that the actual flag doesn't change only pwn.college does

```hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{4M2kCoMsk1t5Ek8NXIaPtn9XHnp.01MxEzNxwyM4kjNzEzW}

hacker@data~translating-characters:~$ 
```

### New Learnings
tr translates the character provided in its first argument to the character provided in its second argument

### References



## Deleting characters
In this level, /challenge/run will print the flag but will contain decoy characters among the flag characters. Use tr -d to delete

### Solve
**Flag:** `pwn.college{kZHeW75MnrFFqZR_ZxR7jEG2jRW.0FNxEzNxwyM4kjNzEzW}`

Go to the challenge/run directory and use tr -d with ^ and % to remove thise characters 

```hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{kZHeW75MnrFFqZR_ZxR7jEG2jRW.0FNxEzNxwyM4kjNzEzW}
hacker@data~deleting-characters:~$  
```

### New Learnings
Insert the characters that need to be removed in '' to remove multiple characters

### References



## Deleting newlines
In this level, /challenge/run will print the flag but will contain bunch of newlines into the flag. Use tr -d to delete

### Solve
**Flag:** `pwn.college{cwgcnNHIbZyFoeVk5HhHsBUfN6K.0VNxEzNxwyM4kjNzEzW}`

Go to the challenge/run directory and use tr -d with ^ and % to remove thise characters 

```hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{cwgcnNHIbZyFoeVk5HhHsBUfN6K.0VNxEzNxwyM4kjNzEzW}hacker@data~deleting-newlines:~$ 
```

### New Learnings
/n is used to define a new line 

### References



## Extracting the first lines with head
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag

### Solve
**Flag:** `pwn.college{47HzndO7CVkaFJQDEpDYuGQ9NXI.0lNxEzNxwyM4kjNzEzW}`

Go to the challenge/run directory and use cut-d and feed it to another pipeline with tr -d '\n'

```hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{47HzndO7CVkaFJQDEpDYuGQ9NXI.0lNxEzNxwyM4kjNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$ 
```

### New Learnings
The head command is used to display the first few lines of its input

### References



## Extracting specific sections of text
In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.

### Solve
**Flag:** `pwn.college{M7L1ujK-NnWZvUkvwonbYZ75P7P.01NxEzNxwyM4kjNzEzW}`

Go to the challenge/run directory and use cut-d and feed it to another pipeline with tr -d '\n'

```hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d '\n'
pwn.college{M7L1ujK-NnWZvUkvwonbYZ75P7P.01NxEzNxwyM4kjNzEzW}hacker@data~extracting-specific-sections-of-text:~$ 
```

### New Learnings
The -f argument specifies which column to extract

### References



## Sorting data
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end

### Solve
**Flag:** `pwn.college{INK_5Qd6eR6rEXpQ_oJJikJJdAA.0FM0MDOxwyM4kjNzEzW}`

Use sort to sort the data alphabetically and since the flag is at the end use -r to reverse the order
```hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{INK_5Qd6eR6rEXpQ_oJJikJJdAA.0FM0MDOxwyM4kjNzEzW}
pwn.college{INK_5Qd6eR6rEXpQ_oJJikJIdAA.0FM0MDOwvyL4kjNzDzW}
pwn.college{INK_5Qd6eR6rEXpQ_oIJhkJJdAA.0FM0MDOxwyM4jjNzEzW}
pwn.college{INK_5Qd6eR6rEWoQ_oJJikJJdAA.0EL0MDOxwyM4jjNzEzW}
pwn.college{INK_5Qd6eR6qEXpQ_oJJikJJdAA.0FM0MDOxwyM4kjNzEzW}
pwn.college{INK_5Qd6eQ5rEXpQ_oJJhkIJdAA.0FM0LCOxwxM4jjMzEzW}
pwn.college{INK_5Qd6dR6rEXpQ_oJJikJJdAA.0FM0MDOxwyM4jjNzEzW}
pwn.college{INK_5Qd5eR6rEXpQ_oJJikJIdAA.0FM0MDOxwyM4kjNzEzW}
pwn.college{INK_5Qd5eR6rEXpQ_oJJijJJdAA.0FM0MDOxwyM4kjNzEyW}
pwn.college{INK_5Qc6eR6rEXpQ_oJJikJJdAA.0FM0MDOxwyM4kjNzEzV}
pwn.college{INK_5Pd5eR6rEXoQ_oJJikJJdAA.0FM0MDOxwyM4kjNzEzW}
pwn.college{INK_4Qd6eR6rEXpQ_oJJikJJdAA.0FM0MDOwwyM4kjNzDzW}
pwn.college{INJ_5Qd6eQ6qEXpQ_oJJikJIdAA.0EM0MDOwwyM4jjNyDyW}
pwn.college{INJ_5Pd6eR6rEWpQ_oJJikJJcAA.0EM0MCOxwyM3jjNzEyV}
pwn.college{IMK_5Qc6eR5rDXpQ_nIJhkJIdAA.0EM0MCOxwyM4kiNzEyW}
pwn.college{HNK_5Qc6dQ6rEXpQ_nIJikJJdAA.0EM0MDOxwyM4kjNzEyW}
pwn.college{HNK_4Pc6eQ6qEXoQ_oJJikJJdAA.0FM0MDOwwyM4kjNzEzW}
pwn.collegd{INK_5Pc6eR6rEXpQ_nIIikJIcAA.0FM0LDNwwyM4kjNyDzW}
pwn.collegd{HNK_5Pd6eR5rDXpP_oJIikJJcAA.0FL0MDOxwyL4jjNzEzW}
pwn.collefe{INK_5Qd6eR6rEXpQ_nJJikJJdAA.0EM0MDOxwyM4kjMzEzW}
pwn.collefe{INK_5Qd6eR6rEXpP_oJJikJJdAA.0FM0MDOxwyM4kjNzEzW}
pwn.collefd{IMK_5Qd6dR5rEXpQ_oIJhkIJdAA.0FM0MDOxwyM4kiNzEzW}
pwn.colldge{INK_4Pd5eR6qEXoP_oJIikIJcAA.0FM0MDOxwyM4kjNyEzW}
pwn.colldfe{INK_5Qd5dR6rEXpQ_nJJhkJJdAA.0FL0MDOxwyM3kjMzEyV}
pwn.colkege{INK_5Qd6eR6rEXpQ_nJJikJJcAA.0FM0LDOxwyM4kjNzEzW}
pwn.colkege{IMK_5Qd6eR6rDXpQ_oJIijIJdAA.0FM0LDNwwyM4jjNyEzW}
pwn.colkege{IMJ_5Qd5dR6qEXpQ_oJJikJIdAA.0FL0MDNwwxM4jiMyEzW}
pwn.colkdge{IMK_5Qd5eR6rDWpQ_oIJhkIIdAA.0FM0LCOxvyL4kjNzEzW}
pwn.coklege{INK_5Qd6eR6rDXpQ_oJJikJJdAA.0FL0MDOxwyM4kjNzEzW}
pwn.coklege{INJ_5Qd5eR6qEXpQ_oJJhkJJdAA.0EL0MDNxwyM4kjNzDzV}
pwn.coklege{IMJ_5Qc6dQ6rEXpP_nJJikJJcAA.0FM0LCNxvyM4jiNzDzW}
pwn.coklege{HMJ_5Pd5eR6rEWpQ_oIJijJJcAA.0FM0MDOxwxL3kiNzEzW}
pwn.coklefe{IMK_4Pc6dR6rEXpQ_oJJijJJdAA.0FL0MDOxvxL3kiNzEzW}
pwn.coklefd{INK_5Qc5eQ6rEXpQ_oJJikJJdAA.0EM0MDOxwxM4kjMzEzW}
pwn.cokkege{IMK_5Qc5dR5rEWpQ_oJJikJIdAA.0FM0MDOwwxM4kiNzEzW}
pwn.cokkefd{INK_4Pd6dR6rEXpQ_oJJikJIcAA.0EM0LCOxwyM3kjMyEyW}
pwn.cnllege{INK_5Pd6eR6rEXpQ_oJJikIJdAA.0FM0MDOxwyM4kjMzEyV}
pwn.cnllegd{IMJ_5Qc6dQ6rEXoQ_nIJijJJdAA.0FM0LDOwwyL4jjNzDzW}
pwn.cnllefe{INK_5Qd6eR6rDXpQ_oJJijIJdAA.0FM0MDNxwyM4kjNzEzW}
pwn.cnlldfe{IMK_5Pd5eR6rDXpQ_oJIhkJJdAA.0FM0MDNwwyM3jiNzEyW}
pwn.cnlkege{INK_5Qc6dQ5rEWpQ_oJJikIJdAA.0FM0LDOwwyL4kiNyDzV}
pwn.cnlkdfe{INK_5Pc5eR5rDWoQ_oJIijJJcAA.0FM0LCOwwxM3kjMzDzW}
pwn.cnklege{IMK_5Pd6eR6rDWpP_oIJijJJcAA.0EM0MCOxvyL4jiNyDyW}
pwn.cnkldfe{INK_5Qd6eQ6rEXpP_oJJijJJdAA.0FM0MDOwwyM4kjNzEzW}
pwn.cnkkege{INK_5Qd6dR6qEXpQ_nJJhkJJcAA.0EM0MDNxwyL4kjMzEzW}
pwn.bolldgd{IMK_5Qc6dQ5rEWpQ_oJJhjJJcAA.0EM0LCOxwyL3jiMzEzW}
pwn.boklege{HMK_4Qc6dR6rEXoQ_oJJhkJJdAA.0FL0MDOxwyL4kjNzEyW}
pwn.bnllege{INJ_5Qd6eR6rEWpQ_nIIhkJJdAA.0FM0MDOxvyM3kjNzEzV}
pwn.bnllege{INJ_5Qd5dR5qEXoQ_oJJhkJJdAA.0FM0MCOwwyM3kjMzEyW}
pwn.bnlldfe{INK_5Pd5dR6rEXpQ_oIIhkJJcAA.0FL0MDNwwyM3kiNyDzV}
pwm.college{INK_5Qc5eR6rEWpQ_oJJhkJJcAA.0FL0MDOwvyL4kiNzDzW}
pwm.college{HNK_5Qd6eR6rEXpQ_oIJhkJJdAA.0EM0MDOxwyM3kiNzEzW}
pwm.college{HNK_5Qd5dR5rEXpQ_oJJikJIdAA.0FL0MDOxwxM4kiNyEzV}
pwm.college{HNK_5Pc6dR6rEXpQ_oJJikJIdAA.0FM0MDOwvxM4kjNzDzW}
pwm.collefd{IMJ_4Qc6dR6rEXpQ_nJJikJJcAA.0EM0MDOwwyM4jjNyEzW}
pwm.colldfd{IMK_4Qd5dR6rEWpQ_nJIijJIdAA.0EM0MDOwwyM3kjMzDzW}
pwm.colkegd{HMJ_5Qc6dR6qEXpQ_oJJikIIdAA.0EL0LCOxvyL4kjMzEzV}
pwm.cnllegd{HMK_5Qc5dR5qEXoQ_oJJikIJdAA.0EM0MCNxvyM3kjMyEyW}
pwm.cnlldge{INJ_4Pd5eR6rEXpQ_oJJikJJcAA.0FM0MDNxwxL4kjNzDzV}
pwm.cnlldgd{INK_5Qd5eR6rEWpQ_nJJikJJdAA.0FL0LDNxwyM3kjNzDzW}
pwm.cnklege{HMK_5Pc6dR6rDWpP_oIJikIIcAA.0FM0LDOxwyM3jjNzEzV}
pwm.cnkldge{INJ_4Pc5eR6rEXpQ_nJJikJIcAA.0EM0MDNxwyM4kiNzEzV}
pwm.cnkldfd{INK_4Qd5dR6qEXpQ_oJJhkJJdAA.0FL0MDOxwyM4kiNzEzW}
pwm.bollege{INK_5Qd6eQ6rDXpQ_oJIikJJdAA.0EM0LCNxwxM4kjNzEyW}
pwm.boklefe{HNK_4Qc5eQ5rEXpQ_oJIikJIdAA.0EM0LDOxwyL4kjNzEzW}
pwm.bnkkegd{INJ_5Pd5eR5qEWoQ_nIJikIIcAA.0FM0MCOxwyL4kjNzEyW}
pvn.colldge{INK_5Qc6eR6rEXoQ_oJIikJIcAA.0FM0LCOxwyM4jiNzEzW}
pvn.colldge{INJ_5Qd6dR6rEXpP_oJJijJIcAA.0EM0MDOxwxM4jjNzDyW}
pvn.colldge{HNK_5Qd6eR6rDXpQ_oJJhkIIdAA.0EM0MDNxwxM4kjNzEyW}
pvn.colkegd{INJ_5Qd5eR6rEXoQ_nIJikJIdAA.0FM0MDOxwyM4jiNyDzW}
pvn.cokkdgd{INK_4Pd6eR6qDWpQ_oIJhkJJdAA.0EM0MCOxvyM4kjNzDzW}
pvn.cnlldfd{INK_5Qc6dR6rDXoQ_oIIhkIJcAA.0FL0MDOwvyM4kjMzDyW}
pvn.bollege{INK_5Qd6eQ6rEXpQ_oIJijIJcAA.0FM0LCOxwyM4kjNzEyW}
pvn.bolkege{HNK_5Qd6eR6rEXoP_oJJikJJdAA.0FM0MCNxwyL4kjNyEzW}
pvn.bolkdfd{INJ_5Qd5dR6rDXpQ_nIIijJIdAA.0FL0MDOxwxL4jjMzDyV}
pvn.boklegd{INJ_5Qd5dQ5rEWpQ_oJJijJJdAA.0EL0MCOwvyM3jjNzEzW}
pvn.bnlldgd{HNK_4Pc6eQ6rEWpQ_oJJikJJdAA.0FM0MDOxvyM3kiNyDzW}
pvm.college{INJ_4Qd6eQ6rEXpQ_nJIijJJdAA.0EM0LDOxwyL4kiNzEyW}
pvm.coklege{INK_4Pc5eR6qEXpQ_oIJijIJcAA.0FL0MDNwvyM4kiMzEzV}
pvm.coklegd{INJ_5Pd6dR5rDXpP_nIJikJJcAA.0FL0LDNwvyM4kjNzEzV}
pvm.coklefd{IMK_5Pd6dQ6rEXoQ_nJJhjJIcAA.0FL0MDNxwyM4kjNzDyV}
own.college{INK_5Qd6eR6rEXpQ_oJJikIJdAA.0EM0MDOxvyM4kjNzEzW}
own.college{INK_5Pd5eR6rEXoQ_nJJikIJdAA.0FM0MDNxwyM4kjNzEyW}
own.college{INK_4Qd6eR6rEWpQ_oJJikJJdAA.0FM0LDOxwyM4kjNzEzW}
own.college{IMK_4Qd6dQ6rDXpQ_oIIijIJcAA.0EM0MDOwwyM4jiNyEzW}
own.colkege{INJ_5Qc6eQ6qDXpP_oJJikJJdAA.0FL0MDOxwyL3kiNzEzV}
own.coklege{INK_5Qd6eQ5rEXpP_oJJikJJcAA.0EM0LCNxvyM4kjMyEzV}
own.cokkdfd{INK_5Pc6eR6rEXpQ_oJIikJIdAA.0FL0LCOxvyM3kjNyEzV}
own.cnlkege{INK_4Qd6dR6rDXoQ_oJJikJJdAA.0FM0LDNxwxM4kjNyEyW}
own.cnklege{HNK_5Qd6eR6rEXpQ_oIJhkJIdAA.0FM0LCNxwyM4kiNzEyW}
own.cnklege{HNK_5Pc5eQ6rDWoP_oJIhkJJcAA.0FM0MDNxvxM3kjNzEyV}
own.bollegd{INJ_5Qd6eR6qDXoQ_oJJikIJdAA.0FL0MDOxwyM4kjNzEyW}
own.boklege{INK_5Qd5eR6rEXpQ_oJIikIJdAA.0FM0LDOxvyM3kiNzDzV}
owm.collegd{IMK_5Qd6eR6rEXpQ_oJJikJJdAA.0FM0MDOxwyL4kjNzEzW}
owm.collegd{IMK_5Qd6dR5rEXpQ_oIJhkJIdAA.0FM0LDOxvyM4kjNyEyW}
owm.collefd{INK_5Pc6eR6rEXpQ_oIJhjJIdAA.0EL0MDNxwxM4kjNzEzV}
ovn.college{INK_5Qd6eR6rEXpQ_oJJikJJdAA.0EM0MDOxwyM4kjNzEzW}
ovn.collefe{HNK_5Qd6eR6rEXoQ_oIJhkIJcAA.0FM0MDOxwyM4jjNzEzW}
ovn.colldfe{INJ_5Qd6eR5qEXpQ_oJJijJJdAA.0EM0MCOwvyM3jjMyEyW}
ovn.cnlkege{INK_4Qd6eR6rEXoQ_nIJikIJcAA.0EM0LDOxwyL3kjNyEyW}
ovm.cokkdge{INJ_5Pd6eQ6qDXpQ_oIIikJJdAA.0EM0MDNxvyL4kjMyEzW}
hacker@data~sorting-data:~$ 
```

### New Learnings
The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order

### References


