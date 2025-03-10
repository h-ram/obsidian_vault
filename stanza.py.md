Stanza is a Python library for natural language processing (NLP) developed by Stanford NLP Group. 
# **Installation**
```bash
pip install stanza
```
2. **Downloading a Language Model**
Stanza supports many languages, but you need to download a model for the language you want to process. 
```python
import stanza
# Download the English model (replace 'en' with another language code like 'es' for Spanish if needed)
stanza.download('en')
```
You only need to run this once. The model will be saved locally.
# **Usage**
#### **Initializing a Pipeline**
Stanza processes text through a "pipeline" that applies a series of NLP processors (e.g., tokenize, pos, lemma, depparse). You specify the language and the processors you want:
```python
# Initialize an English pipeline with default processors
nlp = stanza.Pipeline(lang='en', processors='tokenize,pos,lemma')
```
- `lang='en'`: Specifies English (use 'es' for Spanish, 'fr' for French, etc.).
- `processors='tokenize,pos,lemma'`: Specifies tokenization, part-of-speech tagging, and lemmatization. You can add more like `ner` (named entity recognition) or `depparse` (dependency parsing).
#### **Processing Text**
Once the pipeline is set up, you can process text. Here’s an example:
```python
# Input text
text = "The quick brown fox jumps over the lazy dog."

# Proocess the text
doc = nlp(text)

# Access the results
for sentence in doc.sentences:
    for word in sentence.words:
        print(f"Word: {word.text:<15} Lemma: {word.lemma:<15} POS: {word.pos}")
```

**Output:**
```
Word: The            Lemma: the            POS: DET
Word: quick         Lemma: quick         POS: ADJ
Word: brown         Lemma: brown         POS: ADJ
Word: fox           Lemma: fox           POS: NOUN
Word: jumps         Lemma: jump          POS: VERB
Word: over          Lemma: over          POS: ADP
Word: the           Lemma: the           POS: DET
Word: lazy          Lemma: lazy          POS: ADJ
Word: dog           Lemma: dog           POS: NOUN
Word: .             Lemma: .             POS: PUNCT
```

#### 5. **Customizing the Pipeline**
You can customize the pipeline by adding or removing processors. For example, to include named entity recognition (NER):

```python
nlp = stanza.Pipeline(lang='en', processors='tokenize,ner')

text = "Barack Obama was born in Hawaii."
doc = nlp(text)

# Print named entities
for ent in doc.ents:
    print(f"Entity: {ent.text:<15} Type: {ent.type}")
```

**Output:**
```
Entity: Barack Obama    Type: PERSON
Entity: Hawaii          Type: GPE
```

#### 6. **Supported Languages**
Stanza supports over 60 languages. To use a different language, download its model and specify the language code. For example, for Spanish:

```python
stanza.download('es')
nlp = stanza.Pipeline(lang='es', processors='tokenize,pos')
text = "El perro corre rápido."
doc = nlp(text)

for sentence in doc.sentences:
    for word in sentence.words:
        print(f"Word: {word.text:<15} POS: {word.pos}")
```

#### 7. **Common Processors**
Here are some common processors you can use:
- `tokenize`: Splits text into tokens/words.
- `pos`: Assigns part-of-speech tags (e.g., NOUN, VERB).
- `lemma`: Provides the base form of words.
- `depparse`: Performs dependency parsing.
- `ner`: Identifies named entities (e.g., people, places).
- `sentiment`: Performs sentiment analysis (English only).

#### 8. **Tips**
- **Memory Usage**: For large texts or multiple languages, ensure your system has enough memory, as models can be large.
- **GPU Support**: Stanza supports GPU acceleration if you have PyTorch installed with CUDA. Add `use_gpu=True` to the pipeline:
  ```python
  nlp = stanza.Pipeline('en', processors='tokenize,pos', use_gpu=True)
  ```
- **Documentation**: Check the official Stanza documentation (https://stanfordnlp.github.io/stanza/) for advanced features.

#### Example: Full Pipeline
Here’s a complete example with multiple processors:

```python
import stanza

# Download and initialize pipeline
stanza.download('en')
nlp = stanza.Pipeline('en', processors='tokenize,pos,lemma,ner')

# Process text
text = "Elon Musk founded xAI in 2023."
doc = nlp(text)

# Print tokens, POS, and lemma
print("Tokens, POS, and Lemmas:")
for sentence in doc.sentences:
    for word in sentence.words:
        print(f"Word: {word.text:<15} Lemma: {word.lemma:<15} POS: {word.pos}")

# Print named entities
print("\nNamed Entities:")
for ent in doc.ents:
    print(f"Entity: {ent.text:<15} Type: {ent.type}")
```

**Output:**
```
Tokens, POS, and Lemmas:
Word: Elon           Lemma: Elon           POS: PROPN
Word: Musk          Lemma: Musk          POS: PROPN
Word: founded       Lemma: found         POS: VERB
Word: xAI           Lemma: xAI           POS: PROPN
Word: in            Lemma: in            POS: ADP
Word: 2023          Lemma: 2023          POS: NUM
Word: .             Lemma: .             POS: PUNCT

Named Entities:
Entity: Elon Musk      Type: PERSON
Entity: xAI            Type: ORG
Entity: 2023           Type: DATE
```

### Questions?
Let me know if you need help with a specific task, troubleshooting, or more examples!
---
# Resrouces
- [Online Documentation](https://stanfordnlp.github.io/stanza/)