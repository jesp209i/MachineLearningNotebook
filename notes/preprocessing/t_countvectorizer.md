# CountVectorizer
Bruges til tekst features som indeholder blandet tekst - eksempelvis taler

```python
from sklearn.feature_extraction.text import CountVectorizer
cv = CountVectorizer(min_df=0.1, max_df=0.9)

cv.fit(df['text_clean'])
cv_transformed = cv.transform(df['text_clean'])
# eller
cv_transformed = cv.fit_transform(df['text_clean'])

# omdan cv_transformed til et array
cv_transformed.toarray()

# hent kolonne navnene
feature_names = cv.get_feature_names()

# lav en ny dataframe der indeholde pæne feature navne
cv_df = pd.DataFrame(cv_transformed.toarray(),columns=cv.get_feature_names()).add_prefix()'Counts_'

# kombined den oprindelige Dataframe med teksten, med de nye insights der er fundet. 
df = pd.concat([df, cv_df], axis=1, sort=False)


```

## Hyperparametre
- `min_df` minimun andel af dokumenter ordet skal indgå i
- `max_df` maximum andel af dokumenter ordet kan indgå i
- `token_pattern`
- `ngram_range`
