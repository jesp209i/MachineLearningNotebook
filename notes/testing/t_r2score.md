# r2_score
R2 er bundet af værdier 1 i toppen, men kan blive uendelig lav i bunden. 

Jo lavere score des dårligere model.  

```python
from sklearn.metrics import r2_score
print(r2_score(y_test, y_predicted))
```