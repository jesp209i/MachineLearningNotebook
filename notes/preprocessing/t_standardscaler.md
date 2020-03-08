# StandardScaler
- `from sklearn.preprocessing import StandardScaler`

  _"Standardizes features by removing the mean and scaling to unit variance"_
 ```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()

scaler.fit(df[['Age']])

df['standardized_col'] = scaler.transform(df[['Age']])
```