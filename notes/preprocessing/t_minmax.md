# MinMaxScaler
flytter datapunkter, eksempelvis en aldersfordeling, mellem 20 til 80 år, ned til en skala der går mellem 0 og 1.

```python
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
scaler.fit(df[['Age']])
df['normalized_age'] = scaler.transform(df[['Age']])

```
