# Introduction au traitement du signal

Retour sur le cours de math du signal de l'année d'ing1. (RIP: Siarry)
Comme vous allez voir, il y a deux facettes à ce cours. il y a un volet assez thérorique, scolaire (on va essayer de démystifier la transformée de fourrier), ainsi qu'une séries d'exemples un peu simplistes, concrets, avec lesquels on va jouer.

**[Support de cours](http://www.lrde.epita.fr/~gtochon/MASI/)**

## Introduciton 

### Qu'est ce qu'un signal ?


> Ce sont des **phénoménes physiques** mesurable par un capteur, transportant de l'information dans l'*espace* et le *temps*.

Exemple :
* C'est une fonction
* Une onde (électromagnétique / lumière)
* Courant / tension
* Pression / température


:::info
Nous faisons la distinction entre continu et discret.
:::

**Signal analogique** :
> Dépend continuellement de ses variables.

**Signal numérique** :
> Un signal discret est capturé par un capteur, il devient numérique.

Le traitement du signal est né durant la seconde guerre mondiale. Un de ses pères fondateur est Claude Shannon. Il a fondé d'un point de vue mathematique la theorie du signal.
ex: un téléphone utilise continuellement des algo de traitement de signal.

:::info
Si l'on s'arrête aux images, (classe restreinte) on peut voir des application medicales, militaires, etc...
:::

**Question :** Pourquoi le son est échantilloné 44.1kHz ?

> Theoreme de shannon: il faut que le signal soit echantillonné à une fréquence deux fois plus importante que la fréquence maximale cible (l'oreille humaine entend jusqu'a 20kHz, donc on échantillonne le son à 44kHz).

### Comment fonctionne une oreille ?

**[Explication ouïe e-penser <3](https://www.youtube.com/watch?v=i2bKuw011nk)**

![Schéma Oreille](https://img-3.journaldesfemmes.fr/ecwoCOyevynOUsgpS0zIox4TF5Q=/427x/smart/1f2336d93ec144d8b53c976108f57ea8/ccmcms-jdf/1155604.jpg)


Les vibration mécanique du son sont transformer en impulsion electrique par la cochlée. En fonction de la fréquence de l'onde des cellules cillié différentes vont être activé.

:::success
Donc l'oreille fait une transformée de fourier...
:::



## Signal

La manière génerale de définir un signal, c'est 3 variables de position et 1 variable de temps, mais pour les besoins de ce cours, on ne travaillera qu'avec 1 seule dimension spaciale.

**Signal :**
> Fonction dépendant d'une seule variable de temps $t$ (avec $t \in \mathbb{R}$)

On mesure une certaine quantite unidimensionnelle a valeur dans $\mathbb{R}$ ou $\mathbb{C}$

:::info
Rappel sur les complexes:
$|z|^2 = z * \bar{z}$
:::


Le signal est un module borné. 
:::info
$\bar{\mathbb{R}} = \mathbb{R} \cup \{+\infty; -\infty\}$
:::


On va autoriser potentiellement des discontinuites.
x est continu ou possède un nombre fini / indénombrable de discontinuités.

Si $x_1$ signal et $x_2$ signal et $\lambda \in \mathbb{R}/\mathbb{C}$ alors $x_1 + x_2$ est un signal.

C'est un espace vectoriel.

En pratique dans cet espace vectoriel on va pouvoir definir:
* une base
* un produit scalaire
* une norme 

### Fonctionnement du radar

> Une onde se propage puis va buter contre un obstacle et refléchi un signal vers l'émeteur.

L'operation qui mesure la ressemblance entre 2 element est le produit scalaire. 

## Produit scalaire

$$
    x = \begin{pmatrix}x_1\\x_2\end{pmatrix}\\
    y = \begin{pmatrix}y_1\\y_2\end{pmatrix} \\
    <x,y> = x_1 \times y_1 + x_2 \times y_2 = ||x|| . ||y||.cos(\theta) = \sqrt{x_1^2 + x_2^2}
$$

Si $x,y \in\mathbb{R}^n$ c'est pareil.

$$
    x = \begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix}\\
    y = \begin{pmatrix}y_1\\\vdots\\y_n\end{pmatrix} \\
    <x,y> = x_1 \times y_1 + ... + x_n \times y_n = \sum_{i=1}^nx_i y_i = x^Ty=(x-x_n)\begin{pmatrix}y_1\\\vdots\\y_n\end{pmatrix}
$$

Si $x,y \in\mathbb{C}^n$.

Produit hermitien (équivalent complexe du produit scalaire):
:::info
$<x, y>$ = $\sum_{i=1}^nx_i \bar{y_i} = x^T\bar{y}$ 
:::


**Définition:** Soit $E$ un espace vectoriel sur $\mathbb{R}$

> $$
\begin{align}
    <:> : &  E \times E \rightarrow \mathbb{R} \\
          & (x, y) \rightarrow <x,y>
\end{align}
$$


1) Symetrie $\forall x,y \in E : <x,y> = <y,x>$
2) Bilinearite $\forall x,x_2, y \in \mathbb{E} <x,y> = <y,x> + \lambda <x_2,y>$
3) Positivité: $\forall x \in E, <x,x> \geq 0$
4) Définition: $<x,x>=0 \Longleftrightarrow x=0_E$

Si produit hermitien

* Symétrie hermitienne: $<x,y> = \bar{<y,x>}$
* Semilinéarité: $$<x_1+\lambda x_2,y>=<x_1,y> + \lambda <x_2, y>\\
                   <x,y_1 + \lambda y_2> = <x,y_1> + \lambda <x,y_2>$$


Norme sur E : $$\begin{align}
                    ||.|| : & E \rightarrow \mathbb{R}^+ \\
                            & x \rightarrow ||x||
                \end{align}$$

1) Séparation : $||x|| = 0 \leftrightarrow x = 0_E$



2) Homogeneite $\forall \lambda \in  R / C  || \lambda x = |\lambda||. ||x||$
3) Inégalité triangulaire: $\forall x,y \in E ||x+y|| \leq ||x|| + ||y||$


On peut définir une norme à partir d'un produit scalaire: $||x|| = \sqrt{<x,x>}$

Inégalité de Cauchy Schwarz: $|<x,y>| \leq ||x||.||y||$

On peut définir une distance à partir d'une norme : 
$$d(x,y)=\sqrt{<x-y,x-y>}$$


On veut définir un produit scalaire entre signaux / fonctions


$$<x,y>=x^Ty = \sum_{i=1}^nx_iy_i\\
\begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix} \in \mathbb{R}^n$$

Avec des éléments continus, $\sum$ va devenir $\int$

Une fonction $x : I \rightarrow R / C$ est integrable sur $I$ ssi $\int_I x(t) dt < +\infty$

* $\mathcal{L}^1(I) =$ espace des fonctions intégrables sur $I$
* $\mathcal{L}^P(I) =$ espace des fonctions p-intégrables sur $I$

Si $I=\mathbb{R}$ et $p=2$ $\mathcal{L}^2(\mathbb{R})=$ espace des fonctions de carré intégrable

Ensemble des signaux d'énergie finie :
$x \in \mathcal{L}^2(\mathbb{R}) \Longleftrightarrow \int_\mathbb{R} |x(t)|^2 dt < +\infty$ (energie du signal)


Dans $\mathcal{L}^2 , <x,y> = \int_{\mathbb{R}} x(t) \bar{y(t)}$ 


Si $x, y$ à valeurs réelle $$<x,y>=\int_\mathbb{R}x(t) y(t) dt\\
E_x = \int_\mathbb{R}|x(t)|^2dt = \int_{\mathbb{R}}x(t)\overline{x(t)}dt=<x,x>||x||^2=E_x$$
:::info
Définition de la fonction d'inter corrélation entre $x_{ref}$ et $y$

$$ \Gamma_{x_{ref}y}(\tau) ~ =  ~ <x_{ref}(t),y(t-\tau)> ~ = ~ \int{_\mathbb{R}x_{ref}(t)\overline{y(t-\tau)} dt}$$

$y(t-\tau)  = y(t)$ retardé d'un facteur $\tau$
$y_\tau(t)  = y(t-\tau)$
$y_\tau(0)  = y(-\tau) \Longleftrightarrow y(0)=y_\tau(\tau)$

:::
 
 



### Autocorrélation de x :

$$x \in \mathcal{L}^2 (\mathbb{R}), \Gamma_{xx}(\tau) ~ = ~ <x(t), x(t - \tau)> = \int_{\mathbb{R}}x(t) \overline{x(t - \tau)} dt$$


* 1^er^ propriété 
  * $\Gamma_{xx}$ est maximale pour $\tau=0$
  * $\Gamma_{xx}(0) = <x(t),x(t)> = \int_\mathbb{R}(x(t)^2)dt = ||x||^2 = \bar{\tau}_x$ car $\sqrt{<x(t),x(t)>} = ||x||$


* 2^éme^ propriété
    * $\Gamma_{xx}(\tau) = \overline{\Gamma_{xx}(\tau)}$ symetrie hermitienne
    * Si x est à valeurs réelles : $\Gamma_{xx}(- \tau) = \Gamma(\tau)$ : l'auto correlation est paire

* 3^éme^ propriété
    * $\forall \tau \in \mathbb{R}, |\Gamma_{xx}(\tau)| \leq \Gamma_{xx}(0)$

* Si $x$ est T-periodique : $x(t - \tau) = x(t)$

$\Gamma_{xx}(T)  = <x(t), x(t - \tau)> = <x(t),x(t)> = \Gamma_{xx}(0)$
$\Gamma_{xx}$ est periodique