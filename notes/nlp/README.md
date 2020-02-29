# Natural Language Processing / NLP
Data der kan bruges til NLP:
- Text, dokumenter, taler...


Tokenization
- Opdel en lang streng til mindre segmenter
- gem liste af segmenter
- hvert segment kunne være et ord
Tokenize på whitespace:
 - opdeler teksten baseret på dens mellemrum
Tokenize på whitespace og tegnsætning

# "Bag of words"
- tæller hver gang et ord forekommer
- er ligeglad med ordenes rækkefølge

# "n-gram"
laver en token af "n" ord ved siden af hinanden
- tæller hver gang en kombination af n-ord forekommer
- tager højde for ordenes rækkerfølge

# Repræsenter tekst som tal
Preprocessor: CountVectorizer
- fit
- transform

```python
from sklearn.feature_extraction.text import CountVectorizer
TOKENS_BASIC = '\\\\S+(?=\\\\s+)' # regular expression whitespace
df.Program_Description.fillna('', inplace=True)
vec_basic = CountVectorizer(token_pattern=TOKENS_BASIC)
```
- Tokenizes alle strenge
- Bygger et vokabular
- tæller antallet af forekomster af hver token i vokabularet for hver streng
