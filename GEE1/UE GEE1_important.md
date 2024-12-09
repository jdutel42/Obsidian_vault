- [[#red]]==**Marie Fablet = Génétique des Populations**==
	- **[[#green]]==CM==**
		- # Introduction et rappels
			- Mesurer la différenciation entre population ==> Indice F de Wright
			- ## L'équilibre de Hardy Weinberg
				- Freq allélique constantes au cours des générations
				- Freq génotypiques constantes au cours des générations
				- Freq génotypiques données par le développement de
				  $$\sum((p_i)²)$$
			- ## Population de Wright-Fisher
				- Population d'organismes diploïdes
				- | Mâle / Femelle | A (p) | a (q) |
				  |---|---|---|
				  | A (p) | AA (p² + lambda) | aA (qp - lambda) |
				  | a (q) | Aa (pq + lambda) | aa (q² + lambda) |
		- # Indices F de Wright
		- # Applications de F_{st}
		- # Méthodes d'estimation de F_{st}
		- # Variantes de F_{st}
		- # AMOVA
		- # Illustration : structure des populations humaines
		- # Conclusions
		- # Logiciel STRUCTURE
	- **[[#green]]==TP==**
		- Structure des fichiers
			- 3 colonnes
				- Indiv
					- Identifiant de l'individu
				- Pop
					- Id de la pop
				- Allele
					- Info génétique
			- Chaque ligne
				- 1 allèle = 1 haplotype
				- ==> Pour indiv diploïdes ==> 2 lignes
		- Pour chaque individus on a 2 allèles et pour chaque pop, on a le même nombre d'indiv
			- C'est un plan complet équilibré
				- Il y a 6 pop
				- Il y a 100 individus par pop = 600 au total
			- Le plan de l'expérience est hiérarchique
				- La modalité d'un individu dépend d'une population
		- ![image.png](../assets/image_1732886381923_0.png)
			- On va estimer les \sigma²
			- ![image.png](../assets/image_1732886428256_0.png)
			- Pour le modèle 1
				- Un F_{is} \ne 0 ==> Panmixie = Appariement aléatoire = Proportion de Hardy Weinberg respecté
					- Positif = Excès d'appariement entre apparenté
					- Négatif = Évitement d'appariement entre apparenté
				- F_{st} faible ==> Pas beaucoup de différenciation entre population, les fréquences alléliques sont comparables ==> Il y a beaucoup de flux de gènes entre les population
					- Toujours positive
				- F_{it} intègre les 2 autres valeurs, on regarde au globale l'écart, c'est une synthèse globale, difficile à interpréter, il faut regarder le détail des 2 autres valeurs (fis et fst)
			- Pour le modèle 2
				- Il y a un écart globale car fit grand
				- On reagrde le fis ==> Il est très faible (donc panmixie) et donc tout l'écart est du à ce qui est detecté par le fst
				- Il y a une différenciation significative entre les population ==> Peu de flux de gène ==> Colle bien avec les données de l'énoncé (Population qui dispèrse peu)
			- Pour le modèle 3
				- fit grand ==> Très grand écart dans le cadre de Hardy Weinberg on regarde les autres valeurs
				- fst faible ==> Pas de différenciation entre les pop, beaucoup de flux de gène
				- fis grand ==> Pas de panmixie ==>  beaucoup d'appariement entre apparenté
			- ==> Savoir la méthode cochérame, carré moyen à la variance, anova et obtenir les fit, fis, et fst
			- ==> Savoir interpréter biologiquement les fis, fst et fit
		- Partie 2
			- Localité dans les pays
				- ```r
				  summary(as.factor(world$Population))
				  ```
			- ==> Une région contient des géographie qui contiennent des Pop qui contiennent des Individus (diploides)
			- ```r
			  world[1:5,1:8]
			  ```
				- Dans les colonnes on a l'ID de l'individus, l'id de sa pop, l'id de sa région, pays puis on a des locus de microsatellites
					- Par exemple le premiers individus (2 premieres ligne car diploides) est homozygote pour le 1er locus contrairement au 2e individu (les 2 lignes suivantes)
			- ```r
			  par(mfrow=c(1,2))
			  barplot(table(world[,6]))
			  barplot(table(world[,7]))
			  ```
				- Colonne 6 c'est le premier locus
				- ![image.png](../assets/image_1732891581376_0.png)
				- C'est différent de tout à l'heure car là on a beaucoup d'allele sur chaque locus (les microsatellites ont beaucoup ++++++ d'allele) ==> Le taux de mutation \mu est très élevé et le StepWise mutation ne permet pas de remplir les conditions de Wright, on ne peut pas utiliser le Fst ==> On va utiliser le $\phi_{st}$ (marche tout le temps) qu'on obtient avec une AMOVA ou le R_{st}
					- Le stepwise mutation (mutation pas à pas, une mutation peu donner un allèle déja présent dans la pop) \ne Infinite Allele Mutation model (chaque mutation crée un nouvel Allèle)
			- ```r
			  > 1 - sum(p^2) # C'est Hs sur le premier locus
			  [1] 0.737893
			  ```
				- Hs pour le 1er locus élevé : On est très loin de 0.5, on a donc une richesse allélique très importante pour ce locus
			- Pour tous les locus
				- ![image.png](../assets/image_1732892312333_0.png){:height 529, :width 352}
				- La majorité des loci sont alléliquement très riches
			- Analyse génétique
				- Estimations de F_{stats}
					- ```r
					  > varcomp.glob(levels=worldhier[,1],worldhier[,2:21])
					  $loc
					             [,1]         [,2]      [,3]
					  L001 0.03903386  0.008431775 0.6833494
					  L002 0.10210476  0.008244380 0.7299703
					  L003 0.06337676  0.015744569 0.6497065
					  L004 0.03897771  0.015318130 0.7193516
					  L005 0.05724723  0.006792821 0.7391723
					  L006 0.05803208  0.017274099 0.7065112
					  L007 0.06024469  0.031239391 0.7230769
					  L008 0.05846190 -0.001441341 0.7737512
					  L009 0.05880232  0.020250162 0.6519959
					  L010 0.06981468 -0.003662529 0.5964567
					  L011 0.07999939  0.020621969 0.6485437
					  L012 0.05105740 -0.007879860 0.6267465
					  L013 0.07546957  0.029338969 0.6314721
					  L014 0.08869929 -0.011128343 0.7046371
					  L015 0.04946170  0.024913778 0.6963761
					  L016 0.07110087  0.015768962 0.7150259
					  L017 0.05387471  0.012374498 0.8163694
					  L018 0.05437052  0.015984216 0.6781377
					  L019 0.07602660  0.030398289 0.6257796
					  L020 0.03471916 -0.017018425 0.5958084
					  
					  $overall
					         Pop        Ind      Error 
					   1.2408752  0.2315655 13.7122383 
					  
					  $F
					              Pop        Ind
					  Total 0.0817189 0.09696884
					  Pop   0.0000000 0.01660705
					  ```
						- $overall
							- C'est les Variances (sigma²) comme tout à l'heure
						- $loc
							- Variance par locus
						- $F
							- F_{is} = 0.016
							- F_{st} = 0.08
							- F_{it} = 0.09
								- F_{is} \ne 0 ==> En moyenne, il y a de la panmixie
								- F_{st} à comparer avec le graphique dessous pour faire un test savoir si c'est significativement différent de 0
					- ![image.png](../assets/image_1732893401343_0.png)
					- ```r
					  > testFst$g.star[100]
					  [1] 15460.43
					  > testFst$p.val
					  [1] 0.01
					  ```
						- On voit que la valeur calculé sur les vraie donné sont pas en accord avec la distribution sous H0 ci-dessus + la p-value nous montre que c'est significatifement \ne 0 ==> Différenciation significative
				- Isolement par la distance
					- On utilise le F_{st} comme métrique de distance génétique
					- ![image.png](../assets/image_1732893669800_0.png)
						- Il semble y avoir une corrélation positive, plus les pop sont éloigné géographiquement, moins les flux de gène sont important et donc plus elles sont différentes génétiquement = Isolement par la distance
						- Le problème avec ce graphe c'est que les point ne sont pas indépendant entre eux, on utilise donc le test de Mantel (principe du test de permutation, on mélange les lignes et colonnes, on détruit les potentielles corrélations on calcul la distribution sous l'hypothèse nulle et on compare avec ce que l'on a pour nos vraie données)
					- ```r
					  > ibd = mantel.randtest(distGenet, distGeo, nrepet=1000)
					  > ibd
					  Monte-Carlo test
					  Call: mantel.randtest(m1 = distGenet, m2 = distGeo, nrepet = 1000)
					  
					  Observation: 0.8029049 
					  
					  Based on 1000 replicates
					  Simulated p-value: 0.000999001 
					  Alternative hypothesis: greater 
					  
					      Std.Obs Expectation    Variance 
					  8.095112487 0.002213304 0.009783285 
					  ```
					- ![image.png](../assets/image_1732894073424_0.png)
					- La valeur de test est clairement en dehors de la distribution + p-value très faible et  significative ==> On rejette l'hypothese H0 (il n'y a pas de corrélation entre les 2 matrice) ==> Il y a bien une corrélation significative entre les 2 matrices de distance
				- Diversité génétique par population
					- Pour cela on calcul les hétérozygoties théoriques H_{s}  par population et par locus et faire la moyenne
					- ```r
					  > Htheo[1:4,]
					       [,1]         [,2]               
					  [1,] "Adygei"     "0.716694734223818"
					  [2,] "Balochi"    "0.724429266995916"
					  [3,] "BantuKenya" "0.752143874030711"
					  [4,] "Basque"     "0.712794162552817"
					  ```
					- On a donc ici le $\bar{H_{s}}$ théoriques pour chaque population
				- Relation avec la distance à l'Afrique de l'Est
					- ![image.png](../assets/image_1732894523858_0.png)
					- ```r
					  > cor(as.numeric(Htheo[,2]), distancesAfr$DistAA) ^2 
					  [1] 0.8028861
					  ```
					- ==> Les pop avec le niveau de diversité le plus grande est les pop Africaine cela s'explique par les effets fondateurs en série
						- A partir du site d'origine, un groupe migre à coté (effet fondateur -> derive génétique -> perte de diversité génétique) et à nouveau à chaque migration des pop dans un autre site
						- A chaque nouveau effet fondateur, on accumule les effet fondateurs précédent et donc on accumule les pertes génétiques ==> Moins de diversité génétique
						- On a un R² = 80% de la variation de la variable en Y (la différenciation génétique) expliqué par la relation linéaire en X (la distance de migration, l'histoire démographique de la pop humaine)
					- ==> On s'affiche des commandes mais il faut savoir interpréter les sorties !!!!
-
-
-
- [[#red]]==**Céline Brochier = Phylogénie moléculaire**==
	- **[[#green]]==CM==**
		- Phylogénie et arbres (Exemple des Eucaryotes)
			- ![image.png](../assets/image_1732735934736_0.png)
			- Nœuds
				- Correspondent aux Unités Taxonomiques (UT)
				- Plusieurs types
					- UT Oprérationnelles (UTO)
						- Feuilles de l'arbre
					- UT Hypothétiques (UTH)
						- Nœuds internes de l'arbre
			- Topologie
				- Définition
					- Forme caractéristique de l'arbre
					- Ensemble des branchements (nœuds + branches) de l'arbre
				- Types
					- Phylogramme
						- La longueur des branches est proportionnelle à la distance évolutive entre les séquences (nb substitutions / site)
					- Cladogramme
						- La longueur des branches est arbitraire et ne reflète pas la distance évolutive séparant les séquences
			- Groupe extérieure
				- Définition
					- Ensemble de séquences homologues choisies car elles sont, a priori, moins apparentés que les séquences que l'on analyse
			- Racine
				- Ici, on a un arbre non raciné => Pas enracinée dans le temps, pas de sens de lecture
				- Définition
					- La racine d'un arbre = Point de branchement du groupe extérieur avec le groupe d'étude = Ancêtre commun pour le groupe d'étude
					- Ancêtre commun le plus récent à tous les UTO
					- Nœud reliant le groupe extérieur  aux séquences étudiées
				- Propriétés
					- Sans racine, impossible de déterminer les relations de parenté entre UTO
					- Il y a autant de racines possibles que de branches dans un arbre non raciné
						- Chacune induit une histoire évolutive particulière mais une seule est vraie
			- Base de l'arbre
				- Propriétés
					- Asymétrique et en barreau d’échelle
					- Bien résolu et connu
					- Lignées qui s'écartent du tronc à intervalle régulier = Spéciation
					- Souvent une branche droite
						- Si ligne droite = Très peu de diversité
						- Si triangle = Très grande diversification
				- Ici, ce sont les Archezoa
					- Caractéristiques
						- Eucaryotes
						- Très simples, primitifs
						- Pas de mitochondrie
						- Pas de Golgi, pas de RE
						- ==> Questions : Perdue ou jamais acquis ?
						- ==> Hypothèses
							- Les Archezoa sont des eucaryotes primitifs n'ayant jamais eu de mitochondrie
							- Le noyau à une origine antérieure à l'endosymbiose des mitochondries
							- Les premiers Eucaryotes étaient anaérobiques
						- ==> Preuves du contraire possibles
							- Trouver gènes mitochondriales dans le génome des Archezoa
							- Trouver une branche des Archezoa parmi les espèces aérobiques (avec des mitochondries)
							- Trouver des organelles dérivées des mitochondries chez les archezoa
			- Branches
				- Types
					- Internes
						- Succession d'organismes reliant 2 UTH (les première branches proche de la racine)
					- Externes
						- Succession d'organismes reliant les UTH au UTO (les dernières branches, loin de la racine)
				- Caractéristiques
					- Le temps, sens de lecture = De la racine vers les feuilles
					- La longueur d'une branche est définie par :
						- $$d = \lambda * t$$
							- $d$ = Distance évolutive
							- $\lambda$ = Constante d'évolution (c'est une vitesse) = Taux de substitution par site par intervalle de temps
							- $t$ = Temps
				- Propriétés
					- Artéfact d'attraction des longues branches
						- L'algorithme connecte les branche par vitesse d'évolution similaire
						- Si on a une grande branche = Distance évolutive élévé MAIS :
							- Est ce que c'est parce que j'ai un $\lambda$ moyen, normale et un $t$ très grand OU...
							- Est ce que c'est parce que j'ai un $\lambda$ élevé et un $t$ normale, moyen ?
							- ==> Un grande branche ne veut pas dire que l'espèce est ancienne, elle peut etre récente mais avec une taux de mutation élévée et donc très distante évoltionairement parlant
						- Par reconstruction les grandes branche du groupe modèle seront toujours proches du groupe extérieur car, par définition, le groupe extérieur est très distant du groupe modèle, il a toujours une grande branche
			- Couronne
				- Définition
					- Dans un intervalle de temps toute les lignées s'échappent, et se diversifient très fortement (= Radiation)
				- Ici, on a les organismes multicellulaires = Eucaryotes
					- Complexité graduelle des cellules eucaryotes
					- ==> Émergence tardive
					- ==> Couronne pas parfaitement et totalement résolu
						- Car trop peu de signaux phylogénétiques enregistrer en séquences
							- Il faut donc augmenter le nombre de data, mais pas que sinon :
								- Les modèles évolutionnaires imprécis peuvent biaisés les inférences phylogénétiques
								- Les sampling taxonomiques imprécis peuvent biaisés les inférences phylogénétiques
								- Les biais constitutionnels et les substitutions multiples peuvent affecter les inférences sur les arbres
							- Il faut donc améliorer aussi les méthodes de reconstruction et les modèles évolutionnaires
							- Il faut donc améliorer aussi le sampling taxonomique pour éviter les artefacts liés aux reconstructions des arbres et réduire la saturation
							- Il faut donc aussi brisé les longues branches pour éviter l'artefact de l'attraction des longues branches
								- Éliminer les sites évolutifs rapides permet d'éviter cet artefact
						- Car il y a une saturation substitutionnelle
							- L'ancien signal phylogénétique est progressivement effacé par les multiples substitutions
			- Apparentement et similarité
				- ![image.png](../assets/image_1732743321368_0.png)
			- Construction de l'arbre
				- Vérifier que le groupe extérieure est bien indépendant du groupe d'étude
				- Spécification de critères permettant de sélectionner un ou plusieurs arbres parmi l’ensemble des arbres possibles
				- Plus on a de feuille, plus on a de topologie différentes possibles
					- ![image.png](../assets/image_1732743620252_0.png)
					- Nombre d'arbres non racinés pour n UTO = Nombre d'arbres racinés pour n-1 UTO
				- La meilleure topologie (le meilleur arbre), est le maximum global parmi l'ensemble des arbres possibles
					- Point de départ = Alignement de séquences homologues
					- Arrivée = Arbre décrivant les liens évolutifs entre les séquences de l’alignement
				- Méthodes
					- Méthodes de distance
						- Recherche l’arbre qui représente au mieux les distances évolutives entre paires de séquences
						- Requière l’estimation des distances évolutives entre paires de séquences, sachant un modèle d’évolution
						- UPGMA, NJ, minimum d’évolution, moindres carrés…
					- Méthodes cladistiques
						- Recherche l’arbre impliquant le moins de changements évolutifs permettant d’expliquer les données
						- Considèrent les sites individuellement
						- Maximum de parcimonie
					- Méthodes statistiques
						- Recherche l’arbre ayant la plus forte vraisemblance sous le modèle d’évolution considéré
						- Considèrent les sites individuellement
						- Maximum de vraisemblance, Méthodes bayésiennes
				- Calcul de distance évolutive endre 2 séquences
					- Propriétés
						- Si \lambda constant, alors d évolue linéairement avec t (hypothèse d’horloge moléculaire)
						- Les distances évolutives sont estimées à l’aide de modèles markoviens de substitution
						- Méthodes de distances, de vraisemblance et bayésiennes
				- Outils
					- La p-distance
						- ![image.png](../assets/image_1732746295784_0.png)
					- Matrice de transition
						- C'est la matrice des taux instantanés de substitution
						- ![image.png](../assets/image_1732746502058_0.png)
						- Matrice des probabilités de substitution
							- ![image.png](../assets/image_1732746874794_0.png)
						- Hypothèses des modèles d’évolution markoviens
							- Indépendance des sites
								- Les événements affectant un site ne sont pas influencés et n’influencent pas les événements aux autres sites
								- Permet de simplifier les modèles d’évolution
								- Est rarement vérifiée dans les séquences d’ADN et d’ARN à cause de la présence de structures secondaires
								- Prise en compte nécessiterait une matrice M à 16 entrées
							- Uniformité du processus
								- Tous les sites d’une séquence suivent un processus markovien identique
								- Tous les sites d’une séquence évoluent à la même vitesse
								- Hypothèse notoirement erronée, mais faite par la plupart des modèles d’évolution
								- Peut être corrigée par des améliorations telles que la distribution gamma
								- ==> Pas de variation entre sites : limite \alpha -> \infty tous les u sont égaux
							- Stationnarité du processus
								- Liée à l’hypothèse d’homogénéité constance des taux de substitution instantanées au cours du temps
								- Soit \pi A, \pi T , \pi C, \pi G les fréquences d’équilibre des 4 bases des deux séquences comparées, cad les valeurs vers lesquelles vont tendre les compositions en bases après un temps infini
								- Si le processus est homogène, à l’équilibre toutes les séquences ont la même composition en bases
								- La plupart des modèles d’évolution font l’hypothèse que les séquences étudiées sont à l’équilibre
								- Hypothèse simplificatrice pas toujours vérifiée par les séquences réelles
							- Réversibilité du processus
								- ![image.png](../assets/image_1732747538909_0.png)
			- Les super-phyla
				- Opisthokonta
					- Animaux, champignons
				- Amoebozoa
				- Archaeplastida
				- Harosa = SAR clade
				- Hacrobia = CCTH clade
				- Excavata
				- Les modèles d'évolution ADN/ARN couramment utilisés en PhyloMol
					- Types
						- Modèle de Jukes & Cantor => 1 paramètre
							- ![image.png](../assets/image_1732747823536_0.png){:height 389, :width 656}
						- Modèle de Kimura => 2 paramètres
							- ![image.png](../assets/image_1732747849795_0.png)
					- Calcul de distance évolutive avec variation du taux d’évolution entre sites
						- ![image.png](../assets/image_1732747787614_0.png)
					- La vraisemblance
						- Caractéristiques
							- Bonne consistance <=> convergent vers la valeur correcte du paramètre
							- Bonne efficience <=> ont la plus petite variance possible autour de
							  la vraie valeur du paramètre
							- Le calcul de la vraisemblance se fait, de manière indépendante, pour chacun des sites de l'alignement
						- Hypothèses
							- Le processus de substitution suit un modèle probabiliste dont on connaît l’expression mathématique, mais pas les valeurs numériques
							- Les sites évoluent indépendamment les uns des autres
							- Les sites évoluent suivant le même processus = hypothèse d’uniformité (hypothèse pouvant être levée par l’inclusion d’une loi gamma)
							- Le taux de substitution ne change pas au cours du temps, cad le long
							  d’une branche = hypothèse d’homogénéité, mais il peut varier entre les
							  branches
								- En fait, on suppose que le modèle et ses paramètres qualitatifs sont
								  conservés d’une branche à l’autre, mais que seul la quantité d’évolution varie
								  d’une branche à l’autre
						- Maximisation
							- On considère une topologie T , un site et un ensemble de longueurs de branches b (les longueurs de branches initiales sont en générales estimées par un arbre reconstruit par une méthode de distance, ex. NJ)
							- On calcule la vraisemblance des paramètres = probabilité d’observer les états de caractères au site en fonction des paramètres
							- On fait le calcul pour tous les caractères (T , \theta , b)
							- On calcule les longueurs de branches b et les paramètres \theta du modèle qui maximisent la vraisemblance (procédure complexe)
							- On calcule la vraisemblance pour toutes les topologies possibles
							- ==> On retient la topologie qui a la plus grande vraisemblance
							- Propriétés
								- C’est une des méthodes les plus justifiées d’un point de vue théorique
								- Les simulations montrent que cette méthode est supérieure aux autres dans beaucoup de cas. En particulier elle est moins sensible aux artefacts d’attraction des longues branches
								- Coûteuse en temps de calcul
								- Impossible d’évaluer tous les arbres <=> utilisation d’heuristiques <=> n’est
								  plus certain d’obtenir l’arbre le plus vraisemblable
								- Des tests statistiques dérivés du maximum de vraisemblance permettent d’évaluer si des topologies ayant une vraisemblance moins bonne que la topologie la plus vraisemblable sont significativement différentes
						- Évaluer la robustesse des arbres reconstruits
							- Principe
								- Idée = estimer la variabilité de l’arbre (ou d’une partie de l’arbre)
									- Association d’un estimateur de la robustesse à chaque branche de l’arbre
								- Si un arbre est robuste i.e. fortement soutenu par les données alors sa variabilité sera faible, et les regroupements observés (i.e. bipartitions) devraient être retrouvés même si on perturbe un peu les données
								- Si un arbre est peu robuste alors il aura une grande variabilité, et les regroupements observés seront très instables en cas de perturbation des données
								- PROBLEME : Absence de données indépendantes
								- SOLUTION : Effectuer des ré-échantillonnages des données disponibles, cad de l’alignement initial.
							- Le Bootstrap
								- La procédure de bootstrap s’appuie sur des alignements ré-échantillonnés de même taille que l’alignement initial
								- On réalise X tirages avec remise de n sites parmi les n sites
								  contenus dans l’alignement initial
									- Certains sites seront présents plusieurs fois dans le nouvel alignement
									- Certains sites seront absents du nouvel alignement
									- Pondération des caractères variant entre 0 et n
								- D’un tirage à l’autre les sites absents ou présents plus d’une fois seront différents
								- Chaque tirage (i.e. combinaison de sites) est unique car la pondération des sites est aléatoire d’un tirage à l’autre
								- Pour chaque tirage on calcule la phylogénie correspondante par la même méthode
								- La robustesse de chaque branche de l’arbre initial peut être estimée par le nombre de fois où cette même branche est retrouvée dans les reliquats de bootstrap
								- ==> Une valeur de boostrap de 100% ==> Un noeud ROBUSTE \ne VRAI !
									- Exemple des grandes geules
							- Cause de l’incongruence/problèmes rencontrés en phylogénie moléculaire
								- Problèmes d’échantillonnages
									- Séquences trop courtes => effets stochastiques
									- Échantillonnage taxonomique trop réduit
								- Problèmes liés à la divergence des séquences
									- Séquences pas assez variables
									- Séquences trop divergentes => saturation
									- Séquences présentant des taux d’évolution hétérogènes (Attraction des longues branches)
							- => Facteurs non exclusifs !
-
	- **[[#green]]==TP==**
		- Mitochondrie = alpha proteo bactérie
		- Question
			- Quel est le degré de saturation substitutionnelle
			- Reconstruire la phylogénie de chaque marqueur pour voir celui qui a le signal le + fort
			- Classer les marqueurs dans des catégories, sur la base de leurs signal phyloG
				- Meme catégorie, pour les signaux identiques compatibles
			- Réaliser une analyse pour chacun des groupes séparés
				-
-
- [[#red]]==**Ivan Paz = Paysage**==
-
- [[#red]]==**Aurore = Stress**==
	- **[[#green]]==CM==**
	- [[#green]]==**TP**==
		- # Partie 1
			- Intro
		- # Partie 2
			- Q1
				- Colonne 1 = Référence/Nom de l'assemblage
				- Colonne 2 = Longueur du transcrit associé
				- Colonne 3 = Longueur corrigée par rapport au taux de GC
				- Colonne 4 = TranscriptPerMillion = Comptage de reads alignés normalisés
				- Colonne 5 = Comptage de reads alignés sur l'assemblage
				- Q5
					- Après filtre, il reste 62527 lignes (= transcrits)
		- # Partie 3
			- Le Fold Change, + ou - en fonction de la surexpression du gène dans la condition A ou B
				- + ==> La condition A surexprimé par rapport à la cond B
				- - ==> C'est l'inverse
			- On considère que la padj pas la pvalue (car on a ici des tests multiples)
			- Cond A = 14 DEG / Cond B = 25 DEG / Cond C = 21 DEG
			- Des organismes exposé à un premier stress thermique ne sont plus capables de répondre face à un 2e stress
-
- [[#red]]==**Julien Varaldi = Spéciation**==
	- [[#green]]==**TP**==
		- Question 1 :
			- Les espèces ont des écologies similaires, morphologies...etc ==> Spéciation non écologique
		- DDrad = Séquençage autour des sites de restrictions, polymorphisme du génome visible sans séquencer tout le génome
		- Question 2 :
			- Dans le modèle de Wright :
				- On a une pop (p) qui contient 2 sous-pop (p1 et p2) qui chacune comporte plusieurs individus et dans chaque individus 2 allèles
					- $$\bar{p} = \frac{p_1 + p_2}{2}$$
					- Pour p_{1} :
						- $$Hétérozygotie_{Sous-pop1} = 2*p_1*q1$$
					- Pour p_{2}
						- $$Hétérozygotie_{Sous-pop2} = 2*p_2*q2$$
					- $$\bar{HétérozygotieMoy_{Sous-pop}} = \frac{Hétérozygotie_{Sous-pop1} + Hétérozygotie_{Sous-pop2}}{2}$$
					- Pour la Pop Totale :
						- $$Hétérozygotie_{Pop-Totale} = 2 * \bar{p} * \bar{q}$$
				- Et on peux calculer le taux d'hétérozygotie à ces différentx niveaux
			- $$F_{st} = \frac{Hétérozygotie_{Pop-Totale} - \bar{HétérozygotieMoy_{Sous-pop}}}{Hétérozygotie_{Pop-Totale} } = \frac{Variance(p)}{\bar{p}*(1-\bar{p})} = ?$$
			- Ici, on a :
				- $p_{1} = \frac{2 * 12 +23}{54 * 2} = 0.43$
				- $p_{2} = 0.58$
				- $\bar{HétérozygotieMoy_{Sous-pop}} (\bar{H_s})= 0.49$
				- $\bar{p} = 0.505$
				- $Hétérozygotie_{Pop-Totale} (H_T) = 0.5$
				- $Variance(p) = \frac{1}{2}*(0.43²+0.58²)-0.505²$
			- $F_{st} = \frac{Hétérozygotie_{Pop-Totale} - \bar{HétérozygotieMoy_{Sous-pop}}}{Hétérozygotie_{Pop-Totale} } = \frac{0.5 - 0.49}{0.5} = 0.02$
			- $$F_{st} = \frac{Variance(p)}{\bar{p}*(1-\bar{p})} = \frac{\frac{1}{2}*(0.43²+0.58²)-0.505²}{0.505*(1-0.505)} = 0.022$$
				- C'est la formule brute de la variance : 1/N * Somme des carrés - moyenne carré...etc
		- Question C :
			- On voit des pics de différenciation bien définis et séparés
			- 1 pic de F_{st} = Différence de fréquence allélique, il y a des fréquence d'allèles très différentes (elles ne sont pas fixée sinon on aurait atteint le 1). Les oiseau ne comporte pas les même fréquences d'allèles dans ces sites là
		- Question D :
			- Plus les espèce sont séparé depuis longtemps, plus leurs distance mitochondriales et nucléaire seront différent ==> C'est attendue
			- Il y a un très petit F_{st} = elle est outlier. Elle a une divergence mito de 3 % on s'attendait donc à avoir un F_{st} de 20%. Si ces espèces s'hybrident, les allèles vont pouvoir migrer d'une espèces a l'autre et homogénéiser les fréquence allélique ==> Il y a eu donc beaucoup d'hybridation entre les 2 espèces
		- Question E :
			- Il y a eu un phénomène qui a générer de la diversification au niveau des espèces naissantes (par exemple une barrière physique = allopatrie, voire aussi de la sélection sexuelle divergent entre ces espèces (sur des critère de plumage par exemple)), puis ensuite destruction de la barrière, les 2 pop se sont retrouvés et hybridé, et réduire la diversité génétique (baisse du F_{st}), cette baisse est toutefois pas homogène sur tout le génome, elle ne concerne pas les locus impliqué dans la coloration du plumage, et cette différenciation au niveau de ces locus se maintient car il y a peut être une préférence pour les phénotypes qui sont similaires (homogamie très forte sur la coloration du plumage chez ces espèces de paruline). Cela n’empêche pas d'avoir des hybrides stables, fertiles, et peuvent continué à faire le passage des allèles
		- Exercice 2
			- Une inversion dans un génome (par exemple les gène A, B et C sur un locus deviennent C', B', A') à pour conséquence d’empêcher les recombinaison génétiques, les gènes sur les 2 chromosomes vont muté chacun mais on retrouveras toujours A, B avec C, et A', B' et C' ensemble, ces 3 allèles vont former une sorte de méga-allèle qui ne sera jamais recombiné
			- Question A :
				- Peut être que la pomme est présent plus tôt que l'aubépine, donc il faut être prêt plus tôt pour une mouche, et il faut donc les allèles qui sont adapté pour ça, donc fort déséquilibre ==> Ça suggère que les allèles étaient déjà présentes dans la population et ils sont monté très vite en fréquence quand le pommiers est apparues. Ce n'est pas que les allèles ont évolué, les allèles étaient déjà présent dans la pop (surement par hybridation). 2e preuve dans le tableau on voit que les allèles sont bien plus vieux que l’événement de spéciation en lui même. On avais donc déjà des allèles pré adaptés dans la population avant l’événement de spéciation
			- Question B : \empty
			- Question C : \empty
			- Question D : \empty
- kjk