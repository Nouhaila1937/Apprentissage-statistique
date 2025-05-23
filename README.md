# Apprentissage-statistique


# 📈 Qu'est-ce que la courbe ROC ?

* La courbe ROC (Receiver Operating Characteristic) est un outil graphique utilisé pour évaluer la performance d'un modèle de classification binaire. Elle trace le taux de vrais positifs (sensibilité) en fonction du taux de faux positifs (1 - spécificité) à différents seuils de classification.

* Chaque point sur la courbe correspond à une paire (taux de faux positifs, taux de vrais positifs) pour un seuil spécifique. En ajustant ce seuil, on obtient différents points, formant ainsi la courbe ROC.
  
* On utilise la matrice de confusion pour tracer ces points et bien sur le ROC et l' AUC sont utilisés pour des algorithme de classification

![image](https://github.com/user-attachments/assets/ca303b4d-2381-45b4-a67a-8560228b6969)


# 📐 Qu'est-ce que l'AUC ?
* L'AUC (Area Under the Curve) représente l'aire sous la courbe ROC. Elle fournit une mesure unique de la capacité du modèle à distinguer entre les classes positives et négatives.
  
* Un AUC  plus élevé indique que le modèle a une meilleure capacité à distinguer entre les classes positives et négatives. Cela signifie que, pour un seuil de classification donné, le modèle est plus susceptible de classer correctement les exemples positifs et négatifs.


# 📊 Interprétation de l'AUC
* AUC = 1.0 : Le modèle classe parfaitement tous les exemples.

* AUC = 0.5 : Le modèle n'a aucune capacité discriminante ; ses prédictions sont équivalentes à un tirage aléatoire.

* AUC < 0.5 : Le modèle classe les exemples de manière incorrecte plus souvent que par hasard.

Ainsi, un AUC plus élevé est généralement souhaitable, car il indique une meilleure performance globale du modèle.


# 🤔 Pourquoi utiliser la courbe ROC et l'AUC ?
* Comparaison de modèles : L'AUC permet de comparer objectivement plusieurs modèles de classification.

* Évaluation indépendante du seuil : Contrairement à d'autres métriques comme la précision ou le rappel, l'AUC évalue la performance du modèle sur l'ensemble des seuils possibles.

* Robustesse face au déséquilibre des classes : La courbe ROC et l'AUC sont particulièrement utiles lorsque les classes sont déséquilibrées, car elles ne sont pas influencées par la distribution des classes.

# Exemple
ROC de SVM est meilleure que ROC de logistic (comparaison avec l'AUC)
![image](https://github.com/user-attachments/assets/0f39de65-df4f-4e0b-b486-58370a69e393)



# 🎯 Comment savoir si le Gini est utile ?
* L’indice de Gini mesure l’impureté :

* Plus il est petit, plus les classes sont pures (bien séparées).

* Ce qui compte, c’est la baisse de l’indice de Gini après la séparation.

# ✅ Séparation utile selon Gini si :
* Gini après split < Gini avant split
* ➡️ Il n’y a pas de valeur seuil fixe.
* ➡️ Même une petite diminution signifie une amélioration, donc la séparation est bénéfique.


# ⚠️ Pourquoi le taux d’erreur peut être trompeur ?
Le taux d’erreur regarde seulement la proportion d’erreurs (éléments mal classés selon la classe majoritaire). Il ne tient pas compte du niveau de mélange entre les classes.

# ❌ Exemple typique :
Deux groupes : l’un très pur, l’autre très mélangé

Le taux d’erreur peut rester identique avant/après

Mais Gini, lui, capte la baisse de mélange









