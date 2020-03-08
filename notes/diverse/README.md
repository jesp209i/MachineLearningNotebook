# diverse terminologi
## population
antallet af rækker i 
```python
print(len(basetable))
```

## basetable
historiske data der skal bruges til at skabe en model med

## candidate predictors
features som kan bruges til at predicte med.

## Kategoriske features
Kategoriske features kunne være en farve-egenskab eller fødeland.

Der findes to typer af encoding:
- One-hot encoding
  - `pd.get_dummies(df, columns=['Country], prefix='C)`
  - antal "n" kategorier omdannes til antal "n" features
  - giver features der er nemmere at forklare, da al data er repræsenteret
- Dummy encoding
  - `pd.get_dummies(df, columns=['Country], drop_first=True, prefix='C)`
  - antal "n" kategorier omdannes til antal "n-1" features
  - giver bedre data, da der ikke forekommer redundant data (den ene kategori er repræsenteret på baggrund af "nuller" ved de andre kategorier)

### Reducer kategorier
Kategorier som forekommer få gange kan slås sammen.

I eksemples er det valgt at kategorier med værdier som forekommer mindre end 5 gange, bliver erstattet med `'Other'` 

 ```python
# summer kategorierne
counts = df['Country'].value_counts()
# lav en maske
mask = df['Country'].isin(counts[counts < 5].index) 
df['Country'][mask] = 'Other'
```

# Data leakage
Hvis man bruger test-data til at fitte sin model bliver præcitionen ikke god. 
I virkeligheden har man ikke adgang til 'test-data'.