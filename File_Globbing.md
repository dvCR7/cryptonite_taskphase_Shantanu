## Matching with *
Learnt about the `*` and how the terminal interprets it as a wildcard.<br>
It auto completes or look for a file when given sufficient info.<br>
to get the flag i used `cd /ch*` to go in `/challenge` and used run there.<br>
```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{8bWSDojhFgMYjsNq92I68Yd572L.dFjM4QDLzYTN0czW}
```
/ch*/ru* also works for /challenge/run
## Matching with ?
Fairly easy challenge, the `?` has similar functionality to `*` but only works for a single character.<br>
Used to glob to the `challenge` directory by using `cd /?ha??enge` command and then ran the `/challenge/run` to get the flag.<br>
```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{8-tL2TeU1MY28cfpaGq5RuAGln6.dJjM4QDLzYTN0czW}
```
## Matching with []
works similar to `?` but can check for multiple single characters at once.<br>
To get the flag I had to pass 4 files at once as an argument to `/challenge/run`.<br>
Q- Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!
```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{k2BenPZ_IarwzW7OrmwpYw09_Vs.dNjM4QDLzYTN0czW}
```
## Matching paths with []
Similar to before but learned a new usecase of `[]` that we can use this in absolute paths aswell.<br>
To get the flag I passed the absoulte path of the files a,b,s,h as an argument to run.<br>
```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{MyuhxnTyjc-N5jmirsLk5pwKEVU.dRjM4QDLzYTN0czW}
```
## Multiple Globs
Bash supports the expansion of multiple globs in a single word. For example:
```bash
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).
## Mixing Globs
I just had to run the 3 files in a way that they are less than 6 charecters.<br>
It was easy as first I used `cd /challenge/files` then used `/challenge/run` and as an argument to this I passed `[cep]*`.<br>
The thought process was that I will get the first letter by using [cep] and then the rest of the string bt `*`.<br>
```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files/
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{AMcOHuwp1pFCbM90LNiUeGXJuD0.dVjM4QDLzYTN0czW}
```
## Exclusionary Globbing
Learnt about other function of `[]` that when `^,!` is used in `[]` will filter out all the letters.<br>
used `[!pwn]*` to get the flag.<br>
```bash
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{kHt0bISzlRJ4a_mrW5YlEre07nb.dZjM4QDLzYTN0czW}
```
## Tab Completion
1)Tab Completion
2)Multiple options for tab completion
3)Tab completion on commands
