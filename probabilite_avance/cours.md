# Probabilités et statistiques (niveau avancé)

:::success
On a le droit à un support pour le partiel !!! :+1:
:::

:::warning
Ne pas oublier le SAV **Tochon**
![](https://i.ytimg.com/vi/RejSOsIq8iE/hqdefault.jpg)
:::

## Rappels

* $\Omega$ : L'ensemble des expériences que l'on peut faire
* $\omega \in \Omega$ : Une expérience
* $\omega \longrightarrow (X(\omega), Y(\omega))$ : C'est le fait de réaliser  l'expérience (et d'obtenir un résultat, ici une position $x$ et $y$)

---

Formellement :

* $\Omega$ : L'ensemble des événements élémentaires
* $\omega \in \Omega$ : Un événement élémentaire
* $A \subset \Omega$ : Un événement, $A \in \mathcal{P}(\Omega)$ : *"A parti de Omega"*
* Quand $A$ se produit, on dira *"A est vrai"*.
* Quand $A^c$ ou $\bar{A}$ se produit, on dira *"A est faux"*.
* Quand $A \cap B$ se produit, on dira *"A et B"*.
* Quand $A \cup B$ se produit, on dira *"A ou B"*.
* $A \subseteq B$ se dira *"Si A alors B"*.
* $\emptyset$ est *impossible*.
* $\Omega$ est *certain*.

Une tribu $\mathcal{F}$

* $\emptyset \in \mathcal{F}$
* $A_1,\dots,A_n \in \mathcal{F} \Longleftrightarrow \displaystyle \bigcup_{i=1}^\infty \{A_i\}\subseteq \mathcal{F}$
* $A\in \mathcal{F}$ et $A^c \in \mathcal{F}$

$$
A \rightarrow \mathbb{P}(A) \in[0,1]\\
\mathbb{P}(\emptyset) = 0\\
\mathbb{P}(\Omega) = 1\\
A_1 \dots A_n \forall i,j \: i \ne j)\\
A_i \cap A_j = \emptyset\\
P(\bigcup_{i=1}^\infty A_i )= \sum_{i=1}^\infty P(A_i)
$$
$(\Omega, \mathcal{F}, P)$: Espace probabilisé

Une experience:
\begin{matrix}
             &                  & oui& non  \\
    \omega_1 & ? ~ \omega_1 \in A & 1 & 0.R_1 \\
    \omega_2 & ? ~ \omega_2 \in A & 1 & 0.R_2 \\
             & \vdots           &   &       \\
    \omega_n & ? ~ \omega_n \in A & R_n = 1 & R_n = 0 \\
             & \vdots           &   &
\end{matrix}


$(R_1, ..., R_{50 000 000})$

$\bar{a}n$ je connais $R_{1} \dots R_{n}$
frequence $f_n = \frac{R_1 + \dots + R_n}{n}$

**Propriétés :**
* $\mathcal{P}(A^c)=1-\mathcal{P}(A)$
* $\mathcal{P}(A \cup B)=\mathcal{P}(A) + \mathcal{P}(B) - \mathcal{P}(A \cap B)$

#### Probabilité conditionnelles

* $\mathcal{P}(A | B) = \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}$
* $\mathcal{P}(A) = \mathcal{P}(A | B)\mathcal{P}(B) +\mathcal{P}(A | B^c)\mathcal{P}(B^c)$
* $\mathcal{P}(A \cap B) = \mathcal{P}(A|B)\mathcal{P}(B) = \mathcal{P}(B|A)\mathcal{P}(A)$
    :::success
    **Théorème de Bayes**
    $$\mathcal{P}(A | B) = \frac{\mathcal{P}(B|A)\mathcal{P}(A)}{\mathcal{P}(B)}$$
    :::

### Variable aléatoire

\begin{align}
X: \Omega &\to \mathbb{R}\\
   \omega &\mapsto X(\omega)
\end{align}

---

**Fonction de répartition :**

\begin{align}
F_X: \mathbb{R} &\to [0;1] \\
            x   &\mapsto \mathcal{P}(X \leq x)
\end{align}

$\mathcal{P}(X \in ]a,b]) = F(b) - F(a)$

Si $X$ continu:
* $\mathcal{P}({a})=0$
* $\mathcal{P}(a < X \leq b) = F(b) - F(a)$
* $\mathcal{P}(a < X) = 1 - F(a)$


$A_1 \dots A_n$ événements indépendants de même probabilité $p$

* $\mathbb{I}(A)$: La fonction caractéristique de A
* $\mathbb{I}(A_n)$

$$S_n=\sum_{k=1}^n \mathbb{I}(A_k) ~~~~ f_n=\frac{1}{n}S_n$$

$\forall \epsilon > 0\\
\displaystyle\lim_{n\rightarrow \infty}\mathcal{P}(p-\epsilon \leq f_n \leq p + \epsilon) = 1$
