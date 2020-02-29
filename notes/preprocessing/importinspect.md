# Indlæs data
Typisk bruges her `pandas` og data indlæses til en pandas DataFrame.

```python
import pandas as pd

sample_df = pd.read_csv('sample_data.csv')
```

## undersøg data
- `sample_df.head()` eller  `sample_df.tail()`
  - Viser de første/sidste 5 rækker i sample_df. Hvis man sætter et heltal ind som parameter, vises det antal rækker.
- `sample_df.describe()`
  - 
