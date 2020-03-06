# pyplot
- `import matplotlib.pyplot as plt`

## Labels til akserne
````python
plt.xlabel('tekst til x-akse')
plt.ylabel('tekst til y-akse')
plt.title('overskrift til diagram')
````

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

## hjælpelinjer
- Horizontal linje
  - `.axhline(y=0.85, linestyle='--'')`
- Vertikal linje 
  - `.axvline(x=2, linestyle='--'')`


## Cumulative distribution function (CDF)
```python
df.plot(kind='hist', normed=True, cumulative=True, bins=25)
```
- `kind` type af diagram // her et histogram
- `normed` hvis True, bliver værdierne normaliseret 
- `culumative` hvis True, bliver værdierne hele tiden lagt til den forrige
- `bins` antallet af

## Predictor insights graph
```python
import matplotlib.pyplot as plt
import numpy as np

# plot the graph
plt.ylabel("Size", rotation=0, rotation_mode="anchor", ha = "right")
pig_table["Incidence"].plot(secondary_y = True)
pig_table["Size"].plot(kind='bar', width =0.5, color= "lightgray", edgecolor= "none")

# show the group names
plt.xticks(np.arrange(len(pig_table)), pig_table["Income"])

# center the group names
plt.xlim([-0.5, len(pt)-0,5])
plt.ylabel("Incidence", rotation=0, rotation_mode="anchor", ha = "right")
plt.xlabel("Income")
plt.show()
```