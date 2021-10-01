# Formation Python 3 : échanges équipe de maths / équipe de physique

## 1. Aspects techniques

### Python
Langage multiplateforme ordinateur, calculatrice, microcontroleur

### IDE Environnement de développement
Un IDE réunit :
- un traitement de texte (à coloration syntaxique)
- une console (accès direct)
- un lancement de python

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

#### Autres IDE accessibles du lycée 
- Edupython : connue et souvent montré en démo
- Mu : Pour programmer certains microcontroleurs

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

#### Librairies
Python possède de très nombreuses librairies.
Ce sont des bout de programmes déjà écrits qui permettent d'utiliser des fonctions parfois très complexes.

par exemple la librairie mathématiques

``` python
import math
print(math.sqrt(9))
```

Il y a plusieurs librairies classiques déjà installées :
numpy, scipy, matplotlib, sympy, pygame 


Pour voir la liste de celles qui sont installées au lycée, vous pouvez aller voir dans : `C:\Python3.7\Lib\site-packages`.

Si vous voulez demander l'installation d'une librairie supplémentaire, faites un ticket (`Outils Profs > Support Informatique`).
On peut aussi gérer les paquets à partir de Thonny (:guilabel:`Outils` → :guilabel:`Gérer les paquets`).


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

### Pydiderot : une organisation hébergée sur Github

#### librairies de pydiderotlibs :
Pour faire des graphiques même simples, les manuels utilisent les bibliothéques numpy et matplotlib
``` python
import numpy as np
import matplotlib.pyplot as plt
# U et I sont à compléter par les élèves
# Tableau entre crochets, nombres séparés d'une virgule
U = np.array([-5.0,-4.0,-3.0,-1.0,0,1.0,2.0,3.0,4.0,5.0])
I = np.array([-0.052,-0.039,-0.028,-0.011,0,0.01,0.021,0.032,0.039,0.05])

#Tracé de la courbe
plt.grid()
plt.title('Caractéristique tension-intensité')
plt.xlabel('I(en A)')
plt.ylabel('U(en V)')
plt.plot(I,U,'+',label= 'Points issus de la mesure')
plt.legend()

# Effectuer une regression linéaire et la tracer
Umod = np.polyfit(I,U,1)
print('Um =', round(Umod[0],2),'x','I','+',round(Umod[1],4))

Reg = np.poly1d(Umod)
x = np.linspace(1.2*min(I), 1.2*max(I))
y = Reg(x)
plt.plot(x, Reg(x))

plt.show()

```
Il existe des librairies qui permettent de simplifier cette écriture.
En particulier la librairie **pydiderotlibs** : 
``` python
from pydiderotlibs.repere import *
fenetre()

i=0
while i<10:
    point(i,i**2)
    i=i+1
```


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
 - boucle sans variable --> "répéter n fois"
 - variable (en liaison avec les fonctions d'une variable en maths)
 - boucle avec variable, mais simple (seulement des boucles "while" avec la variable compteur qui est utilisée de façon hyper standardisée)
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

Il faut échanger sur le type d'utilisations qui sont envisagées en maths et en physique.

#### Afficher un repère avec la librairie pydiderotlibs :

```python
from pydiderotlibs.repere import *
  
fenetre()
```
Remarque : l'instruction 
```python
window()
```
est un alias de fenetre().

A la souris, on peut déplacer la fenêtre ; zoomer ; zoomer suivant un seul axe de cooordonnées.

Il y a un lien dans la console pour accéder à la documentation de la librairie.

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
(Ici on demande de répéter 10 fois la fonction f.)

### Voir le fichier avec tous les programmes de 2de

### Les programmes python de Physique Chimie par l'académie de Guyane
https://physique-chimie.dis.ac-guyane.fr/Banque-de-programme-python-pour-le-lycee.html
