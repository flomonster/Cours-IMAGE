# Introduction à la synthèse d'images

## Séance de projet:

Peut être libre -> voir si le projet propose convient.

Si raytracer en TP:

* Ex: partir de ratraycer et changer de technique de rendu ou changer aspect modélisation.
* Ex: modélisation d’arbre

2 choses
* Aspect technique
* Aspect artistique

:::info
Réfléchir à un sujet qui nous plait
On peut faire du path tracing, sur les meshs...
Modélisation d'arbre / végétaux.
Ne pas hésiter à aller voir Fabrizio
:::

S’y prendre tôt, parce que après il y aura beaucoup de projets.
Langage libre, mais tp en c++.
Aspect performance importante, et surtout avoir un beau rendu.

Le projet :
* En **binome** ;
* Une soutenance ;
* Un rapport (quelques pages 24h ou 48h avant la soutenance).
* Une vidéo de 1/2 minutes. Ca peut être une vidéo animé ou autre.

## Partie 1 : Rendu temps réel vs rendu photo réaliste

La synthese d’image est le fait de modeliser une forme , apparence du monde reel ou d’objets imaginaires avec un ordi.

Pour faire un rendu il faut connaît l’optiaque pour rendre un coté réaliste et s’y connaitre en physique

dans la réalité virtuelle, il n’y a pas que l’info visuelle
mais le cours porte surtout la dessus.

**Photo réaliste**:
> Prendre la photo la plus belle possible : assez difficile -> temps importe peu mais qualite avant tout

**Rendu temps réel:**
> Le temps est hyper important, et il faudra avec ce temps cours, la plus belle image possible, on va tricher pour faire un rendu qui sera joli.

Un jour les techniques de rendu temps réel vont disparaitre, quand le matériel le permettra, Nvidia est en train de le faire.
Des algo photoréaliste sont en train de passer en temps réel.



Photoréaliste image la plus jolie, ce qui correspond une photo, photo = rendu
Prend du temps, la qualité soit le plus vrai possible

Temps réel belle image mais ce qui compte le plus le temps, ex jeu video
Image peut être très belle mais pas forcement photorealiste
Tricher pour faire un rendu plus rapide. Les techniques de rendu temps réel vont etre jete a la poubelle car les outils permettent de faire les calculs



## Partie 2 : 

Les domaines de l'image:

* **Géométrie:** Algorithmique discrète
    * Euclidienne 
    * Projective

On peut paralléliser en bas niveau.
On va avoir besoin de bonne connaissance physique a un moment.
Il faut respecter les habitudes du cerveau.

Heureusement beaucoup de logiciels de modélisation le font très bien. Pour mes objets, j’ai besoin d’une équation mathématique (ex: faire un maillage)

La frontière intérieure / extérieure d'un objet importante.

Usuellement on prend des triangles :
* Eviter erreur d’arrondi
* Avantage les 3 points sont toujours coplanaires

On peut augmenter / diminuer résolution mesh. Mesh estimation: réduire le mesh sans trop diminuer la qualité, ne pas les supprimer partout, choisir les zones plat, lorsqu'un objet est trop loin, on enlève des meshs par exemple


* **Multimédia:** Image son vidéo
* **Physique:** 
* **Informatique**
* **Rendu**

ex: rendu de bande dessinée

(Si intéressé pour faire rendu spécifique, aller voir le prof pour en parler pour voir si le sujet, n’est pas trop compliqué ni trop simple.)
Domaine lié programmation GPU.

**Image HDR** *high dynamic range*, essaye de prendre la même scène avec != expositions, capable de repérer les sombres claires et sombres


* **Animation**

La modélisation représente et traite la forme des objets 3D.

On prend souvent des triangles en mesh car c'est coplanaire et permet d'éviter les erreurs d'arondis.

Exemple de projet: 
> Essayer de supprimer des meshs d'un objet 3D compliqué sans trop détériorer le modéle. 

Il y a des domaines liés :
* Programmation GPU
* Traitement d'images (image Hight Dynamic Range HDR)

## Historique

Base : invention de l'écran CRT

Dans les années 60 tout a commencé avec algo(en temps réel) de *Sutherland*.

Dans les annés mis 70, on a des images générés sur ordinateurs pour les films.

Début des années 80 on a de la synthèse sur les films.

Les permiers rendus réel, sont des rendu *fil de fer*. 
La réalité virtuelle permet de faire des simulateurs, mais ce ne sont pas les premiers.

Les simulateurs avant realite virtuelle marchaient avec des modèles miniature.

* **Domaine d’assistance chirurgicale**
    * éviter les faux mouvement.
    * la réalité augmentée va permettre d’aider le chirurgien
    * Les anciens chirurgiens étaient assez réticents, mais cela a changé. Nous en somme cependant encore au balbutiement.

* Domaine de l’architecture: 
    * écoulement des fluides
    * force des vents appliqués aux bâtiments.

**CAO** (confection assistée par ordinateur)
* Modélisation des pièces
* Imprimante 3D font couche par couche, dans quel sens il faut mettre les pièces.

On a les premier jeux et films 3D dans les années 80.

**Films:**
* TRON (1982)
* The last star fighter (1984)
* Terminator 2 (1991)
* Jurassic Park (1993)
* Toy story (1995) (Premier long métrage)
* Mille et une patte (1998)
* Monstre et Co (2001) La fourrure du monstre est cool
* Age de glace (2001)
* Le monde de Nemo (2003)
* Monster Academy (2013) (Full raytracing)

**Jeux Vidéo:**
* Star wars 83-89
* Alone in the dark Resident Evil 
* Wolfenstein 3D 96
* Myst (1993) / Riven (1997) / Exil (2002)
* Descent (1995) / Terminal velocity (1995) / Flight Gear Simulator

## Applications

* Réalité augmentée
* Cinéma
* JV
* Simulation (civil, militaire)
* Assistance chirurgicale
  * Il y a beaucoup de travaux pour faire des opérations assister par ordinateur. Mais il a besoin de la vision.
* Architecture
* Conception Assisté par Ordinateur (CAO)
* ...

Il existait des simulateurs avant la VR. Mais ca aide au réalisme...

## Communauté scientifique

* ACM SCIGGRAPH (surveiller leurs articles)
* Synthèse image a jour
* Blender rendu réaliste (compromis entre complexité et professionnalité)

* Opengl Direct3D bas niveau
* Vulkan risque de remplacer opengl.
* POVRAY: intéressant pour regarder les algos, (open source)(moteur de rendu)

*Second depth shadow mapping* (algo utilisé dans monstre & compagnie)

## Outils

* Modeleurs
* Outils d'animation
* Moteurs de rendu
* Rendu réaliste
  * POVRAY
    * Code libre en C++
  * Blender
  * Maya
  * ...
* Rendu temps réel (API bas niveau)
  * OpenGL / Vulcan
  * Direct 3D
  * Java 3D
  * ...
* Moteurs (API haut niveau)
  * Unity
  * Ogre

## Rappels d'optique et de geometrie euclidienne

Pour modeliser une scene et faire son rendu, on a une source lumineuse primaire, les objets vont recevoir et absober cette lumiere, ils renvoient la lu miere ce sont des sources lumineuses secondaires.

Couleurs primaires:
* **Additive**: Rouge / Vert / Bleu
* **Soustractive**: Cyan / Magenta / Jaune

L'objet renvoie la lumiére en fonction de sa texture / couleur.
Les objets filtrent la lumiére sur la lumière qu'elle diffuse. Cependant, le rayon réfléchi lui n'est pas filtré dans la plus part des cas.

Distance focale permet le zoom (plus on l'augmente plus on zoom), mais reduit l'ouverture de champs, si on augmente l'ouverture de champs, les objets deviennent plus petit.

On a une zone, avant et après cette zone, c'est flou. 

Comment l'image est capturée ?
> Le capteur est une matrice, chaque fois qu'un rayon rencontre un capture, il y a une charge électrique, à chaque tic d'horloge on compte le nombre de charge pour savoir si la région est bien limineux, mais on a pas les longueurs d'ondes, utile pour les images noirs et blancs. 

![Bayer Pattern](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Bayer_pattern_on_sensor.svg/350px-Bayer_pattern_on_sensor.svg.png)