NLTK (Natural Language Toolkit) is python library used for [[Natural Language Processings (NLP)|NLP]].
```bash
pip install nltk
```
# **Usage**
First thing to do is to download [[#Resources]] 
```python
import nltk
nltk.download('popular')  # Downloads a collection of commonly used datasets
nltk.download('popular', quiet=True) # supresses download message
```

# **Resources**
The `.download()` function in NLTK fetches datasets, models, and corpora from the **NLTK Data Repository** and stores them locally in the NLTK data directory (`C:\Users\YourUserName\nltk_data` on Windows). These resources are required for various NLP tasks like **tokenization, POS tagging, Named Entity Recognition (NER), text classification, etc.**
### **1. `punkt`**
- **Purpose:** Tokenization of text into sentences and words.
- **Used For:** `word_tokenize()` and `sent_tokenize()`
    ```python
    from nltk.tokenize import word_tokenize
    word_tokenize("Hello! How are you?")
    # Output: ['Hello', '!', 'How', 'are', 'you', '?']
    ```
### **2. `averaged_perceptron_tagger`**
- **Purpose:** Part-of-Speech (POS) tagging.
- **Used For:** `pos_tag()`
    ```python
    from nltk import pos_tag, word_tokenize
    pos_tag(word_tokenize("The quick brown fox jumps over the lazy dog."))
    # Output: [('The', 'DT'), ('quick', 'JJ'), ('brown', 'JJ'), ('fox', 'NN'), ...]
    ```
### **3. `maxent_ne_chunker`**
- **Purpose:** Named Entity Recognition (NER).
- **Used For:** Extracting proper names, locations, organizations, etc.
    ```python
    from nltk import ne_chunk, pos_tag, word_tokenize
    ne_chunk(pos_tag(word_tokenize("Barack Obama was the president of the USA.")))
    ```
### **4. `words`**
- **Purpose:** Contains a list of English words.
- **Used For:** Spelling correction, word validation.
    ```python
    from nltk.corpus import words
    print(words.words()[:10])  # Prints first 10 words from the list
    ```
### **5. `wordnet`**
- **Purpose:** Provides a lexical database for English.
- **Used For:** Synonyms, antonyms, word relationships.
    ```python
    from nltk.corpus import wordnet
    syns = wordnet.synsets("car")
    print(syns[0].definition())  # Output: 'a motor vehicle with four wheels'
    ```
### **6. `omw-1.4` (Open Multilingual WordNet)**
- **Purpose:** Provides WordNet in multiple languages.
- **Used For:** Finding word meanings across different languages.
    ```python
    from nltk.corpus import wordnet
    print(wordnet.synsets("house", lang="fra"))  # Gets French meanings
    ```
### **7. `stopwords`**
- **Purpose:** A list of common words (e.g., "the", "is", "in") that are often removed in text analysis.
- **Used For:** Text preprocessing, NLP.
    ```python
    from nltk.corpus import stopwords
    print(stopwords.words('english')[:10])  # Outputs first 10 English stopwords
    ```
### **8. `tagsets`**
- **Purpose:** Provides descriptions of different POS tagsets.
- **Used For:** Understanding POS tag meanings.
    ```python
    from nltk.data import load
    print(load('help/tagsets/upenn_tagset.pickle'))
    ```
### **9. `webtext`**
- **Purpose:** Contains example web text (e.g., Firefox forum, movie scripts).
- **Used For:** Testing NLP models on real-world text.
    ```python
    from nltk.corpus import webtext
    print(webtext.raw('pirates.txt')[:500])  # First 500 characters of 'Pirates of the Caribbean' script
    ```
### **10. `twitter_samples`**
- **Purpose:** Provides example tweets for sentiment analysis.
- **Used For:** Training machine learning models for sentiment detection.
    ```python
    from nltk.corpus import twitter_samples
    print(twitter_samples.strings()[:3])  # First 3 sample tweets
    ```
### **11. `popular`**
Includes the previous 10 resources in one.
```
	nltk.download("popular")
```

# **Core NLTK Modules and Functions**
#### 3.1 **Tokenization**
Tokenization is the process of splitting text into words or sentences.
- **Word Tokenization**: Breaking text into individual words.
    ```python
    from nltk.tokenize import word_tokenize
    text = "Hello, how are you?"
    words = word_tokenize(text)
    print(words) # output: ['Hello', ',', 'how', 'are', 'you', '?']
    ```
- **Sentence Tokenization**: Splitting text into sentences.
    ```python
    from nltk.tokenize import sent_tokenize
    text = "Hello. How are you?"
    sentences = sent_tokenize(text)
    print(sentences) # Output : ['Hello.', 'How are you?']
    ```
#### 3.2 **Stopwords**
Stopwords are common words (such as 'is', 'the', 'and') that are often removed in text analysis.
```python
from nltk.corpus import stopwords
nltk.download('stopwords')
stop_words = set(stopwords.words('english'))
print(stop_words)
```
#### 3.3 **Stemming**
Stemming reduces words to their root form (e.g., "running" to "run").
```python
from nltk.stem import PorterStemmer
stemmer = PorterStemmer()
word = "running"
print(stemmer.stem(word))  # Output: run
```
#### 3.4 **Lemmatization**
Lemmatization is similar to stemming but more sophisticated, as it reduces words to their dictionary form.
```python
from nltk.stem import WordNetLemmatizer
nltk.download('wordnet')
lemmatizer = WordNetLemmatizer()
word = "running"
print(lemmatizer.lemmatize(word, pos='v'))  # Output: run (verb)
```
#### 3.5 **POS Tagging (Part-of-Speech)**
POS tagging assigns parts of speech (e.g., noun, verb) to each word in a sentence.
```python
from nltk import pos_tag
from nltk.tokenize import word_tokenize
text = "NLTK is a great library."
tokens = word_tokenize(text)
tags = pos_tag(tokens)
print(tags)
```
Output: `[('NLTK', 'NNP'), ('is', 'VBZ'), ('a', 'DT'), ('great', 'JJ'), ('library', 'NN')]`
#### 3.6 **Named Entity Recognition (NER)**
NER identifies named entities like persons, organizations, and locations.
```python
from nltk import ne_chunk
from nltk.tokenize import word_tokenize
from nltk import pos_tag

sentence = "Barack Obama was born in Hawaii."
tokens = word_tokenize(sentence)
tags = pos_tag(tokens)
entities = ne_chunk(tags)
print(entities)
```
#### 3.7 **Frequency Distribution**
You can analyze the frequency of words in a text.
```python
from nltk import FreqDist
text = "this is a test. this is only a test."
tokens = word_tokenize(text)
fdist = FreqDist(tokens)
print(fdist)
```
Output: `FreqDist({'this': 2, 'is': 2, 'a': 2, 'test': 2, '.': 2, 'only': 1})`
# **Advanced NLP Tasks**
#### 4.1 **Text Classification**
NLTK provides tools to train classifiers. Here's a basic example of training a classifier with labeled text.
```python
from nltk.classify import NaiveBayesClassifier
from nltk.corpus import movie_reviews
import random

# Load the movie reviews dataset
documents = [(list(movie_reviews.words(fileid)), category)
             for category in movie_reviews.categories()
             for fileid in movie_reviews.fileids(category)]
random.shuffle(documents)

# Feature extraction function
def extract_features(words):
    return {word: True for word in words}

# Train a Naive Bayes classifier
train_set = [(extract_features(words), category) for (words, category) in documents[:1500]]
classifier = NaiveBayesClassifier.train(train_set)

# Test classifier
test_set = [(extract_features(words), category) for (words, category) in documents[1500:]]
print("Classifier accuracy:", nltk.classify.accuracy(classifier, test_set))
```
#### 4.2 **Parsing**
Parsing involves analyzing the syntactic structure of sentences. You can create a tree structure of sentences using grammars.
Example of a simple grammar and parsing a sentence:
```python
from nltk import CFG

# Define a grammar
grammar = CFG.fromstring("""
  S -> NP VP
  VP -> V NP
  NP -> Det N
  V -> "saw" | "ate"
  Det -> "a" | "the"
  N -> "man" | "dog"
""")

# Create a parser
from nltk.parse import ChartParser
parser = ChartParser(grammar)

# Parse a sentence
sentence = "the dog saw a man".split()
for tree in parser.parse(sentence):
    tree.pretty_print()
```
#### 4.3 **WordNet**
NLTK includes WordNet, a lexical database for the English language. You can use it for tasks like finding synonyms, antonyms, etc.
```python
from nltk.corpus import wordnet
nltk.download('wordnet')

synonyms = wordnet.synsets("good")
print(synonyms)
```
#### 4.4 **Collocations**
Collocations refer to the frequent co-occurrence of words that appear together more often than expected by chance. NLTK provides functions to find bigrams (pairs of words) or trigrams (triplets).
```python
from nltk.collocations import BigramCollocationFinder
from nltk.metrics import BigramAssocMeasures

# Sample text
text = "I love programming in Python. Python is awesome!"

# Tokenize and find bigrams
tokens = word_tokenize(text)
bigram_finder = BigramCollocationFinder.from_words(tokens)
bigrams = bigram_finder.nbest(BigramAssocMeasures.likelihood_ratio, 5)
print(bigrams)
```
# **Useful NLTK Corpora**
NLTK has several corpora that can be used for NLP tasks, including:
- **movie_reviews**: A dataset of movie reviews for sentiment analysis.
- **gutenberg**: A collection of classic literary works.
- **stopwords**: Commonly used stopwords in different languages.
- **wordnet**: Lexical database for the English language.
To access them:
```python
from nltk.corpus import movie_reviews
nltk.download('movie_reviews')
```
# **NLTK Utilities**
- **nltk.tokenize**: Tokenization of sentences and words.
- **nltk.stem**: Provides stemmers and lemmatizers.
- **nltk.corpus**: Contains various corpora and word lists.
- **nltk.probability**: Tools for statistical analysis.
- **nltk.classify**: Tools for building and training classifiers.
---