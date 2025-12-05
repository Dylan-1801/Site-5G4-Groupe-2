---
title: "Notes de cours"
---

# Unreal Engine

## Introduction

Unreal Engine, créé par Epic Games, est un moteur de jeu 3D
complet qui permet de construire des environnements interactifs. Il contient
toutes les fonctionnalités dont un développeur a besoin : rendu graphique,
physique, animation, gestion des matériaux, son, de même qu’un système de
programmation visuelle appelé Blueprints. La version actuelle est le UE5. Ce
moteur mise énormément sur le réalisme grâce à des technologies comme Lumen,
qui gère l’éclairage dynamique, et Nanite, qui lui permet d’afficher des
modèles très détaillés sans perdre en performance. 
Ce moteur de jeu est devenu l’un des plus populaires,
principalement parce qu’il offre une qualité visuelle impressionnante ainsi
qu’une polyvalence d’utilisation. On peut l’utiliser pour créer des jeux vidéo,
mais aussi pour du cinéma, de l’architecture, de la réalité virtuelle. En plus
de cela, il est gratuit tant que le projet ne génère pas de gros revenus, ce
qui le rend particulièrement intéressant pour les étudiants et les petites
entreprises. 
Aujourd’hui, Unreal Engine est utilisé partout, que ce soit
par des petites startups, par des studios indépendants et même par des plus
grandes compagnies. Epic Games l’utilise notamment pour leur fameux jeu
Fortnite, et de nombreux studios majeurs tournent également sur UE5. Le moteur
est même présent dans le monde du cinéma, par exemple dans la production
virtuelle de séries comme The Mandalorian. 
Si on choisit Unreal Engine plutôt qu’un autre moteur de
jeu, c’est surtout parce qu’il offre un ensemble d’outils professionnels
complets tout en restant accessible au début. Il permet d’obtenir des résultats
incroyables très rapidement, sans avoir à créer un moteur de jeu au complet.
C’est la combinaison de puissance, de réalisme et de facilité d’utilisation qui
fait en sorte qu’Unreal Engine est l’un des moteurs les plus appréciés de
l’industrie.


## Historique/Évolution

L’histoire d’Unreal Engine commence en 1998, lors de la sortie du jeu Unreal par Epic Games. La première version du moteur, UE1, impressionne immédiatement l’industrie des jeux vidéo. À l’époque les outils étaient limités, mais UE1 proposait déjà un éditeur de niveaux intégré, un éclairage dynamique et une architecture logicielle qui sépare clairement le contenu du code. Ces choix techniques posaient les bases de ce que deviendra Unreal plus tard, un moteur complet, accompagné d'outils professionnels directement accessibles aux créateurs. 

Avec Unreal Engine 2, Epic Games améliore surtout la qualité visuelle, la physique et la flexibilité du moteur. Les effets gagnent en précision, les performances montent d’un bon niveau, et plusieurs jeux du début des années 2000 adoptent naturellement ce moteur qui devient vite une référence dans le domaine. 

Unreal Engine 3 est un tournant majeur, l’arrivée des consoles HD comme la Xbox 360 et la PlayStation 3 pousse Epic Games à revoir son pipeline graphique comme les ombres dynamiques plus réalistes, les matériaux beaucoup plus avancés et le rendu modernisé. UE3 domine le marché pendant des années et propulse des titres cultes comme Gears of War, BioShock, Mass Effect ou encore Batman Arkham Asylum. Les outils deviennent plus accessibles pour les développeurs, ce qui contribue à sa popularité. 

En 2014, Unreal Engine 4 change complètement. Epic Games décide de rendre le moteur gratuit, en ne prenant qu’une commission sur les revenus des projets. En plus, UE4 introduit les Blueprints, un système de programmation visuelle qui permet de créer du gameplay sans écrire une seule ligne de C++. Le rendu passe au PBR (physically based rendering), ce qui donne un réalisme beaucoup plus naturel et uniforme. 

Enfin, avec Unreal Engine 5, sorti en 2022, qui apporte deux innovations qui changent la manière de créer des jeux. Ça commence avec Nanite, qui permet d’afficher des modèles détaillés sans casser les performances, et Lumen, un système d’éclairage global dynamique. UE5 améliore aussi la physique avec Chaos, les particules avec Niagara et la gestion des mondes ouverts grâce à World Partition. Tout ça rapproche le rendu en temps réel de la qualité cinématographique et ouvre encore plus de possibilités aux développeurs.


## Architecture interne 

3.1 L’Editor (l’éditeur d’Unreal Engine) 
L’Editor est l’endroit où tout se passe dans Unreal Engine.
C’est l’interface principale dans laquelle on construit les niveaux, on crée
les matériaux, on assemble les animations, on écrit des Blueprints, et même où
l’on gère les collisions ou les interfaces utilisateur. C’est un environnement
complet qui regroupe plusieurs outils dans une seule application, ce qui en
fait le cœur du développement sous Unreal. 

L’Editor est organisé en plusieurs sections essentielles : 
Viewport : la fenêtre 3D principale où l’on voit la scène et où l’on manipule les objets directement. 
Content Browser : la bibliothèque du projet. On y retrouve tous les assets : modèles 3D, textures, sons, animations, Blueprints, etc. 
Details Panel : l’endroit où s’affichent les propriétés de l’objet sélectionné (taille, matériaux, collisions, composants, comportements, etc). 
Éditeurs spécialisés : 
Material Editor pour créer des matériaux visuels complexes, 
Blueprint Editor pour la logique de jeu, 
Niagara pour les effets de particules, 
Animation Blueprint pour gérer les animations, etc. 

L’Editor est pensé pour être très visuel : beaucoup
d’actions se font en glissant-déposant des éléments ou en ajustant des
paramètres. Cette approche réduit la quantité de code à écrire et permet de
prototyper rapidement, ce qui rend Unreal à la fois puissant et accessible,
même pour ceux qui ne maîtrisent pas encore parfaitement le C++. 

3.2 Le Gameplay Framework 
Le Gameplay Framework est la structure qui organise la
logique du jeu. C’est une sorte de squelette conceptuel qui fournit des classes
déjà prêtes pour gérer les éléments essentiels du gameplay. Grâce à lui, on n’a
pas besoin de réinventer à chaque fois la gestion des joueurs, des règles ou
des interactions. 

Voici les principales classes du Framework : 
GameMode : définit les règles générales du jeu (quel personnage le joueur contrôle, ce qui se passe au début d’une partie, comment la victoire est déterminée, etc.). 
GameState : garde en mémoire l’état global du jeu (scores, phases de jeu, minuteurs). Cette classe est particulièrement utilisée en multijoueur. 
PlayerController : reçoit les inputs du joueur (clavier, souris, manette) et décide quoi en faire. 
Pawn / Character : les entités contrôlables dans le monde. 
Pawn : version simple, sans animations. 
Character : version plus complète, avec squelette, animations et déplacements avancés. 
PlayerState : regroupe les informations propres à chaque joueur (nom, équipe, score individuel). 
HUD / UI : gère ce qui apparaît à l’écran : barres de vie, inventaire, menus, etc., via UMG et les Widgets. 

Pourquoi cette structure est-elle importante ? 
Parce qu’elle sépare clairement les responsabilités : 
Le GameMode gère les règles, 
Le PlayerController gère les inputs, 
Le PlayerState gère les données du joueur, 
Le Character représente le personnage dans le monde. 

Pourquoi c’est important ? 
Cette organisation évite d’accumuler toutes les fonctions
dans une seule classe et permet de construire des jeux beaucoup plus propres et
plus modulaires. C’est une des raisons pour lesquelles Unreal est très apprécié
par les studios professionnels : le moteur encourage naturellement des projets
bien structurés, capables de s’adapter à des jeux de grande ampleur.


## Concepts fondamentaux 

Pour comprendre comment fonctionne un projet d’Unreal
Engine, il faut d’abord connaître ses concepts de base. Tout commence avec le Level, qui représente
simplement un niveau ou une scène dans le jeu, c’est l’endroit où on place les
objets, les lumières, le décor et où se déroule l’action. Ces objets placés
dans un niveau sont appelés des Actors,
ce terme englobe tout, qu’il s’agit d’un cube, d’un personnage, d’une porte,
d’une lumière ou d’un ennemi. Chaque Actor est composé d’éléments plus petits
qu’on appelle des Components,
qui lui donnent ses fonctionnalités. Par exemple, un mesh 3D, une collision,
une lumière ou un son sont chacun des Components qu’on assemble pour définir ce
qu’un Actor peut faire ou comment il se comporte. 

Pour tout ce qui est contrôlable dans le jeu, Unreal utilise
deux classes principales : le Pawn et le Character. Le Pawn est l’objet générique
qu’on peut contrôler, comme un robot, un véhicule ou même une caméra mobile. Le
Character est une version plus avancée du Pawn, pensée spécialement pour les
personnages humains. Il inclut déjà un système de mouvement, des collisions
adaptées et un squelette pour les animations. Pour que ces entités puissent
être contrôlées, Unreal utilise des Controllers.
Le PlayerController reçoit les inputs du joueur,
tandis qu’un AIController sert à gérer le comportement
d’ennemis contrôlés par l’intelligence artificielle. 

Ces éléments fonctionnent ensemble grâce au Gameplay Framework, qui
organise la logique du jeu. Le GameMode définit les règles de la partie
: quel personnage est contrôlé, comment le niveau se déroule, ce qui se passe à
la mort du joueur, etc. Le GameInstance,
quant à lui, sert à stocker des informations qui doivent rester accessibles
même lorsqu’on change de niveau, comme un score total, un inventaire global ou
des paramètres du joueur. 

Finalement, Unreal Engine doit une grande partie de sa
popularité aux Blueprints,
qui est son système de programmation visuelle. Grâce à une interface en nœuds,
qui s’assemblent comme un diagramme, on peut créer des interactions, des
comportements, des animations ou des mécaniques complètes sans écrire une seule
ligne de code. C’est un outil qui rend le moteur beaucoup plus accessible pour
les débutants tout en étant suffisamment puissant pour être utilisé dans des
jeux très avancés.


## Les technologies clés d’Unreal Engine 

Unreal Engine 5 se distingue surtout grâce à quelques
technologies majeures qui changent complètement la manière de créer des
environnements 3D. Ces outils rendent le moteur plus puissant, plus réaliste et
surtout plus simple à utiliser. Les technologies les plus importantes à
connaître pour comprendre ce qui fait la force d’UE5 sont : 

Nanite (La géométrie virtuelle) 
Nanite est sans doute l’une des avancées les plus marquantes
d’Unreal Engine 5. Habituellement, les modèles 3D utilisés dans un jeu doivent
être fortement optimisés : 
réduction du nombre de polygones, 
création de multiples LOD (Levels of Detail), 
préparation de différentes versions du même modèle pour éviter les chutes de performance. 
Avec Nanite, ce travail d’optimisation devient inutile. On
peut importer directement des modèles extrêmement détaillés, comme ceux
utilisés dans le cinéma ou la modélisation professionnelle. Ainsi le moteur
s’occupe lui-même de gérer le niveau de détail en fonction de la position de la
caméra. 

Lumen (L’éclairage global en temps réel) 
Lumen est le nouveau système d’éclairage global d’Unreal
Engine 5. 
Avant lui, obtenir une lumière réaliste nécessitait de “baker” les éclairages :
autrement dit, faire des calculs à l’avance pour générer des textures de
lumière statiques. Ce processus était long, rigide et peu adapté aux
environnements dynamiques. 
Avec Lumen, tout se fait en temps réel. La lumière réagit
immédiatement : 
tu ouvres une porte → l’éclairage change instantanément ; 
tu déplaces une lampe → les ombres se réajustent ; 
un objet réfléchit la lumière → l’effet est visible immédiatement. 
Lumen rend les scènes plus naturelles, plus vivantes et
surtout beaucoup plus faciles à modifier. Les créateurs gagnent un temps
considérable, puisque le moteur gère automatiquement les rebonds lumineux,
l’illumination globale et les ombres complexes. 

Niagara (Le système de particules avancé) 
Niagara est l’outil utilisé pour créer les effets visuels :
explosions, fumée, feu, neige, magie, nuages, etc. 
C’est un système très flexible où on peut contrôler presque tous les paramètres
d’une particule : sa vitesse, sa couleur, sa forme, sa trajectoire. On peut
même créer des comportements complexes comme un groupe de particules influencé
par la physique. 
Pour les effets spéciaux, c’est l’un des outils les plus puissants du marché. 

Chaos Physics (Le moteur physique d’UE5) 
Chaos est le moteur de physique intégré dans Unreal Engine 5. Il gère : 
les collisions, 
les destructions d’objets, 
les simulations de vêtements, 
les corps rigides, 
la physique des véhicules 
Avec Chaos Destruction, on peut casser des bâtiments ou des
objets de manière réaliste, sans devoir préanimer ou précalculer quoi que ce
soit. C’est parfait pour les jeux d’action, les simulations, ou même les démos
techniques. 

World Partition (Gestion automatique des mondes ouverts) 
Avant UE5, créer un monde ouvert était compliqué, il fallait
diviser la carte en petits morceaux, les charger à la main ou via des scripts. 
Avec World Partition, le moteur coupe automatiquement le monde en sections et
ne charge que ce qui est proche du joueur. 
Ça rend la création d’open worlds : 
plus simple, 
plus rapide, 
plus efficace. 
C’est aussi ce système qui permet à plusieurs développeurs
de travailler en même temps sur la même carte sans se marcher sur les pieds.


## Le pipeline graphique 

Le pipeline graphique d’Unreal Engine, c’est ce qui s’occupe
de transformer toute l’information 3D d’un jeu, donc les modèles, les textures,
les lumières et les matériaux, en une image finale à l’écran. On peut le voir
comme une chaîne de traitement où chaque étape ajoute un morceau au résultat
final. Même si Unreal Engine est très avancé techniquement, on peut résumer son
pipeline de manière assez simple. 

Tout d'abord, il y a l’étape du rendu des géométries. Unreal prend les modèles 3D présents dans la scène et calcule
leur forme visible, leur position dans le monde et leur relation avec la caméra. Avec UE5, cette partie utilise beaucoup Nanite, ce qui permet d’afficher beaucoup de détails sans trop
ralentir le jeu. Ensuite vient l’étape de l’éclairage,
qui joue un rôle majeur dans le réalisme. C’est à ce
moment-là que Lumen intervient. Ce système calcule la lumière en temps réel, gère les réflexions
et les rebonds lumineux, ce qui donne un rendu beaucoup plus naturel sans
devoir préparer les lumières à l’avance. 

Une fois la géométrie et la lumière calculées, Unreal
applique les matériaux. Les matériaux utilisent
un système basé sur le
PBR (Physically-Based Rendering), ce qui veut dire qu’ils se
comportent comme dans la vraie vie. Du métal, du
bois ou du plastique ont tous leurs propres propriétés, et le moteur s'occupe de la façon dont
la lumière réagit sur
ces surfaces. Après ça, le
moteur passe par une étape de postprocessing,
qui ajoute des effets comme le flou de mouvement, la profondeur de champ, les
couleurs, les effets de caméra et même une ambiance plus cinématographique. 

Finalement, toutes ces données sont combinées et envoyées
vers l’écran pour afficher l’image finale. Même si tout ça semble complexe,
Unreal fait la majorité du travail automatiquement. L’avantage, c’est que les
développeurs peuvent se concentrer sur l’apparence du jeu sans devoir
comprendre chaque étape mathématique derrière le rendu.


## Streaming Levels 

Le Streaming
Levels est une technique qu’Unreal Engine utilise pour charger et décharger
des parties d’un niveau pendant que le joueur
avance dans le jeu. Le concept est simple, au lieu de charger une énorme carte en une seule fois (ce qui prend énormément de mémoire et
ralentit le jeu), le moteur ne garde en RAM que les zones nécessaires. Les autres parties du monde restent endormies et se
chargent automatiquement quand le joueur s’en
approche. 

En tant que telle, cela permet de créer des mondes beaucoup
plus grands et détaillés, sans faire exploser les performances. Par exemple, on
peut diviser une grande map en plusieurs petites sections, comme une ville
séparée en quartiers. Quand le joueur marche vers un nouveau quartier, Unreal
charge la zone suivante en arrièreplan, sans écran de chargement. À l’inverse,
les zones trop loin du joueur se déchargent pour libérer de la mémoire. Ce qui
donne un résultat incroyable, car au final, l’environnement est très fluide. 

Avec UE5,
cette façon de travailler est encore plus simple grâce à World
Partition, qui coupe automatiquement le monde en cellules et gère le streaming de façon
intelligente. Avant, il fallait créer plusieurs
niveaux à la main et configurer leur chargement.
Maintenant, Unreal se charge de tout. Cela facilite le travail d’équipe, plusieurs personnes peuvent travailler sur différentes parties d’un même monde sans se déranger. 

En gros, le Streaming Levels est essentiel pour les mondes
ouverts, les jeux d’aventure ou tout projet où la carte est trop grande pour
tenir dans un seul Level, comme les jeux Subnautica et Borderlands. C’est ce
qui permet de créer des environnements vastes, détaillés et immersifs, même
pour des équipes plus petites ou des projets d’étudiants.


## Avantages & limites d’Unreal Engine 

Unreal Engine est un moteur de jeu extrêmement puissant,
mais comme n’importe quel outil, il a ses forces et ses faiblesses. Comprendre
les avantages et les limites nous permet de savoir dans quels types de projets
il est le plus performant, et dans lesquels il est peut‑être moins performant. 

Avantages 
L’un des plus grands avantages d’Unreal Engine, c’est sa
qualité visuelle. En effet, avec Lumen et Nanite, on peut obtenir des
environnements très réalistes sans passer des heures à optimiser chaque détail.
C’est parfait pour des gros projets, autant en jeux vidéo qu’en cinéma ou en
architecture. 

De plus, un autre point fort, c’est la flexibilité du moteur
de jeu. On peut l’utiliser pour créer un jeu de tir, un jeu de course, une
application de formation VR, une cinématique ou même un rendu architectural
interactif. Peu importe le domaine, le moteur offre toujours les outils
nécessaires. 

On peut aussi parler des Blueprints, qui est un énorme
avantage pour les débutants. Même sans connaître un langage de programmation,
on peut créer des mécaniques complètes juste en reliant des blocs logiques.
C’est très intéressant pour un débutant, car ils voient des résultats assez
rapidement. 

Finalement, Unreal Engine bénéficie d’un écosystème énorme,
documentation complète, tutoriels, forums, modèles gratuits, etc. On ne se
retrouve jamais seul face à un problème. Et surtout, le moteur est gratuit tant
qu’on ne dépasse pas un certain revenu, ce qui le rend accessible aux étudiants
et aux petits studios. 

Limites 
Même s’il est puissant, Unreal Engine n’est pas parfait. Une
première limite, c’est qu’il est lourd. Il demande un ordinateur assez
performant pour bien tourner, surtout avec des projets UE5. Les temps de
compilation ou de chargement peuvent être longs si on n’a pas une bonne
machine. 

Il y a aussi la question de la complexité. Unreal propose
énormément d’outils et de technologies, à tel point que ça peut devenir
beaucoup pour les programmeurs qui ne sont pas habitués. Même si les Blueprints
facilitent la prise en main, certains aspects plus avancés comme le Chaos ou
les shaders complexes demandent du temps pour être compris et maitrisés. 

De plus, Unreal Engine peut être surpuissant pour de petits
projets. Si on veut faire un petit jeu 2D, ou un prototype basique qui doit
fonctionner sur n’importe quel appareil, un moteur plus léger comme Godot ou
Unity 2D pourrait être plus adapté. 

Enfin, même si Unreal offre beaucoup de solutions
automatiques, ça peut pousser certains développeurs à trop compter sur les
systèmes inclus. Le moteur permet d’aller très loin, mais pour exploiter tout
son potentiel, il faut quand même apprendre la logique derrière chaque
technologie comme les Blueprints, les matériaux, les niveaux.