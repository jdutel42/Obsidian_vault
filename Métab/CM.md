-  FBA
	- On maximise la réaction de biomasse (variable de décision)
	- Subject to
		- S.V. = 0 (à l'état stationnaire)
			- S = Matrice de stœchiométrie
			- V = Vecteur de réaction 
				- $\begin{bmatrix}V_{1} \\ V_{2} \\ V_{biomass} \\ \dots \\ Vn \\ 0\end{bmatrix}$
		- On calcule le vecteur de réaction
	- $V_{min} \leq V \leq V_{max}$
	- ==> Le programme retourne un vecteur avec des poids pour chaque réaction (le poids va etre max pour la biomass car, l'algo maximise cette reaction biomass)