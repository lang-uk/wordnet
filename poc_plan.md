Below is our rough plan to POC with tasks and roles:

### Desk research
- [ ] Read the book on Polish Wordnet (@dchaplinsky)
- [ ] Calculate metrics on the depth and distribution of LU in the Polish wordnet (@dchaplinsky)
- [ ] Calculate metrics on the depth and distribution of LU in English wordnet (@dchaplinsky)
- [ ] Find overlap metrics between English and Polish wordnet ontology (@dchaplinsky)
- [ ] Investigate dbpedia/wiktionary as a source of data and describe the findings (@vseloved)
- [ ] Find an ontology, created for the Ukrainian nouns [here](http://science.lpnu.ua/sisn/all-volumes-and-issues/volume-673-2010/rozroblennya-wordnet-podibnogo-slovnika-ukrayinskoyi), (@mariana-scorp)

### Support
- [ ] Create an RDF example of the simple wordnet (@vseloved) [turtle example 1](http://wordnet-rdf.princeton.edu/about), [turtle example 2](https://github.com/globalwordnet/english-wordnet)
- [ ] Load aforementioned example to the Gruff (@vseloved)
- [ ] Generate couple of access tokens to Google Translate Cloud Service (@mariana-scorp, @vseloved, @dchaplinsky) using their $300 credit proposition

### Development
- [ ] Export top-level mixed ontology from pl/PWN to the RDF triplets (@dchaplinsky)
- [ ] Visualise it for @mariana-scorp (@dchaplinsky)
- [ ] Decide on the desired depth of high-level ontology (@mariana-scorp)
- [ ] Describe methodology for the creation of high-level ontology in a separate document (@mariana-scorp)
- [ ] Compile the high-level ontology for Ukrainian language (@mariana-scorp)
- [ ] Create a version annotated for the part of speech for the big enough corpus (@dchaplinsky/@arysin)
- [ ] Calculate frequencies of unigrams and bigrams for the lemmas, grouped and filtered by noun, adj, verb (@dchaplinsky)
- [ ] Annotate existing synsets from English and Polish corpus with some metrics (position at hypernym/hyponym tree, number of hyponyms) (@dchaplinsky)
- [ ] Translate existing synsets using google translate (@dchaplinsky)
- [ ] Try to improve quality of the translation trying differnt LUs from synsets with combination of glosses (@dchaplinsky)
- [ ] Match english part of plWordnet with original PWN and add pwn_ids (@dchaplinsky)
- [ ] Translate existing synsets for English using wikidata and pwn_ids and/or ILI (@dchaplinsky)
- [ ] Translate existing synsets for Polish using links to Polish wikipedia and wikidata (@dchaplinsky)
- [ ] Combine translated LUs with the frequencies of unigrams/ngrams of given POS and synset weight metrics above (@dchaplinsky)
- [ ] Generate and evaluate some hypernym/hyponym relations for translated and ranked LUs
