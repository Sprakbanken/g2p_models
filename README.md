# Grapheme to Phoneme models for Norwegian Bokmål

[![lang-button](https://img.shields.io/badge/-Norsk-blue)](https://github.com/Sprakbanken/g2p_models/blob/main/LESMEG.md) [![lang-button](https://img.shields.io/badge/-English-grey)](https://github.com/Sprakbanken/g2p_models/blob/main/README.md)

This repo contains G2P models for Norwegian bokmål[^1], which produce phonemic transcriptions for *close-to-spoken* pronunciations (such as in spontaneous conversations) and *close-to-written* pronunciations (such as when reading text aloud) for 5 different dialect areas:

1. East Norwegian
2. South West Norwegian
3. West Norwegian
4. Central Norwegian (Trøndersk)
5. North Norwegian

[^1]: Bokmål is the most widely used written standard for Norwegian. The other written standard is Nynorsk. Read more on [Wikipedia](https://en.wikipedia.org/wiki/Norwegian_orthography).


## Setup
Follow installation instructions from  [Phonetisaurus](https://github.com/AdolfVonKleist/Phonetisaurus), steps  "Next grab and install OpenFst-1.7.2" and "Checkout the latest Phonetisaurus from master and compile without bindings".


## Usage

```shell
phonetisaurus-apply --model models/nb_e_spoken.fst --word_list NB-uttale-wordlist_test.txt -n 1  -v  > output.txt
```

- Input data (`--word_list`) should be a list of newline-delimited words. See the file [`NB-uttale-wordlist_test.txt`](./NB-uttale-wordlist_test.txt) for an example.
- The trained G2P-models are `.fst` files located in the `models` folder. The same folder also contains aligned `.corpus` files and phoneme 8-gram models (`.arpa` files), also from the `Phonetisaurus` training process.
- `-n` lets you adjust the number of most probable predictons.

## Evaluation

Run the `evaluate.py` script to get word-error-rate (WER) and phoneme-error-rate (PER) for a G2P-model, given the dialect and pronunciation variant (e.g. "e_spoken"):

```shell
python evalutate.py -l e_spoken
```

Model | Word Error Rate | Phoneme Error Rate
--- | --- | ---
*nb_e_spoken.fst* | 14.0492 | 2.7148
*nb_e_written.fst* | -- | --
*nb_w_spoken.fst* | -- | --
*nb_w_written.fst* | -- | --
*nb_sw_spoken.fst* | -- | --
*nb_sw_written.fst* | -- | --
*nb_t_spoken.fst* | -- | --
*nb_t_written.fst* | -- | --
*nb_n_spoken.fst* | -- | --
*nb_n_written.fst* | -- | --


> **Note:** The code to do WER and PER calculations in `evaluate.py` is copied and modified from the `g2p_stats.py` script in this repo: [Sprakbanken/g2p-nb](https://github.com/Sprakbanken/g2p-nb).


## Data

The pronunciation lexica that were used to train the G2P-models are free to download and use from Språkbanken's resource catalogue: [NB Uttale](https://www.nb.no/sprakbanken/ressurskatalog/oai-nb-no-sbr-79/)

For more information about the data, see the Github repo: [Sprakbanken/nb_uttale](https://github.com/Sprakbanken/nb_uttale)

The data was split into test and train subsets with

### Transcription standard
Although the original NST lexicon uses X-SAMPA as a transcription standard, an equivalent standard is used in this project., which is easier to read by humans, *NoFAbet*. NoFAbet is in part based on [2-letter ARPAbet](https://en.wikipedia.org/wiki/ARPABET) and is made by [Nate Young](https://www.nateyoung.se/) for the National Library of Norway in connection with the development of [*NoFA*](https://www.nb.no/sprakbanken/en/resource-catalogue/oai-nb-no-sbr-59/), a forced aligner for Norwegian. The equivalence table below contains X-SAMPA, IPA and NoFAbet notatations.

### X-SAMPA-NoFAbet equivalence table
X-SAMPA | IPA | NoFAbet | Example
--- | --- | --- |---
A: | ɑː | AA0 | b**a**d
{: | æː | AE0 | v**æ**r
{ | æ | AEH0 | v**æ**rt
{*I | æj | AEJ0 | s**ei**
E*u0 | æw | AEW0 | s**au**
A | ɑ | AH0 | h**a**tt
A*I | ɑj | AJ0 | k**ai**
@ | ə | AX0 | b**e**hage
b | b | B | **b**il
d | d | D | **d**ag
e: | eː | EE0 | l**e**k
E | ɛ | EH0 | p**e**nn
f | f | F | **f**in
g | g | G | **g**ul
h | h | H | **h**es
I | I | IH0 | s**i**tt
i: | iː | II0 | v**i**n
j | j | J | **j**a
k | k | K | **k**ost
C | ç | KJ | **k**ino
l | l | L | **l**and
l= | l̩ | LX0 |
m | m | M | **m**an
m= | m̩ | MX0 |
n | n | N | **n**ord
N | ŋ | NG | e**ng**
n= | n̩ | NX0 |
o: | oː | OA0 | r**å**
O | ɔ | OAH0 | g**å**tt
2: | øː | OE0 | l**ø**k
9 | œ | OEH0 | h**ø**st
9*Y | œj | OEJ0 | k**øy**e
U | u | OH0 | f***o**rt
O*Y | ɔj | OJ0 | konv**oy**
u: | uː | OO0 | b**o**d
@U | oʋ | OU0 | sh**ow**
p | p | P | **p**il
r | r | R | **r**ose
d` | ɖ | RD | reko**rd**
l` | ɭ | RL | pe**rl**e
l`= | ɭ̩ | RLX0 |
n` | ɳ | RN | ba**rn**
n`= | ɳ̩ | RNX0 |
s` | ʂ | SJ | pe**rs**
t` | ʈ | RT | sto**rt**
r= | r̩ | RX0 |
s | s | S | **s**il
S | ʂ | SJ | **sj**u
s= | s̩ | SX0 |
t | t | T | **t**id
u0 | ʉ | UH0 | r**u**ss
u0 j | ʉj | UH0_J | Anh**ui**
}: | ʉː | UU0 | h**u**s
v | v | V | **v**ase
w | w | W | **W**ashington
Y | y | YH0 | n**y**tt
y: | yː | YY0 | n**y**

Unstressed syllables are marked with a 0 after the vowel or consonant syllable nucleus. The nucleus is marked with a *1* for tone 1 and a *2* for tone 2. Secondary stress is marked with *3*. In the material without tone and stress marking, all *3*s are replaced by zeros and all *2*s with *1*s. (sjekk)

For compatibility with NoFA, retroflex *s* is rendered as *SJ* instead of *RS*, which means that there is no distinction between postalveolar and retroflex *s* in the transcriptions. (sjekk)

## License

These models are shared with a [Creative_Commons-ZERO (CC-ZERO)](https://creativecommons.org/publicdomain/zero/1.0/) license, and so are the lexica they are trained on. The models can be used for any purpose, as long as it is compliant with Phonetisaurus' license.
