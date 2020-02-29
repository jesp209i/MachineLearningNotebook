# Indlæs data
Typisk bruges her `pandas` og data indlæses til en pandas DataFrame.

```python
import pandas as pd

sample_df = pd.read_csv('sample_data.csv')
```
pd.read_csv() indlæser data fra en csv-fil.

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
