# TfidfVectorizer
Tf-idf = Term frequency - inverse document frequency

```python
from sklearn.feature_extraction.text import TfidfVectorizer
tv = TfidfVectorizer(max_features=100,stop_words='english')

tv.fit(train_speech_df['text'])
train_tv_transformed = tv.transform(train_speech_df['text'])

train_tv_df = pd.DataFrame(train_tv_transformed.toarray(),columns=tv.get_feature_names()).add_prefix('TFIDF_')
train_speech_df = pd.concat([train_speech_df,train_tv_df], axis=1, sort=False)
```
Undersøg en rækker for at se om resultatet ser ordentligt ud:
```python
examine_row = train_tv_df.iloc[0]
print(examine_row.sort_values(ascending=False))
```

## Parametre
- `max_features` maximun antal kolonner som oprettes ved TF-IDF 
- `stop_words` liste af almindelige ord der skal undlades
- `ngram_range` angiver minimum og maksimen længde på ngrams der inkluderes
  - formatet er `tv = TfidfVectorizer(ngram_range=(2,2))` hvis man vil have min og max 2 ords kombinationer 