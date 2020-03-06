# skplt
```python
import scikitplot as skplt
import matplotlib.pyplot as plt 
```

## cumulative gains curve
jo tættere linjen er på øveste venstre hjørne des bedre model

`skplt.metrics.plot_cumulative_gain(true_values, predictions)`


## lift curve
jo højere lift på kurven des bedre model

`skplt.metrics.plot_lift_curve(true_values, predictions)`