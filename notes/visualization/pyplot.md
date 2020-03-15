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

## Plot en timeseries fra Pandas
```Python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(figsize=(12,6))
data.plot('date', 'close', ax=ax)
ax.set(title='AAPL daily closing price')
```

## Plot hver feature i et datasæt
Kræver muligvis at index i datasættet er en pandas timeseries
```python
fig, ax = plt.subplots()
for column in data:
    data[column].plot(ax=ax, label=column)
ax.legend()
plt.show()
```

## Visualiser relationer mellem timeseries
```python
fig, axs = plt.subplots(1,2)

# make a line plot for each timeseries
axs[0].plot(x , c='k', lw=3, alpha=.2)
axs[0].plot(y)
axs[0].set(xlabel='time', title='X values = time')

# encode time as color in a scatterplot
ax[1].scatter(x_long, y_long, c=np.arange(len(x_long)), cmap='viridis')
axs[1].set(xlabel='x', ylabel='y', title='Color = time')
```

## visualiser outliers
```python
fig, axs = plt.subplots(1,2, figsize=(10,5))
for data, ax in zip([prices, prices_perc_change], axs):
    # Calculate the mean / standard deviation for the data
    this_mean = data.mean()
    this_std = data.std()

    # plot the data, with a window that is 3 standard deviations around the mean
    data.plot(ax=ax)
    ax.axhline(this_mean + this_std * 3, ls='--', c='r')
    ax.axhline(this_mean - this_std * 3, ls='--', c='r')

```