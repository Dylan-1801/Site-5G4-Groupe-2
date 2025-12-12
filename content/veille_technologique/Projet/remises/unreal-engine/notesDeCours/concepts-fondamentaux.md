---
title: "Concepts fondamentaux"
weight: 40
icon: book
---

- Pour comprendre comment fonctionne un projet d’Unreal Engine, il faut d’abord connaître ses concepts de base. Tout commence avec le Level, qui représente simplement un niveau ou une scène dans le jeu, c’est l’endroit où on place les objets, les lumières, le décor et où se déroule l’action. Ces objets placés dans un niveau sont appelés des Actors. Ce terme englobe tout, qu’il s’agit d’un cube, d’un personnage, d’une porte, d’une lumière ou d’un ennemi. Chaque Actor est composé d’éléments plus petits qu’on appelle des Components, qui lui donnent ses fonctionnalités. Par exemple, un mesh 3D (ensemble de lignes et de points qui forment un objet 3D), une collision (sert à détecter les contacts entre objets), une lumière ou un son sont chacun des Components qu’on assemble pour définir ce qu’un Actor peut faire ou comment il se comporte.

- Pour tout ce qui est contrôlable dans le jeu, Unreal utilise deux classes principales : le Pawn et le Character. Le Pawn est l’objet générique qu’on peut contrôler, comme un robot, un véhicule ou même une caméra mobile. Le Character est une version plus avancée du Pawn, pensée spécialement pour les personnages humains. Il inclut déjà un système de mouvement, des collisions adaptées et un squelette pour les animations. Pour que ces entités puissent être contrôlées, Unreal utilise des Controllers. Le PlayerController reçoit les inputs du joueur, tandis qu’un AIController sert à gérer le comportement d’ennemis contrôlés par l’intelligence artificielle.

- Ces éléments fonctionnent ensemble grâce au Gameplay Framework, qui organise la logique du jeu. Le GameMode définit les règles de la partie : quel personnage est contrôlé, comment le niveau se déroule, ce qui se passe à la mort du joueur, etc. Le GameInstance, quant à lui, sert à stocker des informations qui doivent rester accessibles même lorsqu’on change de niveau, comme un score total, un inventaire global ou des paramètres du joueur.

- Finalement, Unreal Engine doit une grande partie de sa popularité aux Blueprints, qui est son système de programmation visuelle. Grâce à une interface en nœuds, qui s’assemblent comme un diagramme, on peut créer des interactions, des comportements, des animations ou des mécaniques complètes sans écrire une seule ligne de code. C’est un outil qui rend le moteur beaucoup plus accessible pour les débutants tout en étant suffisamment puissant pour être utilisé dans des jeux très avancés.
