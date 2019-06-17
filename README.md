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



-         Liste des algos
-   Glouton
-   Hill Climbing
-   Intensification
-   Diversification
-   Evolutionnaire génétiques
-   Tabou
-   Recuit simulé
-   GRASP
-   Recherche local Guidé
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
