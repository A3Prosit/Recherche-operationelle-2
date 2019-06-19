# Recherche opérationnelle 2
 
##	I.        Mots clés
·         Optimum global/local
·         (Méta) Heuristique
·         Accélération sur linéaire*
·         Méthode arborescente
·         Voyageur du commerce*
·         Hill Climbing
·         Borne algorithmique
·         Algorithme du tabou
·         Lagrangien
·         Méthode de relaxation
·         Génération de colonnes*
·         Modélisation de voisinage
·         Convergence de la solution
·         Algorithme génétique
·         Recuit simulé
·         Algorithme simulé
·         Problème de décision*
·         GRASP
·         Méthode de recherche local
·         NP-complet*
·         Rugosité du voisinage
·         Solution de bonne qualité
·         Phase d’intensification/diversification
·         Méthode exacte*
·         Colonie de Fourmies
·         Méthode de construction
·         Glouton

##   II.        Contexte :
Quoi : Trouver une solution rapidement et pseudo-optimal
Comment : en utilisant des méthodes méta-heuristique
Pourquoi : Résoudre le TSP
 
## III.        Contraintes :
·         2 Jours
·         Réalisable en un temps donné
·         Qui peut être arrêté a n’importe quel moment
·         Emilien gestionnaire spécialiste en Chocos Pendant 2 JOURS
 
Problématique : Comment résoudre le TSP avec des méthodes méta-heuristique rapidement et pouvant l’interrompre

## IV.        Généralisation :
·         RO
·         Optimisation
·         Résolution de problèmes complexe

##   V.        Hypothèses :
1.	L’algorithme de hill climbing est dangereux car on peut atteindre le maximum local
2.	Le model de voisinage est un modèle d’approximation
3.	Un algorithme génétique est un algorithme qui apprends de ses erreurs pour avancer
4.	L’algorithme glouton est un algorithme qui fait le meilleur choix local dans l’espoir que ce soit le meilleur choix global
5.	Un algorithme qui résout NP-complet est applicable au problème du voyageur de commerce
 
## VI.        Plan d’action :
Etudes :
-        Algorithme méta-heuristique
-        Définition

Une solution réalisable d’un (PLNE) est une solution x qui satisfait les contraintes du problème

algo de résolution approché : 
On trouve une solution, mais on ne sait pas si c’est la meilleure solution pour toute les instances de ce problème ⇒ notre algorithme est Heuristique

algo dit heuristique : : Un algorithme de résolution Heuristique est un algorithme qui fournit une solution réalisable en un temps polynomial pour un problème N P-difficile.

Algorithmes approchés particuliers (heuristiques) Méthodes par Séparation-Evaluation avortées, méthode gloutonne, arrondi de la solution optimale de la relaxation continue, algorithme par recherche locale, ...

Méthodes génériques (métaheuristiques) Algorithmes mono-solution : I Variable Neighborhood Descent (VND), Variable Neighborhood Search (VNS), recherche tabou, recuit simulé, ... Algorithmes multi-solutions I Algorithmes génétiques, colonies de fourmis, ...

méthode ar séparation-evaluation avortées

exécuter partiellement une méthode par Séparation-Evaluation, et à l’arrêter quand un critère d’arrêt est vérifié : 

Temps limite : risque de ne pas avoir de solution réalisable (borne primale) !
Ecart prédéfini entre borne primale / borne duale 
Critère mixte : temps limite si borne primale existe OU écart prédéfini entre borne primale/duale

heuristique par arroundi de la solution:
Principe : mettre à 1 toutes les variables qui valent 1 dans la solution optimale de la RC (et à 0 les autres)

algo glouton: Un algorithme glouton fait, étape par étape, le choix d’un optimum local.

Le voisinage d’une solution donnée x est l’ensemble de solutions réalisables du problème de départ qui sont obtenues à partir de x via une transformation élémentaire.
On dit que ces solutions sont "proches" de x. La transformation élémentaire nécéssite d’être définie selon les besoins de l’algorithme. La taille d’un voisinage est variable et est au maximum égale au cardinal de l’ensemble des solutions réalisables.
Une solution est un optimum local si elle est meilleure que toutes les autres solutions d’un voisinage prédéfini

La métaheuristique Variable Neihborhood Descent (VND) 
La métaheuristique Variable Neihborhood Search (VNS) 
La métaheuristique Tabou

Un algorithme de résolution métaheuristique est un algorithme heuristique "générique" qu’il faut adapter à chaque problème. Il peut etre basé sur le voisinage ou une recherche locale

l’idée est d’utiliser les métaheuristique pour s’extraire d’un optimum local obtenu par une méthode heuristique.

Variable Neihborhood Descent (VND)
Principe : 
1 On définit k voisinages vk tels que |v1|<|v2|< . . . <|vk |. 
2 On cherche une meilleure solution que x0 dans v1, pui dans v2, etc ... 
3 Lorsqu’une telle solution xbest est trouvée, on tente de l’améliorer d’abord dans le voisinage v1, puis dans v2, etc... 
4 On s’arrête lorsqu’on de peut plus améliorer xbest.

```
VND()
DEBUT
	Choisir une solution initiale x0
	xbest → x0
	TANT QUE xbest peut être amélioré FAIRE
		POUR i allant de 1 à k FAIRE
			POUR TOUT x 0 ∈ vi(x) FAIRE
				SI f (x 0 ) < f (xbest) ALORS 
					xbest → x 0 
					arrêter la boucle POUR 
					arrêter la boucle POUR 
				FIN SI 
			FIN POUR 
		FIN TANT POUR
	FIN TANT QUE 
FIN
```

Variable Neihborhood Search (VNS) 
Principe : 
1 On définit k voisinages vk tels que |v1|<|v2|< . . . <|vk |.
2 On cherche une meilleure solution que x0. Pour cela on va appliquer VND. 
3 Si une telle solution xbest est trouvée, on tente de l’améliorer d’abord dans le voisinage v1, puis dans v2, .. 
4 Sinon on est bloqué sur un optimum local, on tire au hasard une solution qui va devenir la solution à améliorer. 
5 On s’arrête lorsqu’on de peut plus améliorer xbest

```
VNS()
DEBUT 
	Choisir une solution initiale x0
	xbest → x0 
	TANT QUE xbest peut être amélioré FAIRE 
		POUR i allant de 1 à k FAIRE
			Générer un point x 0 au hasard dans le i eme voisinage de x (x 0 ∈ vi(x)) 
			Appliquer VND en partant de x 0, on note x 00 l’optimum local trouvé.
			SI f (x 00) < f (xbest) ALORS 
				xbest → x 00
				i → 1 
			FIN SI 
		FIN POUR 
	FIN TANT QUE 
FIN
```

Voisinage : Le voisinage d'une solution est un sous-ensemble de solutions qu'il est possible d'atteindre par une série de transformations données. Par extension on désigne parfois par le terme « voisinage » l'ensemble des transformations considérées.
Par exmple pour le TSP un voisinage est l'ensemble des olutions possible de construire en swappant 2 villes dans une solution donnée

**Recuit simulé** (simulated annealing)

Moyen de se déplacer dans le searchspace de façon proba

métaheuristique inspirée d'un processus de métallurgie. On alterne des cycles de refroidissement lent et de réchauffage (recuit) qui en métallurgie minimise l'énergie du matériau (= le rendrent plus solide )
La méthode vient du constat que le refroidissement naturel de certains métaux ne permet pas aux atomes de se placer dans la configuration la plus solide. La configuration la plus stable est atteinte en maîtrisant le refroidissement et en le ralentissant par un apport de chaleur externe, ou bien par une isolation

L'algo s'appuie sur l'algo de Metropolis-Hastings qui permet de décrire l'évo d'un système thermodynamique.
On part d'un état donné, on le modif, on obtient un autre état. Si il est plus opti on considère qu'on à baisser l'énergie du système.  Accepter un meilleur critère rapproche de l'optimum dans le voisinage (local) et l'acceptation d'un mauvais critère permet d'explorer une plus grande partie de l'espace des états pour éviter de s'enfermer trop vite dans la recherche d'un opti local.

déroulement: 
on prend un état initial de l'algo au hasard dans l'espace des états possibles. A cet état correspond une énergie initiale (le valeur de la fonction éco). On choisi également une température initiale élevée T = T0 totalement arbitraire

A chaque iter de l'algo on change l'état. Ca entraine une variation de deltaE de l'énergie du système(calcl à partir du critère à opti). Si elle est négative (baisse l'énergie du système) elle est appliquée à l'état courrant. Sinon elle est acceptée avec une probabilité exp(-deltaE/T) ce choix e proba s'appelle règle de Metropolis. On itère selon ce procédé en gardant la température constante

il y a 2 approches possibles pour la variation de température:
- on itère en gardant la température constante. Lorsque le système atteint un équilibre thermodynamique (après un nb d'iter) on diminue la température du système
- on fait baisserla température de façon continue. (loi de décroissance, la plus courante étant Ti+1 = lambda*Ti avec en général lambda =0.99
Dans les 2 cas si la temp atteint un seuil assez bas fixé au préalable ou que le système devient figé l'algo s'arrête
LA température joue un rôle important. A haute temp le système est ibre de se déplacer das l'espace es éats en choisissant des états ne minimisant pas forcément l'énergie du sys. A basse temp les modifs baissant l'énergie du sys sont choisie mais d'autres peuvent être acceptées pour éviter de tomber dnas un minimum local

**pseudo code**
```
s := s0
e := E(s)
k := 0
while (k < kmax && e > emax)
  sn := voisin(s)
  en := E(sn)
  if ( en < e || rand() < P(en - e, temp(k/kmax)) )
    s := sn; e := en
  k := k + 1
return s
```


reformulé:
- on a une fonction h() à max
- on génère une soluce au pif, x
- on set une température initiale  Ti au pif > 0
- on iter un certain nb de fois (on choisi, c'est notre contrainte de temps)
- on fait un rand et on a un nouveau candidat x' = x+rand
- on calc la p value p = exp(deltaH/Ti) où deltaH = h(x') - h(x), 
- on accepte la nouvelle valeur de façon probabilistique avec p
- on met la température à jour: T' = a*T avec  0<a<1, en général T' = 0.99*T ou T' = T/log(T+1) (pas sur, à verif celui là)


**classification des méthodes**
- méthodes de trajectoire

manipulent un seul pt à la fois et tentent de l'améliorer itérativement d'améliorer ce point. elles construisent une traj dans l'espace des points en tentant de se diriger vers les soutions. ex:
-recherhce locale
recuit simulé
recherche tabou
recherche à voisinage variable

- méthode basée sur une population
dispose d'une base de points. ex: algo génétique

-   Liste des algos
-   Glouton
-   Hill Climbing

basic hill climbing:
on a une fonction à max
on iter à chaque fois on cherche le voisinage si ça augmente ou pas
on retourne le plus grand qui devient l'actuel, si aucun n'augmente, on a fini c'est le max local


-   Intensification
ou exploitation vise à utiliser l'info déjà récoltée pour définir et parcourir les zones interessantes du searchspace

-   Diversification
exploration, processus visant à récolter de l'info sur le pb à opti

les métaheuristiques progressent de façon itératives en alternant intensification et diversification
-   Evolutionnaire génétiques
-   Tabou
-   Recuit simulé
-   GRASP
-   Recherche locale guidé
-   Recherche voisinage Variable
	-        Approche
	-         Exemple d’utilisation
-   Appliquer au voyageur de commerce
-        No free lunch
-         Résoudre avec un algo
-         Trouver moyenne d’évaluation qualité
Réalisation
-         Corbeille d’exercice




Objectifs:

 [COMPRÉHENSION] Déterminer les caractéristiques d’un problème d’optimisation difficile

Reformuler le principe de problème difficile en utilisant la notion de voisinage, d’algorithme glouton, et d’optimum local/global

Citer les principales méta-heuristiques, expliquer leur fonctionnement

Différencier les étapes de diversification et d’intensification

 [APPLICATION] Résoudre un problème d’optimisation au moyen d’une méta-heuristique

Décomposer les différentes étapes d’une méthode de recherche locale

Modéliser la notion de voisin d’une solution d’un problème d’optimisation algorithmique

 Classifier les résultats issus de l’état de l’art concernant un problème d’optimisation

 Démontrer la différence entre un optimum local et un optimum global

 [APPLICATION] Réaliser un programme implémentant une méta-heuristique

 Utiliser et combiner des bibliothèques de calcul scientifique

Construire une structure de données pour représenter un problème et ses solutions

Produire un code pour générer le voisinage d’une solution

Produire une méta-heuristique exploitant une méthode de génération de voisinage

 [ANALYSE] Analyser le comportement expérimental d’une méta-heuristique

Classifier les paramètres d’une méta-heuristique selon leur impact sur l’optimalité ou sur la convergence de la méta-heuristique

Comparer la convergence et l’efficacité de différentes méta-heuristiques et différents paramètres de méta-heuristiques
