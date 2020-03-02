# Machine Learning noter
Dette er et forsøg på at strømline machine learning noter.

Macine learning kan deles op i to overordnede faser:
- Fase 1: Learning
- Fase 2. Prediction

Derudover kan der være behov for visualisering af data, enten undervejs eller til slut:
- [Visualisering](./visualization/README.md)

## Fase 1: Learning
Denne fase består groft sagt af 3 steps:
- [Preprocessing](./preprocessing/README.md)
  - import af data
  - cleaning af data
  - formater data
- [Learning](./learning/README.md) - du træner modellerne indenfor:
  - [Supervised learning](./learning/supervised.md)
  - [Unsupervised learning](./learning/unsupervised.md)
  - Reinforcement learning
- [Testing](./testing/README.md) - du tester hvor fornuftige dine modeller bearbejder data
  - mål om modellen er performant
  - test om den valgte algoritme er god

## Fase 2: Prediction
I denne fase bruger du den trænede model fra fase 1 til at udføre predictions på ny ukendt data og skaber derved "Predicted data"
