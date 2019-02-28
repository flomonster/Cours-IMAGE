# Statistique et apprentissage en Python

![Présentation](https://upload.wikimedia.org/wikipedia/en/thumb/3/35/Muse_2nd_law.jpg/220px-Muse_2nd_law.jpg)


> $1$ [voxel](https://en.wikipedia.org/wiki/Voxel) mesure pour le moment $1mm.cm^{-3}$


> Dans python presque tout est bon.[name='Duchesnay Edouard']

## Univariate statistics


> **Définition :** Un **modèle mathématique** est une traduction d'une observation dans le but de lui appliquer les outils, les techniques et les théories mathématiques, puis généralement, en sens inverse, la traduction des résultats mathématiques obtenus en prédictions ou opérations dans le monde réel. [name=Wikipédia]

> **Définition :** Une **statistique** est, au premier abord, le résultat d'une suite d'opérations appliquées à un ensemble de nombres appelé échantillon. D'une façon générale, c'est le résultat de l'application d'une méthode statistique à un ensemble de données. Dans le calcul de la moyenne arithmétique, par exemple, l'algorithme consiste à calculer la somme de toutes les valeurs des données et à diviser par le nombre de données. La moyenne est ainsi une statistique. Pour être complet dans la description de l'utilisation d'une statistique, il faut décrire à la fois la procédure et l'ensemble de données. . [name=Wikipédia]

Le **machine learning** fait fondalement du multivarié.

**Univarié :**
> Première variable d'entrée, on l'associe à la sortie, => corrélation, on fait la même chose pour une deuxieme, une troisieme, etc...

L'idée est de pouvoir connaître si une variable est corrélé à une sortie.

:::info
**Variable quantitative :** (Ex: age) faire de la regression
**Variable qualitative :** (factor, avec des niveaux) (Ex: sexe, couleur de cheveux) 
:::


### Normal distribution

```python=
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
%matplotlib inline

mu = 0 # mean
variance = 2 # variance
sigma = np.sqrt(variance) # standard deviation
x = np.linspace(mu - 3 * variance, mu + 3 * variance, 100)
plt.plot(x, norm.pdf(x, mu, sigma))
```

PDans `scipy` il y a des stats de base. Pour des stats plus avancé on peut utiliser `statsmodels`.

### Distribution Chi square ($\chi^2$)

En **fonction d'erreur** on prend souvent la somme des carrés des erreurs. Cette fonction est bien car elle est différenciable (dérivable).

Il faut savoir que la distribution de cette fonction d'erreur suit une loi Chi^2.

Vous pouvez trouver des infos [ici](https://fr.wikipedia.org/wiki/Loi_du_%CF%87%C2%B2).

La densité de probabilité:

$$f_X(x;k)=\frac{1}{2\frac k2 \tau(\frac k2)}x^{\frac k2 - 1}e^{-\frac x2}$$

### Student's t-test

Pour plus d'info c'est [ici](https://en.wikipedia.org/wiki/Student%27s_t-test)

$$t=\frac{\bar x - \mu_0}{\sigma / \sqrt n}$$

**Exemple :**
```python=
import numpy as np

x = [1.83, 1.83, 1.73, 1.82, 1.83, 1.73, 1.99, 1.85, 1.68, 1.87]
xbar = np.mean(x) # Sample mean
mu0 = 1.75 # Hypothesized value
s = np.std(x, ddof=1) # Sample stadard deviation
n = len(x) # Sample size

tobs = (xbar - mu0) / (s / np.sqrt(n))
print(tobs)
```

### Test de corrélation de Pearson

$$r = \frac{Corrélation}{Variance} = \frac{\sum_{i=1}^n(x_i - \bar x)(y_i \bar y)}{\sqrt{\sum_{i=1}^n(x_i - \bar x)^2}\sqrt{\sum_{i=1}^n(y_i - \bar y)^2}}$$

### Générer des donées

```python=
import numpy as np
import scipy.stats as stats

n = 50
x = np.random.normal(size=n) # On peut prendre une autre loi (Ex: uniforme)
y = 2 * x + np.random.normal(size=n) # Ici le random permet de faire le bruit

cor, pval = stats.pearsonr(x,y)
```

### Étude des variables en fonction de leurs types

|                  | Quantitative |    Qualitative       |
| ---------------- | :----------: | :------------------: |
| **Quantitative** | Corrélation  | T Test               |
| **Qualitative**  | T Test       | Calcul de la moyenne |


### Corrélation Spearman

La **corrélation de Spearman** est une mesure de dépendance statistique non paramétrique entre deux variables. Dit autrement, c'est utilisé pour les tests statistiques de rang.

**Statistique paramétrique :** Statistique classique où les résidus suivent une loi normale.
**Statistique non paramétrique :** Statistique de rang. *Ex: Histogramme*
## Multivariate statistics

### Modéle linéaire

Avec $n$ données d'exemple $(y_i, x_i^1, \dots, x_i p), i=1,\dots,n$ le modéle de regression linéaire. La relation entre l'observation $y_i$ et la variable indépendante $x_i^p$ est formulé comme :
$$\underbrace{y_i}_{\text{target}} = \underbrace{\beta_0 + \beta_1 x_i^1 + \dots + \beta_p x_i^p + \epsilon_i}_{\text{variables}} \quad i=1,\dots,n$$


## Clustering statistics


> Ecart inter classe doit être grand

> Ecart intra classe doit être petit 
















