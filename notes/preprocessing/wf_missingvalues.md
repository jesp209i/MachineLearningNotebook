# Når datasættet mangler værdier

- `from sklearn.impute import SimpleImputer`



## Interpolate i Pandas
```python
# Return a boolean that notes where missing values are
missing = prices.isna()

# Interpolate linearly within missing windows
prices_interp = prices.interpolate('linear')

# plot the interpolated data in red and the data w/ missing values in black
ax = prices_interp.plot(c='r')
prices_interp.plot(c='k', ax=ax, lw=2)
```

### Transformer til procentvis ændring med Pandas
```python
def percent_change(values):
    """Calculates the % change between the last value and the mean of previous values"""
    # Separate the last value and all previous values into variables
    previous_values = values[:-1]
    last_value = values[-1]

    # Calculate the % difference between the last value and the mean of earlier values
    percent_change = (last_value - np.mean(previous_values)) / np.mean(previous_values)
    return percent_change
```