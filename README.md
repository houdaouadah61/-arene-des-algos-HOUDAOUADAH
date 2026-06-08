# Arène des algorithmes

## Présentation du projet

L'objectif de ce projet est de construire un pipeline complet de
Machine Learning et de comparer plusieurs algorithmes de classification.

Les étapes réalisées sont :

* charger et explorer les données ;
* séparer les données en jeu d'entraînement et jeu de test ;
* entraîner plusieurs modèles ;
* comparer leurs accuracies ;
* tester un clustering non supervisé ;
* afficher les résultats avec des graphiques ;
* étudier l'effet du scaling ;
* observer le risque de fuite de données.

## Datasets utilisés

Deux datasets fournis par scikit-learn ont été utilisés.

### Breast Cancer Wisconsin

Ce dataset contient :

* 569 observations ;
* 30 variables ;
* 2 classes : tumeur maligne ou tumeur bénigne.

### Wine

Ce dataset contient :

* 178 observations ;
* 13 variables ;
* 3 classes.

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

## Effet du scaling

La mise à l'échelle améliore surtout les algorithmes qui sont sensibles
aux distances entre les observations, comme le KNN.

La régression logistique peut également mieux converger lorsque les
variables sont mises à la même échelle.

L'arbre de décision est peu influencé par le scaling.

## Fuite de données

Dans la version honnête, le scaler est ajusté uniquement sur les données
d'entraînement.

Dans la version avec fuite de données, le scaler est ajusté sur tout le
dataset avant la séparation entre train et test.

Les deux versions ont obtenu une accuracy de 98,2456 %. La différence est
donc de 0 %.

Même si le résultat est identique dans ce cas, la méthode avec fuite reste
incorrecte, car les données de test ont influencé la préparation des
données.

## Champion retenu

Le modèle retenu est : Régression logistique .

Il a été choisi en tenant compte de son accuracy, mais aussi de sa vitesse,
de son fonctionnement et du type d'erreurs qu'il réalise.

Sur le dataset Breast Cancer, il est particulièrement important d'éviter
de prédire qu'une tumeur maligne est bénigne, car cela pourrait retarder
la prise en charge du patient.

## Conclusion

Ce projet montre qu'un algorithme n'est pas forcément le meilleur sur tous
les datasets.

L'accuracy est utile pour comparer les modèles, mais elle ne suffit pas
toujours. La matrice de confusion permet de mieux comprendre les erreurs
réalisées par le modèle.




