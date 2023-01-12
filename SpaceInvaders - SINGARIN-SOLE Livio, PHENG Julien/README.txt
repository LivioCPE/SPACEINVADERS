Version Python : 3.9
Modules utilisés : tkinter, random, PIL

Données : 
images pour les éléments (la plupart) : https://www.flaticon.com/fr/
images de fonds : sur plusieurs sites d'images différents 

Répartition du travail :
Livio SINGARIN-SOLE : 60 %
Julien PHENG : 40 %

Contraintes :

Liste : il y a plusieurs listes utilisées dans le projet. On peut prendre pour exemple la liste qui stocke les aliens dans la classe Game : "self.aliens"

Pile : il y a en tout 3 piles utilisées dans le projet. En effet on retrouve dans la classe View des piles qui stockent les scores de chaque niveau 
et permettent d'afficher le dernier score de chaque niveau sur la page Home.

File : Nous n'avons pas trouvé de moyens intéressants d'utiliser une file dans le projet. Nous avons donc préféré ne pas en mettre du tout pour éviter d'ajouter des 
éléments inutiles dans le projet.


Ce jeu de SpaceInvaders doit être lancé à partir du fichier python "main.py".
La taille de la fenêtre sont modifiables à partir de ce même fichier python (width et height).

BUT DU JEU :
Tuer tous les aliens ainsi que le boss et avoir le plus haut score possible.
Le jeu s'arrête si un alien touche la bordure verticale du canvas ou si le vaiseau n'a plus de points de vie.

EXPLICATION DES DIFFERENTES CLASSES :
Note : La plupart éléments disposents d'attributs communs comme la vie, l'image, le canvas etc...

CLASS VIEW :
Cette classe permet d'afficher les pages sur la fenêtre Tkinter et les éléments comme les boutons.

Ce jeu de SpaceInvaders est composé de 4 pages:

	*** Home :
		.contient les chemins vers les différents niveaux
		.contient le dernier score de chaque niveau. De plus, lorsque l'on appuie sur le score, le score précédent est maintenant affiché (c'est une pile)

	*** Game 1 :
		.contient le niveau 1

	*** Game 2 :
		.contient le niveau 2

	*** Game 3 :
		.contient le niveau 3

CLASS GAME :

Cette classe est la plus importante car elle gère la coordination de tous les éléments contenus dans le canvas.
Leur affichage, leurs mouvements dans le temps, leurs intéractions etc...

CLASS SPACESHIP : 

La classe spaceship gère le comportement du vaisseau, c'est à dire sa vie, sa vitesse, son attaque et également sa réaction
face à divers évènements; Le vaisseau inflige 10 points d'attaque par tir.
Le vaisseau se déplace uniquement verticalement.
La touche "flèche droite" permet de se déplacer à droite.

La touche "flèche gauche" permet de se déplacer à gauche.

La touche "espace" permet de lancer un projectile. (un seul projectile à la fois pour augmenter la difficulté)

La touche "v" permet de se rajouter 10 points de vies. (si l'on récupère un bonus de vie, la vie passe directement à 5
							car cela met à jour les points de vie par rapport au max.lives 
							du vaisseau)

CLASS ALIENS :

La classe alien gère le comportement des aliens, elle est similaire au vaisseau sauf que le comportement de ces derniers
changent évidemment.

En effet, les aliens se déplacent d'abord horizontalement et lorsque l'un d'eux atteint la bordure ils se déplacent 
veticalent puis s'arrêtent et se déplacent horizontalement mais de l'autre sens.

Cette classe gère aussi la réaction de l'alien si elle touche un autre élément.

Il y a 3 types d'aliens classés par difficultés:
- Alien (easy): 10 points de vie et 1 point d'attaque
- Alien_medium : 20 points de vie et 1 point d'attaque
- Alien_hard : 30 points de vie et 2 points d'attaque

Remarque 1 : les aliens ne se touchent jamais car ils se déplacent à la même vitesse. Il aurait été interressant d'incorporer
	   des aliens avec des vitesses différentes mais nous nous sommes arrêtés à ce niveau là.

Remarque 2 : Les caractéristiques des boss n'ont pas été détaillé ici. (voir le code)

CLASS OBSTACLE : 

Cette classe gère les obstacle servant à protéger le vaisseau. Ils ont également de la vie donc ils peuvent disparaître.

Si un alien touche un obstacle, l'alien est détruit et l'obstacle subit des dégâts.

Ils sont placés en ligne juste devant le vaiseau.

CLASS REPARTITION_OBJECTS :
Cette classe gère la réparion des aliens et des obstacle sur le canvas:

- niveau 1 : 
aliens : 30 aliens faciles
obstacle : 1 

- niveau 2 : 
aliens : 20 aliens facile et 20 aliens moyens
obstacle : 5

- niveau 3 : 
aliens : 20 aliens facile et 20 aliens moyens et 20 aliens difficiles
obstacle : 7 

CLASS SHOT : 

Cette classe gère les projectile. Elle est commune pour les aliens et le vaisseau car elle prend en paramètre 
les ennemis de l'éléments en question.

Les aliens ont donc pour ennemis le vaisseau et les obstacles.
Le vaisseu a pour ennemis les aliens, la soucoupe volante et le boss en fin de partie.

CLASS UFO : 

Cette classe gère la soucoupe volante. 

La soucoupe n'a qu'un seule point de vie donc elle est facilement éliminé.
Elle se deplace horizontalement tout en haut du canvas.
Elle rapporte 50 de score en plus si elle est éliminé par le vaisseau.

CLASS OBJECT_LIVES :

Cette classe, assez simple, gère un bonus de vie qui apparaît en haut du canvas et se déplaçant verticalement.
Si le vaisseau touche le bonus il gagne un bonus de vie aléatoire en 1 et 3.

CLASS OBJECT_SHOT_GOD :

Cette classe gère un bonus de tir puissant qui a un comportement similaire à celui du bonus de vie.
Si le vaisseau touche le bonus il gagne un nombre aléatoire de tir puissant en 1 et 3 qui éliminent tous les ennemis sur
leur passage.

DISCLAIMER : Il y a d'autres détails qui n'ont pas été abordé pendant cette explication car ils n'ont pas grande importance
pour la compréhension du jeu.
Pour plus de détails, je vous renvoie au programme commenté.
D'ailleurs, des erreurs peuvent s'afficher dans la console à certains moments mais n'influencent pas le bon fonctionnement du jeu.
Ces erreurs sont souvent dû à la destruction des éléments dans les differentes frames.