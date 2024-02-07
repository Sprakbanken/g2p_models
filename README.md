# Grapheme-to-Phoneme models for Norwegian Dialects

## Introduction
This repo contains Grapheme-to-Phoneme (G2P) models for five Norwegian dialects for the written standard Norwegian Bokmål. The models are meant to be used with the G2P engine [Phonetisaurus](https://github.com/AdolfVonKleist/Phonetisaurus).
The G2P models can be used to generate pronunciation lexica from word lists. For more information on how to do that, consult the Phonetisaurus repo.

## Content
Content of the repo.

## Transcription standard
Although the original NST lexicon uses X-SAMPA as a transcription standard, an equivalent standard is used in this project, which is easier to read by humans: *NoFAbet*. NoFAbet is in part based on [2-letter ARPAbet](https://en.wikipedia.org/wiki/ARPABET) and is made by [Nate Young](https://www.nateyoung.se/) for the National Library of Norway in connection with the development of *NoFA*, a forced aligner for Norwegian.


### X-SAMPA-NoFAbet equivalence table
X-SAMPA | NoFAbet | Example
--- | --- | ---
A: | AA0 | b**a**d
{: | AE0 | v**æ**r
{ | AEH0 | v**æ**rt
{*I | AEJ0 | s**ei**
E*u0 | AEW0 | s**au**
A | AH0 | h**a**tt
A*I | AJ0 | k**ai**
@ | AX0 | b**e**hage
b | B | **b**il
d | D | **d**ag
e: | EE0 | l**e**k
E | EH0 | p**e**nn
f | F | **f**in
g | G | **g**ul
h | H | **h**es
I | IH0 | s**i**tt
i: | II0 | v**i**n
j | J | **j**a
k | K | **k**ost
C | KJ | **k**ino
l | L | **l**and
l= | LX0 |
m | M | **m**an
m= | MX0 |
n | N | **n**ord
N | NG | e**ng**
n= | NX0 |
o: | OA0 | r**å**
O | OAH0 | g**å**tt
2: | OE0 | l**ø**k
9 | OEH0 | h**ø**st
9*Y | OEJ0 | k**øy**e
U | OH0 | f***o**rt
O*Y | OJ0 | konv**oy**
u: | OO0 | b**o**d
@U | OU0 | sh**ow**
p | P | **p**il
r | R | **r**ose
d` | RD | reko**rd**
l` | RL | pe**rl**e
l`= | RLX0 |
n` | RN | ba**rn**
n`= | RNX0 |
s` | SJ | pe**rs**
t` | RT | sto**rt**
r= | RX0 |
s | S | **s**il
S | SJ | **sj**u
s= | SX0 |
t | T | **t**id
u0 | UH0 | r**u**ss
u0 j | UH0_J | Anh**ui**
}: | UU0 | h**u**s
v | V | **v**ase
w | W | **W**ashington
Y | YH0 | n**y**tt
y: | YY0 | n**y**

Unstressed syllables are marked with a 0 after the vowel or consonant syllable nucleus. The nucleus is marked with a *1* for tone 1 and a *2* for tone 2. Secondary stress is marked with *3*. In the material without tone and stress marking, all *3*s are replaced by zeros and all *2*s with *1*s.

## Evaluation

Model | Word Error Rate | Phoneme Error Rate
--- | --- | ---

## Usage
The models created in this project can be used for any purpose, as long as it is compliant with [Phonetisaurus' license](https://github.com/AdolfVonKleist/Phonetisaurus/blob/master/LICENSE).
