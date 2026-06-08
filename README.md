# Arène des algorithmes
## Présentation du projet

L'objectif de ce projet est de comparer plusieurs algorithmes de
classification sur différents datasets.

Le but est de déterminer quel algorithme obtient les meilleurs résultats,
tout en tenant compte de ses erreurs et de sa facilité d'utilisation.

## Datasets utilisés

Deux datasets fournis par scikit-learn ont été utilisés :

* **Breast Cancer Wisconsin** : 569 observations, 30 variables et
  2 classes, tumeur maligne ou bénigne ;
* **Wine** : 178 observations, 13 variables et 3 classes.

## Algorithmes comparés

Les trois algorithmes comparés sont :

* la régression logistique ;
* le KNN ;
* l'arbre de décision.

## Classement sur Breast Cancer

| Rang | Algorithme  | Accuracy    |
| ---- | ----------- | ----------- |
| 1    | Régression logistique | 96.49% |
| 2    | KNN         | 91.23%|
| 3    | Arbre de décision | 91.23% |

## Classement sur Wine

| Rang | Algorithme            | Accuracy |
| ---- | --------------------- | -------- |
| 1    | Régression logistique | 94,44 %  |
| 1    | Arbre de décision     | 94,44 %  |
| 3    | KNN                   | 80,56 %  |


## Analyse des erreurs

L'accuracy ne suffit pas pour évaluer un modèle médical. Il faut aussi
regarder les erreurs dans la matrice de confusion.

Pour la régression logistique avant scaling, la matrice de confusion
obtenue est :

|                    | Prédit maligne | Prédit bénigne |
| ------------------ | -------------: | -------------: |
| Réellement maligne |             39 |              3 |
| Réellement bénigne |              1 |             71 |

Le modèle fait donc deux types d'erreurs :

* 3 tumeurs malignes ont été prédites comme bénignes ;
* 1 tumeur bénigne a été prédite comme maligne.

L'erreur la plus grave est de classer une tumeur maligne comme bénigne.
Elle pourrait retarder les examens ou la prise en charge du patient.

Une fausse alerte sur une tumeur bénigne reste problématique, mais elle est
moins grave qu'une tumeur maligne non détectée.

Dans une utilisation réelle, il faudrait donc surveiller particulièrement
le nombre de tumeurs malignes prédites comme bénignes, et pas seulement
l'accuracy globale.

## Champion retenu

Le champion retenu est la **régression logistique avec scaling**.

**Régularité :**
Elle obtient de bons résultats sur les deux datasets, contrairement au KNN
qui baisse fortement sur Wine.

**Vitesse :**
Son entraînement et ses prédictions sont rapides sur ce type de données.

**Explicabilité :**
Son fonctionnement peut être expliqué comme un calcul de probabilité à
partir des différentes variables. L'arbre de décision reste plus visuel,
mais la régression logistique offre ici un meilleur compromis entre
performance et simplicité.


## Fuite de données

Deux méthodes ont été comparées :

* une méthode honnête, avec un scaler ajusté uniquement sur le jeu
  d'entraînement ;
* une méthode incorrecte, avec un scaler ajusté sur tout le dataset avant
  la séparation.

Les deux méthodes ont obtenu une accuracy de 98,2456 %. La différence est
donc de 0 point de pourcentage.

Même si le score est identique dans ce cas, la deuxième méthode reste
incorrecte. Elle utilise des informations provenant du jeu de test avant
l'évaluation.

En pratique, les données de test doivent rester totalement inconnues
jusqu'à l'évaluation finale.

## Conclusion

La régression logistique avec scaling est recommandée car elle présente le
meilleur compromis entre performance, régularité, vitesse et
explicabilité.


