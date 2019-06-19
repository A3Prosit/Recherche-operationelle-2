
# Recherche opérationnelle 2
 
##	I.        Mots clés
- Optimum global/local : Valeur maximale dans le voisinage vs valeur maximale de toute la solution.
- (Méta) Heuristique : /
- Accélération sur linéaire*  
- Méthode arborescente : Méthode par abre
- Voyageur du commerce*
- Hill Climbing : /
- Borne algorithmique : Supérieure ou inférieure
- Algorithme du tabou: /
-  Lagrangien : permet d'écrire de manière conscine les équations du mouvement d'un système. ?
- Méthode de relaxation : Méthode itérative (utilisant des suites) pour résoudre des systèmes linéaires (Ax = b) où A est une matrice, et x et b sont des vecteurs de R. On les mets sous une certaine forme, avec w (méthode de relaxation). En fonction de la tridiagonale positive et si w est compris entre 0 et 2 à la fin, alors la suite convere vers l'unique solution. 
- Génération de colonnes*
- Modélisation de voisinage : /
- Convergence de la solution : Se diriger vers la solution
- Algorithme génétique : Famille des évolutionnistes. Heuristiques, utilise la notion de sélection naturelle pour l'appliquer à sa popuplation.
- Recuit simulé : /
- Algorithme simulé : /
- Problème de décision*
- GRASP : /
- Méthode de recherche local : /
- NP-complet*
- Rugosité du voisinage : ? 
- Solution de bonne qualité : /
- Phase d’intensification/diversification : /
- Méthode exacte*
- Colonie de Fourmies : Basé sur les colonies de fourmies, qui utilisent leur environnement. Elles utilisent des féromones pour marquer leur chemin et le plus court sera celui qui sera renforcé par le plus de féromone (le plus de passage). Les plus long seront donc automatiquement détruits. On peut résoudre le pb du voyageur de commerce. Métaheuristiques. Il suffit de mettre un certain coefficiant (poid) sur chaque arrête qui évoluera.
- Méthode de construction : /
- Glouton : /

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

- **Etymologies :** 
	- **Meta** (au delà , dans un niveau supérieur) : Méthode 
	- **Heuristique :** Règles empiriques simples basées sur l'expérience (trouver)
- algorithmique capable de guider et d'orienter le processus de recherche  dans un espace de solution (souvent très grand) à des régions riches en solutions optimales dans le but de trouver des solutions très proche de l'optimum en un temps raisonable.

**- Propriétés :**
	- Stratégies qui permettent de guider la recherche d'une solution optimale
	- Explorer l'espace derecherche efficacement afin de déterminer des solutions (presques optimales)
	- Méthodes de la simple procédure derecherche locale à des processus d'apprentissage complexe
	- Non déterministes et ne donnent aucune garantie d'optimalité. (sort différents résultats à chaque fois)
	- Peut contenir des mécanismes quipermettent d'éviter d'être bloqué dansdes régions de l'espace de recherche
	- Concepts peuvent-être de manière abstraite sans faire appel à un problème spécifique
	- Peut faire appel à des heuristiques qui tiennent  compte de la spécificité du problème traité, mais ces heuristique sont contrôlées par une stratégie de niveau supérieur
	- Peut faire usage de l'expérience accumulée pour mieux guider la suite du processus de recherche

- **Classement selon fonctionnement :** 
	- Méthodes par construction (gloutonn)
		- Cf : Glouton
	- Méthodes de voisinage (recuit simulé, recherche tabou)
		- Cf : Voisinage (Recuit Simulé, Recherche Tabou...)
	- Méthodes évolutives (algo génétiques)
	- Méthodes biomimétiques (algo de colonies de fourmis & d'essaim de particules)

### Liste des algos

**o Glouton :**
- Type d'algorithme
- Permet de construire une solution pas à pas, sans jamais revenir sur ses décisions, en prenant à chaque étape la solution meilleure localement (heuristique). Il prend donc souvent la plus forte pente.
- Pro/Cons : Simples mais performances médiogres
- Peut-être mis en échec ex : 
![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Greedy_Glouton.svg/1024px-Greedy_Glouton.svg.png)

**o Hill Climbing :** 
- Glouton
Prend trois entrées en objet :
- Une configuration initiale
- Une fonction
- Une fonction objectif
⇒ Evaluer les solutions voisines et à choisir la meilleure ce celle ci, en ne recommançant jusqu'à arriver à une meilleure position  que ses précédentes. C'est alors un *optimum local.* Par contre, on peut rater d'autres optimums qui auraient été après.


**o Evolutionnaire génétiques** :
- S'inspire de la théorie de l'évolution pour résoudre des pb (transmission des caractéristiques au descendants)
- Algorithmes dits stochastiques (random)
- Utilisés pour résoudre des pb d'optimisation
- Plus la finesse d'une solution (précision via) est elevée, plus il a de chance de transmettre son "génotype" à la population.
- A chaque étape de l'algorithme, est associé un opérateur qui décrit la façon de manipuler les individus :
	- "Opérateur de sélection pour la sélection et le remplacement"
	- Opérateur de variation pour la mutation et le croisement
- A la fin, on se retrouve avec des solutions évoluées

**o Tabou :**
- A l'inverse du recuit simulé qui génère aléatoirement une solution voisine à chaque itération
 - Examine un échantillonage de solution N et retient la meilleure s' même si s' est plus mauvaise que S
 - /!\ Peut entraîner des cycles s -> s' -> s  pour empêcher ça :
	 - LIste tabou qui mémorise les k denrières solutions visitées et interdit tout mouvement vers une solution de cette liste. On la remplis pour une nombre k d'itéraitions
	 - Suit le principe du FIFO.
	 - On continue jusuq'à la condition d'arrêt
![](https://image.slidesharecdn.com/chapitre4heuristiquesetmta-heuristiques-160202125547/95/chapitre-4-heuristiques-et-mta-heuristiques-45-638.jpg?cb=1454417798)
Pro/Cons : Demande généralement beaucoup de place mémoire et udu temps. 

**o Recuit simulé :**
- Analogie avec la thermodynamique avec Min(energie_Systeme) :  Principe du recuit ( processus physique de chauffage ) ==> Evolution différente de l'énergie en fonction de comment on fait évoluer la température
![](https://image.slidesharecdn.com/chapitre4heuristiquesetmta-heuristiques-160202125547/95/chapitre-4-heuristiques-et-mta-heuristiques-34-638.jpg?cb=1454417798)- On part avec une solution s0 généré random (qui correspond à E0) et une température initiale T0 généralement élevé
- A chaque itération, on fait un changement élémentaire aléatoire pour faire varier l'énergie. 
	- Si variation négative : Solution améliore la fonction objective et diminue l'énergie du système, elle est acceptée.
	- Si moins bonne que précédente, on l'accepte avec une probabilité calculée (distribution de Boltzmaan)
![](https://image.slidesharecdn.com/chapitre4heuristiquesetmta-heuristiques-160202125547/95/chapitre-4-heuristiques-et-mta-heuristiques-36-638.jpg?cb=1454417798)- Pro / Cons : Souple vis à vis des étovlutions du problème, facile à implémenter, évite les pièges des optimaux locaux, excellent résultats pour un nombre de problèmes complexes **MAIS** : Nombreux tests nécessaires pour trouver les bons paramètres, définir les voisinages permettant un calcul efficace du delta de l'énergie

**o GRASP :** Greedy randomized adaptive search procedure) :
- Phase de construction : Combine les méthodes **gloutonnes** et **aléatoires** par étape. A chaque étape, on sélectionne les résultats et on les ajoutes dans une liste appellée RCL (Restricted Candidate List). Cette liste est triée par un algorithme glouton. On tire ensuite aléatoirement les meilleurs résultats pour les ajouter à la solution.
- Phase de recherche locale : On fais une recherche locale sur nos candidats savoir si il est encore possible d'améliorer cette solution.

**o Recherche local Guidé*** (GSL) :
- Aider la recherche locale pour échapper à des optimum locaux (des min en gros)
- Peut-être appliquée sur le voyageur de commerce 
- Utilise une technique de recherche locale dans laquelle la fonction objectif varie durant le processus de recherche, pour rendre les minimum locaux déjà visités moins attractif

 - Simple à utiliser, posable sur de grands nombre de problèmes d'optimisation combinatoire, éfficace (meilleures solutions obtenues en un temps de calcul modéré)
 - MAIS : moins puissante que des méthodes exactes sur certains types de problèmes. Ne garantie pas non plus la découverte d'un optimum global.


**o Recherche voisinage Variable**
- Proposé par Mladenovié et Hansen dans les années 90
- Décomposé en deux phases :
	- Déterministe (recherche locale qui converge vers un optimum)
	- Stochastique : Pour s'en échapper. On génère une nouvelle solution selon un voisin donnée

- On réintère plusieurs fois, à chaque fois en retantant sur un voisin, puis on éffectuant une nouvelle recherche locale...
- Peut s'arêter au bout de X itérations ou un temps de calcul alloué.

**o Voisinage :**  
- Débute avec une config initiale, et réalise un processus itératif qui consiste à remplacer la configuration courante par l'un de ses voisins en tenant compte de la fonction de **coût.** Ce processus s'arrête et retourne la meilleure configuration trouvée quand la condition d'arrêt est réalisée (ex : nombre d'itérations, temps exécution ou objectif à réaliser)
- Pro/Cons : Possibilité de contrôler le temps de calcul, s'améliore si on laisse du temps. Mais la solution obtenue dépend de la solution initiale, de la stratégie de voisinage et de parocurs de ce voisinage

### Diversification & Intensification :
Preponderant dans la conception des métaheuristiques. On doit atteindre un équilibre délicat entre ces deux dynamiques de recheches : exploration puisse rapidement identifier des régions de l'espace de recherche qui contiennent des points de bonne qualité, sans perdre trop de temps à exploiter des régions moins prometteuses.

**o Diversification**  (ou exploration)
- Désigne les processus visant à **récolter de l'information** sur le problème optimisé. 
- Mécanismes pour une exploration assez l'arge de l'espace de recherche
**o Intensification** (ou exploitation)
- Exploitation de l'information accumulée durant la recherche et concentration sur une zone précise

### Exemple d’utilisation

o Appliquer au voyageur de commerce

### No free lunch
- Théorème d'optimisation numérique
- On passe notrevie à optimiser quelque chose, à abritrer entre plusieurs ocntraintes pour choisir la plus adapté
- Les scientifiues sont des gros paresseux et aimeraient des recettes toutes faites pour aborder ce genre de problèmes d'opptimisations : Une méthode générale, applicable à tous les problèmes sans exceptions.
- CA N'EXISTE PAS, et le "No Free Lunch Theorem" l'affirme
- Le monde est trop complexe, il n'existe pas derecette générale perettant d'optimiser n'importe quel problème.  On peut le formuler sous deux manières :
	- Sur tous les problèmes d'optimisations numériques, aucun algo n'est meilleur que les autres. En effet, le coût moyen ne dépend pas de l'algorihme.
	- Le seul moyen de trouver qu'un algo est plus fort qu'un autre est de l'adapter au problème, de connaître certaines structures mathématiques sous-jacente du pb d'optimisation permettant d'améliorer la performance de celui ci.

### Trouver moyenne d’évaluation qualité

Pour tester une métaheuristiques :
- Utiliser des fonctions mathématiques spécialement conçues
- On doit répéter un grand nombre de fois (car stochastiques) puis exploités via des méthodesstatistiques
- Peu répendu dans la litératures spécialisée

### Corbeille d’exercice by MAZᶲ



