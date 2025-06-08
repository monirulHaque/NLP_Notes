<!-- # Preprocessing
## Text
## Speech
# Libraries
- NLTK
- spaCy
- textBlob
- polyglot
- gensim -->

# Preprocessing

## Preprocessing Text

### Preprocessing using NLTK 

First, you'll need to install the Natural Language Toolkit (`nltk`) library and download its data packages.

```python
# Install the library (in your terminal/command prompt)
# pip install nltk

# Download the necessary data packages in Python
import nltk
nltk.download('punkt') # for tokenization
nltk.download('stopwords') # for stop words
nltk.download('wordnet') # for lemmatization
```


#### 1. Tokenization

Breaking down text into smaller pieces, or "tokens".

* **Word Tokenization:** Splits a sentence into words.
* **Sentence Tokenization:** Splits a paragraph into sentences.

```python
from nltk.tokenize import sent_tokenize, word_tokenize

text = "Hello there! NLP is fun. I am learning a lot."

# Sentence Tokenization
sentences = sent_tokenize(text)
print("Sentences:", sentences)
# Output: ['Hello there!', 'NLP is fun.', 'I am learning a lot.']

# Word Tokenization
words = word_tokenize(text)
print("Words:", words)
# Output: ['Hello', 'there', '!', 'NLP', 'is', 'fun', '.', 'I', 'am', 'learning', 'a', 'lot', '.']
```


#### 2. Lowercasing

Changing all text to be lowercase. This helps the computer treat "Hello" and "hello" as the same word.

```python
# Using the 'words' list from the previous step
words = ['Hello', 'there', '!', 'NLP', 'is', 'fun', '.']
lower_words = [word.lower() for word in words]
print(lower_words)
# Output: ['hello', 'there', '!', 'nlp', 'is', 'fun', '.']
```


#### 3. Stop Word Removal

Removing very common words that don't add much meaning (e.g., "a", "an", "the", "is", "in").

```python
from nltk.corpus import stopwords

# We'll work with clean, lowercase words without punctuation
words = ['nlp', 'is', 'fun', 'i', 'am', 'learning', 'a', 'lot']

stop_words = set(stopwords.words('english'))
filtered_words = [word for word in words if word not in stop_words]

print("Original words:", words)
print("Stop words removed:", filtered_words)
# Output: ['nlp', 'fun', 'learning', 'lot']
```


#### 4. Stemming

A quick way to cut words down to their root form by just chopping off the end. The result might not be a real word.

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()
words_to_stem = ["studies", "studying", "studied", "study"]
stemmed_words = [stemmer.stem(word) for word in words_to_stem]

print(stemmed_words)
# Output: ['studi', 'studi', 'studi', 'studi']
```


#### 5. Lemmatization

A smarter way to find the dictionary root of a word (the "lemma"). It is slower but more accurate than stemming.

```python
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()
words_to_lemmatize = ["studies", "studying", "studied", "study"]
lemmatized_words = [lemmatizer.lemmatize(word) for word in words_to_lemmatize]

print("Lemmatized words:", lemmatized_words)
# Output: ['study', 'studying', 'studied', 'study']
# Note: Lemmatization can be improved by providing the part of speech (e.g., verb, noun).

# A better example showing its power
print("Lemmatizing 'better':", lemmatizer.lemmatize("better", pos="a")) # 'a' means adjective
# Output: good
```


## Preprocessing Speech
To be added