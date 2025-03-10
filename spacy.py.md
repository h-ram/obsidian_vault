**spaCy** a library for [[Natural Language Processing (NLP)]]. Unlike [[nltk.py]], which is more academic and educational, spaCy focuses on providing production-ready tools that can be used in real-world applications.
# **Installation**
```bash
pip install spacy
```
After installing spaCy, you'll also need to download a language model (such as `en_core_web_sm` for English):
```bash
python -m spacy download en_core_web_sm
```
All The available models can be seen here: [Available models](https://spacy.io/models)
# **Usage**
```python
import spacy
nlp = spacy.load("en_core_web_sm")
```
#### 3.1 **Processing Text**
Once you load the model, you can process text to create a `Doc` object, which represents the processed text:
```python
text = "SpaCy is an amazing NLP library!"
doc = nlp(text)
```
The `doc` object contains the processed version of the text, which is tokenized and includes linguistic annotations.
#### 3.2 **Tokenization**
In spaCy, tokenization happens automatically when you process a text using the `nlp` object. You can access individual tokens as follows:
```python
for token in doc:
    print(token.text)
```

```bash
# Output
SpaCy
is
an
amazing
NLP
library
!
```
#### 3.3 **Part-of-Speech Tagging (POS)**
spaCy assigns parts of speech (e.g., noun, verb) to each token automatically:
```python
for token in doc:
    print(f"{token.text}: {token.pos_}")
```

```bash
# Output:
SpaCy: PROPN
is: AUX
an: DET
amazing: ADJ
NLP: PROPN
library: NOUN
!: PUNCT
```

- `PROPN` = Proper noun
- `AUX` = Auxiliary verb
- `DET` = Determiner
- `ADJ` = Adjective
- `NOUN` = Noun
- `PUNCT` = Punctuation
#### 3.4 **Named Entity Recognition (NER)**
spaCy can recognize entities like persons, organizations, locations, etc. You can access named entities from the processed `doc`:
```python
for ent in doc.ents:
    print(f"{ent.text}: {ent.label_}")
```

```bash
# Output
SpaCy: ORG
```
- `ORG` = Organization
#### 3.5 **Lemmatization**
Lemmatization reduces words to their base or root form. In spaCy, you can access the lemmatized form of tokens:
```python
for token in doc:
    print(f"{token.text}: {token.lemma_}")
```

```bash
# Output:
SpaCy: SpaCy
is: be
an: an
amazing: amazing
NLP: NLP
library: library
!: !
```
#### 3.6 **Dependency Parsing**
Dependency parsing helps in understanding the grammatical structure of a sentence, identifying relationships between words.
```python
for token in doc:
    print(f"{token.text} -> {token.dep_} -> {token.head.text}")
```

```bash
# Output:
SpaCy -> nsubj -> is
is -> ROOT -> is
an -> det -> library
amazing -> amod -> library
NLP -> compound -> library
library -> attr -> is
! -> punct -> library
```

- `nsubj` = Nominal subject
- `ROOT` = Main verb in the sentence
- `det` = Determiner
- `amod` = Adjective modifier
- `attr` = Attributive modifier
#### 3.7 **Sentence Segmentation**
spaCy can also split text into sentences:
```python
for sent in doc.sents:
    print(sent.text)
```

```bash
# Output
SpaCy is an amazing NLP library!
```
---
# **Etymology**
The name **spaCy** is pronounced "spay-SEE" .
The exact origin of the name isn't officially documented, but it is often thought to be a play on the word "space," indicating that spaCy focuses on parsing and understanding linguistic structures in "space," or text. 

---
Resrouces:
- [Available models](https://spacy.io/models)