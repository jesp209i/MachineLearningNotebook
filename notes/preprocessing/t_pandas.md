# Indlæs data
Typisk bruges her `pandas` og data indlæses til en pandas DataFrame.

```python
import pandas as pd

sample_df = pd.read_csv('sample_data.csv')
```
pd.read_csv() indlæser data fra en csv-fil.
- `nrows` giver mulighed for at angive for mange rækker man vil indlæse:
- `header` angiver hvilken rækker der svarer til overskrifterne til kolonnerne (`header=None` svarer til at der ikke er nogen headers med) 
- `names` skal bruge en liste af overskrifter som skal bruges til kolonnerne
````python
sample_df = pd.read_csv('sample_data.csv', nrows=2000) # importerer de første 2000 rows
````

Pandas indholder selvfølgelig flere muligheder for at importere (og eksportere) data:
- [Pandas IO docs](https://pandas.pydata.org/docs/user_guide/io.html)

# undersøg data
`sample_df` er vores variabal som indeholder en DataFrame.

- `sample_df.info()`
  - Giver et overblik over hvilken type data hver række indeholder, samt hvor mange værdier der er i hver række
- `sample_df.head()` eller  `sample_df.tail()`
  - Viser de første/sidste 5 rækker i sample_df. Hvis man sætter et heltal ind som parameter, vises det antal rækker.
- `sample_df.describe()`
  - viser et overblik over statestikker for de nummeriske kolonner i sample_df
    - Antal af værdier i kolonnen
    - Kolonnens gennemsnitsværdi
    - Kolonnens standard afvigelse
    - kolonnens max og min værdi
- `sample_df.dtypes.value_counts()`
  - tæller antallet af kolonner og summerer på type
- `sample_df.groupby(['column']).mean()`
  - viser grupperede resultater, kolonnen `column` bruges til at gruppere på, og `.mean()` udfører gennemsnitsberegning på de resterende features.
---
For alle statestikfunktioner gælder det at 'null'-værdier ignoreres.
- `sample_df.mean()`
  - viser gennemsnitsværdi for alle tal kolonner 
- `sample_df.std()`
  - viser standarafvigelsen for alle tal kolonner
- `sample_df.median()`
  - viser den midterste værdi for alle tal kolonner
- `sample_df.quantile(0.5)`
  - (0.5) svarer til `.median()`
  - (0.25) ville svare til tallet det ligger på 25% inde i datasættet
- `sample_df.min()` eller `sample_df.max()`  
  - viser den laveste eller højeste værdi for alle tal kolonner

# type af data i en dataframe
- `sample_df.dtypes`
  - giver adgang til kolonne-navne og viser typen for hver.
- `nummeric = sample_df.select_dtypes(include=['int','float'])`
  - vælger alle kolonnerne af typerne `int` og `float` og placerer dem i variable `nummeric`

# tæl værdier i en kolonne
- `counts = sample_df['Country'].value_counts()`
  - tæller hvor mange gange nogle de forskellige værdier optræder i kolonnen, og placerer informationen i variablen `counts`
 
# Find data i Dataframe
- `sample_df.loc['data']`
  - 'data' kan være mange ting - eksempelvis datoer.

# flet to dataframes sammen
- `pd.merge()`  
 
# Broadcasting
Skab en ny kolonne i den dataframe der arbejdes i, og placer en værdi i alle felterne

```python
sample_df['new_column'] = 0
```

# Ændre på index og kolonner
Giv din dataframes kolonner nye overskrifter:
```python
sample_df.columns = ['headline1', 'headline2', 'new headline']
``` 

Du kan også give dataframen nye indexer:
```python
sample_df.index = ['A','B','C','D','E','F','G','H','I','J','K']
```

# Plotting med pandas 
Husk at importere [`matplotlib.pyplot`](../visualization/pyplot.md).  
Man kan typisk tage fat i en dataframe direkte med `.plot()`.
```python
sample_df.plot()
plt.show() # pyplot
```

## Plot flere kolonner i forskellige diagrammer
- `.plot(subplots=True)` giver mulighed for at plotte flere kolonner i forskellige diagramme på samme tid. 
```python
cols = ['headline1', 'new headline']
sample_df[cols].plot(subplots=True)
plt.show()
```

## Forskellig syntaks til næsten samme resultat
Bemærk at man kan opnå næsten det samme med følgenede 3 forskellige typer syntaks.
- Vær opmærksom på at de ikke er 100% ens - se mere i doumentationen.
```python
sample_df.plot(kind='hist')
sample_df.plt.hist()
sample_df.hist()
```

## Datetime
importer filer der indeholder dato/tid på følgende måde:
```python
pd.read_csv('sample_data.csv', parse_dates=True, index_col='dato kolonne')
```
- `index_col` 
  - skal ikke nødvendigvis angives, men på den måde kan man bruge tiddato formatet som index på tabellen.

- `daily_mean = sample_df.resample('D').mean()`
  - skaber en ny variable som tar gennemsnittet per dag (D = daily)
  - resample bruges altid sammen med en statistisk funktion

| Input til resample() | beskrivelse |
|---|---|
| 'min', 'T' | minute |
| 'H' | time |
| 'D' | dag |
| 'B' | hverdag |
| 'W' | uge |
| 'M' | måned |
| 'Q' | kvartal |
| 'A' | år |

# links
- [Data manipulation for ML with pandas](https://towardsdatascience.com/data-manipulation-for-machine-learning-with-pandas-ab23e79ba5de)