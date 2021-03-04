# Langage SQL

## Introduction
*_SQL_* signifie langage de requête structuré (Structured Query Language). SQL est un langage de programmation standard spécialement conçu pour stocker, extraire, gérer ou manipuler les données à l'intérieur d'un système de gestion de bases de données relationnelles (SGBDR). SQL est devenu une norme ISO en 1987.

SQL est le langage de base de données le plus largement mis en oeuvre et soutenu par les systèmes de base de données relationnelles populaires, comme MySQL, SQL Server, et Oracle. Cependant, certaines fonctionnalités de la norme SQL sont implémentées différemment dans différents systèmes de bases de données.

SQL est très populaire car il offre les avantages suivants:

* Permet aux utilisateurs d'accéder aux données des systèmes de gestion de base de données relationnelle.
* Permet aux utilisateurs de décrire les données.
* Permet aux utilisateurs de définir les données dans une base de données et de les manipuler.
* Permet d'intégrer dans d'autres langages en utilisant des modules SQL, des bibliothèques et des pré-compilateurs.
* Permet aux utilisateurs de créer et de supprimer des bases de données et des tables.
* Permet aux utilisateurs de créer une vue, une procédure stockée et des fonctions dans une base de données.
* Permet aux utilisateurs de définir des autorisations sur les tables, les procédures et les vues.

Tout d'abord il faut installer MySQL (Server Workbench): [lien d'installation](https://dev.mysql.com/downloads/mysql/)

## Les commandes SQL

Les commandes SQL standard pour interagir avec les bases de données relationnelles sont **CREATE**, **SELECT**, **INSERT**, **UPDATE**, **DELETE** et **DROP**. Ces commandes peuvent être classées dans les groupes suivants en fonction de leur nature.

### LDD - Langage de définition de données

| Commande | Description |
|:---:|:---:|
| CREATE | Crée une nouvelle table, une vue d’une table ou un autre objet de la base de données.|
| ALTER | Modifie un objet de base de données existant, tel qu'une table.|
| DROP | Supprime une table entière, une vue d'une table ou d'autres objets de la base de données.|

### LMD - Langage de manipulation de données

| Commande | Description |
|:---:|:---:|
| SELECT | Récupère certains enregistrements d'une ou de plusieurs tables.|
| INSERT | Crée un enregistrement. |
| UPDATE | Modifie les enregistrements.| 
| DELETE | Supprime les enregistrements.|

### LCD - Langage de contrôle de données

| Commande | Description |
|:---:|:---:|
| GRANT | Donne un privilège à l'utilisateur. |
| REVOKE | Reprend les privilèges accordés par l'utilisateur. |

## Concepts de base de SGBDR

Un système de gestion de base de données relationnelle (SGBDR) est un système de gestion de base de données basé sur le modèle relationnel.

Une base de données relationnelle est une collection d'un ensemble organisé de tables liées les unes aux autres et à partir desquelles il est facile d'accéder aux données. La base de données relationnelle est la base de données la plus utilisée de nos jours.

### une table dans le modèle SGBDR

Dans le modèle de base de données relationnelle, une table est un ensemble d'éléments de données organisés en lignes et en colonnes. Un tableau est également considéré comme une représentation commode des relations. Mais une table peut avoir une ligne de données en double alors qu'une relation vraie ne peut pas avoir de données en double. La table est la forme la plus simple de stockage de données.
Vous trouverez ci-dessous un exemple de table d'employes.

| Id | Nom | Age | Salaire |
|:---:|:---:|:---:|:---:|
| 1 | Abdelhamid | 22 | 5500 |
| 2 | Mohamed | 24 | 5000 |
| 3 | Mounia | 32 | 70000 |

### un tuple dans le modèle SGBDR

Une seule entrée dans une table est appelée un tuple ou un enregistrement ou une ligne. Un tuple dans une table représente un ensemble de données liées. Par exemple, la table des employes ci-dessus a 3 n-uplets/enregistrements/lignes.

Voici un exemple d'enregistrement simple ou de tuple.

| 2 | Mohamed | 24 | 5000 |

### un attribut dans le modèle SGBDR

Une table est constituée de plusieurs enregistrements (lignes), chaque enregistrement pouvant être décomposé en plusieurs parties de données plus petites appelées attributs. La table des employés ci-dessus comprend quatre attributs, **ID**, **Nom**, **Age** et **Salaire**.

### le schéma de relation

Un schéma de relation décrit la structure de la relation, avec le nom de la relation (nom de la table), ses attributs, leurs noms et leur type.

### une clé de relation

Une clé de relation est un attribut qui peut identifier de manière unique un tuple (ligne) particulier dans une relation (table).

## Syntaxe SQL

Toutes les instructions SQL commencent par l'un des mots clés tels que **SELECT**, **INSERT**, **UPDATE**, **DELETE**, **ALTER**, **DROP**, **CREATE**, **USE**, **SHOW** et __toutes les instructions se terminent par un point-virgule (;)__.

### Instruction SELECT
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table;
```

### Clause DISTINCT
```sql
SELECT DISTINCT colonne1, colonne2 ... colonneN
FROM nom_table;
```

### Clause WHERE
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE CONDITION;
```

### Clause AND/OR
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE CONDITION-1 {AND|OR} CONDITION-2;
```

### Clause IN
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE nom_colonne IN (val-1, val-2,...val-N);
```

### Clause BETWEEN
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE nom_colonne BETWEEN val-1 AND val-2;
```

### Clause LIKE
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE nom_colonne LIKE { PATTERN };
```

### Clause ORDER BY
```sql
SELECT colonne1, colonne2 ... colonneN
FROM nom_table
WHERE CONDITION
ORDER BY nom_colonne {ASC|DESC};
```

### Clause GROUP BY
```sql
SELECT SUM(nom_colonne)
FROM nom_table
WHERE CONDITION
GROUP BY nom_colonne;
```

### Clause COUNT
```sql
SELECT COUNT(nom_colonne)
FROM nom_table
WHERE CONDITION;
```

### Clause HAVING
```sql
SELECT SUM(nom_colonne)
FROM nom_table
WHERE CONDITION
GROUP BY nom_colonne
HAVING (condition de la fonction arithmétique);
```
                            
### Instruction CREATE TABLE
```sql
CREATE TABLE nom_table(
                        colonne1 type_donnees,
                        colonne2 type_donnees,
                        colonne3 type_donnees,
                        .....
                        colonneN type_donnees,
                        PRIMARY KEY( une ou plusieurs colonnes )
                        );
```

### Instruction DROP TABLE
```sql
DROP TABLE nom_table;
```

### Instruction CREATE INDEX
```sql
CREATE UNIQUE INDEX nom_index
        ON nom_table ( colonne1, colonne2,...colonneN);
```

### Instruction DROP INDEX
```sql
ALTER TABLE nom_table
DROP INDEX nom_index;
```

### Instruction DESC
```sql
DESC nom_table;
```

### Instruction TRUNCATE TABLE
```sql
TRUNCATE TABLE nom_table;
```

### Instruction ALTER TABLE
```sql
ALTER TABLE nom_table {ADD|DROP|MODIFY} nom_colonne {type_donnees};
```

### Instruction ALTER TABLE (rename)
```sql
ALTER TABLE nom_table RENAME TO nouveau_nom_table;
```

### Instruction INSERT INTO
```sql
INSERT INTO nom_table( colonne1, colonne2 ... colonneN)
VALUES ( valeur1, valeur2....valeurN);
```

### Instruction UPDATE
```sql
UPDATE nom_table
SET colonne1 = valeur1, colonne2 = valeur2....colonneN=valeurN
[ WHERE  CONDITION ];
```

### Instruction DELETE
```sql
DELETE FROM nom_table
WHERE  {CONDITION};
```
### Instruction CREATE DATABASE
```sql
CREATE DATABASE nom_bd;
```

### Instruction DROP DATABASE
```sql
DROP DATABASE nom_bd;
```

### Instruction USE
```sql
USE nom_bd;
```

### Instruction COMMIT
```sql
COMMIT;
```

### Instruction ROLLBACK
```sql
ROLLBACK;
```

## Opérateurs SQL

Un opérateur est un mot réservé ou un caractère utilisé principalement dans la clause WHERE d'une instruction SQL pour effectuer des opérations, telles que des comparaisons et des opérations arithmétiques. Ces opérateurs sont utilisés pour spécifier des conditions dans une instruction SQL et pour servir de conjonctions pour plusieurs conditions dans une instruction.

* Opérateurs arithmétiques
* Opérateurs de comparaison
* Opérateurs logiques

### Opérateurs arithmétiques

| Opérateur | Description |
|:---:|:---:|
| + (Addition) | Ajoute des valeurs de chaque côté de l'opérateur. |
| - (Soustraction) | Soustrait l'opérande droit de l'opérande gauche. |
| * (Multiplication) |Multiplie les valeurs de chaque côté de l'opérateur. |
| / (Division) | Divise l'opérande gauche par l'opérande droit. |
|  % (Reste de division) | Divise l'opérande gauche par l'opérande droit et renvoie le reste. |

### Opérateurs de comparaison

| Opérateur | Description |
|:---:|:---:|
| = | Vérifie si les valeurs de deux opérandes sont égales ou non, si oui, la condition devient vraie. |
| != | Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales, alors la condition devient vraie. |
| <>| Vérifie si les valeurs de deux opérandes sont égales ou non, si les valeurs ne sont pas égales, alors la condition devient vraie. |
| >	| Vérifie si la valeur de l'opérande gauche est supérieure à la valeur de l'opérande droit. Si oui, la condition devient vraie. |
| <	| Vérifie si la valeur de l'opérande gauche est inférieure à la valeur de l'opérande droit. Si oui, la condition devient vraie. |
| >= | Vérifie si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite, si oui, la condition devient vraie. |
| <= | Vérifie si la valeur de l'opérande gauche est inférieure ou égale à la valeur de l'opérande droit. Si oui, la condition devient vraie. |
| !< | Vérifie si la valeur de l'opérande gauche n'est pas inférieure à la valeur de l'opérande droit. Si la réponse est oui, la condition devient vraie. |
| !> | Vérifie si la valeur de l'opérande de gauche n'est pas supérieure à la valeur de l'opérande de droite, si oui, la condition devient vraie. |

### Opérateurs logiques

| Opérateur | Description |
|:---:|:---:|
| ALL | L'opérateur ALL permet de comparer une valeur à toutes les valeurs d'un autre jeu de valeurs. |
| ANY | L'opérateur ANY est utilisé pour comparer une valeur à une valeur applicable de la liste conformément à la condition. |
| BETWEEN | L'opérateur BETWEEN permet de rechercher des valeurs comprises dans un ensemble de valeurs, en fonction de la valeur minimale et de la valeur maximale. |
| EXISTS | L'opérateur EXISTS est utilisé pour rechercher la présence d'une ligne dans une table spécifiée qui répond à un certain critère. |
| IN | L'opérateur IN est utilisé pour comparer une valeur à une liste de valeurs littérales spécifiées. |
| LIKE | L'opérateur LIKE est utilisé pour comparer une valeur à des valeurs similaires à l'aide d'opérateurs génériques. |
| NOT | L'opérateur NOT inverse la signification de l'opérateur logique avec lequel il est utilisé. Ex.: NOT EXISTS, NOT BETWEEN, NOT IN, etc. Ceci est un opérateur de négation. |
| AND | L'opérateur AND permet l'existence de plusieurs conditions dans la clause WHERE d'une instruction SQL. |
| OR | L'opérateur OR est utilisé pour combiner plusieurs conditions dans la clause WHERE d'une instruction SQL. |
| IS NULL | L'opérateur IS NULL est utilisé pour comparer une valeur avec une valeur NULL. |
| UNIQUE | L'opérateur UNIQUE recherche dans chaque ligne de la table spécifiée l'unicité (pas de doublons). |


## Définition de données

### Création et suppréssion d'une DB

L'instruction **CREATE DATABASE** est utilisée pour créer une nouvelle base de données SQL.

```sql
CREATE DATABASE nomBDonnees;
```
```sh
#Le nom de la base de données doit toujours être unique dans le SGBDR.
```

Une fois la base de données créée, vous pouvez la vérifier comme suit dans la liste des bases de données.

```sql
SHOW DATABASES;
```
### Supprimer une base de données

L'instruction **DROP DATABASE** est utilisée pour supprimer une base de données existante dans un schéma SQL.

```sql
DROP DATABASE nomBDonnees;
```

### Sélectionner une base de données

L'instruction **USE** permet de sélectionner une base de données existante dans le schéma SQL.

```sql
USE nomBDonnees;
```

### TYPES DE DONNÉES SQL

Types de données SQL principalement classés en six catégories pour chaque base de données.

* Types de données de chaînes
* Types de données numériques
* Date et heure
* Types de données binaires tels que binaire, varbinaire, etc.
* Types de données de chaîne de caractères Unicode tels que nchar, nvarchar, ntext, etc.
* Autres types de données tels que clob, blob, XML, curseur, table, etc.

### Types de données numériques

| Type de données | De | A |
|:---:|:---:|:---:|
| bit | 0 | 1 |
| tinyint | 0 | 255 |
| smallint | -32,768 | 32,767 |
| int | -2,147,483,648 | 2,147,483,647 |
| bigint | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |
| decimal | -10^38 +1 | 10^38 -1 |
| numeric | -10^38 +1 | 10^38 -1 |
| float | -1.79E + 308 | 1.79E + 308 |
| real | -3.40E + 38 | 3.40E + 38 |

### Types de données Date et Heure

| Type de données | Description |
|:---:|:---:|
| DATE | Stocke la date dans le format YYYY-MM-DD |
| TIME | Stocke l'heure dans le format HH:MI:SS |
| DATETIME | Stocke les informations de date et heure au format YYYY-MM-DD HH:MI:SS |
| TIMESTAMP	| Stocke le nombre de secondes écoulées depuis l'époque Unix (Horodatage) (‘1970-01-01 00:00:00’ UTC) |
| YEAR | Stocke l'année en format 2 chiffres ou 4 chiffres. Plage 1901 à 2155 en format à 4 chiffres. Plage 70 à 69, représentant 1970 à 2069. |

### Types de données caractères et chaînes

| Type de données | Description |
|:---:|:---:|
| CHAR | Longueur fixe avec une longueur maximale de 8 000 caractères |
| VARCHAR | Stockage de longueur variable avec une longueur maximale de 8 000 caractères |
| VARCHAR(max) | Stockage à longueur variable avec le nombre maximum de caractères fourni, non pris en charge dans MySQL |
| TEXT | Le stockage de longueur variable avec une taille maximale de 2 Go de données |

### Types de données Unicode caractères et chaînes
| Type de données | Description |
|:---:|:---:|
| NCHAR | Longueur fixe avec une longueur maximale de 4 000 caractères |
| NVARCHAR | Stockage de longueur variable avec une longueur maximale de 4 000 caractères |
| NVARCHAR(max)	| Stockage de longueur variable avec max caractères fournis |
| NTEXT	| Stockage de longueur variable avec une taille maximale de 1 Go de données |

### Types de données binaires

| Type de données | Description |
|:---:|:---:|
| BINARY | Longueur fixe avec une longueur maximale de 8 000 octets |
| VARBINARY	| Stockage de longueur variable avec une longueur maximale de 8 000 octets |
| VARBINARY(max) | Stockage de longueur variable avec le nombre max d'octets fournis |
| IMAGE	| Stockage de longueur variable avec une taille maximale de 2 Go de données binaires |

### Autres types de données

| Type de données | Description |
|:---:|:---:|
| CLOB | Grands objets de caractère pouvant contenir jusqu'à 2 Go |
| BLOB | Pour les gros objets binaires |
| XML | Pour stocker des données XML |
| JSON | Pour stocker des données JSON |

## CRÉATION ET SUPPRESSION DES TABLES EN SQL

### CREATE TABLE

L'instruction **CREATE TABLE** permet de créer une nouvelle table.

```sql
CREATE TABLE nom_table(
    column1 type_donnees [contraintes],
    column2 type_donnees [contraintes],
    column3 type_donnees [contraintes],
    .....
    columnN type_donnees [contraintes],
    PRIMARY KEY( une ou plusieurs colonnes )
);
```

### DROP TABLE

L'instruction **DROP TABLE** permet de supprimer une définition de table ainsi que toutes les données, index, déclencheurs, contraintes et spécifications de permission de cette table.

```sql
DROP TABLE nom_table;
```

## MODIFIER LA STRUCTURE D'UNE TABLE

La syntaxe de base d'une commande **ALTER TABLE** pour ajouter une nouvelle colonne dans une table existante est la suivante :

### ALTER TABLE - ADD

**ADD** peut également être utilisé pour créer une contrainte sur les colonnes de la table

```sql
ALTER TABLE table_name
    ADD (colonne1  type_donnees,
    colonne1  type_donnees,
    ...
    colonneN  type_donnees);
```

Exemple:
```sql
ALTER TABLE Employes ADD Adresse Varchar(100);
```

**_Ajouter une contrainte_**
**ADD** peut également être utilisé pour créer une contrainte sur les colonnes de la table
```sql
ALTER TABLE nom_table 
    ADD CONSTRAINT nom_contrainte contrainte
```

Exemple: Pour supprimer la colonne **Age** de la table Employes, vous pouvez utiliser la requête suivante :
```sql
ALTER TABLE Employes
    ADD CONSTRAINT ageContrainte CHECK(Age >= 18);
```

### ALTER TABLE - DROP

**DROP COLUMN** est utilisé pour supprimer une colonne dans une table. Suppression des colonnes indésirables de la table.

```sql
ALTER TABLE nom_table
    DROP COLUMN nom_colonne;
```

**_Supprimer une contrainte_**
**DROP CONSTRAINT** peut également être utilisé pour supprimer une contrainte sur les colonnes de la table
```sql
ALTER TABLE nom_table 
    DROP CONSTRAINT nom_contrainte;
```

Exemple: Pour supprimer la contrainte ageContrainte sur la colonne Age de la table Employes, vous pouvez utiliser la requête suivante :
```sql
ALTER TABLE Employes
    DROP CONSTRAINT ageContrainte;
```

### ALTER TABLE - MODIFY

Elle est utilisée pour modifier les colonnes existantes dans une table. Plusieurs colonnes peuvent également être modifiées à la fois.

```sql
ALTER TABLE nom_table
    MODIFY nom_colonne type_donnees;
```

## Manipulation de données

### INSERT, UPDATE & DELETE

#### INSERT INTO

L'instruction **INSERT INTO** est utilisée pour ajouter de nouvelles lignes de données à une table de la base de données.
```sql
INSERT INTO nom_table (colonne1, colonne2, colonne3,...colonneN)  
VALUES (valeur1, valeur2, value3,...valeurN);
```

#### UPDATE

La requête **UPDATE** est utilisée pour modifier les enregistrements existants dans une table. Vous pouvez utiliser la clause **WHERE** avec la requête **UPDATE** pour mettre à jour les lignes sélectionnées, sinon toutes les lignes seraient affectées.
```sql
UPDATE nom_table
SET colonne1 = valeur1, colonne2 = valeur2...., colonneN = valeurN
[WHERE condition];
```
Vous pouvez combiner un nombre plusieurs conditions à l’aide des opérateurs **AND** ou **OR**.

#### DELETE

La requête **DELETE** est utilisée pour supprimer les enregistrements existants d'une table.

Vous pouvez utiliser la clause **WHERE** avec une requête **DELETE** pour supprimer les lignes sélectionnées, sinon tous les enregistrements seraient supprimés.
```sql
DELETE FROM nom_table
[WHERE condition];
```

### Extraction des données - SELECT

L'instruction **SELECT** en SQL permet d'extraire des données d'une base de données. Nous pouvons récupérer la table entière ou selon certaines règles spécifiées. Les données renvoyées sont stockées dans une table de résultats.
```sql
SELECT colonne1, colonne2,..., colonneN FROM nom_table;
```
Ici, **colonne1, colonne2,..., colonneN** sont les champs d'une table dont vous voulez récupérer les valeurs. Si vous voulez récupérer tous les champs, vous pouvez utiliser la syntaxe suivante :
```sql
SELECT * FROM nom_table;
```

Pour renommer une colonne spécifique dans le jeu de résultats, utilisez le mot clé **AS** dans la requête.

```sql
SELECT Id, Nom AS "Nom d'employé ", Salaire FROM Employes;
```
```
Pour renommer la colonne Nom avec "Nom d'employé" dans le jeu de résultats
                                +----+-----------------+---------+
                                | Id | Nom d'employé   | Salaire |
                                +----+-----------------+---------+
                                |  1 | Issam           | 6000.00 |
                                |  2 | MedAmine        | 8000.40 |
                                |  3 | Hiba            | 6000.00 |
                                |  4 | Oumayma         | 9000.00 |
                                |  5 | Amina           | 7500.00 |
                                +----+-----------------+---------+
```
Vous pouvez également utiliser le mot clé AS pour attribuer un raccourci au nom de la table et utiliser ce raccourci dans la requête. Ceci est très utile lorsque nous traitons plusieurs tables.
```sql
SELECT emp.Id, emp.Nom, Salaire FROM Employes AS emp;
```
Nous pouvons également utiliser des expressions dans l'instruction SELECT
```sql
SELECT Id, Nom, (Salaire*1.5) AS "Nouveau Salaire" FROM Employes;
```

### Filtration des données avec WHERE

La clause SQL **WHERE** est utilisée pour spécifier une condition lors de l'extraction des données d'une seule table ou de plusieurs tables associées. Si la condition donnée est satisfaite, elle renvoie uniquement une valeur spécifique de la table. Vous devez utiliser la clause WHERE pour filtrer les enregistrements et extraire uniquement les enregistrements nécessaires.

La clause WHERE est non seulement utilisée dans l'instruction SELECT, mais également dans l'instruction UPDATE, DELETE, etc.

```sql
SELECT colonne1, colonne2,..., colonneN 
FROM nom_table
WHERE [condition]
```

### Recherche avec LIKE

Parfois, nous pouvons exiger des nuplets de la base de données qui correspondent à certains modèles. Par exemple, nous pouvons souhaiter extraire toutes les colonnes où les n-uplets commencent par la lettre "y" ou par "b" et se terminent par "a", ou même par des motifs de chaîne plus compliqués et restrictifs. C'est ici que la lause LIKE vient nous sauver.
Souvent associée à la clause WHERE en SQL.

Deux types de caractères génériques sont utilisés pour filtrer les résultats:

* %  : Utilisé pour faire correspondre zéro, un ou plusieurs caractères. (Longueur variable)
* _  : Utilisé pour correspondre exactement à un caractère. (Longueur fixe)

Exemple: La requête suivante va chercher tous les employés dont les noms commencent par "Mo"
```sql
SELECT * FROM Employes WHERE Nom LIKE "Mo%";
```

| Modèle | Description |
|:---:|:---:|
| "a%" | Il fait correspondre les chaînes qui commencent par "a" |
| "%a" | Il fait correspondre les chaînes qui se terminent par "a" |
| "a%t" | Il fait correspondre les chaînes qui commencent par «a» et se terminent par «t». |
| "%abc%" | Il fait correspondre les chaînes qui contiennent la sous-chaîne "abc" en n'importe quelle position. |
| "_abc%" | Il fait correspondre les chaînes contenant la sous-chaîne "abc" en deuxième position. |
| "_a%" |	Il fait correspondre les chaînes contenant «a» à la deuxième position. |
| "a_%_%" |	Il fait correspondre les chaînes qui commencent par "a" et contiennent au moins 2 caractères supplémentaires. |

### Trier les données - ORDER BY

L’instruction ORDER BY dans SQL est utilisée pour trier les données extraites par ordre croissant ou décroissant selon une ou plusieurs colonnes.

* Par défaut, ORDER BY trie les données par ordre croissant.
* Vous pouvez utiliser le mot-clé DESC pour trier les données par ordre décroissant et le mot-clé ASC pour trier par ordre croissant.
```sql
SELECT liste-colonnes
FROM nom_table 
[WHERE condition] 
[ORDER BY colonne1, colonne2, .. ] [ASC | DESC];
```
NB: Lorsque vous utilisez ORDER BY sur plusieurs colonnes, le tri commence par la première colonne, si deux ou plusieurs enregistrements ont le même rang, alors le tri passe à la colonne suivante, etc.

### LES JOINTURES EN SQL - JOIN

La clause JOIN est utilisée pour récupérer les données de deux ou plusieurs tables, qui sont jointes pour apparaître comme un seul ensemble de données. Elle est utilisée pour combiner des colonnes de deux tables ou plus en utilisant des valeurs communes aux deux tables.

Le mot-clé JOIN est utilisé dans les requêtes SQL pour joindre deux tables ou plus. Les conditions minimales requises pour joindre la table sont (n-1), n étant le nombre de tables. Une table peut également se joindre à elle-même, appelée SELF JOIN.

Voici les types de jointure que nous pouvons utiliser en SQL:

* CROSS
* INNER
* LEFT
* RIGHT
* SELF


[VEUILLEZ VOIR AIDE MEMOIRE](mysql-aid-memoire-sql.pdf)
[Lien utilie](https://sql.sh/cours)