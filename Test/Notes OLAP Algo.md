
On considère le cube suivant :

![[Pasted image 20241030155654.png]]

2^d avec d = dimensions de l’algorithme

Hypothèses: même coût et même proba d'accéder au tuples dans la BDD

A correspond à la table de base, sans rien de calculé, aucune vue pré-calculé, le but de l'algo est de trouvé les vue (les requêtes SQL à pré-calculé) qui auront le plus de bénéfice, les plus pertinentes qui fourniront n'importe quelles réponse à une requête SQL demandé par les utilisateur sans forcément recalculé dans la BDD → Les calculs coûtent plus chères que la lecture !!! D'où l’intérêt de stocker en mémoire certaines requêtes, les matérialiser, (celles qui ont le meilleures rendement globalement)

Mais pour savoir entre la vue B et la C laquelle est la meilleur ils faut calculer les bénéfices de chacunes des vues


![[Pasted image 20241030160554.png]]

Avec la vue B, on peut accéder à la vue B (elle-même), D, E, G et H.
![[Pasted image 20241030160612.png]]


S = {a}

| Vues |     |
| ---- | --- |
| b    |     |
| c    |     |
| d    |     |
| e    |     |
| f    |     |
| g    |     |
| h    |     |









```

```
