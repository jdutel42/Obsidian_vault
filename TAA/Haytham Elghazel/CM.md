# <mark style="background: #FFB8EBA6;">Apprentissage automatique</mark>

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
				- Décomposition d’un problème de classification en une suite de **tests** (**imbriqués**) portant sur **une variable (parallèle aux axes)** ou **une combinaison linéaire de plusieurs variables (oblique)**.
				- Les tuples sont placés dans la classe associée à la sous-région qu’ils vérifient
				- Différentes approches en fonction de la façon dont l’arbre est construit
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
							- ==> Regarder la variable R --> Pas de feuilles pures --> Pas discriminatoire et donc pas très intéressant de regarder
							- ==> Regarder la variables A --> 2/3 des feuilles pures --> C'est plus intéressant (pour les branches jeunes et âgé)
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