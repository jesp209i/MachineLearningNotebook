# Udvælg relevante features

- brug almindelig sund fornuft til at indskrænke eller udvælge features
  - pas på med ikke at vælge for mange features, da det kan medvirke til overfitting eller uoptimerede modeller.

Indskrænk parametre
- brug "Adjusted R squared"
- brug AIC eller BIC

sklearn model_selection FTest og Chi squared

- SelectKBest
- Lasso
- Univariate Selection
- Feature Importance
- Correlation Matrix with Heatmap

# 12 teknikker
1. procent missing values
  - Drop variabler som har en høj procent af manglende værdier
    - # manglende værdier / # total 
2. Amount of variation
  - Hvis en feature har lav varians har den ikke indfyldelse på modellen 
3. pairwise correlation
  - Hvis to features har høj correlation til hinanden, kan man droppe den ene, uden at miste så meget information
4. multicolinearity
5. Principal Component Analysis (PCA)
6. Cluster analysis
7. Correlation with the target
  - hvis features kun har lav correlation med target, vil den være nyttig til at skabe modellen 
8. forward selection
9. backward elimination (RFE)
10. Stepwise selection
  - 
11. LASSO
12. Tree-based selection