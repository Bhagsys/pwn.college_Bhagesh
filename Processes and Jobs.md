# Processes and Jobs

## Listing Processes
This challenge, .challenge.run is remanned to a random file and u cannot use ls to change to the /challenge directory but it is already launched you can find it running it un the process list. relaunch it directly for the flag

### Solve
**Flag:** `pwn.college{kdez-pcuF_Plm9GC3k1D2Qf2LzA.QX4MDO0wyM4kjNzEzW}`

Use ps -efww to show all running processes and then I searched for a program which starts with /challenge to then run it and get the key 

```hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 05:19 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 05:19 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 05:19 ?        00:00:00 /challenge/19565-run-8771
root         135     132  0 05:19 ?        00:00:00 sleep 6h
hacker       146       1  0 05:19 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true /run/dojo/bin/bash --login
hacker       150     146  0 05:20 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       160     150  0 05:20 pts/0    00:00:00 ps -efww
hacker@processes~listing-processes:~$ /challenge/19565-run-8771
Yahaha, you found me! Here is your flag:
pwn.college{kdez-pcuF_Plm9GC3k1D2Qf2LzA.QX4MDO0wyM4kjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

### New Learnings
Ps -efww or ps auxww is used to disable truncation 

### References



## killing Processes
In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission

### Solve
**Flag:** `pwn.college{MxqGP9PYOWSOOwqobKRcCiLMyX2.QXyQDO0wyM4kjNzEzW}`

Use ps -auxww to open all running programs and then find the PID of /challenge/dont_run and use the kill command to terminate it and then run /challenge/run

```hacker@processes~killing-processes:~$ ps -auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   05:32   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.0  0.0 231708  2560 ?        S    05:32   0:00 /run/dojo/bin/sleep 6h
root         135  0.0  0.0   5204  3520 ?        S    05:32   0:00 su -c /challenge/.launcher hacker
hacker       136  0.0  0.0 231576  3520 ?        Ss   05:32   0:00 /challenge/dont_run
hacker       137  0.0  0.0 231708  2560 ?        S    05:32   0:00 sleep 6h
hacker       148  0.0  0.0  36972 22080 ?        Sl   05:32   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true /run/dojo/bin/bash --login
hacker       152  0.0  0.0 231940  4160 pts/0    Ss   05:32   0:00 /run/dojo/bin/bash --login
hacker       162  0.0  0.0 233600  3840 pts/0    R+   05:33   0:00 ps -auxww
hacker@processes~killing-processes:~$ kill 135
bash: kill: (135) - Operation not permitted
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{MxqGP9PYOWSOOwqobKRcCiLMyX2.QXyQDO0wyM4kjNzEzW}
hacker@processes~killing-processes:~$ 
```

### New Learnings
Kill command is used to terminate a process

### References



## Interrupting Processes
In this challenge,/challenge/run will refuse to give you the flag until you interrupt it.

### Solve
**Flag:** `pwn.college{kI8-BLDyR2cWe3P6vu1-6YudSxy.QXzQDO0wyM4kjNzEzW}`

Run /challenge/run then hold control C to get the flag

```hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{kI8-BLDyR2cWe3P6vu1-6YudSxy.QXzQDO0wyM4kjNzEzW}
hacker@processes~interrupting-processes:~$  
```

### New Learnings
Control C is used to get rid off the process thats clogging up your terminal 

### References



## Killing Misbehaving Processes
In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill this process.

Your general workflow should be:

Check what processes are running.
Find /challenge/decoy in the list and figure out its process ID.
kill it.
Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its output; it'll write to the FIFO on its own).

### Solve
**Flag:** `pwn.college{UzIlGVlvbdNlQeyPrSBuKrFL805.0FNzMDOxwyM4kjNzEzW}`

Use ps -ef to see all running processes and kill using PID of the decoy program then run /challenge/run when then wrote the flag to /tmp/flag_fifo, reading which the last flag was the actual flag

```hacker@processes~killing-misbehaving-processes:~$ ps -ef | grep /challenge/decoy
root         139       1  0 06:31 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142     139  0 06:31 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       166     155  0 06:32 pts/0    00:00:00 grep --color=auto /challenge/decoy
hacker@processes~killing-misbehaving-processes:~$ kill 166
bash: kill: (166) - No such process
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run &
[1] 172
hacker@processes~killing-misbehaving-processes:~$ Sending the flag to /tmp/flag_fifo!
cat /tmp/flag_fifo
pwn.college{T-45o4HT3e0lFqzMTBzst.ebwjaweRHME7JZo6.tAkVskJs}
pwn.college{KrCuKseWHshTIrmiVFXQ6eTZTxNJWaafFRhuWCLm3DfSHlo}
pwn.college{gaxJwyx9.PdDbNKWX4hwdcdlOzisBS0FfEVStHXq6z2qZIL}
pwn.college{xtbioqhQKgO7015uhi.mx00JfF6hdojDqwuInTNQgRWRpzi}
pwn.college{YrsCfvH2s4-7XSwgca.xjr5xT3Ckoo8qmEqi3VNGutp4fMj}
pwn.college{lXzPFRKmqpuKFca7yurcf5ZUFxcA2RnBEV6HNZEthPOIoqY}
pwn.college{8UKmViMV.M4Ej9CJaE-L5YhhwksLR4UxDBNrBByD.tJYBKQ}
pwn.college{TA52t5jk7WHm4PfNFPEqvtkB8DodROPpovB97d7InzvzTPQ}
pwn.college{TtxuReUNE5gXIpQ9B0R6y4UDmuSFSWrEAmOFmW5Bbd1vHL1}
pwn.college{wjYZsfZTDtE7aSNN2bPZXBOpeqTWIkllCKNorEHiHKwYdzX}
pwn.college{-N.FnNlrw1ArXpXyndku3WPE37O-dF6AKvYLI4Efz-qRyi7}
pwn.college{ZvYpGIfuZFSp5km6zLH9bteejhL61XRCz9aa66KlxbMYdSO}
pwn.college{AsDvtoYPxogppovGwWQIASzet2.4AlLBMa7syJGLasqn8kK}
pwn.college{jUhjAuMmqeJzhXoQp6rOY29vi-LoEDLEcQGjKt42ELhfP-h}
pwn.college{06g6eHJIH4ae-J-9bp4YWbjqFEU0czrSDY1GX9GKsaPVeLG}
pwn.college{SFndczb3YmvCzHNGqYj5cO-iFCHTUba8Y9aFTKSdEsqB5VI}
pwn.college{K0kNV25EvX1l0uGT6gPyRYBM54VdY-G4m2KTSkQiOoZ4UXu}
pwn.college{IiDTazqMYTOOv1Pu9f98gCZwfi.rReiVbx3l.kpv4PwN3GL}
pwn.college{FKmFSydKmVfBY.6o0D66dZ7ktMsB4.gJp3Iifeqn1yQm1Za}
pwn.college{l6UXa8.-AKweKiepMFkVH9mQT2zfCKvVN81eJJyPEAX6Q2b}
pwn.college{SE6U3ZXeApFREF78bU-zVjw-gOXUfCLe243XVaIGPPbBBGl}
pwn.college{18HEo.yl8aaIHueO-J9C28wyclSlQJvKVRTaEmAS9P5tkRr}
pwn.college{a6twl5tXHbCMjo-S90eyEg1yarWOtWMErE1Qau0iVHpQhoH}
pwn.college{Fn355fvLXguMyncsIFnuAIejNMVIIC0Y9pOB.0LeNnC0nXi}
pwn.college{36TAieTAX7RSx0aWs76eL7cjx64dz4z1zHFzdVC.PIHtqRV}
pwn.college{CFGz456kJqezTfJ6f6R..DAI8mcEKILaM-ay-trRZeawrbN}
pwn.college{h7rTwazr0oFKvKtahdY9YifVqzeJX7qDXn4zXqvdwdZyN.L}
pwn.college{GumDSTOrKxm0GmVTQvDq2Xcu6W7sLKzsLZW4VCqY.rQfhkg}
pwn.college{HB006KfjjEWgd5ywe.NIjk7tU5e7sSIOgMEsdUx1MFW45U7}
pwn.college{8ph2E.X5Obq9RL.QFsDKbYFRSRO22rLgob5Pv4vyURRWTme}
pwn.college{X0wJAVZShOc7PcSLqpxvCOQYSgP7WMfrNp5Mp5X9VVdm07z}
pwn.college{rT2UFTgY8xPUJIh7H4XQulsX7AKkf8tR2q5lQ-kZRSMkNzp}
pwn.college{.3hHQSaHIO6gqpbjsnjOINF.fSISmHIb5BeQEiaG38o-b3-}
pwn.college{WtMfSVi2Eo-5Wv3Hli92ETSCcQMszfe11ln85xNYF8Cnlfl}
pwn.college{KptHMlgUt6oxhCLBjBMFhEuwqWmrtpkpTRX1IwZIOnRqyaA}
pwn.college{btwl7N8dx7M4IE3l2fkPpBk9UL-OHBWkiLhthZbTRad6xWl}
pwn.college{oayPHHYCvIBRn4LdQ4I.kXr86mPcBR7gnLGh3WqvIXr0sK6}
pwn.college{QfU.y0cEDcPkz7y54N9JpZVTn56lPP5VMWn9G0hB5AdtIIk}
pwn.college{v5KBCgtnIN74KMYKw3d6BFZc5BM57.jfxVlyaM6kSKVCH4q}
pwn.college{JwR8JYjej3dJ3oyZRYJtHn1UG341-KYjvvQAHjzBsVNb42q}
pwn.college{ZjeeSNpdA8Yi-Rue9mzWzzgoEDwfM016doZe5hSI5C8pjAe}
pwn.college{gkos0pZ6UbidF8ibS4h6Hry9bswUcsSmTCRBT1nDejM46Bi}
pwn.college{zVPcvn5xKXDvB629Rz.2vBM2dzV5Gx5ZI-3iXIMwBwaoyuj}
pwn.college{kxinLpTFo2puWxEte0PaT0ke4-bTNht708Y3OkObPEc3ogl}
pwn.college{lQ.HvRdK1cki8k2QKSSZd3kqNU1Dpf4F.OO5iv4N-YIbnFr}
pwn.college{jiuPsrkrv3O-ikrTbrtUQ0a7wIjbR5YXb8qXqwwux7QSNsO}
pwn.college{YHIRoo-IPaE0ShQrsjPXDHUdW0zdMhfqmdAWs0SAlyBuCs6}
pwn.college{VYYQnNgGVVVvhdkHkLoOGnHDEDsE-ABOtfY9-4oP4G7MUP5}
pwn.college{u1Ea9lpYcpMqnUpH0wkm2gXuggGtIEJ4fNOvjuWuF3.bwq3}
pwn.college{WNp1xLpqxlrsK3AN1DLpwmW.KEInON0eaTvBujMZm.hOoPJ}
pwn.college{ny7loLcfyx3gpJPTTOnXL6Gt-wbfFsyRAR4l0upxTICBdRC}
pwn.college{rEat6r4cDMfAxyv4hvOUeWOleDzTvEosFvby5Eko9VefDSz}
pwn.college{kV8ouhj5HVypB6TSlWI5k0ShL.yj6enld.IDejjkA04NdOQ}
pwn.college{bMinOspyeF3rL5Iw37KHRaPS63v1us8BkOpiibp4cr5fke.}
pwn.college{IY0NFRkCsKm9uUpz9IyOeBMLRBDBIXODZdtHcZFGcwCIG3E}
pwn.college{U1XBdLBYRoR7dT5LZU8V53gvT8mZq7yfpYWmLp.jCCb0Uni}
pwn.college{VHjkhzHkK9CEeS9ZZKxIcHW1G.ZHV4VZMPH27mUTRW3C9ep}
pwn.college{hlxQz39lzRdDZECxvhijB5sU6dElWhppotW-x9mW5rNrBWa}
pwn.college{4tmyMnPlTA8p3E5-JNczV1ZdZw2rHv0WRH1tk3klzrihwNS}
pwn.college{xUXsdeULdWOB.BFayEGcF3ivHnK8XPK3Gt-TkkFMQpptwAg}
pwn.college{yk2CHzhg9SJX5taWUVIFYrEijLchWHytYOLRzQnAgINd.jZ}
pwn.college{vkt2eY6UfsUcKb6yv8TfsmdIjHlZK3igWtkRjh0mnVJ5v-U}
pwn.college{M1vxnff4m.HuugdQli3UiuFG-KLEwAjyyPkhv5rQTId1aXj}
pwn.college{OgjIkuN.oeCpRtE4RD0DUdLza43XFMO7JhUen6yghvg1zvK}
pwn.college{G-Pe7rJPCR05bnRvMnoPt7wgiJkXtgsQ2Ho.ZjkiOK26gbu}
pwn.college{zIltHF7p5bnRU2FjjunbnWBBrDE5fsOrtIppKS4zIMwypND}
pwn.college{OBjsslBwD-S7ywJby2cFysFjzXeET2qGoThlCrrKBjNXsfs}
pwn.college{GUiPNNFS.wrIXFGk5.KiLk8QEAQE37zRwL3ziGmAcIA6jUx}
pwn.college{evwnPUJIhJmsNRyhXEX97XCOX--W.Rh.TCU2IzfRLWzaAIq}
pwn.college{hJGIsHbt7BZ-8ihZG3ssivymRRnVO1KiMCJoGoRKjV3nEjx}
pwn.college{T4LNBdRc5p6ADL4zt2HB4Bcq7l2eZsHt8cykOwCIy2WRUT2}
pwn.college{2Zb5fv80ih8EYXjwIdREOd2Af8VmFPqG-acrpO25aBKC0v.}
pwn.college{I7Iag1aXJLCKZyjV4iLiQeiwAOYtrbNTGm3jGQ5eEq6MFyz}
pwn.college{O3lbPZpdLYpoyqi7Z962yhU50xU606MoF2ssETiRiE2EuSP}
pwn.college{lo.gSjkZ3uyR-8rXW9fZJycwpYz4lv6E6AZsk1rANk6qEx.}
pwn.college{EcHevbhFGm112.g.c8UrzeVB-667lJkwLkvmC7rJ3oQcaJd}
pwn.college{B0GHWrSxJqmNj85mIIOJWX8sewsbdWOwtW1y7IplP976ZKQ}
pwn.college{AMYHLFO.xJhfT6w2.dve0JhB9Ch5aNTCD82FmSbTUlKY3qI}
pwn.college{MgOgV7ko9FdJKU3OueVj8mmcw-lPP7ZC8iCMM190DN4tvmN}
pwn.college{ftfmLjnq-Qfi9YSOUgW7OodV33cdWDA0OH.-FIDRS4wdRcT}
pwn.college{pNk.1cirT0V4MsYwvNMsGrEUInSkY2zIzWtkOI1GZEVJcax}
pwn.college{lNZZkk1G6.ANyvW84jt4b113uDBZdRoVs0l0hSQHx-re.-v}
pwn.college{pg.8pBqyVV9czzLZK2KzFFfmuvJi1YlJhuC9CXaomaLEZGz}
pwn.college{3dxrvLJlOBjYOgXowROwiORJ6y5-j4f6HyYdTefG.tnffsH}
pwn.college{V-fyhqMdJUxMWukXM0AR7Gr2oAje0bwcn-.F56PokaDkM2E}
pwn.college{DzETCtRY3OAhSbXXxL-XdtgfIBD96LaQNu1o0zTqJDCynjc}
pwn.college{.dXIlr9J.thYGkhkXRWtGWTQh5WPzSmuhhjH85jzOX39Jt.}
pwn.college{QcjcqrAMnaHxjHrVCvnqgCm3biG6V-h7f82DoHhd.KAcWnz}
pwn.college{s8VowhiLRomgl0kZO.TCsif8n.kIUWj8yA7qrXH35HF9vJp}
pwn.college{D6GR8Ykd0.IKMoGfjdJOmJ0I8j7aFG-Bum2-FhKTvHyOC9O}
pwn.college{1bMAH3Z9ha-smpTy2K72t8vuqtb7492pLjyxIxmpgFRH7Kr}
pwn.college{yENrfXVLJzad.7vG7loY36j47Usy8HhAnUcC1GGGHJYzJlC}
pwn.college{.sDYrhvPEBR7C58F91WPmTSgxQAfmQLnJSveHYJGUhG.6o0}
pwn.college{dWmV6bMmH.-wM.1vK5w2IVYjYXYUWqlIQ9uOaHmiyU6EGLo}
pwn.college{IscFDOia0O6bb9Bf3dlNPb5KjTWq18cei5Q3KrmaR1dXyxo}
pwn.college{j3fqbVG.K3WGNYdxSohpefNF3NXOQL9sMvAFIoMpZ2HgDUk}
pwn.college{NgRFrA3I0g5ltEhWE.HLKSP.8zaWjQzXk.z8KRYg67.4VCh}
pwn.college{5t3sjszwvkSPV1.I4btGQOMVpmw7.7Kly5R9gGf4Ddp0LLc}
pwn.college{-1m4xNcyY02PwTyiSX7PK0d7GF.6Q6ME1QMCL4DwA551IoA}
pwn.college{Rtvpq8Epg1t5wTkBB9BZXVbhSj98jIKL5yMsJjasPTapBdm}
pwn.college{6Lz8Y-LD449naX-R6Tn7OY4ezSTlxlE2ID9B1NMFbcc2nxo}
pwn.college{0PlXWalHofy3HcKBMKqqt-KhQHSecWbaFifOZFZdwxtoBXp}
pwn.college{02SIC6LbWfXg12p8Q5VgVdQHc55R5btb.R1-BQSfYa3Smzg}
pwn.college{sK6044iRmm7Tjqi98fr9ruhej9ZO0Jsc8INOg3s5WyPu0u0}
pwn.college{Q68dTDqgiGknlEVN9o0ByWe9zmykchC92rFLK15keKwTCeU}
pwn.college{hynGEQFIeUya-e1RZgZ-MgXOTucVTFI1yRbAD.I13i5sTio}
pwn.college{x8R.jnL38NBDNNqZ8iwI3nR8HpODI7DRmAMn-U2HdF34WxG}
pwn.college{R12v3bBAwkRts69f32yj8Vc5nG8dnXYnw0JFiOidPEfR.kD}
pwn.college{V0BPuILBypyBQ60BAePvywEuYG7HkNfEJwWYjRSTRh9qKUn}
pwn.college{t6k1viGOQz.coKxph50AaT43ebSKggRikDBZeXdJTwLpnmX}
pwn.college{7.yVF5SNHIQsWMbk4vJ3.WDueQgBN7g0EeYdTkZMqq9Tfyd}
pwn.college{shrz4MwSfB8b18TB.-nYtC5dyf8BPzFQGHoD28dWxm8uq04}
pwn.college{OmCnL7Gp1jpoPa0.6CNX4l2PmpJI6uSL5YAbm0ZDejRiqHr}
pwn.college{uIa11NTdorpkoWVhgbGDnyzySZoaNCMst3v4iKW8vMKLj9f}
pwn.college{ctDCg3xRXKMkBoPE.q1OxKwqyNvfnxj9aijxsUi5yGu4mEF}
pwn.college{6H4I1zzwhf6G-AgyMU0TUs.RJ4.gkLE-9ja9vRRo6jQPJSh}
pwn.college{85wFWfwzFLYWxdserZ0eiiLUNEKb.yOKeOUAeSsLKh-iYD.}
pwn.college{-NKeTwGO7rJEKpBolcdDTf6GSyb4mse7EWk12vC6un13DWp}
pwn.college{wj9SajYZ80ddZPNha6FRhw4KRlsS2Hz8sW2EVpruNfkD-ST}
pwn.college{m4Dp7fd3lZSXJuv6TWP0ggvG8ldz3J5teNLSvcReVYlPnDw}
pwn.college{KzQqDVAeaagcv6koZQeuI.4FgnyZ4Vu6u0Ydnk7pkiIBGEM}
pwn.college{me5MKhoIVzQ941P-1n.lqX.7FqtmGG8efogLWZoGUTq5UX4}
pwn.college{FZJ0iNrSm2-7InbdlOc67gdCmlSUcZTwRnC5f5fBPc7zbrq}
pwn.college{auhqGhioJYC.pHo2-S6pskCJ7x1z5y9WAFOK4DGH.YwXRIb}
pwn.college{72n00eqeGtY3caOKKFBpt7wF1gpHJXf6ZxNPb.4tLLZO2O7}
pwn.college{zaSwvY2o4F2peyFms.siHgMXgwH7QPY13NtUVlEYl03vq87}
pwn.college{O5RxPvvgamzdCLJBxwBrwe7e0FvOHJu9zBPwB3nfhZnRU5i}
pwn.college{DXPmcQspf9M-yoDbGAm5g8Wk0JjI7UAdfnaZ4tiS1xYPFki}
pwn.college{PIqCpGNGiMt8EtpChbsY6XBaFUi-jsUUzSHBhsqLfhwqU3T}
pwn.college{F5P8EyF0lUEZDxYq005XUekfjmFtNmU30t7B9Zqn.2j7AQ6}
pwn.college{iLtvy2JUGn2N-0TYvSuAQLOcHj3SbAV7UyK1GxJ4clVJny5}
pwn.college{f0t5AWYrnjlVC1ISG0t2Pu8HNlOvPL951BfPkXMeQlOGUC7}
pwn.college{lZqUbLDFm2QZ0xWb8eMUn8FnplYxHaM3-f.NnsBzfrTXQHQ}
pwn.college{gV-q.PaG.m1ckCk-Uk8tQvPYX5QXam4SK0VqGHmM4-QoeVH}
pwn.college{UzIlGVlvbdNlQeyPrSBuKrFL805.0FNzMDOxwyM4kjNzEzW}

```

### New Learnings
Run programs in the background using & so that the shell doesn't get stuck processing command

### References
Used Gemini for assistance cause the program didn't return shell after sending the flag to fifo



## Suspending Processes
This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended

### Solve
**Flag:** `pwn.college{g1Gyg_xeTISdfpGPGrKW8rWuqhI.QX1QDO0wyM4kjNzEzW}`

Use control z after running /challenge/run just like control c to get the flag

```hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 06:40 pts/0    00:00:00 bash /challenge/run
root         148     146  0 06:40 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 06:40 pts/0    00:00:00 bash /challenge/run
root         153     136  0 06:40 pts/0    00:00:00 bash /challenge/run
root         155     153  0 06:40 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{g1Gyg_xeTISdfpGPGrKW8rWuqhI.QX1QDO0wyM4kjNzEzW}
hacker@processes~suspending-processes:~$ 
```

### New Learnings
Control z is used to suspend programs

### References



## Resuming Processes
This challenge's run needs you to suspend it, then resume it.

### Solve
**Flag:** `pwn.college{8L76Wk5oZ8gkn5wN2DacJQ0yp4x.QX2QDO0wyM4kjNzEzW} `

Use control z after running /challenge/run to suspend then use fg to resume and get flag

```hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{8L76Wk5oZ8gkn5wN2DacJQ0yp4x.QX2QDO0wyM4kjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
hacker@processes~resuming-processes:~$ 
```

### New Learnings
Fg is used to resume programs

### References



## Background Processes
This challenge's run needs you to suspend it, then resume it in the background.

### Solve
**Flag:** `pwn.college{86YzfiS4grixXtFGfqMsLhT8lpH.QX3QDO0wyM4kjNzEzW}`

Use control z after running /challenge/run to suspend then use bg to resume and get flag

```hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ 
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{86YzfiS4grixXtFGfqMsLhT8lpH.QX3QDO0wyM4kjNzEzW}
hacker@processes~backgrounding-processes:~$ 
```

### New Learnings
Bg is used to resume programs in the background

### References



## Foreground Processes
This challenge's run needs you to suspend it, then run it in the background then being it to the background.

### Solve
**Flag:** `pwn.college{0kxOJ47tMrChsUpV0tZvjxWJh-P.QX4QDO0wyM4kjNzEzW}`

Use control z after running /challenge/run to suspend then use bg to resume and then use fg to bring into foreground to get flag

```hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{0kxOJ47tMrChsUpV0tZvjxWJh-P.QX4QDO0wyM4kjNzEzW}
hacker@processes~foregrounding-processes:~$ 
 
```

### New Learnings
Fg is used to bring programs in the background to the foreground 

### References



## Starting Backgrounded Processes
This challenge's run needs you run a program in the background to get the flag

### Solve
**Flag:** `pwn.college{MeqWNVehw4m9EJzOp1lt_TbdpSN.QX5QDO0wyM4kjNzEzW}`

Run program with /challenge/run with & in the end

```hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 149
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{MeqWNVehw4m9EJzOp1lt_TbdpSN.QX5QDO0wyM4kjNzEzW}

[1]+  Done                    /challenge/run
hacker@processes~starting-backgrounded-processes:~$ 
```

### New Learnings
& is used to run program in the background

### References



## Process Exit Codes
In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument.

### Solve
**Flag:** `pwn.college{chyekZXnvdsEMxG9F_p1PJ9kxHp.QX5YDO1wyM4kjNzEzW}`

Run program with /challenge/run with & in the end

```hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ /challenge/submit-code $?
CORRECT! Here is your flag:
pwn.college{chyekZXnvdsEMxG9F_p1PJ9kxHp.QX5YDO1wyM4kjNzEzW}
hacker@processes~process-exit-codes:~$ 
```

### New Learnings
You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value)

### References