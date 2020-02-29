# Preprocessing
pandas og numpy er bruges ofte i forbindelse med ML. Det er værktøjer til import og manipulation af data.

```python 
import pandas as pd
import numpy as pd
```

## Workflows
- [Manglende værdier](missingvalues.md)

## Værktøjer
- [Pipeline](pipeline.mp)
- [StandardScaler](standardscaler.md)
- [Normalizer](normalizer.md)

# gamle noter//Preprocessing data
 Scikit-learn understøtter ikke kategori features per default
 - Category features skal encodes til tal
 - converter til 'dummy variables'
   - 0: observationer var ikke den kategori
   - 1: observationer var den kategori

## Dummy variabler

| Origin |
|---|
| US |
| Europe |
| Asia |

ovenstående muteres til følgende:

| Origin_Asia | Origin_US | Origin_Europe |
|---|---|---|
| 0 | 1 | 0 |
| 0 | 0 | 1 |
| 1 | 0 | 0 |

nogle modeller kræver at redundans fjernes - her er Europa den midterste (da den ikke er nogen af de andre)

| Origin_Asia | Origin_US |
|---|---|
| 0 | 1 |
| 0 | 0 |
| 1 | 0 |

## Encode dummy variabler
- scikit-learn: OneHotEncodes()
- pandas: get_dummies()

```python
import pandas as pd

df = pd.read_csv('auto.csv')

df_origin = pd.get_dummies(df)
print(df_origin.head())

df_origin = df_origin.drop('origin_Asia', axis=1)
print(df_origin.head())

```

## håndter manglende data
Impute - udregn noget data til de manglende

```python
from sklearn.preprocessing import Imputer

imp = Imputer(missing_values='NaN', strategy='mean', axis=0)
imp.fit(X)
X = imp.transform(X)
```


## Pipeline object
Alle steps i en pipeline skal være en transformers, minus sidste sted, som skal være en estimator (classifier eller regressor)

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import Imputer

imp = Imputer(missing_values='NaN', strategy='mean', axis=0)
logreg = LogisticRegression()
steps = [('imputation', imp), ('logistic_regression', logreg)]
pipeline = Pipeline(steps)

X_train, X_test, y_train, y_test = train_test_split(X,y,test_size=0.3, random_state=42)
pipeline.fit(X_train, y_train)
y_pred = pipeline.predict(X_test)
pipeline.score(X_test, y_test)
```

## Centering and scaling
Normalisering af data

- Standardization: træk gennemsnittet fra pg divider med variansen
  - Alle features bliver centraliseret og har varians en
- træk minimum fra og divider med datas range
  - minimum nul og maximum 1
- Ranger data fra -1 til +1

```python
from sklearn.preprocessing import scale
X_scaled = scale(X)
np.mean(X), np.std(X)
np.mean(X_scaled), np.std(X_scaled)
```

## CV og scaling in a pipeline
```python
steps = [('scaler', StandardScaler()), ('knn', KNeighborsClassifier())]
pipeline = Pipeline(steps)
parameters = {knn__n_neighbors : np.arrange(1,50)}
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=21)
cv = GridSearchCV(pipeline, param_grid=parameters)
cv.fit(X_train, y_train)

y_pred = cv.predict(X_test)
print(cv.best_params_)
print(cv.score(X_test, y_test))
print(classification_report(y_test, y_pred))
```
