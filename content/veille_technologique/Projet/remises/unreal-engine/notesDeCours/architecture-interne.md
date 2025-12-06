---
title: "Architecture interne"
weight: 30
icon: layers
---


## 3.1 L’Editor

- L’Editor est l’endroit où tout se passe dans Unreal Engine. C’est l’interface principale dans laquelle on construit les niveaux, on crée les matériaux, on assemble les animations, on écrit des Blueprints, et même où l’on gère les collisions ou les interfaces utilisateur. C’est un environnement complet qui regroupe plusieurs outils dans une seule application, ce qui en fait le cœur du développement sous Unreal.

- L’Editor est organisé en plusieurs sections essentielles : 

    - Viewport : la fenêtre 3D principale où l’on voit la scène et où l’on manipule les objets directement.

    - Content Browser : la bibliothèque du projet. On y retrouve tous les assets : modèles 3D, textures, sons, animations, Blueprints, etc.

    - Details Panel : l’endroit où s’affichent les propriétés de l’objet sélectionné (taille, matériaux, collisions, composants, comportements, etc).

    - Éditeurs spécialisés : Material Editor pour créer des matériaux visuels complexes, Blueprint Editor pour la logique de jeu, Niagara pour les effets de particules, Animation Blueprint pour gérer les animations, etc.

L’Editor est pensé pour être très visuel : beaucoup d’actions se font en glissant-déposant des éléments ou en ajustant des paramètres. Cette approche réduit la quantité de code à écrire et permet de prototyper rapidement, ce qui rend Unreal à la fois puissant et accessible, même pour ceux qui ne maîtrisent pas encore parfaitement le C++.

## 3.2 Gameplay Framework

Le Gameplay Framework est la structure qui organise la logique du jeu. C’est une sorte de squelette conceptuel qui fournit des classes déjà prêtes pour gérer les éléments essentiels du gameplay. Grâce à lui, on n’a pas besoin de réinventer à chaque fois la gestion des joueurs, des règles ou des interactions.

- Principales classes du Framework : 

    - GameMode : définit les règles générales du jeu (quel personnage le joueur contrôle, ce qui se passe au début d’une partie, comment la victoire est déterminée, etc.). 

    - GameState : garde en mémoire l’état global du jeu (scores, phases de jeu, minuteurs). Cette classe est particulièrement utilisée en multijoueur. 

    - PlayerController : interprète les inputs du joueur et contrôle les actions dans le monde. 

    - Pawn / Character : les entités contrôlables dans le monde. Pawn : version simple, sans animations. Character : version plus complète, avec squelette, animations et déplacements avancés. 

    - PlayerState : regroupe les informations propres à chaque joueur (nom, équipe, score individuel). 

    - HUD / UI : gère ce qui apparaît à l’écran : barres de vie, inventaire, menus, etc., via UMG et les Widgets.


Pourquoi cette structure est-elle importante ? Parce qu’elle sépare clairement les responsabilités : Le GameMode gère les règles, Le PlayerController gère les inputs, Le PlayerState gère les données du joueur, Le Character représente le personnage dans le monde.

Cette organisation évite d’accumuler toutes les fonctions dans une seule classe et permet de construire des jeux beaucoup plus propres et plus modulaires. C’est une des raisons pour lesquelles Unreal est très apprécié par les studios professionnels : le moteur encourage naturellement des projets bien structurés, capables de s’adapter à des jeux de grande ampleur.
