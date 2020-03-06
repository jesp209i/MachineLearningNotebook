# pyplot
- `import matplotlib.pyplot as plt`

## Labels til akserne
````python
plt.xlabel('tekst til x-akse')
plt.ylabel('tekst til y-akse')
plt.title('overskrift til diagram')
````



## Cumulative distribution function (CDF)
```python
df.plot(kind='hist', normed=True, cumulative=True, bins=25)
```
- `kind` type af diagram // her et histogram
- `normed` hvis True, bliver værdierne normaliseret 
- `culumative` hvis True, bliver værdierne hele tiden lagt til den forrige
- `bins` antallet af


# line og plot types
- `style` ændrer på linjens type/farve
  - style består af 3 tegn - se nogle betydninger i tabellen nedenfor.
    - Første tegn er for farve
    - Andet tegn angiver type af markør
    - tredje tegn angiver linje type
  - eksempel: `df.plot(style='k.-')`
  
| tegn / Farve | tegn / markør | tegn / linje |
|---|---|---|
| k : sort | . : prik | - : solid linje |
| b : blå | o : cirkel | : prikker (intet foran kolon) |
| g : grøn | * : stjerne | - : stribet |
| r : rød | s : kvadrat |  |
| c : cyan | + : plus |  |

typer af diagrammer:
 - `bar`
 - `box`
 - `area`
 - `hist`

Med parametren `kind` kan man angive typen af diagram man vil lave:
```python
df.plot(kind='hist')
```

# subplots
Producer flere diagrammer samtidig med `subplots`.

Dette kræver at den dataframe der arbejdes med indeholde 2 eller flere serier af data 
 
```python
df.plot(subplots=True)
```