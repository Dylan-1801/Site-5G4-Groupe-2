---
title: "Streaming Levels"
weight: 70
icon: map
---


- Le Streaming Levels est une technique qu’Unreal Engine utilise pour charger et décharger des parties d’un niveau pendant que le joueur avance dans le jeu. L’idée est simple : au lieu de charger une énorme carte en une seule fois (ce qui prend énormément de mémoire et ralentit le jeu), le moteur ne garde en RAM que les zones nécessaires. Les autres parties du monde restent “endormies” et se chargent automatiquement quand le joueur s’en approche. 

- Dans la pratique, cela permet de créer des mondes beaucoup plus grands et détaillés, sans faire exploser les performances. Par exemple, on peut diviser une grande map en plusieurs petites sections, comme une ville séparée en quartiers. Quand le joueur marche vers un nouveau quartier, Unreal charge la zone suivante en arrière-plan, sans écran de chargement. À l’inverse, les zones trop loin du joueur se déchargent pour libérer de la mémoire. Le résultat est une expérience fluide, où tout semble connecté. 

- Avec UE5, cette façon de travailler est encore plus simple grâce à World Partition, qui coupe automatiquement le monde en cellules et gère le streaming de façon intelligente. Avant, il fallait créer plusieurs niveaux à la main et configurer leur chargement. Maintenant, Unreal se charge de presque tout. Cela facilite le travail d’équipe : plusieurs personnes peuvent travailler sur différentes parties d’un même monde sans se gêner. 

- En gros, le Streaming Levels est essentiel pour les mondes ouverts, les jeux d’aventure ou tout projet où la carte est trop grande pour tenir dans un seul Level. C’est ce qui permet de créer des environnements vastes, détaillés et immersifs, même pour des équipes plus petites ou des projets étudiants. 
