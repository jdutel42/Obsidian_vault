# ==**TP 3**==

- ## Exercice 1
	- On a le vecteur Reaction avec tous les gènes
		- $\begin{bmatrix}V_{1} \\ V_{2} \\ V_{biomass} \\ \dots \\ Vn \\ 0\end{bmatrix}$ --> 0 --> Production de biomass
	- Algorithme FBA
	- On va chercher quelles réactions sont essentielles ou non 
```
list_essential_reaction = []

for r in Reaction :
	max Vbiomass
	Subject to 
		S.V = 0
		V_min <= V <= V_max
		V_r = 0
		return Vbiomass
		if Vbiomass = 0 
			list_essential_reaction.append(Vr)
			print("La réaction Vr est essentielle")
```
- On ne connaissait pas la valeur de biomasse optimalle avec cette algo on peut savoir la valeur de biomasse optimale
	- Par exemple : $V = (1, 1, 2, \dots, V_{biomass}^{opt}=8.3, \dots)$

- ## Exercice 2 : FVA
	- Maintenant qu'on a la valeur de biomasse optimale, on cherche à trouver toutes les façons d'obtenir le $V_{biomass}^{opt}$
	- Admettons que nous ayons déjà calculé la liste des réactions essentielle $V_{biomass}^{opt}$
		-  
```
V_biomass_opt = MaxVbiomass()
For v in V :
	max v
	subject to :
		S.V. = 0
		Vmin <= Vniomass <= Vmax
		Vbiomasse = Vbiomass_opt
	min v
	subject to :
		S.V. = 0
		Vmin <= Vniomass <= Vmax
		Vbiomasse = Vbiomass_opt
	return vmin et vmax
```

 $Vmin = \begin{bmatrix}V_{min1} \\ V_{min2} \\ \dots \\ V_{minbiomass} \\ \dots \\ V_{min n}\end{bmatrix}$
 
 $Vmax = \begin{bmatrix}V_{max1} \\ V_{max2} \\ \dots \\ V_{maxbiomass} \\ \dots \\ V_{max n}\end{bmatrix}$

- ## Exercice 3 : Parcimonious FVA
	- On a maintenant les vecteur vmin et vmax, on cherche le chemin des réaction le plus petit = le plus efficace
```
V_biomass_opt = MaxVbiomass()
min( somme(abs(vi) (pour i allant de 1 à r))) 
subject to :
	S.V. = 0
	Vmin <= Vniomass <= Vmax
	Vbiomasse = Vbiomass_opt
```