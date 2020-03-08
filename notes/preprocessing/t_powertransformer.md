# PowerTransformer
Logaritmisk transformering

 ```python
from sklearn.preprocessing import PowerTransformer
log = PowerTransformer()

log.fit(df[['ConvertedSalary']])

df['log_ConvertedSalary'] = log.transform(df[['ConvertedSalary']])
```