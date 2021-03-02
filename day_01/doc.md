# Merise (MCD, MLD et MPD)

## Introduction
*_Merise_* est le nom d'une méthode, ou d'un ensemble de méthodes, développée en France dans les années 1970, et qui a été très largement employée depuis lors. Depuis une quinzaine d'années, Merise laisse peu à peu place à UML.

Toute base de données va donner lieu à une double représentation :

1. le plan le plus abstrait (mais qui contient déjà toutes les informations indispensables pour la construction de la base de données) . Ce plan porte le nom de fort poétique de **Modèle Conceptuel de Données (MCD)**.
2. un plan plus proche de ce que sera la base effective, telle qu'elle sera réalisée sur machine : le **Modèle Logique des Données (MLD)**.

Le point crucial à enregistrer dès maintenant, c'est que *le MLD se déduit strictement du MCD d'après des règles formelles*. Autrement dit, une fois le MCD réalisé, il n'y a plus besoin de réfléchir une seule seconde pour produire le MLD : tout se fait par automatismes. La meilleure preuve, c'est qu'il existe des logiciels qui se proposent de réaliser le MLD d'un clic de souris, d'après le MCD. En revanche, il n'existe rien de tel pour concevoir le MCD : le seul ingrédient qui entre dans sa composition est l'huile de neurones. N'oubliez pas de faire quelques provisions...

## MCD, Les entités et les relations

Les informations à traiter doivent être regroupées en ensembles cohérents, comme dans les tableaux que nous avons constitués il y a un instant. Dans les conventions de Merise, ces ensembles s'appellent des **entités**, et sont symbolisés par des **rectangles**. Chaque entité porte un **nom**, qui l'identifie de manière unique. Ce nom sera obligatoirement un *_substantif au pluriel_* : pour notre discothèque, on propose très logiquement « Disques » et « Genres ».

Les entités comprennent toujours un certain nombre d'éléments appelés **propriétés** (on parlera aussi d'**attributs**). Il s'agit des différentes rubriques qui devront être renseignées pour chaque individu.

Chaque entité, lorsqu'on passera au MLD (puis à la réalisation concrète de la base) donnera lieu à un tableau (on parle plus volontiers de **tables**). L'entité Disques du MCD produira donc une table Disques dans le MLD, et l'entité Genres, une table Genre. Les différentes propriétés de l'entité, qui sont donc écrites les unes sous les autres, deviendront *_les titres des colonnes_* de ces tables. Et dans ces colonnes, on fera figurer les différentes valeurs que prennent ces propriétés pour chacun des éléments de nos tables. Si vous trouvez cette explication un peu compliquée, pensez tout simplement à l'entité / table Disques : le titre, l'année et l'artiste sont disposés les uns sous les autres lorsqu'on parle de l'entité, et les uns à côté des autres (ce sont des en-têtes de colonne) lorsqu'on la représente comme une table.

Il ne reste plus à signifier que pour que chaque CD possède un genre (et pas n'importe lequel), mes deux entités doivent se trouver en **relation** l'une avec l'autre. Cette relation (on peut aussi parler d'**association**) sera symbolisée par un **ovale**, et sera nommée (par un *_verbe_*).

Voilà donc ce que cela donne :
![fig1](./assets/fig01.png)

Cette représentation ne se lit pas n'importe comment. Pour être certain de ne pas commettre de contresens, lorsqu'on traduit le schéma ci-dessus, il vaut mieux éviter de dire « les disques possèdent des genres », ou pire encore « la table disque possède certains genres » La bonne traduction, celle qui vous évitera au maximum de commettre des erreurs, consiste à dire que « Chaque élément de la table Disques possède un (ou plusieurs ?) genres ». En prenant l'affaire par l'autre bout, on peut tout aussi bien dire (même si c'est un peu laid à l'oreille) : « Chaque genre est possédé par un (ou plusieurs ?) disques » (on verra un peu plus loin comment en avoir le cœur net sur ces points d'interrogation).

Résumons-nous :

+ les données doivent être systématiquement regroupées de manière à éviter les **redondances**, source de gâchis et, surtout, d'erreurs. Ce regroupement est la base de la modélisation.
+ chacun des groupements (correspond, dans le MCD, à une **entité**, qui se traduira par une table dans la Base de Données.
+ toute **entité** est symbolisée par un **rectangle**. Elle est nommée par un substantif au pluriel, désignant les éléments qu'elle contient
+ les **propriétés** d'une **entité** correspondent aux colonnes de la table qui sera déduite de cette entité.
+ les entités (c'est-à-dire : les individus présents dans les entités) peuvent être mises en rapport via des **relations** (ou **associations**)
+ toute **relation** est symbolisée par un **ovale**. Elle est nommée par un verbe.

## Éléments supplémentaires

### Deux nouveaux mots de vocabulaire

Dans une table, on évite de parler de « lignes » et de « colonnes ».

+ Les lignes correspondent aux différents individus, ou aux différents objets individuels, répertoriés dans une table : dans la table Disques, chaque ligne correspond à un de mes CD. Ces différents éléments individuels qui correspondent aux lignes sont appelés **enregistrements**.
+ Les colonnes, qui correspondent aux propriétés de l'entité dans le MCD, sont appelées des **champs**.

### Typage des propriétés

Vous ne serez guère étonnés d'appendre que les informations contenues dans les entités (donc, dans les tables) vont devoir au bout du compte être codées numériquement afin d'être stockées sur un support informatique, sous un nom qui est celui de la propriété.

Pour chaque enregistrement, celle-ci se comporte donc comme un **nom de variable**… ce qui est somme toute logique, car à de menus détails près, c'en est une. Tout ceci nous amène au fait que les propriétés, à l'instar des variables, relèvent de certains **types**.

Dans le détail, les types disponibles pour les propriétés varient légèrement d'un système de gestion de bases de données à l'autre. En ce qui nous concerne, nous pouvons en rester à un niveau assez général, en considérant les types les plus courants :

+ **numérique** : on y distingue systématiquement l'entier (« Integer ») du nombre à virgule (« Float »). Le type « AutoIncrement », souvent utilisé pour gérer les **clés primaires** [MODE NO PANIC ON] vous saurez ce que c'est très bientôt  [MODE NO PANIC OFF], correspond à un entier dont la valeur est automatiquement attribuée à la création d'un nouvel enregistrement. Les bases de données proposent également toujours au moins un type Date/Heure.
+ **texte** : on aura éventuellement différents types correspondant à différentes longueurs maximales du texte.
+ **booléen** : inévitable !

Outre les informations précédemment citées, les documents de modélisation, MCD et MLD, devront donc faire apparaître, pour chaque entité, le type de chaque propriété.

## Propriété identifiante (clé primaire)

Tout système de bases de données impose dans chaque entité, chaque individu (chaque enregistrement) puisse être identifié de manière unique, sans ambiguité, par la machine. Le procédé le plus courant consiste à dédier à cela une propriété spéciale, appelée **propriété identifiante** ou encore **clé primaire**. On peut constituer une clé primaire à partir d'une combinaison de champs, mais nous verrons que c'est une solution qui n'est employée que dans certains cas particuliers ; restons-en donc pour le moment à l'idée que la clé primaire est un champ spécial. La clé primaire est alors généralement placée en tête de la liste des propriétés, en la soulignant pour indiquer son statut particulier :

![fig2](./assets/fig02.png)

Il est en fait assez rare de trouver spontanément une propriété capable de jouer ce rôle. Même les propriétés qui semblent faire de bonnes candidates (par exemple, une plaque d'immatriculation ou un numéro de sécurité sociale) ne sont pas forcément aussi opportuns qu'elles en ont l'air, pour un certain nombre de raisons. Et il n'est pas rare qu'aucune des propriétés présentes ne puisse nous prémunir contre les doublons ; c'est le cas avec l'entité Disques de notre exemple : plusieurs Cd peuvent très bien avoir le même titre, et je ne parle pas de l'auteur ni de l'année. On ne peut pas davantage exclure la possibilité que deux auteurs homonymes aient sorti la même année un disque portant le même titre (ce qui nous empêche donc d'avoir confiance dans une clé primaire constituée de la combinaison des trois propriétés).

Voilà pourquoi le plus souvent, on sera amené à créer une *_propriété supplémentaire_* destinée uniquement à jouer le rôle d'indentifiant / clé primaire. Il s'agira presque toujours d'un code, unique pour chaque occurrence de l'entité (et voilà pourquoi un nombre de type « autoincrement » est si pratique). Ce code sera rarement visible par l'utilisateur, qui ignorera sans doute son existence : il n'en sera pas moins indispensable pour le système informatique. Ainsi, notre modèle de discothèque deviendra-t-il :

![fig 3](./assets/fig03.png)

## Les cardinalités

Contrairement à ce que certains pourraient penser, ce terme n'indique ni le fait de devenir cardinal (Dieu m'en garde !) ni le fait de se situer à l'un des quatre points cardinaux (en l'occurrence, complètement à l'Ouest). Non, la cardinalité, c'est un mot savant de mathématicien pour dire tout bêtement que l'affaire a un rapport avec des nombres et des quantités. Pour dire la même chose, on aurait pu donc tout simplement parler de « quantité » ou de « numération ». Sauf que dans un dîner de famille, placez subrepticement « cardinalité » entre la poire et le fromage, et vous pourrez vérifier par vous-mêmes que l'effet obtenu n'est pas du tout le même.

## Du MCD au MLD : première approche



## Relations multiples

## La réflexivité

## Relations avec attributs

## Relations de dimension supérieure à 2

## Exercice #1

Une bibliothèque de prêt dispose d'un certain nombre d'ouvrages, classés par rayon (Littérature, Histoire, Géographie, etc.). Chaque ouvrage est l'oeuvre d'un ou plusieurs auteurs, et doit également être référencé selon un certain nombre de mots-clés.

Chaque adhérent peut emprunter jusqu'à 5 livres en même temps, et dispose d'un certain délai passé lequel il doit recevoir des relances puis des pénalités.

On se place dans quatre cas successifs, de complexité croissante :

1. la bibliothèque ne possède qu'un seul exemplaire de chaque ouvrage. Elle enregistre uniquement les emprunts présents (il n'y a pas d'historique des emprunts passés).
2. la bibliothèque ne possède qu'un seul exemplaire de chaque ouvrage, mais elle tient un historique de tous les emprunts qui ont été effectués.
3. la bibliothèque tient un historique... et elle est maintenant susceptible de posséder plusieurs exemplaires de certains ouvrages
4. en plus de cela, il existe une bibliothèque centrale et des antennes locales. Chaque antenne possède un fonds qui lui est propre, et peut de surcroit se procurer certains ouvrages auprès de la bibliothèque centrale (mais pas d'une autre bibliothèque locale). Tout adhérent peut automatiquement emprunter des ouvrages dans toutes les antennes locales.

Etablir le MCD et le MLD adéquats dans les quatre cas.

