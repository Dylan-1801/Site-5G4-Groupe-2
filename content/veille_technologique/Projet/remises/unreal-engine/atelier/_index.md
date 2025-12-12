---
title: "Atelier"
icon: rocket
weight: 1
chapter: true
---

# Création d’un jeu avec Unreal Engine (en C++)

Dans cet atelier, nous allons créer **deux jeux simples dans Unreal Engine 5** en utilisant **C++** :

1. **Le jeu de ramassage de pièces (Coin Game)**  
2. **Le jeu de tir sur cible (Target Game)**  

L’objectif était de comprendre :  
- la création de classes C++,  
- l’héritage depuis `Actor` et `Character`,  
- le système de composants (mesh, collision, mouvement),  
- la gestion des collisions,  
- la construction d’un niveau jouable.

---

# 1. Jeu de ramassage de pièces (Coin Game)

Le but du jeu : **ramasser une pièce lorsque le joueur la touche**.

## Étapes :

### 1. Création du projet C++
Création d’un projet Unreal → *Games → Blank → C++*.

### 2. Classe `Coin`
Ajout d’une classe dérivée d’`Actor`.

Dans le constructeur :  
- ajout d’un mesh (pièce),  
- ajout d’un composant de collision,  
- activation de l’événement de collision.

### 2. Mettre le mech pour la pièce
Dans la scène:
- Ajout de l'objet créé.
- Donnez a l'objet un mech.

### 3. Démarrer le jeu 
Résultat attendu:

----

#  2. Jeu de tir sur cible (Target Game)

Le but du jeu : **tirer un projectile qui touche une cible**.

## Étapes :

### 1. Classe `TargetActor`
Création d’une classe dérivée d’`Actor`.

Dans le constructeur :  
- ajout d’un mesh représentant la cible,  
- ajout d’un composant de collision,  
- activation de l’événement de détection d’impact.

### 2. Classes du personnage:
Dans les classes du personnage :
- ajout d'une fonction pour tirer.
- ajout d'input pour que le joueur puisse tirer.

### 3. Mettre le mech pour l'objet
Dans la scène:
- Ajout de l'objet créé.
- Donnez a l'objet un mech.

### 4. Démarrer le jeu 
Résultat attendu:
<img src="/images/res-final.png" width="400">

{{< children sort="weight" >}}