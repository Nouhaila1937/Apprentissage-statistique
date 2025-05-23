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


# 🧠 Critères de séparation en arbre de décision
## ✅ 1. Indice de Gini
Formule : ![image](https://github.com/user-attachments/assets/0ac6519e-5b84-468d-8f95-2e874b57e335)

Valeurs :

- Gini = 0 : ensemble pur (une seule classe)

- Gini ≈ 1 : classes très mélangées

## ❌ 2. Taux d'erreur
Formule :
![image](https://github.com/user-attachments/assets/4109c632-c32e-40f9-8e25-7c9283978b2f)

- Taux d’erreur est la proportion de la classe majoritaire.

- Limite : ne détecte pas les mélanges subtils entre classes.

- Séparation utile si :
Erreur_apres_split < Erreur_avant_split

## 🔥 3. Entropie (Shannon)
- Formule :
![image](https://github.com/user-attachments/assets/209f4fa2-ddbf-4b96-82e9-0e59e5ca0dc9)
- Valeurs :

Entropie = 0 : ensemble pur

Entropie max = log₂(C) si les classes sont équilibrées

Séparation utile si :
Entropie apres split<Entropie avant split
## 📈 4. Gain d'information
Formule :
Gain=Impurete avant split−Impurete apres split


Peut être appliqué avec :
- Gini → Gain de Gini
- Entropie → Information Gain

➡️ Plus le **gain est élevé**, meilleure est la séparation.

---

## ✅ Règles générales à retenir

| Critère        | Formule                        | Bonne séparation ?         |
|----------------|--------------------------------|----------------------------|
| Gini           | `1 - ∑ pᵢ²`                     | Gini_après < Gini_avant    |
| Entropie       | `- ∑ pᵢ * log₂(pᵢ)`             | Entropie_après < Entropie_avant |
| Taux d’erreur  | `1 - max(pᵢ)`                   | Erreur_après < Erreur_avant|
| Gain           | `Impureté_avant - Impureté_après` | Plus il est élevé, mieux c'est |

---

# 🎯 À retenir sur Gini et taux d’erreur

## ✅ Gini
- Mesure l’impureté.
- Plus il est **faible**, plus le nœud est **pur**.
- Une **petite baisse** de Gini = **split bénéfique**.

## ❌ Taux d’erreur
- Ignore les mélanges subtils.
- Peut être **trompeur** : un nœud très mélangé peut avoir le même taux d’erreur qu’un nœud presque pur.

---

## 📝 Exemple typique
- Groupe 1 : 100% classe A → erreur = 0
- Groupe 2 : 51% classe A, 49% classe B → erreur = 0.49  
→ Le taux d’erreur ne capte **pas** le niveau de mélange, mais **Gini, oui**.

---



# 🎯 Comment savoir si le Gini est utile ?
* L’indice de Gini mesure l’impureté :

* Plus il est petit, plus les classes sont pures (bien séparées).

* Ce qui compte, c’est la baisse de l’indice de Gini après la séparation.

# ✅ Séparation utile selon Gini si :
* Gini après split < Gini avant split
* ➡️ Il n’y a pas de valeur seuil fixe.
* ➡️ Même une petite diminution signifie une amélioration, donc la séparation est bénéfique.


# ⚠️ Pourquoi le taux d’erreur peut être trompeur ?
* Le taux d’erreur regarde seulement la proportion d’erreurs (éléments mal classés selon la classe majoritaire). Il ne tient pas compte du niveau de mélange entre les classes.

# ❌ Exemple typique :
* Deux groupes : l’un très pur, l’autre très mélangé

* Le taux d’erreur peut rester identique avant/après

* Mais Gini, lui, capte la baisse de mélange










