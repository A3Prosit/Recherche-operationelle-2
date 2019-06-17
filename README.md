
# Recherche opérationnelle 2
 
##	I.        Mots clés
- Optimum global/local
- (Méta) Heuristique
- Accélération sur linéaire* ; 
- Méthode arborescente
- Voyageur du commerce*
- Hill Climbing
- Borne algorithmique
- Algorithme du tabou
-  Lagrangien
- Méthode de relaxation
- Génération de colonnes*
- Modélisation de voisinage
- Convergence de la solution
- Algorithme génétique
- Recuit simulé
- Algorithme simulé
- Problème de décision*
- GRASP
- Méthode de recherche local
- NP-complet*
- Rugosité du voisinage
- Solution de bonne qualité
- Phase d’intensification/diversification
- Méthode exacte*
- Colonie de Fourmies
- Méthode de construction
- Glouton

##   II.        Contexte :
Quoi : Trouver une solution rapidement et pseudo-optimal
Comment : en utilisant des méthodes méta-heuristique
Pourquoi : Résoudre le TSP
 
## III.        Contraintes :
- 2 Jours
- Réalisable en un temps donné
- Qui peut être arrêté a n’importe quel moment
- Emilien gestionnaire spécialiste en Chocos Pendant 2 JOURS
 
Problématique : Comment résoudre le TSP avec des méthodes méta-heuristique rapidement et pouvant l’interrompre

## IV.        Généralisation :
- RO
- Optimisation
- Résolution de problèmes complexe

##   V.        Hypothèses :
1.	L’algorithme de hill climbing est dangereux car on peut atteindre le maximum local
2.	Le model de voisinage est un modèle d’approximation
3.	Un algorithme génétique est un algorithme qui apprends de ses erreurs pour avancer
4.	L’algorithme glouton est un algorithme qui fait le meilleur choix local dans l’espoir que ce soit le meilleur choix global
5.	Un algorithme qui résout NP-complet est applicable au problème du voyageur de commerce
 
## VI.        Plan d’action :
Etudes :

### Algorithme méta-heuristique
- Les méthodes approchés ont pour but de trouver une solution admissible en un temps raisonnable, sans garantie l'optimalité de cette solution. On en trouve deux classes : Heuristiques & Méta-Heurisques

- Heuristique : Règles empiriques simples basées sur l'expérience (trouver)
- Meta (au delà , dans un niveau supérieur) : Méthode algorithmique capable de guider et d'orienter le processus de recherche  dans un espace de solution (souvent très grand) à des régions riches en solutions optimales dans le but de trouver des solutions très proche de l'optimum en un temps raisonable.
- Il respecte les propriétés suivantes :
	- Stratégies qui permettentde guider la recherche d'une solution optimale
	- Explorer l'espace derecherche efficacement afin de déterminer des solutions (presques optimales)
	- Méthodes de la simple procédure derecherche locale à des processus d'apprentissage complexe
	- Non déterministes et ne donnent aucune garantie d'optimalité. (sort différents résultats à chaque fois)
- Peut contenir des mécanismes quipermettent d'éviter d'être bloqué dansdes régions de l'espace de recherche
- Concepts peuvent-être de manière abstraite sans faire appel à un problème spécifique
- Peut faire appel à des heuristiques qui tiennent  compte de la spécificité du problème traité, mais ces heuristique sont contrôlées par une stratégie de niveau supérieur
- Peut faire usage de l'expérience accumulée pour mieux guider la suite du processus de recherche

On peut les classer selon leur principe de fonctionnement :
- Méthodes par construction (gloutonn)
	- On démarre une solution initiale vide
	- A chaque itération, une variable est choisie (aléatoirement ou via heuristique)
	- Le critère d'arrêt est l'affectation d'une valeur à toutes les variables du problème
	- Pro/Cons : Simples mais performances médiogres
	- Ex : (Méthode gloutone)
- Méthodes de voisinage (recuit ismulé, recherche tabou)
	- **[DIAPO 30/48 -**  //TO BE CONTINUED VA DORMIR EMILIEN
- Méthodes évolutives (algo génétiques)
- Méthodes biomimétiques (algo de colonies de fourmis & d'essaim de particules)




### Définition

### Liste des algos

o Glouton :
- Permet de construire une solution pas à pas
- Sans jamais revenir sur ses décisions
- En prenant à chaque étape la solution meilleure localement (heuristique)
- En sépérant obtenir une solution optimale

o Hill Climbing

o Intensification

o Diversification

o Evolutionnaire génétiques

o Tabou

o Recuit simulé

o GRASP

o Recherche local Guidé

o Recherche voisinage Variable

### Approche

### Exemple d’utilisation

o Appliquer au voyageur de commerce

### No free lunch

### Résoudre avec un algo

### Trouver moyenne d’évaluation qualité



### Corbeille d’exercice by MAZᶲ
