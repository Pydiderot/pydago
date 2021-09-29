# Formation Python 3 : échanges équipe de maths / équipe de physique

## 1. Aspects techniques

### L'IDE Thonny
.. figure:: https://thonny.org/img/get_started.png
    :align: right
    :width: 200px

A partir du bureau des ordinateurs du lycée: `Logiciels > Python > Thonny`

Quand on lance Thonny, il y a deux zones :

- la zone du haut où on travaille dans un fichier, qui peut être exécuté quand on le demande, et qui DOIT 
être enregistré (sur cette image, le fichier s'appelle "Hello.py")
- la zone du bas qui est un **shell** (ou **console**) : comme un écran de calculatrice, mais qui exécute des commandes Python 
(on ne peut pas l'enregistrer).
C'est dans cette zone qu'apparaissent les résultats des commandes exécutées 
depuis un fichier de la zone du haut.

#### Quelques instructions à essayer dans la console :
```python
3 + 4
print("hello world")
"hello" + "world"
```
#### Quelques exemples à enregistrer dans un fichier :
```python
3 + 4
print("hello world")
"hello" + "world"
```
Pour exécuter le fichier, il faut cliquer sur le bouton |run|  ou appuyer sur :guilabel:`F5`.
Il faut donner un nom au fichier. Le fichier sera sauvegardé par défaut dans : `U:\Documents`

.. |run| image:: /source/_static/bouton_run.png

#### Quelques remarques pour l'utilisation avec les élèves :

 - Lors de la vidéoprojection de thonny, les caractères sont trop petits. On peut utiliser 
 :guilabel:`ctrl` + :guilabel:`+` ou :guilabel:`ctrl` +  :guilabel:`molette` pour zoomer.
 - La config est enregistrée automatiquement quand on quitte thonny.
 - Pour afficher les numéros des lignes:
 :guilabel:`Outils` → :guilabel:`Otions` → :guilabel:`Editeur` → :guilabel:`Afficher les numéros de ligne`
 - La notion de variable informatique n'est pas du tout évidente à appréhender pour les élèves. Il peut être 
bon d'expliquer que concrètement, à chaque nouvelle variable `x`, la machine va créer un espace (une boite) 
dans la mémoire vive étiquetée par le nom de la variable (`x`). Nous pouvons ensuite lire le contenu de la 
boite avec `print(x)` et changer ce qu'elle contient avec par exemple `x = 3`.

.. figure:: https://thonny.org/img/variables.png
    :align: right
    :width: 200px

- Pour l'affichage dynamique du contenu des variables :

:guilabel:`Affichage` → :guilabel:`Variables` 
(A désactiver lorsqu'on importe de grosses librairies car sinon l'onglet 
affichera le contenu de toutes les fonctions et variables importées, ce qui peut ralentir 
l'utilisation.)

- Pour exécuter en mode débug : bouton |bouton_debug| ou touches :guilabel:`crtl` + :guilabel:`F5`  
qui permet l'éxécution du script en mode « pas à pas ». Cela activera le menu debug :|menu_debug|

.. |bouton_debug| image:: /source/_static/bouton_debug.png
.. |menu_debug| image:: /source/_static/menu_debug.png


### iTALC

Ce qui ne marche pas : parler à un groupe d'élèves qui sont chacun devant leur écran.

Le petit outil iTALC (dans une salle informatique, accessible depuis : `Outils Profs > iTALC`) permet de mieux gérer les moments où on réclame
l'attention des élèves.

.. figure:: https://raw.githubusercontent.com/Pydiderot/pydago/main/formation/Capture_iTALC.PNG
    :align: right
    :width: 600px

Avec iTALC on peut : 

- verrouiller tous les écrans (il y a parfois un ou deux écrans qui ne se verrouillent pas !)
- envoyer le contenu de son écran vers les écrans de tous les élèves (avec la commande "démo")
- annoncer au groupe "je vais vous envoyer l'écran de -nom d'élève-" (avec la commande clic droit > "laisser faire une démo")

### Procédure pour installer des librairies

L'utilisation de Python est basée sur de nombreuse librairies qui ne sont pas forcément installées au lycée.
Pour voir la liste de celles qui sont installées au lycée, vous pouvez aller voir dans : `C:\Python3.7\Lib\site-packages`.
Si vous voulez demander l'installation d'une librairie supplémentaire, faites un ticket (`Outils Profs > Support Informatique`).
On peut aussi gérer les paquets à partir de Thonny (:guilabel:`Outils` → :guilabel:`Gérer les paquets`).

### Pydiderot

Tout un tas de ressources sont disponibles sur un compte Github qui a été développé par l'équipe de maths (à la suite de Clément Spaier).
https://github.com/Pydiderot
Vous pourrez y trouver :
- les notes de cette pettie formation en allant dans pydago https://pydago.readthedocs.io
- les librairies "maison" en allant dans pydiderotlibs https://pydiderotlibs.readthedocs.io
- des liens pour télécharger thonny en allant dans pydiderotIDE https://pydiderotide.readthedocs.io

## 2. Aspects pédagogiques

Proposition de progression commune concernant l'algo au lycée (à re-discuter...)

### Seconde : 

 - fonction (expliquer les différences avec les fonctions en maths)
 - boucle (sans variable --> "répéter n fois")
 - variable (en liaison avec les fonctions d'une variable en maths)
 - boucle avec variable, mais simple (que des while avec la variable compteur qui est utilisée de façon hyper standardisée)
 - condition "if..." (pose peu de difficulté avec les élèves)


### Première :


 - notion de liste
 - boucle "for"
 - types string, integer, float...
 - boucles avec variables plus compliquées (typiquement : boucles pour résoudre les problèmes sur les suites, dans lesquels il y a aussi bien un travail possible sur l'indice de la suite que sur la valeur du terme de la suite)
 - boucle avec un "append" (instruction qui ajoute un élément à une liste)

### Terminale :

- rien de plus, retravail de ces notions

### Exemples en classe de seconde :

#### Une fonction qui n'utilise presqu'aucune variable :

```python
from pydiderotlibs.repere import *
from random import randint
def flocon():
    x=randint(-100,100)/10
    y=randint(-100,100)/10
    point(x,y,'pink',2)
    
fenetre()
flocon()
```

#### Une boucle utilisant la fonction précédente et utilisant une variable, mais n'utilisant aucune liste :

```python
i=0
while i<1000 :
    flocon()
    i=i+1
```

### Exemples en classe de première : 

perso je n'ai rien à proposer...

On peut espérer qu'avec un peu de travail les élèves puissent écrire à partir de zéro du code ressemblant à cela :

```python
u=5
for i in range(11):
    u=u*3
    print('u_'+str(i)+' = '+str(u))
    i=i+1
```
Les difficultés ici sont : 
- utilisation de variables
- utilisation d'une boucle (avec indentation)
- utilisation de liste (dont la première valeur est 0 et pas 1)
- typage des objets (types integer ou float, type string)

Donc ça fait plusieurs difficultés...

Il y a une discussion sur des difficultés que peuvent rencontrer les élèves ici : https://pydago.readthedocs.io/formation/enseignants2.html#difficultes 

Dans la librairie pydiderotlibs, il y a une boucle sans variable (avec toutes les limitations que cela implique, mais qui 
peut rendre service dans certains cas, avec des élèves débutants) :

```python
repeat(f,10)
```
(Ici on demande de répéter 10 fouis la fonction f.)
