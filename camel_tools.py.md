The `camel-tools` library is a powerful suite of tools for Arabic natural language processing (NLP), developed by the CAMeL Lab at New York University Abu Dhabi

---
# Installation
You need `python3.6+` and it is recommened to use `venv` due to the size of the library
```bash
$ python -m venv venv
$ source venv/bin/activate
(venv) $ pip install camel-tools
```
#### Data Installation
Many `camel-tools` components require pre-trained models or data files. After installing the library, you need to download this data using the `camel_data` command:
```bash
camel_data -i all
```

- `-i all`: Installs all available datasets (e.g., for morphology, disambiguation, sentiment analysis).
- **Size**: This can take ~1-2 GB of disk space, so ensure you have enough storage.
- **Location**: Data is typically stored in `~/.camel_tools/data/`.

For specific components only replace `all` with a package name like `morphology-db-calima-msa` (see the full list in the [documentation](https://camel-tools.readthedocs.io/en/latest/index.html)).

---
# Usage
#### 1. **Tokenization**
The `Tokenizer` splits Arabic text into tokens, handling clitics (e.g., prepositions, conjunctions) appropriately.
```python
from camel_tools.tokenizers.word import simple_word_tokenize
from camel_tools.utils.dediac import dediac_ar

text = "والكتاب الموجود على الطاولة"

# Remove diacritics (optional)
text_dediac = dediac_ar(text)
# Simple tokenization
tokens = simple_word_tokenize(text_dediac)
print("Tokens:", tokens)
```
**Output**:
```
Tokens: ['و', 'الكتاب', 'الموجود', 'على', 'الطاولة']
```
For more advanced tokenization (e.g., splitting clitics), use the `MorphologicalTokenizer` with a morphology database (see below).

---
#### 2. **Morphological Analysis and Disambiguation**
The `MorphologyDB` and `Analyzer` classes allow you to analyze and disambiguate Arabic words.

```python
from camel_tools.morphology.database import MorphologyDB
from camel_tools.morphology.analyzer import Analyzer

# Load the default Modern Standard Arabic (MSA) morphology database
db = MorphologyDB.builtin_db('calima-msa')

# Create an analyzer
analyzer = Analyzer(db)

# Analyze a word
word = "يكتبون"
analyses = analyzer.analyze(word)

# Print all possible analyses
for analysis in analyses:
    print("Lemma:", analysis['lex'], "| POS:", analysis['pos'], "| Gloss:", analysis['gloss'])
```

**Sample Output**:
```
Lemma: كتب | POS: verb | Gloss: write
...
```

To disambiguate in context, use the `Disambiguator`:

```python
from camel_tools.disambig.mle import MLEDisambiguator
from camel_tools.tokenizers.word import simple_word_tokenize

# Load the pre-trained MLE disambiguator for MSA
mle = MLEDisambiguator.pretrained('calima-msa')

# Example sentence
sentence = "يكتبون الكتاب"
tokens = simple_word_tokenize(sentence)

# Disambiguate
disambig = mle.disambiguate(tokens)

# Extract lemma and POS for each token
for d in disambig:
    print(f"Word: {d.word} | Lemma: {d.analyses[0].analysis['lex']} | POS: {d.analyses[0].analysis['pos']}")
```
**Output**:
```
Word: يكتبون | Lemma: كتب | POS: verb
Word: الكتاب | Lemma: كتاب | POS: noun
```
---
#### 3. **Dialect Identification**
The `DialectIdentifier` classifies Arabic text into dialects (e.g., Egyptian, Gulf, Levantine).

```python
from camel_tools.dialectid import DialectIdentifier

# Load the pre-trained dialect identifier
did = DialectIdentifier.pretrained()

# Example sentences
sentences = [
    "الكتاب ده حلو اوي",  # Egyptian
    "الكتاب حلو مرة"     # Gulf
]

# Predict dialects
predictions = did.predict(sentences, 'city')  # 'city' for city-level, 'region' for broader regions

for sentence, pred in zip(sentences, predictions):
    print(f"Sentence: {sentence} | Dialect: {pred.top}")
```
**Output**:
```
Sentence: الكتاب ده حلو اوي | Dialect: Cairo
Sentence: الكتاب حلو مرة | Dialect: Riyadh
```
---
#### 4. **Sentiment Analysis**
The `SentimentAnalyzer` predicts sentiment (positive, negative, neutral).
```python
from camel_tools.sentiment import SentimentAnalyzer

# Load the pre-trained sentiment analyzer
sa = SentimentAnalyzer.pretrained('ar')

# Example sentences
sentences = [
    "الكتاب رائع جدا",
    "الكتاب سيء للغاية"
]

# Predict sentiment
sentiments = sa.predict(sentences)

for sentence, sentiment in zip(sentences, sentiments):
    print(f"Sentence: {sentence} | Sentiment: {sentiment}")
```
**Output**:
```
Sentence: الكتاب رائع جدا | Sentiment: positive
Sentence: الكتاب سيء للغاية | Sentiment: negative
```
---
### Step 4: Advanced Features
#### Morphological Tokenization
For splitting clitics (e.g., "والكتاب" → "و +ال +كتاب"):
```python
from camel_tools.morphology.database import MorphologyDB
from camel_tools.tokenizers.morphological import MorphologicalTokenizer
from camel_tools.disambig.mle import MLEDisambiguator

# Load morphology database and disambiguator
db = MorphologyDB.builtin_db('calima-msa')
mle = MLEDisambiguator.pretrained('calima-msa')

# Create tokenizer
tokenizer = MorphologicalTokenizer(db, scheme='atbtok')  # 'atbtok' for ATB-style tokenization

# Example sentence
sentence = "والكتاب الموجود"
tokens = simple_word_tokenize(sentence)
disambig = mle.disambiguate(tokens)
morph_tokens = tokenizer.tokenize(disambig)

print("Morphological Tokens:", morph_tokens)
```
**Output**:
```
Morphological Tokens: ['و', '+ال', 'كتاب', '+ال', 'موجود']
```
#### Transliteration
Convert Arabic script to Latin (Buckwalter scheme):
```python
from camel_tools.utils.charmap import CharMapper

# Create a mapper for Arabic to Buckwalter
mapper = CharMapper.builtin_mapper('arc2bw')

# Example text
text = "الكتاب"
translit = mapper.map_string(text)

print("Buckwalter Transliteration:", translit)
```
**Output**:
```
Buckwalter Transliteration: AlktAb
```
---
# Troubleshooting
1. **Data Not Found**:
   - Ensure you ran `camel_data -i all` successfully.
   - Check `~/.camel_tools/data/` for the downloaded files.
1. **Memory Issues**:
   - Some components (e.g., sentiment analysis) use PyTorch and may require significant RAM/GPU. Reduce batch sizes or use a smaller model if needed.
1. **Unsupported Dialect/Model**:
   - Verify available models with `camel_data -l` (lists packages).
---
# Resources
- **Documentation**: Full details are available at https://camel-tools.readthedocs.io/.
- **Source**: GitHub repo: https://github.com/CAMeL-Lab/camel_tools.