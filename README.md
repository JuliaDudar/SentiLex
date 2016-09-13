# Dictionary-, Corpus-, and NWE-based Generation of Sentiment Lexicons

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This project provides scripts and executable files for generating
sentiment lexicons from `GermaNet` (a German equivalent of `WordNet`),
raw text corpora, and neural word embeddings.

## Examples

### Hu and Liu (2004)

To generate a sentiment lexicon using the method of
[Hu and Liu (2004)](https://www.cs.uic.edu/~liub/publications/kdd04-revSummary.pdf),
you should envoke the following command:

```shell

./scripts/generate_lexicon.py hu \
--form2lemma=data/GermaNet_v9.0/gn_form2lemma.txt \
data/seeds/hu_liu_seedset.txt data/GermaNet_v9.0

```

### Takamura et al. (2005)

To generate a sentiment lexicon using the method of [Takamura et
al. (2005)](http://delivery.acm.org/10.1145/1220000/1219857/p133-takamura.pdf?ip=77.179.90.234&id=1219857&acc=OPEN&key=4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E6D218144511F3437&CFID=830128042&CFTOKEN=27668650&__acm__=1472910085_b90c7157c9757c8c7e7ccacc73a39bb5),
you should use the following command (note that the file
`data/corpus/cc.txt` is not included in this repository due to its big
size):

```shell

./scripts/generate_lexicon.py takamura --form2lemma=data/GermaNet_v9.0/gn_form2lemma.txt \
    --plot=png data/seeds/turney_littman_2003.txt data/GermaNet_v9.0/ data/corpus/cc.txt -1

```

### Esuli and Sebastiani (2006)

For generating a sentiment lexicon using the `SentiWordNet` method of
[Esuli and Sebastiani (2006)](http://ontotext.fbk.eu/Publications/sentiWN-TR.pdf),
you should use the following command:

```shell

./scripts/generate_lexicon.py esuli \
--form2lemma=data/GermaNet_v9.0/gn_form2lemma.txt \
data/seeds/turney_littman_gi_seedset.txt data/GermaNet_v9.0

```

### Blair-Goldensohn (2008)

To generate a sentiment lexicon using the method of
[Blair-Goldensohn et al. (2008)](http://www.australianscience.com.au/research/google/34368.pdf),
use the following command:

```shell

./scripts/generate_lexicon.py blair-goldensohn \
 --ext-syn-rels --seed-pos=adj \
 --form2lemma=data/GermaNet_v9.0/gn_form2lemma.txt \
 data/seeds/hu_liu_seedset.txt data/GermaNet_v9.0/

```

### Hassan (2010)

To generate a sentiment lexicon using the method of
[Hassan and Radev (2010)](https://www.aclweb.org/anthology/P/P10/P10-1041.pdf),
you should use the following command:

```shell

./scripts/generate_lexicon.py awdallah --ext-syn-rels \
--seed-pos=adj --form2lemma=data/GermaNet_v9.0/gn_form2lemma.txt \
data/seeds/hu_liu_seedset.txt data/GermaNet_v9.0/

```

Evaluation
----------

You can evaluate the resulting sentiment lexicon on the
[PotTS](https://github.com/WladimirSidorenko/PotTS) dataset by using
the following command and providing a valid path to the downloaded
corpus data:

```shell

./scripts/evaluate.py -l data/form2lemma.txt \
	data/results/esuli-sebastiani/esuli-sebastiani.ext-syn-rels.turney-littman-seedset.txt \
	${PATH_TO_PotTS}/corpus/basedata/ ${PATH_TO_PotTS}/corpus/annotator-2/markables/

```
