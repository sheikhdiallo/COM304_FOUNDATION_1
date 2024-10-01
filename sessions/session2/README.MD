[Main Menu](../../sessions/README.md) | [session2](../session2/) 

# Session 2

## Introduction
In this session, we will consolidate looking at Github and begin looking at computer architecture.

## Short history of computing

Presentation: [short History of computing](../session2/docs/com304-foundation-history-1.0.pdf)


## Computer Architecture

Presentation: [Computer Architecrure](../session2/docs/com304-foundation-computer-Architecture-1.0.pdf)

### Exercise 1 - Binary and Hex

Because computers work with binary numbers it is important to be familiar with binary and hexadecimal notation.

Bottom 4 bits of an 8 bit byte


| decimal | binary | hexadecimal |
|=------- |=-------|=------------|
| 0       | 0000   | 0           |
| 1       | 0001   | 1           |
| 2       | 0010   | 2           |
| 3       | 0011   | 3           |
| 4       | 0100   | 4           |
| 5       | 0101   | 5           |
| 6       | 0110   | 6           |
| 7       | 0111   | 7           |
| 8       | 1000   | 8           |
| 9       | 1001   | 9           |
| 10      | 1010   | A           |
| 11      | 1011   | B           |
| 12      | 1100   | C           |
| 13      | 1101   | D           |
| 14      | 1110   | E           |
| 15      | 1111   | F           |

Top 4 bits of an 8 bit byte

11111111 = FF = 255 

128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255 = FF


| decimal | binary | hexadecimal |
|=------- |=-------|=------------|
| 0       | 00000000   | 00      |
| 16      | 00010000   | 10      |
| 32      | 00100000   | 20      |
| 48      | 00110000   | 30      |
| 64      | 01000000   | 40      |
| 80      | 01010000   | 50      |
| 96      | 01100000   | 60      |
| 112     | 01110000   | 70      |
| 128     | 10000000   | 80      |
| 144     | 10010000   | 90      |
| 160     | 10100000   | A0      |
| 176     | 10110000   | B0      |
| 192     | 11000000   | C0      |
| 208     | 11010000   | D0      |
| 224     | 11100000   | E0      |
| 240     | 11110000   | F0      |

If you want a little practice with binary numbers try the cisco binary game 

[cisco binary game ](https://learningnetwork.cisco.com/s/binary-game)

[cisco binary game NOTES](https://learningcontent.cisco.com/games/binary/index.html)

If you want a little practice with hexadecimal numbers try the HEX game

[HEX GAME](hex game https://studio.code.org/projects/applab/q5Mw0Zhs58a_Chr-zn75thpwnjMTw6n2hh_2aN1hwSE)  Enter the hexadecimal value in the green box. If you see a hexadecimal number on the right, click the bits to make the binary number match.

Also try the [hex calculator](https://www.calculator.net/hex-calculator.html)

### Exercise 2 - Boolean Algebra

Boolean Algebra is the basis of computing. 
You need to be bfamiliar with the basics of AND, OR, NOT etc.

If you are unsure of Boolean Algebra there are a really good series of tutorials here

[Boolean Function Tutorials](https://www.electronics-tutorials.ws/boolean/bool_1.html)

[Boolean Algebra Tutorials](https://www.electronics-tutorials.ws/boolean)

### Exercise 3 Logigator

To help you understand how simple logic gates are put together to make complex machines

https://logigator.com/

[Logigator tutorial - The Editor ](https://www.youtube.com/watch?v=tX7HT_0MZRo) 

Look at the following examples

[Logigator Examples](https://logigator.com/en/examples)

Look at the following very complex example of a CPU (Note this is not complete but it does illustrate how a CPU is put together)

[logigator 16-Bit General Purpose CPU](https://logigator.com/en/community/project/8a738598-3e90-4be8-bd02-50e892f4c488)

[somewhat better documentation can be found here:](https://docs.google.com/spreadsheets/d/1MG44B5RzTul4EMDJowlx4hgNE3XYFRoyR7EFi6A0o3M/edit?usp=sharing)

### Exercise 4 ARM Simulator



Look at arm simulation

Can you change the 7 segment LED's

Can you run the picture 

Can you change the picture

On PI
Look at TOP
What memory is used
What swap is used
How much time are processors in use 

## Github clone and merge

You should already have created your github account.

You now need to clone your forked repository on to your pc and merge it with my latest branch.

To do this, you will need to install git on your own machine. 

See [download git for windows https://git-scm.com/downloads/win](https://git-scm.com/downloads/win)

Once GIT is installed, you will need to generate your own public and private keys and clone your repository.

You now need to follow the instructions in [Introduction to Github](../../../main/introductionToGitHub.md) 

Check out the repo on your local PC.

Later you will also check out your repo on your Raspberry Pi
