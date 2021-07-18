# Ukrainian wordnet assorted assumptions, its validation and yes/no strategies

## General & Impact

*Assumption:*
It is possible to build a decent POC for Ukrainian wordnet using parallel wordnets from English, Polish (and probably EWN) and a combination of tricky machine translation, aux datasets, nifty algorithms and some manual labor

*Assumption:*
it is possible to craft a hi-tech solution for Ukrainian wordnet that will require minimal (binary decisions-like) quant of highly qualified manual labor

*Assumption:*
POC of Ukrainian wordnet is enough to make a difference for Ukrainian NLP


## Funding
*Assumption:*
The idea is big enough and it’s impact is big enough and aligned enough with donors perception of a good project, expertise of a core team and good record of its members will allow to find sufficient amount of funds

*Assumption:*
it’s feasible to register a dedicated NGO to search for funding, grow the brand of Lang-Uk and partner with universities

## Human resources
*Assumption:*
our team has enough of free time and expertise on graphs, data science, NLP, project management and product design to deliver a POC

*Assumption:*
after delivering a POC we can expand our team quick enough to cover following areas: linguistics, grant management and funding, finance

*Assumption:*
properly designed crowdsourcing platform is enough to attract highly qualified man power, which will enable the growth of the POC while maintaining sufficient quality

*Assumption:*
there are enough skilled Ukrainian linguists, and they are available for the part-time work as volunteers or for the reasonable price


## Tech

*Assumption:*
there is good development of modern NLP algorithms (translation, corpora, classification, word vectors) that was introduced in the last 10-15 years that will help to achieve better quality of semi-automatic part of the algorithms beneath Ukrainian wordnet

*Assumption:*
existing data (corpora, vectors, dictionaries, like VESUM and ULIF, parallel datasets like wikidata/dbpedia/wiktionary) and work done by number of Ukrainian researchers (UWN, etc) can contribute to the wordnet development.

*Assumption:*
existing hi-level ontology (PWN, plWordnet, ILI, work done by Ukrainian researches) is enough to create a solid, aligned and meaningful ontology for Ukrainian language without massive investment to the manual labor of linguists.


*Assumption:*
ranking of LU candidates by frequency and machine translation will allow to pick important candidates close to high-level ontology

*Assumption:*
machine translation (using LU and glosses) from English, Polish or other languages (and the ensemble combination of the translation results) is sufficient enough to give a set of hypothesis about Ukrainian synsets and its relations

*Assumption:*
manual validation of generated RDF hypothesis for the LU candidates will yield a small forest of trees (were most of  LUs will belong to a couple of trees) rather than a lake of loosely connected facts

*Assumption:*
it is possible to identify most of pwn-ids (internal ids used in the original wordnet) for the English synsets from the plWordnet

*Assumption:*
it is possible to match synsets with wikidata using pwn-id, ILI-id or links to the Polish Wikipedia found in plWordNet to translate LU/find glosses with the help of Wikipedia

*Assumption:*
it is possible to use good word vectors to suggests synonyms/antonyms for Ukrainian wordnet

*Assumption:*
it is possible to train a classifier for key relations using train data and word vectors to suggest hyponyms, hypernyms, synonyms, antonyms and other nyms

*Assumption:*
it is possible to identify key LU candidates for inclusion to Ukrainian wordnet using frequencies of unigrams, bigrams (and probably trigrams) obtained from Ubertext and information on POS of lemmas 

*Assumption:*
most LUs are unigrams

*Assumption:*
hypernym/hyponym tree is not very deep
