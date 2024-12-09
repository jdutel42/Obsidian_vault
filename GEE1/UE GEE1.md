# ==Marie Fablet = Génétique des Populations==

- # Rappels
	- ## Équilibre de Hardy Weinberg (HW)
		- Comportement d'une population théorique idéale :
			- Population d’organismes diploïdes à reproduction sexuée
			- Générations non chevauchantes
			- Effectif infini
			- Panmixie
			- Absence de migrations, sélection, mutations
		- ![[Pasted image 20241130121020.png]]
		- ==> À chaque génération, les génotypes sont formés par association aléatoire des allèles
			- ==> Composition génétique -> $Génération(t+1) = Génération(t)$
	- ## Population de Wright-Fisher
		- ### Définition
			- C'est comme l’équilibre HW sauf que :
				- Panmixie pas toujours supposé
				- Effectif limité, constant
					- La taille des familles ~ Loi de Poisson de paramètre $\lambda = 2$
				- ==> À chaque génération, les génotypes **NE** sont **PAS** formés par association aléatoire des allèles
					- ==> Composition génétique -> $Génération(t+1) \ne Génération(t)$
					- ==> Il y a de la dérive génétique
		- ### Métriques
			- Écart en hétérozygotes $f$
				- ![[Pasted image 20241130122458.png]]
					- (Ce n'est pas le même $\lambda$ que plus haut)
				- Cela correspond au coefficient de corrélation $f$ :
					- $$f = \frac{cov(X,Y)}{\sqrt{V(X)*V(Y)}} = \frac{\lambda}{p*q}$$
				- On peut voir ce $f$ comme l'écart en hétérozygotes observés par rapport aux hétérozygotes à l'ÉHW 
					- $$freq(Aa) = 2pq - 2\lambda = 2pq - 2fpq$$
					- $$f = \frac{2pq - freq(Aa)}{2pq} = 1 - \frac{freq(Aa)_{obs}}{freq(Aa)_{théo}}$$
				- ==> Ce $f$ est un **coefficient de corrélation** calculé à partir des **fréquence génotypiques** de la **population** au locus considéré, et dont la valeur est comprise entre **$[-1;1]$**
					- ==> Ce $f$ est la **mesure du système d'appariement, comme écart aux fréquences attendues sous panmixie**
			- Coefficient de consanguinité $F$
				- Pour une génération
					- Probabilité d'être auto-zygote à un locus donné
					- Proba que, à un locus donné, les 2 allèles soient identiques par descendance
					- ==> Ce $F$ est la **probabilité (compris entre $[0;1]$) d'identité** **par descendance** à un locus autosomal donné pour **un individu donné**, du fait de l'appariement de ses parents
					- ==> $F \ne f$
					- On peut définir un $\bar{F}=F_{moy}$ (la moyenne de tous les $F$ des individus de la population) qui n'est pas une mesure du système d'appariement, mais une **mesure de la dérive génétique**
					- Exemples
						- Exemple 1
							- ![[Pasted image 20241130141618.png]]
							- $$f = 1 - \frac{freq(Aa)_{obs}}{freq(Aa)_{théo}} = 1 - \frac{\frac{1220}{1083+1220+260}}{\frac{1150}{1083+1220+260} } = 0.061$$
							- ==> $f$ est proche de 0 ==> On a un faible écart des hétérozygotes observés dans la population comparé aux hétérozygotes théoriques (en condition panmictique, modèle de HW) ==> On observe donc pas un faible nombre d'hétérozygote (et donc un fort nombre d'homozygote) typique du phénomène de consanguinité ==> Absence notable de consanguinité
						- Exemple 2
							- ![[Pasted image 20241130144517.png]]
				- Pour la $t^{e}$ génération
					- Si on généralise le $F_{moy}$ pour t générations (**$\bar{F_t}$**) :
						- ![[Pasted image 20241130150742.png]]
							- $t$ : Génération t
							- $Ne$ : la taille efficace
								- (Taille de la population pour laquelle on obtiendrait la même valeur de $\bar{F}$ après le même nombre de générations. C'est la valeur de $N$ qui vérifie l'expression ==> C'est une référence commune pour mesurer la force de la dérive dans une population donnée)
								- Plus $Ne$ est faible, plus on atteindra rapidement un coefficient de consanguinité $\bar{F}$ important au fil des générations
					- Ajout des autres effets de dérive génétique
						- On peut ajouter à cette mesure $\bar{F_t}$ de la dérive génétique, les effets $m$ liés aux migrations des population ==> Les effets fondateurs
							-  ![[Pasted image 20241130151503.png]]
						- On peut aussi ajouter les effets des mutations génétiques $µ$ (même si en soit $µ<<m$)
							- ![[Pasted image 20241130151933.png]]
					- À l'équilibre
						- Le $\bar{F}$ dans chaque sous-population atteint une valeur dépendante de $Ne$​ et du flux de gènes entre les sous-populations
						- ![[Pasted image 20241130152434.png]]
						- ==>==>==> $\bar{F_{eq}}$ mesure le rapport entre dérive génétique et flux de gène  
							- ==>==>==> C'est le $F_{st}$ de Wright
- # Indices F de Wright
	- ## Indice $F_{st}$ et $f_{st}$
		- ### Définition
			- #### Définition
				- Mesure le rapport entre flux génétiques et dérive génétique
				- Mesure la proportion de variation génétique entre individus due aux différences génétiques entre sous-population
				- Exemple : *Homo sapiens* -> $F_{st} = 0.15 << 1$
					- Populations très homogènes
			- #### Calculs
				- Il est aussi défini à partir des variances des fréquences alléliques dans les sous populations
					- $$f_{st} = \frac{Var(p)}{\bar{p}*\bar{q}}$$
					- Cela correspond à l'écart aux proportion de HW pour la population totale dû aux variations de fréquences alléliques dans les sous-populations
					- ==> C'est la corrélation entre les allèles **au sein des sous pop** par rapport à **la population totale**
				- Avec cela, on peut définir les fréquences alléliques
					- $$f(AA) = \bar{p}² + f_{st} * \bar{p} * \bar{q}$$
					- $$f(Aa) = 2 * \bar{p} * \bar{q} - 2 * f_{st} * \bar{p} * \bar{q}$$
					- $$f(aa) = \bar{q}² + f_{st} * \bar{p} * \bar{q}$$
				- On peut réécrire :
					- $$f_{st} = 1 - \frac{f(Aa)}{2 * \bar{p} * \bar{q}} = \frac{H_t - \bar{H_i}}{H_t} = \frac{2\bar{p}\bar{q} - \sum(\frac{N_i}{N})*2p_iq_i}{2\bar{p}\bar{q}}$$
					- $H_t = 2\bar{p}\bar{q}$ : Hétérozygotie attendue dans la pop totale si HW
					- $\bar{H_i} = f(Aa)$ : Hétérozygotie observée dans la pop totale, Moyenne des hétérozygotie dans les sous-pop (en supposant l'équilibre HW dans les sous pop)
			- #### Conclusions
				- ==> $F_{st}$ et $f_{st}$ mesurent le rapport entre flux génétiques et dérive **MAIS**...
				- ... $F_{st}$ et $f_{st}$ sont biologiquement différents et peuvent avoir des valeurs différentes, car considèrent des aspects différents de la dérive :
					- $F_{st}$ ==> Identité par descendance
					- $f_{st}$ ==> Variance des fréquences alléliques
				- ==> $f_{st}$ est plus sensible que $F_{st}$ aux événements récents qui modifient l'équilibre
				- ==> ==> ==> $F_{st}$ et $f_{st}$ ne sont pas équivalents !!!
			- #### Interprétations
				- $F_{st} \epsilon [0;1]$
					- $F_{st} = 0$ (ou proche de 0) : Pas de différenciation génétique entre les pop
					- $F_{st} > 0$ : Différenciation significative
					- $F_{st} >>> 0$ : Absence de flux de gènes
				- $F_{st}$ n'est pas une statistique
				- Il faut tenir compte de la taille de l'échantillon
				- ![[Pasted image 20241130165814.png]]
			- #### Tests
				- ##### Test d'homogénéité du $\chi²$ sur les fréquences alléliques
					- ![[Pasted image 20241130165442.png]]
				- ##### Permutations
					- ![[Pasted image 20241130165532.png]]
		- ### Applications
			- #### Inférence de l'histoire démographique
			- #### Identification de régions du génome sous sélection
				- Comparaison des estimations de $F_{st}$ pour un grand nombre de locus
					- Si différenciation significative élevée -> Locus soumis à sélection diversifiante
					- Si différenciation significative faible -> Locus soumis à sélection stabilisatrice
			- #### Police scientifique
				- Calcul de la probabilité d'un match aléatoire entre le profil d'un indice sur une scène de crime et le profil d'un suspect (cad proba que le suspect soit innocent)
				- Si le suspect appartient à une population pour laquelle les fréquences alléliques ne sont pas connues, proba corrigée en fonction de $F_{st}$
		- ### Méthodes d'estimation
			- #### Méthode des moments (Cockerham)
				- On fait une ANOVA hiérarchique des fréquence alléliques, en décomposant les effets :
					- $a$ -> Effet de la sous population
					- $b$ -> Effet de l'individus
					- $w$ -> Effet intra(individu)
				- On peut décomposé la variance totale selon la variance de chaque effet :
					- $$\sigma² = \sigma²_{a} + \sigma²_{b} +\sigma²_{w}$$
				- ![[Pasted image 20241130180450.png]]
				- Pour Cockerham :
					- $f \to f_{is}$
						- ![[Pasted image 20241130181321.png]]
					- $\theta \to f_{st}$
						- ![[Pasted image 20241130181309.png]]
					- $F \to f_{it}$
						- ![[Pasted image 20241130181250.png]]
			- #### Maximum de vraisemblance
				- Beaucoup de calculs
				- Estimations biaisées, mais variance plus faible
				- ==> Méthode très largement utilisée
			- #### Estimations bayésiennes
				- Beaucoup de temps de calcul
				- Mais prise en compte possible de très nombreux paramètres
		- ### Variantes
			- #### Intérêts
				- Les hypothèses du calcul $F_{st}$ pas toujours vraies, par exemple :
					- Le modèle de migration : archipel
					- m faible
					- modèle de mutation : infinite allele
					- µ <<< m
				- S'il y a de nombreuses différences entre allèles dans toutes les populations --> Le $H_T$ et $H_S$ sont très proches de 1
				- Prise en compte des différences quantitatives entre 2 allèles --> Augmente puissance et sensibilité pour détection de la structuration
				- Dans le cas des micro-satellites, il y a de l'homoplasie (ce qui est hors du cadre de l'Infinite Allele Model) et µ peut être très élevé
			- #### Le $G_{st}$
				- ##### Définition
					- C'est l'écart à la différenciation totale (contrairement au $F_{st}$ qui est l'écart à la panmixie)
					- C'est la proportion de diversité allélique existant entre les population, distance entre les populations
					- Le $G_{st}$ est adapté aux cas de forte diversité allélique
				- ##### Calculs
					- $$1 = \frac{\bar{H_s}}{H_t} + \frac{D_{st}}{H_t} = \frac{\bar{H_s}}{H_t} + G_{st}$$
						- $H_t$ : Diversité totale
						- $\bar{H_s}$ : Diversité intra sous population
						- $D_{st}$ : Diversité inter sous pop
			- #### Le $R_{st}$
				- ##### Définition
				- ##### Calculs
					- $$R_{st} = \frac{S - S_w}{S}$$
						- $S$ : Moyenne des carrés des écarts de taille entre allèles pour toutes les paires d'allèles possibles
						- $S_w$ : Moyenne des carrés des écarts de taille entre allèles pour les paires d'allèles pris dans la même sous pop
			- #### Le $Q_{st}$
				- ##### Définition
					- Proportion de variance génétique additive du trait due aux différences entre populations
					- $Q_{st} = f_{st}$ 
						- Si trait neutre
						- Si toute la variation génétique est additive
						- Si même taux de mutation que pour les autres loci
				- ##### Calculs
					- $$Q_{st} = \frac{\sigma²_{GP}}{\sigma²_{GP}+2\sigma²_{GI}}$$
						- $\sigma²_{GP}$ : Variance génétique additive entre populations
						- $\sigma²_{GI}$ : Variance génétique additive au sein des populations
				- #### Interprétations
					- Pour un nombre de population suffisante (>20)
						- Si $Q_{st} > f_{st}$ --> Sélection diversifiante
						- Si $Q_{st} < f_{st}$ --> Sélection stabilisatrice
			- #### Le $\phi_{st}$
				- ##### Définition
					- Sur les données d'haplotypes
					- Notation générique pour tous les variants de $\bar{F_{st}}$ prenant en compte la distance génétique moléculaire entre allèles
	- ## Indice $f_{is}$
		- ### Définition
			- Mesure l'écart à la panmixie dans les sous population (est ce que les appariements dans les sous population sont non aléatoires ?)
			- ==> C'est la **moyenne sur toutes les sous-pop** des corrélations entre les allèles **au sein des individus** par rapport à **la sous pop**
		- ### Calculs
			- $$f_{is} = \frac{H_s - H_i}{H_s} = \frac{f(Aa)}{2p_iq_i}$$
				- $H_i$ : Hétérozygotie observée dans la sous-pop
				- $H_s$ : Hétérozygotie attendue si panmixie
		- ### Interprétations
			- 
	- ## Indice $f_{it}$
		- ### Définition
			- Mesure l'écart globale dans la population totale à l'équilibre HW, et est composé de 2 composantes :
				- Le système d'appariement dans la sous population ==> $f_{is}$
				- La différence de fréquences alléliques entre les sous populations ==> $f_{st}$
				- ==> C'est le coefficient de corrélation entre allèles **au sein des individus** par rapport à la **population totale**
			- De manière globale, on a :
				- $$(1-f_{it}) = (1-f_{st}) * (1-f_{is})$$
		- ### Calculs
			- $$f_{it} = \frac{H_t - \bar{H_i}}{H_t} = \frac{2\bar{p}\bar{q} - \sum(\frac{N_i}{N})*2p_iq_i}{2\bar{p}\bar{q}}$$
				- $H_t$ : Hétérozygotie totale attendue
				- $H_s$ : Hétérozygotie attendue si panmixie  
	- ## AMOVA
		- ### Définition
			- Analysis of Molecular Variance
			- Elle fournit des estimation des composantes de la variance et des analogues aux statistiques $F$, notés $\phi$
			- C'est une ANOVA hiérarchique sur une matrice de distances entre paires d'haplotypes
			- Cela convient pour tout type de données moléculaires
		- ### Principe
			- On encode chaque haplotype sous forme de vecteur $p_i$ en binaire
				- $0$ si absnece du marqueur
				- $1$ si présence du marqueur
			- On fait une matrice
				- Colonnes = les différentes pop
				- Lignes = Les différents vecteurs $p_i$ des marqueurs
			- On calcul les $\delta²_{jk}$ = carré de la distance entre les vecteurs $j$ et $k$ 
			- On obtient une matrice de pondération $D²$ qui regroupe toutes les paires
			- Par analogie avec l'approche de Cockerham
				- ![[Pasted image 20241130190859.png]]
				- ![[Pasted image 20241130190931.png]]
			- Différence avec l'ANOVA
				- Condition de normalité non remplie (distance entre vecteurs de 0 et de 1)
				- Distribution nulle obtenue par permutation (individus assignés à une population aléatoirement choisie)
- # Exemple : Structure des populations humaines
	- Chez les *Gorilla gorilla* : $F_{st} = 0.38$
	- Chez les Pan troglodytes : $F_{st} = 0.32$
	- Chez les *Homo sapiens* : $F_{st} = 0.15$
	- ==> *Homo sapiens* à la plus faible diversité parmi les primates, les population les moins différenciées
	- ==> On a une corrélation positive entre les distances génétiques (paires de $F_{st}$) et distances géographiques
		- ![[Pasted image 20241130191737.png]]
	- ==> Corrélation négative entre distance géographique à l’Est de l’Afrique et diversité génétique des populations
		- ![[Pasted image 20241130191823.png]]
	- ==> ==> Les différences génétiques entre populations africaines sont supérieures à celles observées entre populations eurasiennes et africaines
	- ==> ==> Les allèles spécifiques à des continents sont rares en général, mais plus communs en Afrique
	- ==> ==> Les allèles mis en évidence hors Afrique sont souvent une fraction du pool allélique africain
	- ==> ==> ==> Colonisation du monde à partir de l’Afrique par un petit groupe de fondateurs il y a environ $[40 000 ; 70 000]$ ans
- # Conclusions
	- $F_{st}$ et ses variantes sont très utilisés en génétique des populations :
		- Identification des contours des populations
		- Mesure des flux génétiques entre pops
		- Reconstitution de l’histoire évolutive des pops
	- Multiplication des analyses possibles avec l’arrivée de données génomiques en masse
- # Logiciel "Structure"
	- Affectation des individus à des groupes
	- On choisit K = le nombre de groupes (On ne choisit PAS le contour des groupes)
	- Pour chaque individu, calcul de la probabilité d’appartenance à chacun des K groupes
	- Représentation graphique avec code couleur
	- Choix du "meilleur" K par maximum de vraisemblance
	- On regarde la structuration
		- ![[Pasted image 20241130192434.png]]

---

# ==Julien Varaldi = Spéciation==

- # Introduction
	- ## Critère pour distinguer les espèces
		- Morphologie similaires
		- Inter-fertilité
			- Les individus sont capable par conception biologique de générer une descendance fertile
		- Histoire évolutive commune
	- ## Mécanismes des isolements reproducteurs
		- ### Définition
			- Toute propriété de 2 espèces qui limite leur hybridation
		- ### Fonction
			- L'isolement reproducteur est au cœur de la spéciation 
		- ### Types
			- Pré-zygotique
				- Avant la fécondation
			- Post-zygotique
				- Après la fécondation
	- ## Les types de spéciation
		- ### Allopatrique
			- #### Définition
				- Elle survient lorsque des populations d'une même espèce sont **géographiquement isolées** les unes des autres par une barrière physique (montagne, rivière, océan, etc.)
				- Cette séparation empêche le flux de gènes entre les populations, favorisant leur évolution indépendante par dérive génétique, mutation, et sélection naturelle, ce qui peut conduire à l'apparition de nouvelles espèces
			- #### Exemple
				- Formation de nouvelles espèces de poissons dans des lacs isolés
		- ### Péripatrique
			- #### Définition
				- Se produit lorsqu'une petite population marginale s'isole **à la périphérie** de la population principale
				- Cette petite taille favorise un effet fondateur et une évolution rapide par dérive génétique et sélection
			- #### Exemple
				- Apparition de nouvelles espèces sur des îles éloignées de la population source continentale
		- ### Parapatrique
			- #### Définition
				- Elle survient lorsque deux populations adjacentes occupent des habitats **contigus mais différents** et que la sélection naturelle favorise des adaptations locales 
				- Bien qu’il n’y ait pas de barrière géographique stricte, le flux de gènes est réduit en raison de la sélection divergente ou d'un accouplement non aléatoire
			- #### Exemple
				- Diversification des plantes en réponse à des sols toxiques dans une partie de leur aire de répartition.
		- ### Sympatrique
			- #### Définition
				- Elle se produit dans une **même région géographique** (les aires se chevauche largement voire complètement), sans séparation physique, en raison de mécanismes biologiques comme la polyploïdie, la sélection sexuelle, ou l'adaptation à des niches écologiques distinctes.
			- #### Critères
				- Les aires se chevauche largement voire complètement
				- L'histoire biogéographique et évolutive des groupes doit rendre l'existence d'une phase allopatrique très improbable (exemple, les poissons dans les lacs de volcan en pointe)
				- La spéciation doit montrer un isolement reproductif important
				- Les espèces sympatriques doivent être des espèces sœurs endémiques formant un clade monophylétiques
			- #### Exemple
				- Divergence des poissons cichlidés dans le même lac, exploitant différentes ressources alimentaires.
		- ==> ![[Pasted image 20241130205258.png]]
- # Modèles d'évolution des gènes dans la spéciation
	- ## Spéciation écologique (cause extrinsèque)
		- ### Définition
			- Processus par lequel de nouvelles espèces se forment à la suite d'une sélection divergente entre environnements écologiquement contrastés
			- Sélection divergente sur des loci impliqués dans l’isolement reproducteur
				- Pre-zygotique : ex: gènes impliqués dans le choix de l’habitat
				- Post-zygotique : ex: si les hybrides sont contre sélectionnés
		- ### Types
			- Modèle DA ("Divergent Adaptation")
			- Modèle SO ("Shared Optimum")
	- ## Spéciation non écologique (cause intrinsèques)
		- ## Définition
			- Processus par lequel de nouvelles espèces se forment ~~à la suite d'une~~ **sans** sélection divergente entre environnements ~~écologiquement contrastés~~ **similaires**
			- Divergence sur des loci impliqués dans l'isolement reproducteur
				- Pre-zygotique : ex: gènes impliqués dans le choix de l’habitat
				- Post-zygotique : ex: si les hybrides sont contre sélectionnés
		- ## Règle de Haldane
			- ### Principe
				- `Lorsque, dans une espèce hybride, un sexe est absent, rare ou stérile, ce sera presque toujours le sexe hétérogamétique.`
				- Si un croisement interspécifique produit des hybrides, ceux-ci peuvent souffrir de problèmes comme l'**inviabilité (mortalité)** ou la **stérilité**.
			- ### Pourquoi ?
				- #### Hypothèse du déséquilibre de dominance
					- Les gènes responsables des incompatibilités hybrides (incompatibilités entre les génomes des deux espèces) sont souvent liés au chromosome X ou Z. Comme le sexe hétérogamétique n’a qu’un exemplaire de ces chromosomes (et donc pas de copie "de secours"), les effets des mutations délétères ou incompatibilités sont plus sévères.
				- #### Effets des incompatibilités génétiques
					- L’accumulation de différences génétiques entre espèces peut perturber le développement des hybrides, en particulier lorsqu’il y a des déséquilibres dans l’expression des gènes liés aux chromosomes sexuels
			- ### Exemples
				- #### Chez les mammifères
					- Sexe hétérogamétique : mâles XY : Les hybrides mâles issus du croisement entre deux espèces sont souvent stériles ou non viables (ex. : le croisement entre un âne et une jument produit des mulets stériles)
				- #### Chez les oiseaux
					- Sexe hétérogamétique : femelles ZW : Les femelles hybrides sont plus susceptibles d’être stériles ou non viables que les mâles.
			- ### Limites
				- S'applique principalement aux croisements entre espèces proches (spéciation récente)
		- ## Modèle Bateson-Dobzhansky-Muller : Théorie de la dominance
			- ### Définition
				- Utilisée pour expliquer pourquoi les hybrides entre deux espèces proches présentent souvent des caractères asymétriques d'inviabilité ou de stérilité, selon leur sexe (en lien avec la règle de Haldane).
				- Elle postule que les incompatibilités génétiques responsables des problèmes chez les hybrides résultent de **mutations récessives** présentes sur les chromosomes sexuels (comme le chromosome X chez les mammifères) ou les autosomes.
				- Chez les hybrides **hétérogamétiques** (ex. : XY chez les mammifères, ZW chez les oiseaux), il n’y a qu’un seul exemplaire du chromosome sexuel hétérozygote (par exemple X ou Z) 
					- --> Les allèles récessifs incompatibles sur ces chromosomes s’expriment directement, car il n'y a pas d’allèle "dominant" pour compenser l’effet de ces mutations 
					- --> En revanche, chez les hybrides **homogamétiques** (XX ou ZZ), ces mutations récessives sont masquées par la présence d’un allèle normal sur l’autre chromosome
			- ==> Le sexe heterogamétique devrait subir la règle de Haldane, que se soit les mâles ou les femelles
			- ==> Le sexe heterogamétique devrait être plus rapidement affecté par la divergence durant la speciation
		- ## Spéciation conflictuelle
			- ### Définition
				- Différences de mode de transmission entre loci du genome ==> Conflit intra-génomique
				- Ce conflit peut entraîner l’évolution de résistance
				- Ces systèmes à 2 loci peuvent être spécifiques de chaque population
			- ### Exemple
				- #### Distortion de la ségrégation sex-ratio
					- Certains allèles manipulent les règles du jeu de la meïose
					- Exemple du X "mante religieuse", où on a de - en - de mâles dan sla pop
					- ==> Toute mutation « résistante » à ce phénotype localisée sur le Y ou sur les autosomes sera fortement sélectionnée
					- ==> Evolution de gènes de résistance sur les autosomes
				- #### Conflits nucléo-cytoplasmiques
				- #### Conflits entre les éléments transposables et le génome (dysgénèse hybride)
	- ==> Dans les 2 cas (Modèle DA ou SO) : divergence attendue sur les loci impliqués dans l’isolement reproducteur
	- ## Comment détecter ces gènes de spéciation ?
		- Croisement au laboratoire en analysant les recombinants
		- « Genome divergence scan » sur des espèces en formation à la recherche d’îlots de différentiation
		- ==> Flux géniques attendus sur les loci non impliqués dans l’isolement reproducteur
		- ==> Absence de flux géniques attendus sur les loci impliqués dans l’isolement reproducteur
		- En utilisant des hybrides : Théorie du renforcement
			- L’isolement pré-zygotique est plus fort pour les espèces sympatriques
			- ![[Pasted image 20241130224032.png]]
			- `« Lorsque les hybrides ont un désavantage sélectif, la sélection naturelle va favoriser les individus porteurs de traits leur permettant d’éviter de produire ces hybrides »`
- # Admixture
	- ## Définition
		- Désigne le processus par lequel des populations génétiquement distinctes s'hybrident, entraînant un mélange de leurs génomes dans la descendance. Cela résulte souvent de migrations ou de flux de gènes entre populations qui étaient auparavant isolées.
	- ## Caractéristiques
		- Concerne des populations ou des espèces distinctes.
		- Produit un génome hybride contenant des proportions variables des génomes ancestraux.
	- ## Exemples
		- Le mélange génétique entre Néandertaliens et Homo sapiens.
		- L'admixture entre Européens, Africains, et Amérindiens dans les populations des Amériques.
- # Introgression
	- ## Définition
		- Cas particulier de flux de gènes où des allèles ou des segments génomiques d'une espèce (ou population) s'intègrent dans le génome d'une autre espèce (ou population) à la suite d’hybridation et de croisements répétés avec l'espèce réceptrice.
	- ## Caractéristiques
		- Ne concerne généralement que certaines parties du génome, pas un mélange complet comme dans l'admixture.
		- Se produit souvent sur plusieurs générations, par rétro-croisements avec l'espèce réceptrice.
	- ## Exemples
		- Des allèles adaptatifs d’espèces archaïques (comme Néandertal ou Denisovien) présents dans le génome des Homo sapiens modernes.
		- L'introgression d’allèles de résistance à certains parasites chez des plantes cultivées à partir d’espèces sauvages apparentées.
- ![[Pasted image 20241130224802.png]]

---

# ==Aurore Gallot = Stress des génomes==

- # Introduction
	- ## Quels sont les stress ?
		- N'importe quelle conditions de vie sous-optimal ==> Un environnement qui réduit la fitness de l'individu
	- ## Les types de réponse
		- ### Immédiate
			- ![[Pasted image 20241130232159.png]]
		- ### Long terme
			- ![[Pasted image 20241130232218.png]]
	- ## Les couches génomiques concernées
		- ### Expression de gène
			- #### Organismes modèles
				- Les levures ==> Stress osmotique
				- Les drosophiles ==> Stress thermique
					- Après un stress, on peut voir sur les chromosomes des puffs indiquant une activité intense de synthèse d'ARN
			- #### Cinétique et dynamiques
				- ##### Modification post-traductionnelle
					- Immédiate mais transitoire
				- ##### Régulation post-transcriptionnelle
					- Régulation de la traduction et export des ARN
				- ##### Synthèse transcriptionnelle
					- Important changement après 1 à 3min
				- ##### Synthèse protéique
					- Maximale en 30min
			- #### Les targets
				- ##### La machinerie de sensing
					- Les senseurs spécifiques
						- HSP (=Heat Shock Protein)
							- Détection de l'accumulation de protéines dénaturées
						- HSF (=Heat Shock Factor)
							- Facteurs de transcription
					- La déstabilisation structurale
						- Altération de l'ADN
						- Les RNA hairpins meltings
						- Dénaturation des protéines
						- Destabilisation des lipides membranaires
				- ##### Les signaux de transductions
					- SAPK (=Stress-Activated Protein Kinase)
						- Dans tous les eucaryotes
					- MAPK (= Mitogen-Activated Protein Kinase)
						- Principal voie d'activation des réponse aux stress physiques, chimiques et biologiques
				- ##### Les effecteurs
					- Activation transitoire (limité dans le temps) sinon cela réduit la fitness des individus
					- Réponse de la transcription proportionnelle à l'intensité du stress
			- #### Réponses de la transcription
				- ##### Chez la levure
					- ![[Pasted image 20241130235110.png]]
				- ##### Chez les multicellulaire 
					- ![[Pasted image 20241130235129.png]]
				- ==> ![[Pasted image 20241130235431.png]]
			- #### Que nous apprend les autres espèces
				- ##### Daphnia pulex
					- 36% de gènes orphelins
					- Certaines familles de gène extrêmement dupliqué (x70)
					- ==> Les gènes orphelins sont plus exprimé en condition de stress
					- ==> Importance des duplications local des gènes pour la néo/sub-fonctionnalisation
					- ==> La majorité du transcriptome est spécifique de l'environnement
					- ==> Grande importance de l'ARN non codant
				- ##### Corail
					- Perte de leur algue endo-symbiote = Bleaching
					- ==> Certains profils transcriptionnels de gènes confèrent de la tolérance au stress : 3 types de profils
						- Frontloading
							- Lorsque les gènes avec un taux d'expression basale élevée mais avec une plasticité d'expression réduite facilite la tolérance au stress ==> Promeut les réponses immunitaires protectrices
							- Exemples : HSP70, TNF
						- Dampening
							- Plasticité réduite de gènes (métabolique, ribosomal, apoptose, HSP) associée à une tolérance au stress 
							- Les coraux tolérents retournent à une baseline d'espression des gènes plus rapidement après un stress thermique
						- Plasticité entière du transcriptome
							- Réseau de gènes protecteurs activé à haut niveau pour les coraux tolérants
			- ==>  Rapid gene expression (within minute) + Massive gene expression shift + Shift transitory only + Stress genes overexpression associated to an overall reduction of constitutive genes expression
		- ### Éléments transposables (TE)
			- L'activité des TE peut être trigger par les conditions de l'environnement via des pertes de contrôle et de répression de mécanismes épigénétiques
			- La réactivation de ces TE va faire de la mutagenèse d'insertion
			- Certains TE sont activables spécifiquement par un types de stress
				- Stress thermique et le TE mariner-Mos1, mais pas d'effet avec stress UV
			- Le TE peut simplement s'exciser (sans réinsertion)
			- ==> Stress spécifique --> Activer la mobilité pour des TE spécifiques --> Accélérer le taux de mutation --> Moduler l'expression de certains gènes (insertion (CDS ou promoteur) + dupplication) de façon **qualitative** et **quantitative**, voire héritable si dans les cellules germinales --> Modifications phénotypiques
		- ### Composantes épigénétique
			- #### Généralités
				- Modifications qui ne persistent pas toute la vie
				- Changements très précis dans le temps et l'espace (stades de développement par exemple)
				- Contribue à l'expression spécifique des gènes selon le tissus et la ligné cellulaire
				- Peut réprimer l'activité des TE
				- Certaines modifications peuvent être héritables
			- #### Modification ADN : Méthylations îlots CpG
				- Évènements d'hyper ou hypo-méthylation
				- Principalement sur les îlots riches en CpG
			- #### Modification chromatine : Histones
			- #### ARN non codants
			- ==> Il y a une forte relation entre les modifications épigénétiques et les TE
		- ### Mutations induites par le stress
			- Le plus souvent les réparations et mutations sont détectées et réparées (ou tolérées) MAIS... parfois non --> On a donc des mutations qui persistent et qui dépendent de :
				- Locus 
					- Les méthylations sur les CpG augmentent la proba de muter les T
					- Grandes indels dans les régions de chromatines ouvertes
					- Évolution accélérée dans les régions activement transcrites (euchromatine)
				- Espèce
				- Conditions environnementales (stress)
					- Augmente les dommages à l'ADN
						- Directement
							- Cassures des brins (simples ou doubles)
							- Sites apuriques
							- Déamination des cytosines...
						- Indirectement
							- Augmentation de la production des ROS (=Reactive Oxygen Species)
					- Augmentent les mutations
						- Stress oxidatif, thermique, UV, hypoxie, salinité, pH
					- Inhibition des systèmes de réparations et la fidélité des réparations
						- Stress thermique limite le base excision repair
						- L'hypoxie et des toxines inhibe le mismatch repair
						- Stress thermique et hypoxie favorise les jointures d'extrémités non-homologues
			- ==> Le stress augmente l'incidence des mutations
			- ==> Le stress augment la rétention des mutations
			- ==> ==> Accumulation des mutation et donc de la diversité génétique
		- ### Réarrangements chromosomiques
			- C'est le cas le plus dramatique de mutations et le plus extrême et délétère (cancer)
- # Conclusions
	- ![[Pasted image 20241201005320.png]]
	- ![[Pasted image 20241201005337.png]]
	- ![[Pasted image 20241201005353.png]]

---

# ==Ivan Paz-Vinas = Paysages==

- # Introduction
	- ## Biodiversité
		- ### Définition
			- Concept multi-facettes qui regroupe la diversité de toutes les formes du Vivant sur Terre
		- ### Types
			- Diversité écosystème
			- Diversité spécifique
			- Diversité génétique
		- ==> La distribution de la biodiversité est **hétérogène** MAIS...
		- ==> ... **Non aléatoire** (variable dans **l'espace et le temps**) !
		- ==> ==> C'est **dynamique** !
	- ## Paysage
		- ### Définition
			- Territoire hétérogène, composée d’ensembles d’écosystèmes en interaction
			- Niveau d’organisation supérieur à l’écosystème
			- En constante évolution (dynamique paysagère)
			- Résultat de l'interaction de facteurs naturels et/ou humains
		- ### Types
			- Terrestres
			- Montagneux
			- Côtiers / marins
			- Hydrographiques, fluviaux
			- ==> Plusieurs types de paysage, avec des contraintes et méthodes parfois spécifiques
	- ## Écologie du paysage
		- ### Définition
			- Étude des processus écologiques à l'échelle des paysages
			- C'est une recherche trans et interdisciplinaire
	- ## Génétique du paysage
		- ### Définition
			- Décrire l'influence des structures éco-paysagères sur la structuration spatiale de la variabilité génétique
			- Il y a différentes approches 
				- Individu-centrées
				- Populationnelles
- # Planifier une étude paysagère
	- ![[Pasted image 20241201113218.png]]
	- ## Concepts
		- ### Pour les paysages globales
			- ### Théorie de la percolation
				- #### À l'origine
					- Formalisation des propriétés d'écoulement dans les milieux poreux
				- #### En écologie du paysage
					- Mesurer la connectivité fonctionnelle entre habitats et des taux de migration
			- ### Théorie des circuits
				- Similarités entre les circuits électriques et les paysage écologiques (résistance, conductance, courant, voltage) 
			- ### Résistance paysagère
				- Certains obstacles physiques des paysage vont modéliser la répartition de la biodiversité
			- ### Hypothèse de la perturbation intermédiaire
				- Diversité spécifique plus importante à des niveaux de perturbation intermédiaires
				- Gradients de perturbation à mesurer -> Permet de définir échelle de l’étude
		- ### Pour un type de paysage spécifique
			- #### Concept de continuum fluvial
				- Modèle descriptif longitudinal du fonctionnement écologique des cours d’eau des zones tempérées
				- Permet de faire des prédictions sur la distribution de la biodiversité le long de gradients (amont-aval, ordres des cours d’eau…)
			- #### Patrons spatiaux de variation génétique
				- ##### Types d'isolements
					- ###### Isolement par la distance
						- Plus la distance entre populations est élevée, plus la différenciation génétique entre ces populations est grande
					- ###### Isolement par l'environnement
					- ###### Isolement par les barrières
					- ###### Isolement par la résistance
					- ###### Isolement par le flux
				- ##### Diversité génétique
					- Diminution graduelle de la diversité génétique selon l’avancée du front de colonisation
	- ## Design
		- Prendre en compte l’échelle, la couverture spatiale, la résolution et la densité de l'échantillonnage
		- ### Échantillonnage conventionnel Vs à l'échelle du paysage
			- ![[Pasted image 20241201115441.png]]
			- ![[Pasted image 20241201115513.png]]
			- ![[Pasted image 20241201115527.png]]
			- ![[Pasted image 20241201115548.png]]
	- ## Données
		- ### Types
			- Environnemental Vs Génétique
		- ### Variables
			- Le plus souvent c'est : on a des variables explicatives et on cherche à expliquer certaines autres variables (On a la conséquence, on cherche la cause)
			- Mais parfois : on a des variables à expliquer et on cherche les variables explicatives (On a les causes et on veut savoir les conséquences)
		- ### Acquisition
			- Extraction ADN --> Séquençage
		- ### Statistiques et métriques
			- Cours Fablet
		- ### Bases de données
			- Suivi démographique et environnemental
			- Géographiques
			- Occupation des sols / télédétection
			- Impact humain
			- Socio-économiques
			- (Macro-)écologiques, climatiques, spatiales
	- ## Analyse
		- ![[Pasted image 20241201120746.png]]
		- ### Exemples individu-centré
			- Effets d’ouvrages routiers et ferroviaires sur le triton alpestre Ichthyosaura alpestris
			- Hypothèse 
				- Les deux ouvrages (30-40 ans) ont impacté la structuration génétique et le flux de gènes du triton
			- Simulations pour estimer le temps de latence entre la construction des ouvrages et la détectabilité de ses effets génétiques
			- Effets détectables de façon significative 
				- ==> Effets A6 théoriquement détectables
				- ==> Effets LGV-PSE non détectables
			- Seulement IBDs (Isolement By Distance) (modèles nuls) significatifs
				- Hypothèse originale non vérifiée (pas d’effets des barrières)
			- Analyses de structuration spatiale : pas d’effet des deux ouvrages
				- Dans ce cas précis : l’autoroute A6 semble perméable au flux de gènes
		- ### Exemple à l'échelle de la population
			- ![[Pasted image 20241201121742.png]]
			- Patrons spatiaux de diversité dans les paysages fluviaux
				- Concepts
					- Des attendus théoriques concernant les patrons spatiaux de diversité taxonomique dans les paysages fluviaux :
					- ==> Patron général attendu : ↗ diversité spécifique et ↘ différentiation vers l’aval ==> **« DIGD » pour Downstream Increase in Genetic Diversity**
				- Processus
					- Processus 1 : Asymétrie de flux de gènes amont/aval
					- Processus 2 : Différentiel de tailles efficaces des populations
					- Processus 3 : Processus de colonisation
					- ==> Méta-analyse et approche par simulations
					- ==> Les 3 processus peuvent générer le patron DIGD
					- ==> DIGD est un patron général MAIS il y a des exceptions !
						- Le modèle NUL et diversité maximale à perturbation intermédiaire
						- ![[Pasted image 20241201122250.png]]
			- Corrélations entre diversités génétiques/spécifiques
				- ![[Pasted image 20241201122701.png]]
				- ==> Ce qui est vrai dans un bassin versant et un groupe taxonomique donné ne l’est pas forcement ailleurs !
			- Comprendre les facteurs qui peuvent expliquer la diversité génétique observée
				- GWAS
					- Rechercher les associations loci adaptatif (non neutres) et environnement

# ==Céline Brochier = Phylogénie==

- #red^^**Céline Brochier = Phylogénie moléculaire**^^
	- **[[#green]]^^CM^^**
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
						-
$$d = \lambda * t$$							- $d$ = Distance évolutive
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
						- Si λ constant, alors d évolue linéairement avec t (hypothèse d’horloge moléculaire)
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
								- ==> Pas de variation entre sites : limite α -> ∞ tous les u sont égaux
							- Stationnarité du processus
								- Liée à l’hypothèse d’homogénéité constance des taux de substitution instantanées au cours du temps
								- Soit π A, π T , π C, π G les fréquences d’équilibre des 4 bases des deux séquences comparées, cad les valeurs vers lesquelles vont tendre les compositions en bases après un temps infini
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
							- On fait le calcul pour tous les caractères (T , θ , b)
							- On calcule les longueurs de branches b et les paramètres θ du modèle qui maximisent la vraisemblance (procédure complexe)
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
								- ==> Une valeur de boostrap de 100% ==> Un noeud ROBUSTE ≠ VRAI !
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


---
---

- # ==TP==
	- ## ==Marie Fablet==
		- ### Partie 1
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
				- ![[image_1732886381923_0.png]]
				- On va estimer les $\sigma²$
				- ![image.png](../assets/image_1732886428256_0.png)
				- Pour le modèle 1
					- Un $F_{is} \ne 0$ ==> Panmixie = Appariement aléatoire = Proportion de Hardy Weinberg respecté
						- Positif = Excès d'appariement entre apparenté
						- Négatif = Évitement d'appariement entre apparenté
					- $F_{st}$ faible ==> Pas beaucoup de différenciation entre population, les fréquences alléliques sont comparables ==> Il y a beaucoup de flux de gènes entre les population
						- Toujours positive
					- $F_{it}$ intègre les 2 autres valeurs, on regarde au globale l'écart, c'est une synthèse globale, difficile à interpréter, il faut regarder le détail des 2 autres valeurs (fis et fst)
				- Pour le modèle 2
					- Il y a un écart globale car fit grand
					- On reagrde le fis ==> Il est très faible (donc panmixie) et donc tout l'écart est du à ce qui est détecté par le fst
					- Il y a une différenciation significative entre les population ==> Peu de flux de gène ==> Colle bien avec les données de l'énoncé (Population qui dispèrse peu)
				- Pour le modèle 3
					- fit grand ==> Très grand écart dans le cadre de Hardy Weinberg on regarde les autres valeurs
					- fst faible ==> Pas de différenciation entre les pop, beaucoup de flux de gène
					- fis grand ==> Pas de panmixie ==>  beaucoup d'appariement entre apparenté
				- ==> Savoir la méthode cochérame, carré moyen à la variance, anova et obtenir les fit, fis, et fst
				- ==> Savoir interpréter biologiquement les fis, fst et fit
		- ### Partie 2
			- Localité dans les pays
				```R
				summary(as.factor(world$Population))
				```
			- ==> Une région contient des géographie qui contiennent des Pop qui contiennent des Individus (diploïdes)
				```r 
				world[1:5,1:8]
				```
			- Dans les colonnes on a l'ID de l'individus, l'id de sa pop, l'id de sa région, pays puis on a des locus de micro-satellites
				- Par exemple le premiers individus (2 premieres ligne car diploïdes) est homozygote pour le 1er locus contrairement au 2e individu (les 2 lignes suivantes)
				```r
				par(mfrow=c(1,2))
				barplot(table(world[,6]))
				barplot(table(world[,7]))
				```
				- Colonne 6 c'est le premier locus
				 ![image.png](../assets/image_1732891581376_0.png)
				 - C'est différent de tout à l'heure car là on a beaucoup d'allele sur chaque locus (les micro-satellites ont beaucoup ++++++ d'allele) ==> Le taux de mutation \mu est très élevé et le StepWise mutation ne permet pas de remplir les conditions de Wright, on ne peut pas utiliser le Fst ==> On va utiliser le $\phi_{st}$ (marche tout le temps) qu'on obtient avec une AMOVA ou le $R_{st}$
					 - Le stepwise mutation (mutation pas à pas, une mutation peu donner un allèle déja présent dans la pop) \ne Infinite Allele Mutation model (chaque mutation crée un nouvel Allèle)
		```r
		1 - sum(p^2) # C'est Hs sur le premier locus
		[1] 0.737893
		```
		- Hs pour le 1er locus élevé : On est très loin de 0.5, on a donc une richesse allélique très importante pour ce locus
			- Pour tous les locus
				 ![image.png](../assets/image_1732892312333_0.png)
				 - La majorité des loci sont alléliquement très riches
		 - Analyse génétique
			 - Estimations de F_{stats}
				```r
				varcomp.glob(levels=worldhier[,1],worldhier[,2:21])
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
				- `$overall`
					- C'est les Variances (sigma²) comme tout à l'heure
				- `$loc`
					- Variance par locus
				- `$F`
					- $F_{is} = 0.016$
					- $F_{st} = 0.08$
					- $F_{it} = 0.09$
					- $F_{is} \ne 0$ ==> En moyenne, il y a de la panmixie
					- $F_{st}$ à comparer avec le graphique dessous pour faire un test savoir si c'est significativement différent de 0
					 ![image.png](../assets/image_1732893401343_0.png)
					```r
					testFst$g.star[100]
					15460.43
					testFst$p.val
					0.01
					```
				- On voit que la valeur calculé sur les vraie donné sont pas en accord avec la distribution sous H0 ci-dessus + la p-value nous montre que c'est significativement $\ne 0$ ==> Différenciation significative
					- Isolement par la distance
					- On utilise le $F_{st}$ comme métrique de distance génétique
				- ![image.png](../assets/image_1732893669800_0.png)
					- Il semble y avoir une corrélation positive, plus les pop sont éloigné géographiquement, moins les flux de gène sont important et donc plus elles sont différentes génétiquement = Isolement par la distance
					- Le problème avec ce graphe c'est que les point ne sont pas indépendant entre eux, on utilise donc le test de Mantel (principe du test de permutation, on mélange les lignes et colonnes, on détruit les potentielles corrélations on calcul la distribution sous l'hypothèse nulle et on compare avec ce que l'on a pour nos vraie données)
				```r
				ibd = mantel.randtest(distGenet, distGeo, nrepet=1000)
				ibd
				
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
			```r
			Htheo[1:4,]
			[,1]         [,2]               
			[1,] "Adygei"     "0.716694734223818"
			[2,] "Balochi"    "0.724429266995916"
			[3,] "BantuKenya" "0.752143874030711"
			[4,] "Basque"     "0.712794162552817"
			```
			- On a donc ici le $\bar{H_{s}}$ théoriques pour chaque population
				- Relation avec la distance à l'Afrique de l'Est
					 ![image.png](../assets/image_1732894523858_0.png)
					```r
					cor(as.numeric(Htheo[,2]), distancesAfr$DistAA) ^2 
					[1] 0.8028861
					```
					- ==> Les pop avec le niveau de diversité le plus grande est les pop Africaine cela s'explique par les effets fondateurs en série
						- A partir du site d'origine, un groupe migre à coté (effet fondateur -> derive génétique -> perte de diversité génétique) et à nouveau à chaque migration des pop dans un autre site
						- A chaque nouveau effet fondateur, on accumule les effet fondateurs précédent et donc on accumule les pertes génétiques ==> Moins de diversité génétique
						- On a un R² = 80% de la variation de la variable en Y (la différenciation génétique) expliqué par la relation linéaire en X (la distance de migration, l'histoire démographique de la pop humaine)
						- ==> On s'en fiche des commandes mais il faut savoir interpréter les sorties !!!!

	- ## ==Ivan Paz-Vinas==
		- ## IP Paysage
			Question 1 :
				Dans CHE.txt
					Une première ligne libre, pas d'information
					n premières lignes => Noms des marqueurs (ici de type micro-satellite)
						Ca01, CypG30, ...etc
					Une ligne = 1 individus
						Colonne 1 = Nom de la pop
							AGOLav
						Colonne 1 à n = Allèles portés par l'individus pour les n marqueurs
					Les 10 premiers chiffres de la ligne
						08|10 => individu hétérozygote : 1 allèle 08 et un autre allèle 10 pour le gène Ca01
			Question 2 :
			Question 3 :
				Gendata@tab
					Est ce que l'allèle 01 du marqueur/locus Ca01 est présent (1) ou non (0)
				Gendata@loc.n.all
					Nombre total d'allèle différents par marqueur dans toute la population
						Le + polymorphe ici est CypG27
				Gendata@all.names
					Nom de l'allèle pour chaque marqueurs
				Gendata@pop
					Nom de la population pour chaque individu
						Ici on a 66 pop différentes
			Question 4 :
				La richesse allélique moyenne (AR) par locus et par population
					On aura 1 seule valeur par pop
					Renseigne sur la diversité génétique d'une population
					C'est différent du nombre moyen d’allèle par population car on peut avoir un effet d'échantillonnage
					Cette valeur est standardisé, corrigé pour éviter ce biais là d'échantillonnage
						Il n'y aura pas plus de diversité parce qu'il y aura plus d'échantillon
				L’hétérozygotie attendue moyenne (He) par locus et par population
					Plus elle est élevé, plus il y a de la diversité génétique dans la pop
				La richesse en allèles privés moyenne (PA) par locus et par population
					Allèle privé = allèle exclusif à une population et pas retrouvé dans une autre pop
					Plus PA est élevé, plus elle a des allèles spécifique à cette pop, plus cette pop est unique => On a toute intérêt à préserver ces pop sinon on perd ces allèles
			Question 5 :
				![1686550a-0b7e-48bc-9b48-36e44d1f51d5.png](../assets/1686550a-0b7e-48bc-9b48-36e44d1f51d5_1733151262724_0.png)
				Oui il semble y avoir un patron
				L'aval est à gauche, on est proche de l'embouchure et on a le plus de diversité génétique
				L'amont est à droite, on est loin de l'embouchure et on a le moins de diversité génétique
				On a une accumulation de diversité génétique
			Question 6 :
				![40dd2ddf-14d8-4677-9663-f4524ee8c021.png](../assets/40dd2ddf-14d8-4677-9663-f4524ee8c021_1733151432683_0.png)
				C'est pareil, He et AR sont très corrélé
				![feade899-ba7d-4db4-a468-046efd372026.png](../assets/feade899-ba7d-4db4-a468-046efd372026_1733151477254_0.png)
				On voit que là cela semble pas significatif
			Question 7 :
				![b0a3dfeb-a296-4426-b7c8-f42db646f1d7.png](../assets/b0a3dfeb-a296-4426-b7c8-f42db646f1d7_1733151527215_0.png){:height 431, :width 718}
			Question 9 :
				![01f893ae-acf8-457b-90e6-9c5671ea3fe7.png](../assets/01f893ae-acf8-457b-90e6-9c5671ea3fe7_1733151564800_0.png){:height 431, :width 718}
				![3551592d-9bc7-4cc3-bba4-456d7a9dedbe.png](../assets/3551592d-9bc7-4cc3-bba4-456d7a9dedbe_1733151584113_0.png){:height 431, :width 718}
				On voit qu'il y a 2 populations qui sont bien différentes génétiquement des autres pop
			![430fecf0-43b4-4561-bfce-5d5b6c81177a.png](../assets/430fecf0-43b4-4561-bfce-5d5b6c81177a_1733151606877_0.png)
			On calcule la distance physique entre chaque point
			![07d45bd6-dd70-481a-a7cc-9d8170e2361b.png](../assets/07d45bd6-dd70-481a-a7cc-9d8170e2361b_1733151624714_0.png){:height 449, :width 749}
				On regarde a quelles point les points sont distant du réseau des rivières (les coordonnées GPS prises sur le terrain ne sont pas toujours super précises et pas forcément sur les coordonnées de la rivières => On utilise donc un snapping)
				On prend les points et les rapproche du cours d'eau le plus proche et après on peux calculer la matrice de distance
				![75828d3d-bbd2-4c56-aa6f-312394b5a4db.png](../assets/75828d3d-bbd2-4c56-aa6f-312394b5a4db_1733151650152_0.png){:height 431, :width 718}
			Question 10 :
				![0fdff9d2-65e9-4ddb-bf90-8900b3c5feb0.png](../assets/0fdff9d2-65e9-4ddb-bf90-8900b3c5feb0_1733151668643_0.png)
				Le mantel nous dit que c'est significatif et que le patron IBD est bien réel, plus les pop sont distantes plus elles sont différentes génétiquement
				On a une augmentation générale de la diversité génétique en fonction de la distance entre chaque pop
			Question 11 :
				La mrm montre qu'il semble il y a voir un effet mais peu fort du courant

	- ## ==Julien Varaldi = Spéciation==
		- Question 1 :
			- Les espèces ont des écologies similaires, morphologies...etc ==> Spéciation non écologique
		- DDrad = Séquençage autour des sites de restrictions, polymorphisme du génome visible sans séquencer tout le génome
		- Question 2 :
			- Dans le modèle de Wright :
				- On a une pop (p) qui contient 2 sous-pop (p1 et p2) qui chacune comporte plusieurs individus et dans chaque individus 2 allèles
					-
$$\bar{p} = \frac{p_1 + p_2}{2}$$					- Pour $p_{ 1}$ :
						-
$$Hétérozygotie_{Sous-pop1} = 2*p_1*q1$$					- Pour $p_{ 2}$
						-
$$Hétérozygotie_{Sous-pop2} = 2*p_2*q2$$					-
$$\bar{HétérozygotieMoy_{Sous-pop}} = \frac{Hétérozygotie_{Sous-pop1} + Hétérozygotie_{Sous-pop2}}{2}$$					- Pour la Pop Totale :
						-
$$Hétérozygotie_{Pop-Totale} = 2 * \bar{p} * \bar{q}$$				- Et on peux calculer le taux d'hétérozygotie à ces différentx niveaux
			-
$$F_{st} = \frac{Hétérozygotie_{Pop-Totale} - \bar{HétérozygotieMoy_{Sous-pop}}}{Hétérozygotie_{Pop-Totale} } = \frac{Variance(p)}{\bar{p}*(1-\bar{p})} = ?$$			- Ici, on a :
				- $p_{1} = \frac{2 * 12 +23}{54 * 2} = 0.43$
				- $p_{2} = 0.58$
				- $\bar{HétérozygotieMoy_{Sous-pop}} (\bar{H_s})= 0.49$
				- $\bar{p} = 0.505$
				- $Hétérozygotie_{Pop-Totale} (H_T) = 0.5$
				- $Variance(p) = \frac{1}{2}*(0.43²+0.58²)-0.505²$
			- $F_{st} = \frac{Hétérozygotie_{Pop-Totale} - \bar{HétérozygotieMoy_{Sous-pop}}}{Hétérozygotie_{Pop-Totale} } = \frac{0.5 - 0.49}{0.5} = 0.02$
			-
$$F_{st} = \frac{Variance(p)}{\bar{p}*(1-\bar{p})} = \frac{\frac{1}{2}*(0.43²+0.58²)-0.505²}{0.505*(1-0.505)} = 0.022$$				- C'est la formule brute de la variance : 1/N * Somme des carrés - moyenne carré...etc
		- Question C :
			- On voit des pics de différenciation bien définis et séparés
			- 1 pic de F_{ st} = Différence de fréquence allélique, il y a des fréquence d'allèles très différentes (elles ne sont pas fixée sinon on aurait atteint le 1). Les oiseau ne comporte pas les même fréquences d'allèles dans ces sites là
		- Question D :
			- Plus les espèce sont séparé depuis longtemps, plus leurs distance mitochondriales et nucléaire seront différent ==> C'est attendue
			- Il y a un très petit F_{ st} = elle est outlier. Elle a une divergence mito de 3 % on s'attendait donc à avoir un F_{ st} de 20%. Si ces espèces s'hybrident, les allèles vont pouvoir migrer d'une espèces a l'autre et homogénéiser les fréquence allélique ==> Il y a eu donc beaucoup d'hybridation entre les 2 espèces
		- Question E :
			- Il y a eu un phénomène qui a générer de la diversification au niveau des espèces naissantes (par exemple une barrière physique = allopatrie, voire aussi de la sélection sexuelle divergent entre ces espèces (sur des critère de plumage par exemple)), puis ensuite destruction de la barrière, les 2 pop se sont retrouvés et hybridé, et réduire la diversité génétique (baisse du F_{ st}), cette baisse est toutefois pas homogène sur tout le génome, elle ne concerne pas les locus impliqué dans la coloration du plumage, et cette différenciation au niveau de ces locus se maintient car il y a peut être une préférence pour les phénotypes qui sont similaires (homogamie très forte sur la coloration du plumage chez ces espèces de paruline). Cela n’empêche pas d'avoir des hybrides stables, fertiles, et peuvent continué à faire le passage des allèles
		- Exercice 2
			- Une inversion dans un génome (par exemple les gène A, B et C sur un locus deviennent C', B', A') à pour conséquence d’empêcher les recombinaison génétiques, les gènes sur les 2 chromosomes vont muté chacun mais on retrouveras toujours A, B avec C, et A', B' et C' ensemble, ces 3 allèles vont former une sorte de méga-allèle qui ne sera jamais recombiné
			- Question A :
				- Peut être que la pomme est présent plus tôt que l'aubépine, donc il faut être prêt plus tôt pour une mouche, et il faut donc les allèles qui sont adapté pour ça, donc fort déséquilibre ==> Ça suggère que les allèles étaient déjà présentes dans la population et ils sont monté très vite en fréquence quand le pommiers est apparues. Ce n'est pas que les allèles ont évolué, les allèles étaient déjà présent dans la pop (surement par hybridation). 2e preuve dans le tableau on voit que les allèles sont bien plus vieux que l’événement de spéciation en lui même. On avais donc déjà des allèles pré adaptés dans la population avant l’événement de spéciation
			- Question B : ∅
			- Question C : ∅
			- Question D : ∅

	- ## ==Aurore Galot==
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

	- ## ==Céline Brochier==
		- La branche existe 
			- Et elle est soutenue par un support de boostrap fort 
			- Et elle est soutenue par un support de boostrap faible 
		- La branche n’existe pas dans l’arbre reconstruit $\to$ Il y a à la place un regroupement alternatif 
			- Le regroupement alt est soutenue par un support boostrap fort 
			- Le regroupement alt est soutenue par un support boostrap faible 
			- 90-100 : fortement soutenue 
			- 80-89 : modérément soutenue 
			- <80 : pas soutenue 
		- Branche 7 ==> Retrouver par tous les marqueurs ==> Regroupement ou il y aura aucune diff 
		- Le Br 1 ==> uniquement 3 marqueurs pour supporter le regroupement loche + carpe 
			- Booststrap 63 < 80 => Manque de signal 
			- Le regroupement va être difficile à résoudre avec nos marqueurs 
		- Br 2 ==> Pas trop difficile  
		- Br 3 ==> Un peu comme la Br 1, Pour NADH4L a la limite du signal fort ==> tester d’autres méthodes pour approfondir, tester d’autres reconstructions phylogénétiques… 
		- Br 4 ==>
		- Br 5 ==> Comme  
		- NADH5 ==> Un marqueur plein de signal n’est forcement un bon marqueur qui donne la bonne phylogénie 
		- Si un marqueur est pas terrible ==> On peut écarter soit complètement un marqueur OU le garder mais retirer les séquences qui pose problème 
			- Jeter un marqueur parce qu’il y a un qu’une seule séquence qui pose problème c’est dommage 
		- Probabilité d’obs les données à condition que les séquences ont évolué le long de l’arbre que l’on considère et le modèle considéré 
		- Paramètre du modèle TN93 = 6 paramètres 
			- Pi_A : freq de la base A dans la sequence 
			- Pi_C 
			- Pi_T 
			- (Pi_G) 
			- ==> Somme des Pi = 1
		- Alpha_r = taux de transition entre bases puriques A <-> G 
		- Alpha_y = taux de transition entre bases pyrimidiques C <-> T 
		- Beta = taux de transversion base purique vers pyrim et inversement : A <-> C, A <-> T, G <-> C,… 
		- Hypothèses des modèles : le taux d’évolution est le même dans chaque colonne ==> Or ce n’est pas tout le temps réaliste ==> On doit donc corriger cela : 
			- On a 2 population qui sont évolutionnairement invariables 
			- Un autre qui est librement variable 
		- NNI = Petit pas autour de l’espace des arbres ==> Bien pour raffiner un arbre pour lequel on connait bien on est sur le point de depart 
		- SPR = Grands pas dans l’espace des arbres ==> Pratique si on est pas sur du point de départ mais nul pour raffiner le résultats  
		- On a un gain de vraisemblance de +730 ==> La distribution gamma est le plus fort contributeur pour le gain de la variance > Puis les invariant > Puis les méthodes d’explo des arbres 
		- Ce gain de vraisemblance n’est pas additif, certains gains pour chaque paramètre se recoupent entre elles 
		- Monophylétique ==> On peut couper une branche de l’arbre pour que tous les espèces soit du meme groupe =  caractéristique d'un groupe qui contient l'espèce souche dont descendent tous ses membres.

---
---

# ==Annales==

Fablet 2023-2024
- ### **Question 1 : Analyse en composantes principales (PCA, Figure 1)**
	- La PCA permet de visualiser la structure génétique entre les populations.
		- **Explication** : 
			- Les axes représentent les principales sources de variation génétique. Les individus proches sur le graphe partagent une similarité génétique. Le premier axe explique 4.51% de la variance totale du jeu de donnée et le 2e axe en explique 2.24%. Au total ces 2 axes expliquent assez peu de variances. 
			- Le premier axe PC1 permet de bien discriminer les population sauvages des populations commerciales. L'espèce *dalmatinus* se place entre ces 2 types de bourdons sur l'axe PC1. 
			- L'axe PC2 permet de bien différencier différents groupes parmi les espèces commercial (non native), mais pas du tout pour les espèces sauvages
		- **Résultats possibles** :
		    - Si les populations "commerciales" et "sauvages" se séparent clairement, cela indique une différenciation génétique. Ici c'est plutôt bien le cas.
		    - Une superposition pourrait suggérer un mélange ou une introgression.

- ### **Question 2 : Analyse STRUCTURE (Figure 2)**
	- STRUCTURE assigne à chaque individu une proportion d'appartenance à un ou plusieurs groupes génétiques (clusters). Dans la figure :
		- Chaque barre verticale représente un individu.
		- Les différentes couleurs correspondent aux clusters génétiques identifiés.
		- La hauteur des segments colorés indique la proportion d'appartenance à chaque cluster pour un individu.
	- **Explication** :
	    - K=2 et K=3 indiquent deux ou trois clusters génétiques prédominants.
	    - ![[Pasted image 20241205172047.png]]
	    - Avec K = 2
	        - Si les populations commerciales natives forment un cluster distinct, cela soutient leur différenciation.
	        - Les espèces sauvages froment aussi un cluster distinct, c'est donc une espèce bien différencié
	        - L'espèce dalmatinus à un chevauchement de cluster cela suggère un flux génétique entre les pop
	    - Avec K = 3
	        - Les espèce sauvage loin des fermes avec des espèces commerciales ne présentent pas d'introgression génétique (flux de gène). Les 2 pop sont bien différencié
	        - Les espèces un peu plus proches des fermes avec des espèces commerciales (comme Bognor, Broadway...) présentent très peu d'introgression génétique car dans ces espèces là on retrouve un peu les meme couleur que l'on retrouve pour les espèces commerciales, mais cela reste très faible ==> Globalement pas de flux de gène entre eux, bonne différenciation et pas d'hybridation
	        - Les espèce commerciales de la meme manières ne partagent pas les même couleur que les espèces sauvages, donc pas de flux de gène et d'hybridation (hormis entre les différentes espèces commerciales entre elles natives et non natives ==> On a une origine distinctes entre commerciales natives et commerciales non natives, elles sont génétiquement assez différentes)
	        - L'espèce dalmatinus en revanche présente clairement un mélange des couleurs que l'on retrouve chez les espèces sauvages et chez les espèces commerciales ==> Il y a donc bien un flux de gène entre les espèces ==> Introgression génétiques des espèces sauvages vers cette espèce ==> C'est une espèces commerciales qui s'hybride un peu avec toutes les autres sauvages ==> Peut etre par cet intermédiaire que l'on retrouve les très légères ressemblances génétiques entre les autres sauvages et les commerciales, dalmatinus fait le gap, le pont en s'hybridant avec les 2
	        - ==> L’analyse STRUCTURE montre une différenciation nette entre les populations commerciales et sauvages pour K=2, avec des signes d’introgression dans les populations proches des fermes. Pour K=3, un troisième cluster distinct souligne une divergence génétique entre les populations commerciales non-natives et les populations sauvages. Ces résultats suggèrent un impact génétique des bourdons commerciaux sur les populations autochtones, principalement par flux génétique dans les zones proches des fermes, et principalement pour l'espèce dalmatinus.

- ### **Question 3 : Interprétation des Fst (Tableau 1)**
	- Le Fst mesure la différenciation génétique entre populations (0 = pas de différenciation, 1 = différenciation complète).
	- **Explication** :
	    - Des Fst élevés entre populations sauvages et commerciales montrent une séparation génétique.
	    - Des valeurs faibles entre certaines populations sauvages pourraient refléter une homogénéité ou un flux génique.
	- On voit que :
		- Les espèces sauvages échantillonées à Bognor ne sont pas différencié génétiquement de celle de Broadway, celles de Treborth pas différencié de celles de Bognor et Templeton pas différencié de Broadway ==> Origine plutôt commune
		- L'espèce commercial native
			- Est différencié de l'espèce commercial non native (peu de flux de gènes entre elles), et bien différencié avec les espèces sauvages (toutes confondues)
		- L'espèce commercial non native
			- Est bien différencié des espèces commerciales natives, encore mieux des espèces sauvages vivants proches des commerciales (Bognor, Broadway, Brockholes) et encore plus différencié des espèces sauvages vivant loin des commerciales. Il ne semble donc pas y avoir de flux de gènes entre ces espèces et de panmixie entre les populations ==> Elles sont bien différenciée
		- L'espèce commercial dalmatinus
			- On retrouve les même résultats que les espèces commercial, pas de flux de gène entre sauvages et commerciales, cependant on constate que les Fst sont moins forts comparé aux autres espèces commercial, mais cela reste significativement différent de 0, donc pas de flux de gène. Mais cette espèce semblent joué un rôle un peu plus pivot

- ### **Question 4 : Analyse avec hierfstat**
	- #### a) **Explication de l’analyse et des calculs** :
		- ![[Pasted image 20241209182702.png]]
		- Pour obtenir ces valeurs, on a réalisé une ANOVA hiérarchique (méthode des moment de Cockerham ou AMOVA si normalité non respecté) des fréquence alléliques, en décomposant les effets :
			- a -> Effet de la sous population
			- b -> Effet de l'individus
			- w -> Effet intra(individu)
		- La partie `$overall` présente la variance totale (individus, populations, erreurs).
		- La partie `$F` décompose cette variance pour calculer des indices F (Fst, Fit, Fis) : 
		- $F_{{it}}​ = \frac{\sigma²_{pop} + \sigma²_{ind}}{\sigma²_{pop} + \sigma²_{ind} +\sigma²_{error}} = \frac{9.491374 + 1.505261}{9.491374 + 1.505261 + 104.861109} = 0.0949$
			- Proportion de la variance génétique totale qui est due à la différenciation entre individus, sans tenir compte des populations.
			- Plus FIT​ est élevé, plus les individus dans l'ensemble des populations diffèrent les uns des autres (indépendamment de la population d'origine).
		- $F_{\text{st}} = \frac{\sigma²_{pop}}{\sigma²_{pop} + \sigma²_{ind} +\sigma²_{error}} = \frac{9.491374}{9.491374 + 1.505261 + 104.861109} = 0.0819$
			- Proportion de la variance génétique totale due à la différenciation entre les populations.
			- **Interprétation :**
				- FST​ proche de 0 : Les populations ne sont pas différenciées (fort flux génétique).
				- FST​ proche de 1 : Les populations sont très différenciées (isolement reproductif ou faible flux génétique) ==> Il y a une forte structuration des populations
		- $F_{\text{is}} = \frac{\sigma²_{ind}}{\sigma²_{ind} +\sigma²_{error}} = \frac{1.505261}{1.505261 + 104.861109} = 0.0141$
			- Déviation de l'hétérozygotie observée au sein des populations par rapport à l'hétérozygotie attendue sous un équilibre Hardy-Weinberg.
			- **Interprétation :**
				- FIS>0 indique un déficit en hétérozygotes dans les populations (inbreeding ou consanguinité locale).
				- FIS<0 indique un excès d'hétérozygotes (Avantage sélectif pour les hétérozygotes, Lorsque deux ou plusieurs populations, initialement différenciées, se mélangent, et augmentent artificiellement la proportion d'hétérozygotes par rapport à l'équilibre attendu, mutations récentes, assortative mating (Des individus qui préfèrent s'accoupler avec des partenaires génétiquement très différents), Migration et flux génétique important).
				- FIS=0 signifie que les populations respectent l'équilibre Hardy-Weinberg et donc manmixie.
	- #### b) **Test de significativité** :
		- Un test (par permutation ou bootstrap) évalue si le Fst observé est significativement différent de 0.
			- Permutation
				- Test de Mantel ==> Principe du test de permutation, on mélange les lignes et colonnes, on détruit les potentielles corrélations on calcul la distribution sous l'hypothèse nulle et on compare avec ce que l'on a pour nos vraie données)
	- #### c) **Interprétation des résultats** :
		- $F_{{it}}​ = \frac{\sigma²_{pop} + \sigma²_{ind}}{\sigma²_{pop} + \sigma²_{ind} +\sigma²_{error}} = \frac{9.491374 + 1.505261}{9.491374 + 1.505261 + 104.861109} = 0.0949$
			- $F_{\text{it}} \ne 0$ --> **Les individus dans l'ensemble des populations semblent différer les uns des autres (indépendamment de la population d'origine)**, (il faut toutefois faire un test de significativité (test de Mantel via permutation ou bootstrap ?) )
			- On regarde les autres valeurs F pour avoir plus de précision
		- $F_{\text{st}} = \frac{\sigma²_{pop}}{\sigma²_{pop} + \sigma²_{ind} +\sigma²_{error}} = \frac{9.491374}{9.491374 + 1.505261 + 104.861109} = 0.0819$
			- **8.19% de la variation génétique totale** est attribuée aux différences entre populations 
			- $F_{\text{st}}$ est significativement différent de 0 (selon la consigne) --> Il y a donc **significativement peu de flux entre les 2 populations** et les **fréquences alléliques ne sont pas significativement comparables** -->On a donc **2 populations (commerciales et sauvages) avec un génome significativement différent** l'une de l'autre --> **Pas d'introgression/hybridation des colonies commerciales vers les colonies sauvages** --> L'introduction des espèces commerciales n'impacte pas les espèces sauvages
		- $F_{\text{is}} = \frac{\sigma²_{ind}}{\sigma²_{ind} +\sigma²_{error}} = \frac{1.505261}{1.505261 + 104.861109} = 0.0141​ > 0$
			- Coefficient de consanguinité/hétérozygotie intra-population
			- **1.4% de la variation génétique totale** est attribuée aux différences de proportion d'hétérozygote dans les population par rapport aux attentes sous Hardy-Weinberg
			- $F_{\text{is}} \text{ proche de } 0$ --> Il faut tout de même réaliser un test de significativité mais on peut supposer qu'il y a une **panmixie** = Appariements **aléatoires** des individus = Proportions de **Hardy Weinberg respectées** --> Les espèces commerciales et sauvages s'hybrident entre elles ==> Résultats contradictoires avec le $F_{st}$ ???
		- ==> Conclusions : On ne peut donc pas conclure que les espèces de frelons commerciaux soient invasives pour les espèces sauvages, car les différentes métriques montrent que les populations sont génétiquement bien différentes et les 2 populations ne s'hybrident pas entre elles.
		- Un Fst élevé implique une différenciation génétique notable entre populations.
		- Le $F_{it}$ = 0.09 faible
			- Différenciation globale (individus par rapport à l’ensemble des populations)
			- Intègre les 2 autres valeurs, on regarde au globale l'écart, c'est une synthèse globale, difficile à interpréter, il faut regarder le détail des 2 autres valeurs (fis et fst)
			- Faible écart dans le cadre de Hardy Weinberg on regarde les autres valeurs
			- Environ **9% de la variation génétique totale** est attribuée à la structure génétique globale.
		- Le $F_{is}$ = 0.0141
			- Évalue l'écart par rapport à l'équilibre de Hardy-Weinberg au sein des populations (déficit ou excès d'hétérozygotie).
			- Un $F_{is} = 0$, ou proche de 0 ==> Panmixie = Appariement aléatoire = Proportion de Hardy Weinerg respecté
			- Un $F_{is} \ne 0$ ==> Non Panmixie = Appariement non aléatoire = Proportion de Hardy Weinerg non respecté
				- Négatif = Évitement d'appariement entre apparenté ==> Excès en hétérozygote et déficit en homozygote 
					- ==> Avantage sélectif pour les hétérozygotes, Lorsque deux ou plusieurs populations, initialement différenciées, se mélangent, et augmentent artificiellement la proportion d'hétérozygotes par rapport à l'équilibre attendu, mutations récentes, assortative mating (Des individus qui préfèrent s'accoupler avec des partenaires génétiquement très différents), Migration et flux génétique important
				- Positif = Excès d'appariement entre apparenté ==> Déficit en hétérozygote et excès en homozygote
					- => Consanguinité locale ou des sous-structures au sein des populations (les individus ne s'accouplent pas aléatoirement).
- ### **Question 5 : Bilan de la structure génétique**
	- #### Synthèse des résultats :
		- Les populations sauvages ne sont pas influencées par l'introduction des populations commerciales
		- Toutefois la différenciation génétique varie selon la proximité aux fermes commerciales, mais globalement, il n'y a significativement pas d'introgression d'une espèce vers l'autre.

- ### **Question 6 : Régions du génome à Fst élevé**
	- Des régions avec un Fst élevé suggèrent une forte sélection diversifiante/perturbatrice localement 
		- Définition
			- Dans certains scénarios, deux extrêmes d’un trait peuvent être plus favorables dans l’environnement qu’un trait intermédiaire. Le pyréneste ponceau (_Pyrenestes ostrinus_) présente un polymorphisme impressionnant pour la taille du bec qui n’est déterminé ni par le sexe, ni par la taille du corps, ni par l’âge ni par l’origine géographique. Il existe deux morphologies distinctes majeures, à petit bec et à grand bec. Ce trait est contrôlé par un seul locus autosomique, les grands becs étant dominants. Ces deux morphologies distinctes du bec permettent au pyréneste ponceau de manger facilement les graines de différents carex. Les pyrénestes ponceaux à petit bec mangent principalement des espèces de carex avec des graines plus molles, tandis que les oiseaux à gros bec peuvent casser les graines plus dures d’autres espèces de carex. Cependant, les oiseaux avec des becs de tailles intermédiaires ne peuvent manger facilement ni l’un ni l’autre type de graines et donc on ne les voit pas souvent.
		- **Interprétation** :
		    - Fst grand --> Grande différentiation génétique entre les différentes pop pour ces locus 
		    - Les gènes du système gustatif pourraient être sous forte sélection diversifiante, peut-être liés à des adaptations alimentaires ou des préférences spécifiques pour des groupes spécifiques au sein des populations --> Cela permet aux différentes populations de ne pas être en compétitions pour les ressources et de pouvoir coexister sans s'hybrider 

- ### **Question 7 : Comparaison Fst et Qst**
	- Le Qst mesure la différenciation phénotypique (ici la pigmentation).
	- **Interprétation** :
	    - Un Qst plus élevé que le Fst indique une sélection divergente sur la pigmentation entre Broadway et Thurso
	    - Les 2 populations sont donc bien significativement différente même d'un point de vue phénotypique

---

Varaldi 2023
- ### **1. Quels phénomènes, importants du point de vue de la spéciation, ont pu se mettre en place pendant la période d’isolement génétique ?**
	- **Isolement géographique** : 
		- Pendant les glaciations, les populations de _Setophaga occidentalis_ et _Setophaga townsendi_ étaient séparées géographiquement. Cela a permis l'arrêt du flux génétique entre les populations.
	- **Dérive génétique** : 
		- Avec l'isolement géographique, les mutations se sont accumulées dans chaque population, renforçant les différences génétiques.
	- **Sélection naturelle divergente** : 
		- Dans des environnements distincts, chaque espèce a évolué pour s'adapter à ses conditions locales.
	- **Spéciation allopatrique** :
		- Ce processus a pu conduire à des divergences phénotypiques et comportementales favorisant l'isolement reproducteur.
	- **Effet fondateur :**
		- S’il y a eu colonisation de nouveaux habitats par de petits groupes d’individus pendant les glaciations. Il aurait alors contribué à l’accumulation de différences génétiques favorisant la spéciation allopatrique.

- ### **2. Qu’appelle-t-on "zone hybride" et quel est l’intérêt d’étudier ces zones ?**
	- Définition
		- Une **zone hybride** est une région géographique où deux espèces proches interagissent et s’hybrident, produisant des individus aux génomes mixtes.
	- **Intérêt scientifique** :
	    - Étudier le flux génétique et les barrières à l’hybridation.
	    - Comprendre la compatibilité phénotypique et génétique des hybrides.
	    - Explorer les processus évolutifs, tels que l'introgression et la sélection.

- ### **3. Interprétez la figure 1**
	- **Figure 1A** :
		- Carte des distributions. Les zones en turquoise et magenta montrent les aires respectives de _S. occidentalis_ et _S. townsendi_, tandis que la zone jaune illustre la région hybride.
	- **Figure 1B** : 
		- Les différences de plumage. _S. occidentalis_ a une joue entièrement caroténoïde (gauche), _S. townsendi_ a une tache mélanique (droite), et les hybrides ont des phénotypes intermédiaires.
	- **Figure 1C** : 
		- Indice d’hybridation. Les valeurs varient de 0 (occidentalis pur) à 1 (townsendi pur) le long de la zone hybride.
	- **Figure 1D** : 
		- Analyse en composante principale (ACP). Les hybrides se répartissent le long des axes EV1 et EV2, reflétant leur variation génétique et leur correspondance avec l'indice de plumage. L'axe EV1 explique 1.05% de la variance totale mais permet de bien discriminer les différents indice d'hybridation des individus, cet axe colle bien l'aire de répartition géographique des espèces

- ### **4. Interprétez la figure 2**
	- Cette figure montre les résultats d’un GWAS (Genome-Wide Association Study) liant le génotype à des traits phénotypiques spécifiques.
	- Les pics avec des valeurs de -log10(p-value) élevées (au-dessus du seuil de significativité) indiquent des SNPs associés de manière significative à un trait.
	- Le zoom (Fig. 2A) met en évidence le gène RALY, suggérant qu’il joue un rôle clé dans les différences de plumage au niveau de "crown", "cheek", "breast yellow" et "flank".

- ### **5. Interprétez la figure 3, en lien avec le phénotype et la fitness des hybrides**
	- Cette figure montre une association entre le SNP dans le gène RALY et le phénotype des hybrides.
	- Les génotypes "OO" (occidentalis) et "TT" (townsendi) montrent des phénotypes distincts, tandis que "OT" (hétérozygotes) présentent des caractéristiques intermédiaires.
	- Les phénotypes hybrides peuvent influencer la **fitness**, en étant soit désavantagés (en cas de sélection disruptive), soit avantageux dans des conditions intermédiaires.
	- Au niveau des parties Crown et Cheek il semble que les hybrides (OT) sont phénotypiquement plu proche des *occidentaliss* pur (OO) que des *townsendi* pur (TT)
	- Les hybrides ont des phénotypes plus intermédiaires entre les 2 autres phénotypes purs

- ### **6. Décrivez l’indice Fst et interprétez les figures 4 et 5**
    - **Indice Fst** :
        - Mesure la différenciation génétique entre populations (0 = absence de différenciation, +++ flux de gène entre les pop, 1 = différenciation totale, pas de flux de gène).
    - **Figure 4** :
        - La plupart des SNPs ont un Fst proche de la moyenne (0,03), suggérant un flux génétique modéré.
        - Certains SNPs "outliers" (Fst > 0,6) révèlent des loci soumis à une forte sélection divergente.
    - **Figure 5** :
        - La fréquence de l’allèle "O" du locus en position 1981369 augmente progressivement dans la zone hybride, suggérant une introgression limitée ou une sélection contre certains génotypes.

- ### **7. Que pouvez-vous dire concernant l’isolement reproducteur dans ce système ?**
	- L’isolement reproducteur est partiel. Bien que les hybrides existent, des mécanismes tels que la sélection contre certains phénotypes hybrides ou la différenciation génétique (Fst élevé) à des loci spécifiques réduisent l’introgression.
	- Les différences phénotypiques (ex. plumage) jouent probablement un rôle dans la reconnaissance et le choix du partenaire.

---

Paz Vinas 2024
- ### **1. Quels types de patrons spatiaux de variation génétique pourraient être attendus pour une espèce de poisson d’eau douce dans ce bassin versant ?**
	- Pour une espèce comme le silure glane, plusieurs types de patrons spatiaux de variation génétique peuvent être attendus :
		- **Isolation par la distance (IBD)** : Les populations géographiquement proches devraient être génétiquement plus similaires, car la dispersion se fait le long des rivières (avec une richesse allélique et diversité plus importante en aval qu'en amont.
		- **Effet des barrières physiques ou écologiques** : Les obstacles naturels (chutes d'eau, barrages) ou anthropiques (écluses, infrastructures humaines) peuvent limiter la dispersion, créant des différences génétiques.
		- **Effets liés aux introductions multiples** : Si des populations génétiquement distinctes ont été introduites à différents endroits, cela pourrait générer des clusters génétiques non liés à la distance.

- ### **2. Interprétez la Figure 2 et dites quel type de patron spatial de variation génétique est représenté dans ce graphique.**
	- **Figure 2** montre la différenciation génétique (axe des ordonnées, probablement mesurée par un indice comme $F_{st}$ en fonction de la distance topologique (axe des abscisses, correspondant à la distance mesurée le long du réseau fluvial).
	- **Interprétation** : Les points bleus suivent une relation positive. Cela signifie qu’à mesure que la distance augmente, la différenciation génétique s’accentue.
	- **Patron spatial** : Ce graphique illustre un modèle d’**isolation par la distance** (IBD), où les populations proches échangent plus de gènes que celles éloignées.
		- ==> Cela confirme donc un **partron IBD**

- ### **3. Supposons que vous avez accès à un ordinateur, avec le logiciel R installé. Quels types de données devriez-vous avoir à votre disposition pour pouvoir tracer la Figure 2 ? Justifiez.**
	- **Données génétiques** : Des génotypes individuels (SNPs, microsatellites, etc.) pour les différentes populations.
	- **Distances géographiques** : Les distances topologiques (en km) entre chaque paire de populations, calculées le long du réseau hydrographique.
	- **Indice de différenciation génétique** : Les valeurs de ​$F_{st}$ ou un équivalent pour chaque paire de populations, obtenues à partir des données génétiques.
	- **Justification** : La relation entre la distance et la différenciation nécessite des données de génétique des populations et des distances géographiques pour chaque paire.

- ### **4. Interprétez la Figure 3. Pouvez-vous en déduire le nombre minimum d’introductions de silures qui ont pu avoir lieu dans le bassin versant ?**
	- **Figure 3** est un graphique STRUCTURE qui montre la composition génétique des individus par site.
	- Chaque couleur représente un cluster génétique distinct, et les proportions de couleurs indiquent le mélange dans chaque population.
	- **Nombre minimum d’introductions** :
	    - La présence de plusieurs clusters distincts (couleurs) dans différentes rivières suggère que **plusieurs introductions indépendantes** ont eu lieu.
	    - Si certaines populations présentent des clusters génétiques uniques (non partagés avec d'autres rivières), cela indique une **introduction directe** pour ces groupes.
	    - On peut probablement déduire un minimum de **3 ou 4 introductions**, en fonction du nombre de clusters distincts.

- ### **5. Pouvez-vous identifier des endroits où les contraintes à la dispersion des silures semblent être plus fortes qu’ailleurs ? Hypothèses sur les facteurs du paysage.**
    - **Identification des zones de contraintes** :
        - Les zones où les populations montrent des clusters génétiques distincts (peu de mélange entre couleurs) indiquent une dispersion limitée.
        - Par exemple, des barrières peuvent exister **entre GAR7 et GAR8**, ou **à l’aval de GAR6**, si des changements brusques dans la composition génétique sont observés.
    - **Hypothèses sur les facteurs du paysage** :
        - **Barrières naturelles** : Rapides, chutes d’eau.
        - **Barrières anthropiques** : Barrages, écluses ou ouvrages hydrauliques limitant les déplacements des poissons.
        - **Facteurs écologiques** : Différences de qualité de l’eau, pollution, ou absence d’habitats favorables.

---

PhyloG 2023-2024
- ### **Question 1 : Quelles sont les caractéristiques d’un groupe extérieur judicieusement choisi ?**
	- #### **Caractéristiques d’un groupe extérieur :**
		- **Position phylogénétique proche mais distincte** : Le groupe extérieur doit être suffisamment proche du groupe d’étude pour permettre une comparaison valide, mais suffisamment éloigné pour ne pas appartenir à ce groupe ==> Ainsi il partage un ancêtre commun avec le groupe intérieur, mais ne fait pas partie du clade étudié.
			- Un groupe extérieur trop éloigné peut introduire des biais dus à la saturation des mutations ou à des taux d’évolution divergents. Cela peut fausser les estimations phylogénétiques.
		- **Relations bien établies** : Sa position phylogénétique par rapport au groupe d’étude doit être connue pour enraciner correctement l’arbre phylogénétique (ex : des études précédentes fiables ou des données moléculaires robustes).
		- **Absence d’événements de transfert horizontal** significatifs avec le groupe d’étude, afin de limiter les biais. (et potentiellement d'autres événements comme Duplication génique: orthologie/ paralogie)
	- #### **Groupes possibles pour le choix du groupe extérieur :**
		- En se basant sur la figure 1, les génomes choisis pourraient provenir d’autres lignées de **Gammaproteobacteria** proches des Enterobacterales, mais distinctes :
			1. **Xanthomonadales**
			2. **Aeromonadales**
			3. **Vibrionales**
			4. **Pseudomonadales**
	- #### **Justification :**
		- Ces groupes partagent une origine évolutive avec les Enterobacterales (proches dans la phylogénie), tout en représentant des lignées divergentes, permettant d’établir une racine correcte.
	- #### Alternative :
		- Faire l'hypothèse de l'horloge moléculaire
			- Toutes les lignées sont supposées évoluer à la même vitesse depuis leur divergence; la racine est au point de l’arbre équidistant de toutes ses feuilles. ==> Ca évite d'enraciner l'arbre
			- Mais on sait qu'il y a des sites de l'ADN qui ont un taux de mutation, qui évoluent plus vites que d'autres

- ### **Question 2 : Intérêt et construction des supermatrices en phylogénie moléculaire**
	- #### **Intérêt des supermatrices :**
		- **Réduction des biais** : L’utilisation de plusieurs gènes combinés permet de réduire l’effet des biais spécifiques à un seul gène.
		- **Augmentation de la robustesse** : Une supermatrice intègre des informations multiples de plusieurs loci, augmentant le pouvoir de résolution phylogénétique.
		- **Prise en compte de données disparates** : Ces méthodes permettent d’inclure des données provenant de gènes avec des taux d’évolution variés.
	- #### **Construction des supermatrices :**
		1. **Sélection des gènes orthologues** :
		    - Identifier des gènes homologues (par exemple, les gènes présents en une seule copie dans tous les génomes).
		2. **Alignement multiple** :
		    - Aligner chaque gène individuellement.
		3. **Concaténation** :
		    - Combiner tous les alignements dans une matrice unique.
		4. **Traitement des données manquantes** :
		    - Remplir les lacunes (par exemple, si certaines espèces ne possèdent pas un gène donné).
	- **Schéma simplifié** :
		```python
		Espèce 1 : Gène1 | Gène2 | Gène3 ...
		Espèce 2 : Gène1 | Gène2 | Gène3 ...
		Espèce 3 : Gène1 | Gène2 | Gène3 ...
		```
	- #### **Points de vigilance :**
		- **Orthologie** : S’assurer que les gènes sont orthologues et non paralogues pour éviter des conflits phylogénétiques.
		- **Proportion de données manquantes** : Trop de données absentes peuvent biaiser l’analyse.
		- **Hétérogénéité évolutive** : Les différences de taux d’évolution entre gènes peuvent poser problème et les différentes sources de données (par exemple, génomes mitochondriaux vs nucléaires) peuvent porter des signaux conflictuels, rendant difficile l’interprétation des résultats.

- ### **Question 3 : Comparaison des phylogénies des groupes de gènes A, B, C et D**
	- ![[Pasted image 20241208141909.png]]
	- #### **Regroupements d’espèces fortement soutenus :**
		- **Groupe A** : Identifier les clades où des branches sont soutenues par de fortes valeurs de bootstrap (ou mesures similaires).
			- Escherichie + Salmonella
			- Yersinia
			- Buchnera + Wigglesworthia
			- Dickeya + Pectobacterium
		- **Groupe B, C, D** : Répéter le processus pour chaque groupe.
	- #### **Signal conflictuel ou absence de signal phylogénétique ?**
		- **Absence de signal** : Si les relations entre espèces sont mal résolues ou supportées par de faibles valeurs, cela suggère un manque d'information dans les gènes analysés.
		- **Signal conflictuel** : Si les phylogénies diffèrent et montrent des regroupements incongrus, cela indique un signal conflictuel.
	- #### **Origine du signal conflictuel :**
		- **Transferts horizontaux de gènes (HGT)** : Commun dans les bactéries, cela peut brouiller les signaux phylogénétiques.
		- **Événements de duplication et perte de gènes** : Peuvent introduire des erreurs dans l'identification des relations.
		- **Pressions sélectives différentes** : Des forces évolutives distinctes sur certains gènes peuvent produire des topologies divergentes.
	- #### **Groupes de gènes pour la supermatrice :**
		- Seuls les gènes sans signal conflictuel majeur (groupes A ou B, par exemple) devraient être utilisés pour construire une supermatrice fiable.

- ### **Question 4 : Dessiner la phylogénie obtenue avec la supermatrice**
	- #### **Phylogénie attendue :**
		- La phylogénie devrait refléter les relations majoritaires observées dans les groupes de gènes bien supportés (A et/ou B).
	- **Topologie probable** :
	    - Les espèces les plus proches (en termes de distances génétiques) devraient former des clades.
	    - La position du groupe extérieur enracinera l’arbre.



# ==Bonus==
## Synthèse sur le bootstrap en phylogénie

#### 1. **Mise en place et calcul**

- **Rééchantillonnage des données** : Les colonnes d’un alignement de séquences sont rééchantillonnées aléatoirement avec remplacement pour générer plusieurs jeux de données modifiés.
- **Reconstruction d'arbres** : Un arbre phylogénétique est reconstruit pour chaque jeu de données rééchantillonné.
- **Fréquence des regroupements** : Pour chaque regroupement (clade) dans l’arbre final, le pourcentage de fois où il apparaît dans les arbres reconstruits est calculé : c'est la valeur de **bootstrap**.

---

#### 2. **Pourquoi un bootstrap élevé n'est pas synonyme de véracité**

- Un bootstrap élevé indique uniquement que le **signal dans les données est cohérent et répétable**.
- Cela ne garantit pas que ce signal reflète la **véritable histoire évolutive**. Des biais dans les données peuvent produire des regroupements erronés malgré un fort soutien.

---

#### 3. **Ce que représente réellement le bootstrap**

- Il mesure la **stabilité statistique** d’un regroupement dans l’arbre phylogénétique.
- C’est une estimation de la **force du signal évolutif** dans le jeu de données utilisé.
- Permet de savoir si une branche est statistiquement solide sur le jeu de données utilisé

---

#### 4. **Interprétation des valeurs de bootstrap**

- **Bootstrap élevé (≥ 70-80%)** : Regroupement statistiquement stable, fortement soutenu par les données, mais pas nécessairement correct.
- **Bootstrap faible (< 50-60%)** : Regroupement peu fiable, nécessitant davantage de données ou des analyses complémentaires.

---

#### 5. **Causes d’un bootstrap fort mais faux**

- **Saturation mutationnelle** : Trop de mutations masquent les relations profondes (homoplasies).
- **Biais systématiques** : Problèmes liés à des méthodes ou modèles inadéquats.
- **Échantillonnage insuffisant** : Jeu de données trop petit ou déséquilibré.
- **Signal évolutif trompeur** : Effets de longue branche (groupement incorrect de taxons très divergents).

---

#### 6. **Doit-on considérer les bootstraps faibles ?**

- Oui, car ils indiquent des zones de **faible confiance** où l'arbre pourrait être incorrect.
- Ces régions peuvent nécessiter des analyses supplémentaires ou des données plus informatives.

---

#### 7. **Solutions pour éviter de se tromper**

- **Augmenter la taille du jeu de données** : Utiliser davantage de gènes ou de séquences.
- **Modèles évolutifs appropriés** : Sélectionner des modèles capables de corriger les biais.
- **Méthodes complémentaires** : Comparer les résultats avec des analyses bayésiennes ou d’autres approches statistiques.
- **Utilisation de phylogénies de référence** : Vérifier la cohérence des résultats avec des phylogénies validées ou des données indépendantes.







## L'attraction des longues branches (Long Branch Attraction, LBA)

#### **Définition :**

L’attraction des longues branches (LBA) est un artefact phylogénétique dans lequel des taxons très divergents, souvent avec de longues branches évolutives dans l'arbre, sont incorrectement regroupés ensemble. Ce regroupement erroné est dû à des similitudes dans les données, non pas parce qu’ils partagent un ancêtre commun proche, mais en raison de **taux de substitution élevés** qui masquent les vraies relations évolutives.

---

#### **Pourquoi cela arrive :**

1. **Saturation mutationnelle :**
    
    - Lorsque des positions homologues dans un alignement accumulent trop de mutations indépendantes, les différences réelles entre les séquences deviennent difficiles à distinguer.
    - Cela conduit à des similitudes apparentes dues au hasard ou à des substitutions convergentes (homoplasies).
2. **Effet statistique :**
    
    - Les longues branches accumulent davantage de substitutions que les courtes branches.
    - Les méthodes phylogénétiques, en particulier celles basées sur la parcimonie ou des modèles inadéquats, peuvent confondre ces substitutions aléatoires comme un signal évolutif commun.
3. **Modèles évolutifs simplifiés :**
    
    - Des modèles d'évolution qui ne corrigent pas correctement les taux de substitution ou qui sous-estiment la variabilité du taux entre les sites peuvent amplifier l'effet de LBA.

---

#### **Conséquences de la LBA :**

- Les taxons avec des longues branches sont faussement placés comme proches parents, créant une phylogénie incorrecte.
- Cela peut masquer les relations réelles avec d’autres taxons et produire des conclusions biologiques erronées.

---

#### **Comment s’en prévenir :**

1. **Utiliser des modèles d'évolution robustes :**
    
    - Les modèles qui prennent en compte la variabilité des taux de substitution entre sites (par exemple, **modèles avec distribution gamma**) peuvent réduire l’impact de la LBA.
    - Optez pour des méthodes bayésiennes ou de maximum de vraisemblance plutôt que la parcimonie, qui est plus sensible à la LBA.
2. **Augmenter le nombre de caractères :**
    
    - Utiliser des alignements contenant davantage de séquences ou de gènes réduit l'effet des biais locaux et améliore la résolution globale.
3. **Inclure des taxons intermédiaires :**
    
    - Ajouter des taxons proches ou des groupes ayant divergé plus récemment aide à briser les longues branches, fournissant un meilleur contexte évolutif.
4. **Tester pour l'effet de LBA :**
    
    - Comparer des arbres générés avec différentes méthodes (parcimonie, maximum de vraisemblance, bayésien) peut révéler des regroupements suspects.
    - Analysez les regroupements inattendus et évaluez leur robustesse.
5. **Filtrer les données fortement saturées :**
    
    - Exclure les sites ou les gènes où la saturation mutationnelle est élevée peut limiter l’influence de la LBA.




## Comment savoir si Les différences observées au niveau des topologies correspondent-elles à une absence de signal phylogénétique ou à la présence de signaux phylogénétiques conflictuels ?

#### c) **Bootstrap et incongruences :**

- Examinez les valeurs de **bootstrap** : des valeurs élevées dans des topologies contradictoires révèlent des **signaux conflictuels**.
- Des regroupements mal soutenus (faible bootstrap) peuvent indiquer une **absence de signal**.

### 3. **Rechercher les causes des différences :**

#### a) **Bruit ou biais :**

- Absence de signal : Provoqué par des données insuffisantes, saturation mutationnelle, ou un trop faible nombre de sites informatifs.
- Signaux conflictuels : Provoqués par des biais comme l'attraction des longues branches, recombinaison, ou évolution convergente.

#### b) **Approche du signal évolutif :**

- Identifiez les **sites informatifs** dans l'alignement. Si ces sites favorisent des topologies différentes, cela indique des **signaux conflictuels**.



![[Pasted image 20241208162633.png]]






## Qu'est ce qu'un site informatif ?

![[Pasted image 20241208165308.png]]
![[Pasted image 20241208165327.png]]

Un site (colonne) d'un alignement multiple est informatifs ssi dans cette colonne :
- Il n'y a **pas de singleton** (Une des espèces est la seule à avoir une base spécifique à ce site et pas les autres
- Il y a **au moins 2 espèces/séquences avec des bases différentes** pour ce site 