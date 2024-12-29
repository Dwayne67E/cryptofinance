# Exercice 1 : Un mineur temporairement byzantin

## Problème
Un mineur dispose d'un **fork privé** contenant \( a \) blocs d'avance par rapport à la blockchain officielle. Cependant, la blockchain officielle a ajouté \( h \) blocs depuis cette divergence. En fonction de sa puissance relative de hachage \( q \), quelle est la meilleure action à prendre pour maximiser ses gains ?  
Deux options s'offrent au mineur à chaque instant :

1. **Continuer à miner sur son fork privé.**  
   L'objectif est de surpasser la blockchain officielle avant d'être dépassé irrémédiablement.

2. **Abandonner le fork privé et revenir miner sur la blockchain officielle.**  
   Cela signifie miner honnêtement ou publier le fork pour obtenir un gain immédiat (si \( a > 0 \)).

Le mineur redevient honnête à tout jamais une fois qu'il retourne miner sur la blockchain officielle.

## Analyse

### Condition pour continuer sur le fork
Pour que le mineur ait intérêt à continuer, la probabilité qu'il rattrape ou maintienne son avantage doit être suffisante. Cette probabilité dépend de \( q \), sa puissance de hachage relative.

- Si \( q \) est élevé (proche de 1), le mineur a une forte probabilité de surpasser la blockchain officielle et devrait persister.
- Si \( q \) est faible, les chances de succès deviennent trop faibles pour justifier de continuer.

### Calcul pour \( a = 1 \) et \( h = 2 \)
Pour cette situation, le mineur doit obtenir **2 blocs consécutifs** avant que la blockchain officielle ne mine un autre bloc. La probabilité de succès est :
\[
P_{\text{succès}} = q^2
\]
Le mineur doit continuer si \( P_{\text{succès}} \) est supérieur à la probabilité de succès de la blockchain officielle, soit \( 1 - q \). Cela donne :
\[
q^2 > 1 - q
\]
Simplifions cette équation :
\[
q^2 + q - 1 = 0
\]
En résolvant cette équation quadratique :
\[
q = \frac{-1 + \sqrt{5}}{2} \approx 0.618
\]

### Tableau des résultats
Voici un tableau des meilleures actions en fonction des paramètres \( a \), \( h \), et \( q \) :

| \( a \) | \( h \) | Seuil \( q \) pour continuer | Action si \( q < \text{seuil} \) | Action si \( q \geq \text{seuil} \) |
|--------|---------|------------------------------|----------------------------------|-------------------------------------|
| 1      | 2       | \( \approx 0.618 \)          | Revenir sur la blockchain        | Continuer sur le fork               |
| 1      | 1       | \( 0.5 \)                    | Revenir sur la blockchain        | Continuer sur le fork               |
| 2      | 2       | \( \approx 0.723 \)          | Revenir sur la blockchain        | Continuer sur le fork               |
| 2      | 1       | \( 0.618 \)                  | Revenir sur la blockchain        | Continuer sur le fork               |

## Conclusion
Pour \( a = 1 \) et \( h = 2 \), le mineur a intérêt à **continuer sur son fork** si \( q \geq 0.618 \).  
En revanche, si \( q < 0.618 \), il est préférable de revenir miner sur la blockchain officielle.

Cette analyse peut être étendue à d'autres valeurs de \( a \) et \( h \) en suivant une démarche similaire.
