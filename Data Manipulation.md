## Translating Characters
tr - (tr)anslates character provided in its first argument to the character provided in its second argument
It can also handle multiple characters, with the characters in different positions of the first argument replaced with associated characters in the second argument.
Challenge- /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?
```bash
hacker@data~translating-characters:~$ /challenge/run | tr AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ
yOUR CASE-SWAPPED FLAG:
pwn.college{0l2RVSWPD99Q-CZ3QVO20yncM4d.01MxEzNxwCO2UDOzEzW}

## Deleting Characters
tr can also translate characters to nothing (i.e delete them) by using - tr -d (character(s))
```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^!
Your character-stuffed flag:
pwn%.c%ol%l%e%g%e%{%s%C%T%b%c%eWO%Obf%Q%T%0%S%Ms%v5%S%l%y6%l%CN6%.0%F%Nx%E%zN%xwC%O2%U%D%O%z%E%zW}
hacker@data~deleting-characters:~$ /challenge/run | tr -d %^
Your character-stuffed flag:
pwn.college{sCTbceWOObfQT0SMsv5Sly6lCN6.0FNxEzNxwCO2UDOzEzW}
hacker@data~deleting-characters:~$
```
## Deleting newlines
```bash
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```
EXAMPLE -
```bash
hacker@data~deleting-newlines:~$ /challenge/run 
Your line-split flag: 
p
wn.
colle
ge
{0
EAOd
8t
L
WUZ
I
s
G
f
Q
z
RAI
oq
_
Sa
K
M
.
0
V
N
xE
z
N
x
w
C
O2
U
D
O
z
E
z
W}


hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{0EAOd8tLWUZIsGfQzRAIoq_SaKM.0VNxEzNxwCO2UDOzEzW}hacker@data~deleting-newlines:~$ 
```
## Extracting first lines using head
Used to grab just the early output.
```bash
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```
by default head extracts the first 10 lines but that can be controlled using -n
```bash
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```
## Extractiing specific section of text
cut command : cut -d (arg1) -f (arg2)
(arg1) - column delimiter i.e. how the columns are seperated
(arg2) - field number i.e. which column to extract
Challenge - in this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns.
Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. 
Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.
```bash
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run 
21011 p
7543 w
12485 n
22072 .
8794 c
21456 o
12133 l
19077 l
27018 e
5602 g
17153 e
2110 {
20082 0
16938 i
22100 s
22441 g
21417 d
11586 x
30469 Y
30124 f
31769 e
20819 i
23145 W
14535 M
5034 p
7365 0
30745 o
29187 C
19616 E
14861 H
12882 A
21368 -
327 C
1804 w
19189 q
14270 p
23548 Z
2047 _
2029 l
23062 .
28374 0
16137 1
6269 N
28878 x
28798 E
28787 z
15556 N
29279 x
21062 w
2381 C
19855 O
1512 2
20330 U
22545 D
22664 O
20798 z
25896 E
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{0isgdxYfeiWMp0oCEHA-CwqpZ_l.01NxEzNxwCO2UDOzEzW}hacker@data~extracting-specific-sections-of-text:~$
```
## Sorting Data
The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order
```bash
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```
By default, sort orders lines alphabetically. Arguments can change this:

    -r: reverse order (Z to A)
    -n: numeric sort (for numbers)
    -u: unique lines only (remove duplicates)
    -R: random order!
