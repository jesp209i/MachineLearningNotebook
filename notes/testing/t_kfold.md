# KFold
```python
from sklearn.model_selection import KFold
cv = KFold(n_splits=5)
for tr, tt in cv.split(X.y):
    fig, axs = plt.subplots(2,1)
    
    # Plot the indices chosen for validation on each loop 
    axs[0].scatter(tt, [0] * len(tt), marker='_', s=2, lw=40)
    axs[0].set(ylim=[-.1,.1], title='Test set indices (color=CV loop)', xlabel='Index of raw data')

    # Plot the model predictions on each iteration
    axs[1].plot(model.predict(X[tt]))
    axs[1].set(title='Test set predictions on each CV loop', xlabel='Predictions index')
```


# Se også:
- [ShuffleSplit](./t_shufflesplit.md)