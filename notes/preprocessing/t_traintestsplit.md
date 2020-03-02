# train_test_split
Det kan være nødvendigt at opdele datasættene for at kunne teste hvor godt de preformer.

- Data skal være klargjort inden man kører `train_test_split` 
- Se noter om [pandas](t_pandas.md) angående klargøring af data. 

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X,y,test_size=0.2,random_state=42)
```




## Anden mulig splitter
- `StratifiedShuffleSplit`
  - virker kun med en target variable
