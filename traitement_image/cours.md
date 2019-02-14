# Traitement d'images

## Les Domaines:

* Vision par ordinateur: Calibrage
* Rendu cartoon
* Rendu photo-réaliste
* reconnaissance d'objets
* codage / qualite de l'image
    * ex: reparer photo
* Vidéo surveillance
    - De flux
    - Suivi de personnes **/!\\ Alerte éthique /!\\** (éthi... quoi ?)
    - Radars automatiques
    - Empreinte digitale
    - ...
* Assistance
    * Aide aux personnes malvoyantes
    * Assistance à la conduite
    * ...
* Film / Photo /Art
    * Effets spéciaux
    * Traitements embarqués sur appareil photo
    * Restauration
    * ...

## Historique

* Photographie
    * Debut 1800 : Nicephore Niepse (Fr)
* Photographie couleur
    * 1869 : Charles Cros (Fr) parallèlement à Louis Ducos du Hauron (Fr)
* Cinematographie
    * 1895 : Louis Lumière

* Disque de Nipkow
    * 1884: Paul Nipkow (Allemagne)
        * Television / transmission 
* Capteur CMOS
    * 1967 : Frank Wanlass (Etat-Unis)
    * Soit pas chere et pas ouf / Soit chere et cool
* Capteur CCD
    * 1969: Geore E. Smith (USA) et Willard Boyle (Canada/USA)
    * Milieu de gamme
* Logiciels
    * Gimp <3
    * Photoshop ;(
    * ...
* Bibliothèques
    * Olena <3
    * OpenCV
    * ITK
    * ...
    
:::info
Différence CMOS vs CCD [ici](https://electronics.howstuffworks.com/cameras-photography/digital/question362.htm)
:::

    
## Projet

* A faire en binôme

## TP

1) Améliorer une image
2) Elimination du bruit
3) Motif de bayer => image finie (?)

## Formation d'une image

*CF: Cours synthèse d'image*

**Acquisition** : 

![Bayer pattern](https://cdn2.hubspot.net/hub/20421/file-39331860-png/images/1-ccd-and-bayer-color.png)

:::info
Les artefacts lumineux sont souvent du a une surcharge d'un capteur qui va propagé la charge sur les autre capteurs.
:::

Transfert de données :
* Entrelacé
    * Les fabriquants flush une ligne sur deux à chaque tick d'horloge.
        * Pour les moniteurs CRT (tube cathodique) ce n'est pas génant.
        * Aujourd'hui c'est un problème.
* Progressif (progressive scan)
    * Flush l'image entiérement à chaque tick.




**Visualisation** : 

* Utilisation de CRT
    * Canon à électrons
* Utilisation de LCD 
    * Rétro-éclairage (néons/diodes)
    * On peut orienté les cristaux avec un courant
    * Aujourd'hui on utilise des LED

:::info
* CRT = Cathode Ray Tube
* LCD = Liquid Cristal Display
:::

**Perception** :

![Schéma d'un oeil](https://fr.cdn.v5.futura-sciences.com/buildsv6/images/mediumoriginal/4/6/e/46ebf5a87e_50101321_3240-0eeaa530ae.jpg)


Capteurs de l'oeil
* Cônes (7 000 000) perception RGB
* Batonnet (120 000 000) perception intensité

* Perception
    * Log
    * Maximum dans le vert
    * Varie dans le temps (persistance rétinieene..)
* Interprétation
    * Filtrage - Analyse
    * Affect

## Codage / représentation des couleurs

#### RGB

Première idée intuitive, représenter le spectre visible avec RGB.
repère tridimensionnel.

![Représentation RGB](http://matlab.izmiran.ru/help/toolbox/images/colorcube.jpg)

#### HLS

* H: Teinte (Correspond à un angle)
* L: Luminance (Correspond à la hauteur)
* S: Saturation (Pureté de a couleur) (Correspond à la distance du disque)

![Modele HLS](https://images.slideplayer.com/27/9226883/slides/slide_21.jpg)

:::info
HSV est une variante de HLS
:::

#### CMY

* Cyan
* Magenta
* Yellow

C'est quand on travaille en synthése soustractive.

#### YUV

* Y: Luminosité
* U et V: La teinte

C'est intéréssant car il sépare la chrominance du reste.


### Changement d'espace 

#### RGB $\leftrightarrow$ HLS

On peut retrouver la formule.

#### RGB $\leftrightarrow$ YIQ

Le passage de l'un à l'autre est simple :

$$
\begin{pmatrix}
    Y \\
    I \\
    Q
\end{pmatrix} =
\begin{pmatrix}
    0.30 & 0.59 & 0.11 \\
    0.60 & -0.28 & -0.32 \\
    0.21 & -0.52 & 0.31 \\
\end{pmatrix} 
\begin{pmatrix}
    R \\
    G \\
    B
\end{pmatrix}
$$

Les coefficients peuvent un peu variés. Ca dépend des perceptions.

#### RGB $\leftrightarrow$ noir et blanc

Formule simple :

$$L = 0.299 R + 0.587 G + 0.114 B$$

:::info	
Pour recoloriser il faut le faire à la main.
Il y a des recherches pour le faire avec du ML
:::


#### Binarisation

On a souvent envie de binariser pour separer le fond de la forme.
ex: verification dans une chaine de production.

#### Façon usuelle d'enregistrer une image
* matrice de pixel


:::info
pixel = picture element
:::

## Codage d'une image

### Codage par matrice

On utilise une matrice dans laquelle on stock:

* Directement la couleur
* Un index qui refere à une palette

#### Implémentation

On peut soit utiliser une *matrice* soit un *vecteur*.

:::warning
Pour parcourir une image il faut la parcourir de manière contigu en mémoire.
:::

### Caractéritique de l'image 

* Discrétisation spatiale (résolution)
* Échantillonnage (amplitude)

### Autres Représentation 

On peut représenter notre image avec :
* Arbre 
* Graphe
* ...

On peut utiliser d'autre maillage que rectangulaire.
Sauf que ca pose un problème topologique.
Est ce qu'ils ont une connexité de 4 ou 8 ?

On peut utiliser un maillage hexagonal.

![Maillage hexagonal](https://i.stack.imgur.com/a264L.gif)


[Theoreme de Jordan](https://fr.wikipedia.org/wiki/Th%C3%A9or%C3%A8me_de_Jordan)

### Stockage et transfert

Différents formats : **JPEG** / **TIFF** / **PNM** / **PNG** / **BMP** / **GIF** / **TGA**  ...

Choix en fonction de criteres:
* Avec ou sans compression
* Avec ou sans couleur
* avec ou sans palette
* Une seule image ou plusieurs
* Optimise pour une architecture (Ex: BMP sauvegardée à l'envers)
* Libre ou pas (Ex: GIF et Computeserve)


:::info
Ne pas oublier de passer dans un referentiel exponentiel pour effectuer le changement de valeur des composantes des pixels. L'oeil humain est sensible logarithmiquement.
:::