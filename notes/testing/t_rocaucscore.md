# roc_auc_score
Evaluer om din model er god.

```python
from sklearn.metrics import roc_auc_score

# ... udfør fitting
# logreg.fit(X_train,y_train)

#  ... og predict på X_train, y_train
# prob_target = logreg.predict_proba(X_test)



roc_auc_score(true_target, prob_target)


```