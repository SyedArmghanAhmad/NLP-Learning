
# NLP Learning Repository

This repository contains Python scripts, experiments, and exercises related to Natural Language Processing (NLP) techniques that I have learned and practiced. It includes code snippets demonstrating various NLP techniques, from tokenization to Named Entity Recognition (NER), stemming, lemmatization, and part-of-speech tagging. The primary goal is to showcase how different NLP tasks are performed using libraries like **NLTK** and **svgling**.

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Techniques Covered](#techniques-covered)
    - [Tokenization](#tokenization)
    - [Stemming](#stemming)
    - [Lemmatization](#lemmatization)
    - [POS Tagging](#pos-tagging)
    - [Named Entity Recognition](#named-entity-recognition)
4. [Code Examples](#code-examples)
5. [Visualizations](#visualizations)
6. [Contributing](#contributing)
7. [License](#license)

---

## Introduction

This repository focuses on several fundamental NLP tasks:

- **Tokenization**: Breaking a sentence or paragraph into smaller units (words, sentences, etc.).
- **Stemming**: Reducing words to their base or root form.
- **Lemmatization**: Normalizing words to their lemma based on context.
- **Part-of-Speech (POS) Tagging**: Identifying the grammatical category of each word.
- **Named Entity Recognition (NER)**: Recognizing entities such as names, organizations, locations, dates, etc.
- **Tree Visualization**: Visualizing parsed trees and syntactic structures.

---

## Installation

To run the scripts in this repository, you'll need the following Python packages installed:

```bash
pip install nltk svgling
```

You'll also need to download specific NLTK data files in your Python script. This is done using:

```python
import nltk
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('maxent_ne_chunker')
nltk.download('words')
nltk.download('stopwords')
```

---

## Techniques Covered

### Tokenization

Tokenization is the process of splitting text into smaller components, such as words or sentences. In this repository, we have implemented both word and sentence tokenization using NLTK.

- **Example**: Sentence → Words

  ```python
  nltk.word_tokenize("Elon Musk announced that Tesla will build a new Gigafactory in Berlin by the end of 2025.")
  ```

### Stemming

Stemming is the process of reducing words to their root form. We explored the **Porter Stemmer**, **Regexp Stemmer**, and **Snowball Stemmer** for stemming words.

- **Example**: "Running" → "run"

  ```python
  from nltk.stem import PorterStemmer
  ps = PorterStemmer()
  ps.stem("running")  # Output: "run"
  ```

### Lemmatization

Lemmatization is similar to stemming but more context-sensitive. Using NLTK's **WordNetLemmatizer**, we can reduce words to their base form based on their part-of-speech (POS).

- **Example**: "Better" → "Good"

  ```python
  from nltk.stem import WordNetLemmatizer
  lemmatizer = WordNetLemmatizer()
  lemmatizer.lemmatize("better", pos='a')  # Output: "good"
  ```

### Part-of-Speech (POS) Tagging

POS tagging is used to assign a grammatical category to each word (e.g., noun, verb, adjective). We used NLTK’s **POS Tagger** for this purpose.

- **Example**: "Elon" → Proper Noun (NNP)

  ```python
  nltk.pos_tag(["Elon", "Musk"])  # Output: [('Elon', 'NNP'), ('Musk', 'NNP')]
  ```

### Named Entity Recognition (NER)

NER identifies entities like names, organizations, and locations. Using NLTK’s **NE Chunker**, we extracted named entities from sentences.

- **Example**: "Elon Musk" → Person

  ```python
  nltk.ne_chunk(nltk.pos_tag(["Elon", "Musk"]))  # Output: (S (GPE Elon/NNP Musk/NNP))
  ```

---

## Code Examples

### Example 1: Tokenization, Stemming, and Lemmatization

```python
import nltk
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer, WordNetLemmatizer
from nltk.corpus import stopwords

nltk.download('punkt')
nltk.download('stopwords')

sentence = "Elon Musk announced that Tesla will build a new Gigafactory in Berlin by the end of 2025."
words = word_tokenize(sentence)

# Stemming
ps = PorterStemmer()
stemmed_words = [ps.stem(word) for word in words if word not in stopwords.words('english')]
print("Stemmed words:", stemmed_words)

# Lemmatization
lemmatizer = WordNetLemmatizer()
lemmatized_words = [lemmatizer.lemmatize(word, pos='v') for word in words if word not in stopwords.words('english')]
print("Lemmatized words:", lemmatized_words)
```

### Example 2: POS Tagging and NER

```python
nltk.download('averaged_perceptron_tagger')
nltk.download('maxent_ne_chunker')
nltk.download('words')

sentence = "Elon Musk announced that Tesla will build a new Gigafactory in Berlin by the end of 2025."
words = nltk.word_tokenize(sentence)
tagged_words = nltk.pos_tag(words)
ner_tree = nltk.ne_chunk(tagged_words)

print("POS Tagging:", tagged_words)
print("Named Entities:", ner_tree)
```

---

## Visualizations

For Named Entity Recognition (NER), we used the **svgling** library to visualize the syntactic tree of sentences.

- **Example**:

  ```python
  import svgling
  tree = nltk.ne_chunk(nltk.pos_tag(nltk.word_tokenize(sentence)))
  svgling.draw_tree(tree)
  ```

This produces a tree-like structure where named entities are highlighted and visualized, allowing a clearer understanding of their grammatical relationships.

---

## Contributing

Feel free to fork this repository, create branches, and submit pull requests. Contributions are welcome for enhancing the NLP techniques or adding additional functionalities.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
