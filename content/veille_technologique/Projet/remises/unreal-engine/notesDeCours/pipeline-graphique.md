---
title: "Pipeline graphique"
weight: 60
icon: palette
---

#### Étapes principales :

1. Rendu des géométries (Nanite)  
2. Calcul de l’éclairage (Lumen)  
3. Application des matériaux (PBR)  
4. Postprocessing  
5. Image finale affichée à l’écran

- Le pipeline graphique d’Unreal Engine, c’est ce qui s’occupe de transformer toute l’information 3D d’un jeu (les modèles, les textures, les lumières, les matériaux, etc.) en une image finale à l’écran. On peut le voir comme une chaîne de traitement où chaque étape ajoute un morceau du rendu final. Même si Unreal Engine est très avancé techniquement, on peut résumer son pipeline de manière assez simple. 

- Tout d'abord, il y a l’étape du rendu des géométries : Unreal prend les modèles 3D présents dans la scène et calcule leur forme visible, leur position dans le monde et leur relation avec la caméra. Avec UE5, cette partie utilise beaucoup Nanite, ce qui permet d’afficher énormément de détails sans trop ralentir le jeu. Ensuite vient l’étape de l’éclairage, qui joue un rôle majeur dans le réalisme. C’est là que Lumen intervient : ce système calcule la lumière en temps réel, gère les réflexions et les rebonds lumineux, ce qui donne un rendu très naturel sans devoir préparer les lumières à l’avance. 

- Une fois la géométrie et la lumière calculées, Unreal applique les matériaux. Les matériaux utilisent un système basé sur le PBR (Physically-Based Rendering), ce qui veut dire qu’ils se comportent comme dans la vraie vie : un métal, un bois ou un plastique ont tous leurs propres propriétés, et le moteur s'occupe de la façon dont la lumière réagit sur ces surfaces. Après ça, le moteur passe par une étape de postprocessing, qui ajoute des effets comme le flou de mouvement, la profondeur de champ, les couleurs, les effets de caméra ou même une ambiance plus cinématographique. 

- Finalement, toutes ces données sont combinées et envoyées vers l’écran pour afficher l’image finale. Même si tout ça semble complexe, Unreal fait la majorité du travail automatiquement. L’avantage, c’est que les développeurs peuvent se concentrer sur l’apparence du jeu sans devoir comprendre chaque étape mathématique derrière le rendu. Résultat : on obtient des visuels très réalistes, même dans des projets faits par de petites équipes ou des étudiants. 


