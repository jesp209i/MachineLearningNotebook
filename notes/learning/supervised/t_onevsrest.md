# OneVsRestClassifier
- `from sklearn.multiclass import OneVsRestClassifier`

```python
from sklearn.multiclass import OneVsRestClassifier
from sklearn.linear_model import LogisticRegression
clf = OneVsRestClassifier(LogisticRegression())
clf.fit(X_train, y_train)
```
- `X_train` indeholder features
- `y_train` indeholder labels som passer til features
