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

## License

These models are shared with a [Creative_Commons-ZERO (CC-ZERO)](https://creativecommons.org/publicdomain/zero/1.0/) license, and so are the lexica they are trained on. The models can be used for any purpose, as long as it is compliant with Phonetisaurus' license.
