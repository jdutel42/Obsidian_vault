# <mark style="background: #BBFABBA6;">Apprentissage automatique</mark>

- # Contexte
	- ## Objectifs
		- Consiste à inférer des connaissances sur les données
		- Se base sur des échantillons d'apprentissage
		- Si présence d'une cible
			- ==> Apprentissage supervisé
		- Si absence d'une cible
			- ==> Apprentissage non supervisé
	- ## Données initiales
		- Des individus/instances/Objets --> n
		- Des variables/features/descripteurs --> p
		- Des labels
		- ==> ![[Pasted image 20241212183417.png]]
- # Apprentissage supervisé
	- ## Définition
		- Méthode d’apprentissage utilisée pour construire un **classiffieur** (ou modèle ou hypothèse), à partir d’une **base d’exemples étiquetés par des labels**, pour **prédire le label d’un nouvel individu** qui arrive.
	- ## Algorithmes
		- ### Réseaux bayésiens
		- ### Réseau de neurones
		- ### K-plus proches voisins
		- ### Arbres de décision
			- #### Définition & Fonctionnement
				- Processus récursif de division de l’espace des données en sous-régions de plus en plus **pures** en terme de classes.
				- Les tuples sont placés dans la classe associée à la sous-région qu’ils vérifient
				- Différentes approches en fonction de la façon dont l’arbre est construit
			- Décomposition d’un problème de classification en une suite de **tests** (**imbriqués**) portant sur **une variable (parallèle aux axes)** ou **une combinaison linéaire de plusieurs variables (oblique)**.
			- #### Exemple
				- On veut faire un decision tree répondant à l'objectif : **Déterminer si un client consultera son compte par Internet, en fonctions des données que l'on a sur lui**
				- On a un échantillon d'apprentissage : ![[Pasted image 20241212184621.png]]
					- On a 8 individus
					- On a 4 variables (avec différentes valeurs possibles):
						- M --> Moyenne du solde de comptes
						- A --> Age
						- R --> Résidence
						- E --> Niveau d’études
					- On a les labels associés :
						- Oui --> L'individu consulte son compte par Internet
						- Non --> L'individu ne consulte pas son compte par Internet
				- ##### Cinétique
					- ###### Racine de l'arbre
						- Pas de test à faire, nous avons déjà les labels
							- (3,5)
								- 3 Oui
								- 5 Non
					- ###### Premier test
						- On va privilégier les tests qui produisent des **feuilles pures** = Tout les individus sont dans une **même classe** ![[Pasted image 20241212185800.png]]
							- ==> Regarder/Tester la variable R --> Pas de feuilles pures --> Pas discriminatoire et donc pas très intéressant de regarder
							- ==> Regarder/Tester la variable A --> 2/3 des feuilles pures --> C'est plus intéressant (pour les branches jeunes et âgé)
						- Comment mathématiquement coder ça ?
							- Cf Méthodes
				- ##### Méthodes 
					- ###### Entropie
						- Définition
							- Il nous faudrait une méthode qui puisse repérer ces variables et tests intéressants
							- Ce serait donc une fonction qui serait :
								- Minimum (=0) lorsque le nœud est pur
								- Maximum lorsque les individus sont équi-répartis dans les classes
							- ==> **Entropie** = Mesure du désordre
								- ![[Pasted image 20241212191301.png]] 
									- $p$ --> Nombre totale d'individus classé
									- $k$ --> Nombre d'individus classé pour chaque classe
						- Exemple
							- ![[Pasted image 20241212192848.png]]
					- ###### L'indice de Gini
						- Définition
							- On peut adapter la formule de l'entropie pour obtenir **l'indice de Gini**, qui est plus rapide et moins coûteux à calculer
							- ![[Pasted image 20241212191437.png]]
							- Mesure la probabilité qu'une observation choisie au hasard soit mal classée si elle était attribuée à une classe au hasard
						- Interprétation
							- $Gini (p) = 0$ --> Pureté maximale = Toutes les données dans une seule classe
							- $Gini (p) = 0.5$ --> Pour un ensemble binaire, indique une grande incertitude = Les classes sont réparties équitablement
						- ==> On a des méthodes (Entropie et Gini) pour mesurer le désordre mais il faudrait une méthode pour savoir quel test choisir, quelle variables à tester
							- ==> Fonction de gain
					- ###### Fonction de Gain
						- Définition
							- Évaluer l'efficacité d'une division des données en fonction d'une caractéristique et mesure la réduction de l'incertitude (ou de l'impureté) après une division
							- ![[Pasted image 20241212204357.png]]
								- $p$ --> Position (avant la division)
								- $test$ -> Variable que l'on test
								- $P_{j}$ --> Fréquence totale d'individu/d'observation pour un nœud enfant donné de la variable à tester
								- $i(p)$ ou $i(p_{j})$ --> $Entropie(p)$ ou $Gini(p)$ = Entropie ou Gini à la position p (avant la division) = Impureté du nœud parent ($i(p)$), ou nœud enfant ($p_{j}$)
							- ==> Le test à choisir est celui qui possède le plus grand gain
						- Exemple
							- ![[Pasted image 20241212204721.png]]
							- De la même manière :
								- ($Gain(\in, M) =0.266$)
								- $Gain(\in, A) =0.454$
								- $Gain(\in, R) =0.016$
								- $Gain(\in, E) =0.348$
							- ==> Il faut mieux réaliser tester A (le plus grand gain)
				- ##### Algorithme
					- ![[Pasted image 20241212210523.png]]
					- Pseudocode
						- Input: Dataset (D), Liste des caractéristiques (Features), Critère d'impureté (Entropie ou Gini), Profondeur maximale (MaxDepth)
						- Procedure DecisionTree(D, Features, CurrentDepth)
							- Si tous les exemples dans D appartiennent à la même classe :
								- Retourner une feuille avec la classe dominante.
							- Si Features est vide OU CurrentDepth ≥ MaxDepth :
								- Retourner une feuille avec la classe dominante dans D.
							- Calculer l'impureté parentale (ex. Entropie ou Gini) pour D.
							- Pour chaque caractéristique f dans Features :
								- Diviser les données en sous-ensembles basés sur les valeurs possibles de f.
								- Calculer l'impureté pondérée des enfants après la division.
								- Calculer le Gain d'information pour f.
							- Sélectionner la caractéristique (BestFeature) qui donne le Gain d'information maximal.
							- Diviser D en sous-ensembles (Subsets) basés sur BestFeature.
							- Créer un nœud interne pour BestFeature.
							- Pour chaque sous-ensemble (Subset) obtenu :
								- Si Subset est vide :
									- Ajouter une feuille avec la classe dominante de D comme prédiction.
								- Sinon :
									- Ajouter un sous-nœud en appelant récursivement DecisionTree(Subset, Features - {BestFeature}, CurrentDepth + 1).
							- Retourner le nœud construit.
			- #### Évaluation
				- Sur un nouveau jeu de donnée étiqueté, différent du jeu de donnée d'entrainement, on utilise l'algorithme pour prédire les labels -> On réalise la table de confusion et on calcule des métrique :
					- L'accuracy
					- L'erreur
					- Le Rappel(Oui)
					- La Précision(Oui)
					- La F-mesure(Oui)
				- ![[Pasted image 20241212213205.png]]


# <mark style="background: #BBFABBA6;">Méthodes ensemblistes</mark>

- # Définition
	- Méthode qui combine les décisions individuelles de plusieurs hypothèses h1 , . . . , hT pour classer de nouveaux exemples.
		- Un classifieur peut se tromper, un comité de classifieur **indépendant** à moins de chance de se tromper, on a un consensus
	- Il faut cependant que :
		- Les hypothèses construites ont un taux de succès meilleur que l’aléatoire (erreur<0.5 dans le cas de deux classes équilibrées).
		- Les hypothèses présentent une certaine diversité.
- # Types
	- ## Hétérogènes
		- Ensemble d'hypothèse produite par :
			- **Des algorithmes différents ($L_{n}$) sur une même distribution ($D$) des exemples d'apprentissage ($A$)**
			- *Ou...*
			- **Un même algorithme mais avec des paramètres et/ou initialisation différentes**
	- ## Homogènes
		- ### Définition
			- Ensemble d'hypothèse produite par un **même algorithme ($L$)** mais avec **des distributions ($D_{t}$) différentes ( tirages aléatoires, pondérations différentes...) dans la base d'apprentissage**
			- Méthode générale et facilement applicable car basique
		- ### Stratégies
			- #### Boosting
				- ##### Définition
					- Utiliser une stratégie adaptative pour booster des performances, applicable à tout type d’algorithme (Réseau de neurones, CART, etc.)
					- Méthode générale pour convertir des règles de prédiction peu performantes en une règle de prédiction (très) performante
						- Étant donné un algorithme d’apprentissage L “faible” qui peut toujours retourner une hypothèse h de taux d’erreurs $\leq$ 0.5 - $\gamma$ (où $\gamma$ est l’amélioration de h par rapport à une décision aléatoire)
						- Un algorithme de boosting peut construire (de manière prouvée) une règle de décision (hypothèse) de taux d’erreur $\leq$ e
				- ##### Adaboost
					- ###### Définition
						- Adaptative Boosting
						- Algorithme itératif pour l’ajout des classifieurs
						- Variantes de la base d’apprentissage obtenues par des pondérations successives des mêmes exemples (calculées pour «se focaliser» sur les exemples «difficiles»)
						- **On augmente l’importance des exemples mal-classés lors de l’itération précédente**
						- ==> Combine plusieurs modèles faibles (**weak learners**) pour créer un modèle global plus performant (**strong learner**). L'objectif est de corriger les erreurs des modèles faibles successifs afin d'améliorer la précision globale.
					- ###### Exemple
						- Etape 0
							-  ![[Pasted image 20241212221750.png]] 
						- Etape 1
							-  ![[Pasted image 20241212221811.png]]
								- $\epsilon_{1}$ --> Erreur pondéré
								- $\alpha$ --> Performance du modèle 
							- Cinétique
								- Un modèle est construit --> Il classe correctement 70% des données et se trompe sur 30% --> Les erreurs reçoivent des poids plus élevés.
						- Etape 2
							- ![[Pasted image 20241212221906.png]]
							- Cinétique
								- Un nouveau modèle est construit en se concentrant sur les exemples mal classés du premier modèle --> Il corrige certaines erreurs du premier modèle
						- Etape 3
							- ![[Pasted image 20241212221927.png]]
						- Hypothèse finale
							- ![[Pasted image 20241212221956.png]]
							- Cinétique
								- Les 3 modèles sont combinés en tenant compte de leur importance respective ($\alpha_{t}$).
					- ###### Avantages
						-  Performance élevée sur des tâches de classification.
						- Pas de réglage complexe : Seul le nombre d'itérations TT doit être spécifié.
						- Interprétable : Les poids $\alpha_{t}$ ​ montrent l'importance des modèles faibles.
					- ###### Bilan adaboost
						- ==> Utilisé un algorithme de classification (L) qui intègre le poids des individus dans la phase d'apprentissage
							- ==> Par exemple : Arbre de décision, Réseaux de neurones, ...
						- ==> A chaque itération t un nouvel échantillon d’apprentissage est considéré en sélectionnant au hasard avec remise $m$ exemples suivants les poids
				- ##### Bilan Boosting
					- ==> La puissance du boosting vient du ré-échantillonnage adaptatif
					- ==> Réduit la variance
					- ==> Réduit le biais en obligeant l'algorithme à focaliser sur les cas difficiles → hypothèse combinée beaucoup plus flexible
					- ==> Convergence rapide
					- ==> Sensible au bruit : les apprenants de base classent mal les exemples bruités ⇒ poids augmentent ⇒ sur-ajustement au exemples bruités
			- #### Bagging
				- ##### Définition
					- Utiliser l’aléatoire pour améliorer les performances d’algorithmes de « faibles » performances. C’est applicable à différents algorithmes et RF est un aménagement spécifique à CART.
					- Bootstrap aggregation
					- Variantes de la base d’apprentissage obtenues par tirages aléatoires avec remise depuis la base initiale (sorte de «bootstrap»)
						- Un ensemble de données « bootstrap » est un ensemble de données obtenu en sélectionnant au hasard avec remise m observations parmi les m observations de l’ensemble d’entraînement.
						- Certaines observations sont dupliquées tandis que d’autres sont absentes; ce qui introduit une part d’aléatoire.
					- L’intérêt de telle méthode est de répéter la procédure et d’utiliser chaque ensemble de données pour construire un modèle. Nous disposons alors de différentes réalisations de la statistique estimée (ou du modèle).
				- ###### Principe
					- Génération de k échantillons « bootstrap » par tirage avec remise dans l’ensemble d’apprentissage A= {(x1,y1), … ,(xm,ym)}.
					- Pour chaque échantillon, apprentissage d’un classifieur en utilisant le même algorithme d’apprentissage
					- La prédiction finale pour un nouvel exemple est obtenue par vote (simple) des classifieurs
				- ###### Bilan Bagging
					- ==> But
						- Atténuer l'instabilité inhérente à certaines méthode de discrimination
							- Si un changement mineur dans les données provoque un changement assez important de modèle = Méthode de discrimination instable 
					- ==> Utile et efficace si algorithme de base utilisé est instable car différences entre variantes de base --> classifieurs élémentaires très différents
					- ==> Évite l’overfitting (sur-apprentissage), car on a la «moyenne» des classifieurs construits avec différentes réalisations aléatoires des mêmes données.
					- ==> Il est souvent dit que le bagging fonctionne en réduisant la variance en laissant le biais inchangé
			- #### Random Forest
				- ##### Principe
					- Est ce qu’à partir d’un ensemble de faible classifieurs (arbres de décision) ont peut créer un classifieur plus performant?
					- L’union fait-elle la force?
						- La réponse est oui à condition que les arbres sont complémentaires.
					- Le résultat sera donc autant plus intéressant que les arbres sont indépendants et le plus efficaces possible.
					- On va construire un grand nombre d’arbres de décision différents pour un même problème: une forêt (forest).
					- Pour construire une forêt on injecte de l’aléatoire: 
						- On rajoute de l’aléatoire avant ou pendant la construction d’un arbre (Algorithme CART); on construit plusieurs arbres “randomisés”
						- On agrège l’ensemble des arbres obtenus:
							- Pour classer un individu on prend la décision finale par un vote majoritaire
					- Pour rajouter l’aléatoire, RF combine la sélection aléatoire d'instances avec la sélection aléatoire de variables.
						- On lance la construction de l’arbre sur un sous échantillon tiré aléatoirement : Breiman propose d’utiliser le bagging
						- On tire à chaque nœud de l’arbre **mtry** variables uniformément et on cherche la “meilleure” coupure uniquement parmi ces variables-ci.
						- Les arbres de décision sont complets : construits automatiquement sans pre- ou post-élagage.
				- ##### Algorithme
					- ![[Pasted image 20241212230942.png]]
				- ##### Avantages
					- Comme on tire aléatoirement les observations, une partie des observations non tirées (appelées OOB = Out Of Bag) serviront à 
						- Évaluer en interne la forêt
						- Estimer l'importance des variables pour la selections des variables
				- ##### Évaluation
					- Estimation de l'erreur en généralisation
						- ![[Pasted image 20241212231518.png]]
				- ##### Optimisation
					- ![[Pasted image 20241212231553.png]]
					- Le nombre optimal de variables dépend du nombre d'arbre dans la forêt mais globalement le plus optimal est 6 classes de variable
				- ##### Applications
					- ###### Clustering
						- ![[Pasted image 20241212231929.png]]
					- ###### Sélection de variables
						- ![[Pasted image 20241212231946.png]]
					- ###### Gestion des valeurs manquantes
						- ![[Pasted image 20241212232009.png]]
				- ##### Bilan Random Forest
					- ==> Facile en utiliser
					- ==> Sélection d'un sous-ensembles des observations
						- ==> Gain de temps et de calcul
						- ==> Grande diversité des modèles
					- ==> Agrégation des valeurs ou classes prédites pour chaque modèles donne un classifieur robuste et précis






































- # Détection d'anomalies
	- ## Approches
		- Détection d'outliers
			- Apprendre à détecter des anomalies dans le jeu de donnée initial en cherchant des régions denses tout en ignorant les anomalies
		- Détection de nouveauté
			- Ici le jeu de donnée pas pollué par les annomalies
			- Il faut detecter des anomalies dans les données futures non observées
	- ## Méthodes
		- ### Non supervisées
			- Pas de labels fournis
			- Base d'apprentissage = Données normales + anomalies
			- Les anomalies sont très rares
			- #### Types
				- Approches basées sur le voisinages
					- Local Outlier Factor
						- Paramètres
							- $D_k(x)$ = Distance par rapport à son k^{ie} plus proche voisin 
							- $N_k(x)$ = L'ensemble de ses k plus proche voisin
							- $R_k(x,y$ = Distance d’accessibilité de x par rapport à y comme étant le $max(d(x,y) et D_x(y))$
							- $AR_k(x)$ = Distance d'accessibilité moyenne de x comme étant égale à la moyenne des distances d'accessibilité de x avec tous les points de son voisinage ($N_k(x)$)
							- $f_k(x)$ = Densité d'accessibilité = Inverse de $AR_k(x)$
								- Une instance normale est sensée avoir une densité locale similaires à ses voisins, alors q'une instance anormale est sensée avoir une beaucoup plus petite densité locale
							- $LOF(x)$ = Moyenne du rapport $f_k(y)/f_k(x)$ pour tous les y dans $N_k(x)$
								- Mesure l'écart local d'un point par rapport à ses k voisins les plus proches
								- Si ce score est porche de 1, nous pouvons en conclure que l'observation est comparable à ses voisins
								- Si ce score est $< 1$, nous pouvons dire que l'observation se trouve dans une région dense
								- Dans les 2 cas, l'observation n'est pas considérée comme un outlier
								- Un score est largement supérieur à 1 indique qu'on a à faire à un outlier
						-  Utilisée pour la détection de nouveauté ou d'outliers
						- Méthode très puissante
					- One class SVM : Pour la détection de nouveauté
						- Objectifs
					- Isolation forest
						- Principe
							- Les anomalies sont rares et différentes ==> Elles sont donc susceptibles au mécanismes d'isolation
							- Construction d'ensemble d'arbres complement aléatoires : isolation tree
							- Chaque arbres est construit sur échantillon aléatoire des instances
							- Divisions opéré dans chaque nœud via un filtrage aléatoire d'une variable et
								- 1 seul
								- ..........
		- ### Supervisées
			- Labels à la fois pour les instances normales et anomalies
			- Anomalies appartiennent à la classe rare
			- Données déséquilibrées
			- Adaptation des approches supervisées existantes
			- #### Types
				- Random Under-sampling et Random Oversampling
					- Under-sampling
							- Sous échantillonnage
							- On diminue le nombre d'individus pour que les effectifs soient égaux
							- ==> Le classifieur risque d'apprendre dans un espace qui ne reflète pas la réalité ==> Il faut corriger les probabilité
						- Oversampling
							- Sur échantillonnage
							- On va dupliquer aléatoirement certains individus
							- ==> Le classifieur risque d'apprendre dans un espace qui ne reflète pas la réalité ==> Il faut corriger les probabilité
						- Balancing
							- Pondération des classes
							- On va utiliser ici un LogLoss pondéré pour calculer l'erreur de notre classifieur ==> On la veut à 0 ou proche
				- SMOTE (Synthetic Minority Oversampling Technique)
					- Approche d'oversampling
					- Étapes
						- ...........
			- #### Évaluations
				- Accuracy déconseillé
				- Si on est intéressé par la classe en sortie
					- Balanced accuracy
						- Si on veut les classes positives et négatives
					- F 1-score
						- Si on est intéressé par la classe positive
				- Si on est intéressé par les probabilités des classes en sortie
					- AUC-ROC
						- Si on est autant intéressé par les classe + que -
					- AUC-PR (Average Precision Score)
						- Calcul l'aire sous la courbe formée par les points ........
						- Si on est plus intéressé par la classe +
				- ==> Ne pas évaluer les modèles sur un échantillon équilibré
				- ==> Les anomalies sont souvent complètement nouvelle ==> Le modèle ne pourra pas détecter les nouvelles anomalies sur lesquelles il n'a pas été entraîné
---

# ==Fouilles des données textuelles==
- # Introduction
	- Processus d'extraction non triviale d'info utiles inconnues a priori à partir de grands volumes de textes
- # Préparation des données
	- ## Pré-traitement des données textuelles
		- Uniformisation du codage, élimination éventuelle de ceraines caractèe spéciaux
	- ## Extraction d'informations
		- Suppression des mot ignorés
	- ## Extraction d'entités primaires
	- ## Étiquetage grammaticale
	- ## Extraction d'entités nommées
		- Nom de personnes, lieux, organisation, dates qui ont un role important 
- # Exploitation
	- ## Représentation vectorielle des textes
		- Elle prend les mot qui apparaisse le plus dans me texte mais ne prend pas en compte le contexte la grammaire et syntaxe ==> On perds beaucoup d'info
		- Comparaison des vecteurs avec la distance cosinus :
			- Le norme du vecteur étant proportionnelle à la longueur du texte
		- On utilise parfois la similarité cosinus
		- .......
		- Évolutions de la représentation vectorielle de base
			- Pondération des termes : TF-IDF
				- Pondération les termes selon leur importance déterminé dans le texte
				- On utilise le TF (Term Frequency) dans le document
				- On multiplie le TD par IDF (Inverse Document Frequency) 
					- C'est l'importance d'un terme pour tous les documents ..........
					- Concept du LSA (=Latent Semantic Analysis)
						- ........
			- Sélection des termes : 
			- 
	- ## Développement de modèles
	- ## Utilisation des modèles
- # Challenges
	- ## Résolution référentielle
	- ## Analyse syntaxique (générale ou spécifique)