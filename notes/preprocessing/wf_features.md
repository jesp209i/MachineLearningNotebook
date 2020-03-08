# Udvælg relevante features

- brug almindelig sund fornuft til at indskrænke eller udvælge features
  - pas på med ikke at vælge for mange features, da det kan medvirke til overfitting eller uoptimerede modeller.

Indskrænk parametre
- brug "Adjusted R squared"
- brug AIC eller BIC

sklearn model_selection FTest og Chi squared

- SelectKBest
- Lasso
- Univariate Selection
- Feature Importance
- Correlation Matrix with Heatmap

# 12 teknikker
1. procent missing values
  - Drop variabler som har en høj procent af manglende værdier
    - # manglende værdier / # total 
2. Amount of variation
  - Hvis en feature har lav varians har den ikke indfyldelse på modellen 
3. pairwise correlation
  - Hvis to features har høj correlation til hinanden, kan man droppe den ene, uden at miste så meget information
4. multicolinearity
5. Principal Component Analysis (PCA)
6. Cluster analysis
7. Correlation with the target
  - hvis features kun har lav correlation med target, vil den være nyttig til at skabe modellen 
8. forward selection
9. backward elimination (RFE)
10. Stepwise selection
  - 
11. LASSO
12. Tree-based selection

# forbedr features
## gør værdier "binære"
laver to kategorier:
- restaurenter uden anmærkninger `df['Binary_Violation'] = 0`
- restaurenter med 1 eller flere anmærkninger `df['Binary_Violation'] = 1`

```python
df['Binary_Violation'] = 0
df.loc['Number_of_Violations'] > 0, 'Binary_Violation'] = 1
df['Binary_Violation'] = pd.cut(df['Number_of_violations'], bins=[-np.inf, 0,2,np.inf], labels=[1,2,3])
```

## "Bin" værdier 
kombiner værdier, så intevaller af værdier tilhører samme kategori
- 3 kategorier:
  - Nul anmærkninger : `df['Binned_Group'] = 1`
  - 1-2 anmærkninger : `df['Binned_Group'] = 2`
  - over 2 anmærkninger : `df['Binned_Group'] = 3`
```python
import numpy as np
df['Binned_Group'] = pd.cut(df['Number_of_violations'], bins=[-np.inf, 0,2,np.inf], labels=[1,2,3])
```

# manglende data i et datasæt
Få en grundlæggende ide om manglende data. Se om nogle af features er underbefolket
```python
df.info()
```

Vis alle felter der mangler værdier, de får værdier true: 
```python
print(df.isnull())
```
Tæl det omvendte ved at bruge:
```python
print(df.notnull())
```

Optæl manglende værdier i en kolonne:
```python
print(df['StackOverflowJobsRecommend'].isnull().sum())
```

## håndter manglende data
### Listwise deletion
Fjern rækker som mangler data i en eller flere af rækkens felter
```python
df.dropna(how='any')
```
Fjerner hele rækken, hvis kolonnen med `VersionControl` mangler værdi
```python
df.dropna(subset=['VersionControl'])
```

### Erstat manglende værdier med en streng
```python
df['VersionControl'].fillna(value='None Given', inplace=True)
```

### Registrer manglende data
Hvis de manglende data i en kolonne er vigtig i en eller anden forstand, kan dette konverteres til om feature værdien eksisterer eller ej, og selve featuren kan droppes.
```python
df['SalaryGiven'] = df['ConvertedSalary'].notnull()
df.drop(columns=['ConvertedSalary'])
```

### Erstat manglende værdier - strategier:
Ved kategoriske features kan man sætte den kategori der forekommer oftest, eller lave kategorien "None".

Ved nummeriske features skal man erstatte med en mere passende værdi:
  - `df['ConvertedSalary'] = df['ConvertedSalary'].fillna(df['ConvertedSalary'].mean())`
  - `df['ConvertedSalary'] = df['ConvertedSalary'].fillna(df['ConvertedSalary'].median())`
  - Fjern evt komma tal ved at ændre typen til int:
    - `df['ConvertedSalary'] = df['ConvertedSalary'].astype('int64')`
  - Eller afrund tallet ved hjælp af `round()`:
    - `df['ConvertedSalary'] = df['ConvertedSalary'].fillna(round(df['ConvertedSalary'].mean()))`

### Fjern forkerte tegn fra talværdier
Hvis en kolonne som burde være nummerisk, indeholde forkerte tegn (eksempelvis komma eller valuta symboler) skal disse fjernes så data kan bearbejdes.
- Kolonnen vil være af typen object, da den indeholder 'ikke-tal' værdier
```python
df['RawSalary'] = df['RawSalary'].str.replace(',', '')
df['RawSalary'] = df['RawSalary'].astype('float')  # konverter kolonne til komma-tal
```