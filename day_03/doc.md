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

```
Pendant ce cours, nous allons travailler sur ces deux tables
Table - Employes                                      
+----+---------+-----+---------+------------+------+
| Id | Nom     | Age | Salaire | Profession | Dep  |
+----+---------+-----+---------+------------+------+
|  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |
+----+---------+-----+---------+------------+------+ 
Table - Departement
+--------+--------------+
| Id_dep | Nom_dep      |
+--------+--------------+
|      1 | Informatique |
|      2 | RH           |
|      3 | Vente        |
|      4 | Strategies   |
+--------+--------------+
```

### CROSS JOIN

Ce type de **JOIN** renvoie le produit cartésien des lignes des tables de la jointure. Elle renverra un jeu de résultats des enregistrements combinant chaque ligne de la première table avec chaque ligne de la deuxième table.
```sql
SELECT liste-colonnes
FROM
table1 CROSS JOIN table2;
```

Exemple:
```sql
SELECT * FROM Departement CROSS JOIN Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+--------+--------------+----+---------+-----+---------+------------+------+
| Id_dep | Nom_dep      | Id | Nom     | Age | Salaire | Profession | Dep  |
+--------+--------------+----+---------+-----+---------+------------+------+
|      1 | Informatique |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|      2 | RH           |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|      3 | Vente        |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|      4 | Strategies   |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|      1 | Informatique |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|      2 | RH           |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|      3 | Vente        |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|      4 | Strategies   |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|      1 | Informatique |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|      2 | RH           |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|      3 | Vente        |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|      4 | Strategies   |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|      1 | Informatique |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|      2 | RH           |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|      3 | Vente        |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|      4 | Strategies   |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|      1 | Informatique |  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
|      2 | RH           |  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
|      3 | Vente        |  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
|      4 | Strategies   |  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
|      1 | Informatique |  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |
|      2 | RH           |  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |
|      3 | Vente        |  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |
|      4 | Strategies   |  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |
+--------+--------------+----+---------+-----+---------+------------+------+
Comme vous pouvez le constater, cette jointure renvoie le produit cartésien de tous les enregistrements présents dans les deux tables.
```

### INNER JOIN

La jointure la plus importante et la plus utilisée est la jointure **INNER**. Elle est également appelée jointure d'égalité.

**INNER JOIN** crée un jeu de résultats en combinant les valeurs de colonne de deux tables **(table1 et table2)** en fonction du prédicat de jointure. La requête compare chaque ligne de **table1(A)** avec chaque ligne de **table2(B)** pour rechercher toutes les paires de lignes satisfaisant le prédicat de jointure. Lorsque le prédicat de jointure est satisfait, les valeurs de colonne de chaque paire de lignes correspondante de **A** et de **B** sont combinées dans une ligne de résultat.

```sql
SELECT liste-colonnes
FROM
table1 INNER JOIN table2
ON table1.champ_commun = table1.champ_commun;
```

La plupart des gens utilisent cette syntaxe à la place de la première syntaxe

```sql
SELECT liste-colonnes
FROM
table1, table2
WHERE table1.champ_commun = table1.champ_commun;
```

Exemple:
```sql
SELECT * FROM Departement AS D INNER JOIN Employes AS E ON D.Id_dep=E.Dep;
```
```
Cette requête produira le jeu de résultats suivant :

+--------+--------------+----+---------+-----+---------+------------+------+
| Id_dep | Nom_dep      | Id | Nom     | Age | Salaire | Profession | Dep  |
+--------+--------------+----+---------+-----+---------+------------+------+
|      2 | RH           |  1 | Rajae   |  25 | 6000.00 | Assistante |    2 |
|      1 | Informatique |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|      3 | Vente        |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|      4 | Strategies   |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|      1 | Informatique |  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |
+--------+--------------+----+---------+-----+---------+------------+------+
```

### LEFT JOIN

**LEFT JOIN** renvoie toutes les lignes de la table de gauche, même s'il n'y a pas de correspondance dans la table de droite. Cela signifie que si la clause **ON** correspond à 0 (zéro) enregistrements dans la table de droite; la jointure retournera toujours une ligne dans le résultat, mais avec **NULL** dans chaque colonne de la table de droite.

Cela signifie qu'une jointure gauche renvoie toutes les valeurs de la table de gauche, ainsi que les valeurs correspondantes de la table de droite ou NULL en cas d'absence de prédicat de jointure correspondant.
```sql
SELECT liste-colonnes
FROM
table1 LEFT JOIN table2
ON table1.champ_commun = table1.champ_commun;
```

Exemple:
```sql
SELECT * FROM Employes AS E LEFT JOIN Departement as D ON D.Id_dep=E.Dep;
```
```
Cette requête produira le jeu de résultats suivant :
+----+---------+-----+---------+------------+------+--------+--------------+
| Id | Nom     | Age | Salaire | Profession | Dep  | Id_dep | Nom_dep      |
+----+---------+-----+---------+------------+------+--------+--------------+
|  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |      1 | Informatique |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |      1 | Informatique |
|  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |      2 | RH           |
|  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |      3 | Vente        |
|  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |      4 | Strategies   |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |   NULL | NULL         |
+----+---------+-----+---------+------------+------+--------+--------------+
```

### RIGHT JOIN

**RIGHT JOIN** renvoie toutes les lignes de la table de droite, même s'il n'y a pas de correspondance dans la table de gauche. Cela signifie que si la clause **ON** correspond à 0 (zéro) enregistrements dans la table de gauche; la jointure retournera toujours une ligne dans le résultat, mais avec **NULL** dans chaque colonne de la table de gauche.
```sql
SELECT liste-colonnes
FROM
table1 RIGHT JOIN table2
ON table1.champ_commun = table1.champ_commun;
```

Exemple:
```sql
SELECT * FROM Employes AS E RIGHT JOIN Departement as D ON D.Id_dep=E.Dep;
```
```
Cette requête produira le jeu de résultats suivant :

+------+---------+------+---------+------------+------+--------+--------------+
| Id   | Nom     | Age  | Salaire | Profession | Dep  | Id_dep | Nom_dep      |
+------+---------+------+---------+------------+------+--------+--------------+
|    1 | Rajae   |   22 | 6000.00 | Assistante |    2 |      2 | RH           |
|    2 | Mohamed |   24 | 8000.40 | Directeur  |    1 |      1 | Informatique |
|    3 | Mahamat |   29 | 6000.00 | Directeur  |    3 |      3 | Vente        |
|    4 | Mounia  |   32 | 7000.00 | Assistante |    4 |      4 | Strategies   |
|    5 | Ziad    |   21 | 9000.00 | Ingenieur  |    1 |      1 | Informatique |
+------+---------+------+---------+------------+------+--------+--------------+ 
```

### SELF JOIN

**SELF JOIN** est utilisée pour joindre une table à elle-même comme si la table était deux tables; renommer temporairement au moins une table dans l'instruction SQL.
```sql
SELECT * FROM Employes AS T1, Employes AS T2 WHERE T1.Salaire>T2.Salaire;
```
```
Cette requête produira le jeu de résultats suivant :

+----+---------+-----+---------+------------+------+----+---------+-----+---------+------------+------+
| Id | Nom     | Age | Salaire | Profession | Dep  | Id | Nom     | Age | Salaire | Profession | Dep  |
+----+---------+-----+---------+------------+------+----+---------+-----+---------+------------+------+
|  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |  1 | Rajae   |  22 | 6000.00 | Assistante |    2 |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |
|  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |  3 | Mahamat |  29 | 6000.00 | Directeur  |    3 |
|  2 | Mohamed |  24 | 8000.40 | Directeur  |    1 |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|  5 | Ziad    |  21 | 9000.00 | Ingenieur  |    1 |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
|  7 | Anas    |  23 | 9000.00 | Ingenieur  | NULL |  4 | Mounia  |  32 | 7000.00 | Assistante |    4 |
+----+---------+-----+---------+------------+------+----+---------+-----+---------+------------+------+
```

## FONCTIONS D'AGRÉGATION EN SQL - SUM, COUNT, AVG, MIN ET MAX

La fonction d'agrégation SQL est utilisée pour effectuer les calculs sur plusieurs lignes d'une seule colonne d'une table. Elle retourne une valeur unique.

Elle est également utilisée pour résumer les données.

La norme ISO définit cinq fonctions d'agrégation, à savoir:

* COUNT
* SUM
* AVG
* MIN
* MAX

### SUM
La fonction **SUM** renvoie la somme de toutes les valeurs de la colonne spécifiée. SUM fonctionne uniquement sur les champs numériques.
```sql
SUM( [ALL|DISTINCT] nom_colonne ) 
```

Exemple: La requête suivante renvoie la somme des salaires,
```sql
SELECT SUM(Salaire) FROM Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+--------------+
| SUM(Salaire) |
+--------------+
|     43500.40 |
+--------------+
```

### COUNT
La fonction **COUNT** est utilisée pour compter le nombre de lignes dans une table de base de données. Il peut fonctionner sur les types de données numériques et non numériques.

La fonction **COUNT** utilise **COUNT(\*)** qui renvoie le nombre de toutes les lignes d'une table spécifiée. **COUNT(*)** considère les doublons et Null.
```sql
COUNT(*)  
// ou 
COUNT( [ALL|DISTINCT] nom_colonne )
```
Exemple: La requête suivante comptera les enregistrements dans la table Employes
```sql
SELECT count(*) FROM Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+----------+
| count(*) |
+----------+
|        6 |
+----------+
```

### AVG
La fonction **AVG** renvoie la moyenne des valeurs d'une colonne spécifiée. Tout comme la fonction SUM, elle ne fonctionne que sur les types de données numériques.
```sql
AVG( [ALL|DISTINCT] nom_colonne ) 
```
Exemple: La requête suivante renvoie le salaire moyen de la table Employes
```sql
SELECT AVG(Salaire) FROM Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+--------------+
| AVG(Salaire) |
+--------------+
|  7250.066667 |
+--------------+
```

### MIN
La fonction **MIN** est utilisée pour déterminer la plus petite valeur de toutes les valeurs sélectionnées d'une colonne.
```sql
MIN( [ALL|DISTINCT] nom_colonne )
```
Exemple: La requête suivante renvoie le salaire minimum de la table Employes
```sql
SELECT MIN(Salaire) FROM Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+--------------+
| MIN(Salaire) |
+--------------+
|      6000.00 |
+--------------+
```

### MAX
Comme son nom l'indique, la fonction **MAX** est l'opposé de la fonction **MIN**. Elle renvoie la plus grande valeur de toutes les valeurs sélectionnées d'une colonne.
```sql
MAX( [ALL|DISTINCT] nom_colonne ) 
```
Exemple: La requête suivante renvoie le salaire maximum de la table Employes
```sql
SELECT MAX(Salaire) FROM Employes;
```
```
Cette requête produira le jeu de résultats suivant :

+--------------+
| MAX(Salaire) |
+--------------+
|      9000.00 |
+--------------+
```

## ORGANISER DES DONNÉES IDENTIQUES EN GROUPES - GROUP BY ET HAVING

### Clause GROUP BY
La clause **GROUP BY** en SQL permet d’organiser des données identiques en groupes à l’aide de certaines fonctions. C'est-à-dire si une colonne particulière a les mêmes valeurs dans différentes lignes, elle organisera ces lignes dans un groupe.

* La clause **GROUP BY** est utilisée avec l'instruction **SELECT**.
* Dans la requête, la clause **GROUP BY** est placée après la clause **WHERE**.
* Dans la requête, la clause **GROUP BY** est placée avant la clause ORDER BY si elle est utilisée.

Vous pouvez également utiliser certaines fonctions d'agrégation telles que **COUNT**, **SUM**, **MIN**, **MAX**, **AVG**, etc. sur la colonne groupée.
```sql
SELECT colonne1, colonne2, ... colonneN,   
fonction_agregation (nom_colonne)  
FROM tables  
[WHERE conditions]  
GROUP BY colonne1, colonne2, ... colonneN;
```
**colonne1**, **colonne2**, ... **colonneN** - spécifie les colonnes(ou expressions) qui ne sont pas encapsulées dans une fonction d'agrégation et doivent être incluses dans la clause **GROUP BY**.

**fonction_agregation (nom_colonne)** - Nom de la fonction d'agrégation utilisée, par exemple, **SUM()**, **AVG ()**...

**WHERE conditions** - C'est optionnel. Elle spécifie les conditions qui doivent être remplies pour que les enregistrements soient sélectionnés.

### Clause HAVING
Nous savons que la clause **WHERE** est utilisée pour imposer des conditions aux colonnes, mais que se passe-t-il si nous voulons imposer des conditions aux groupes?

C'est ici que la clause **HAVING** entre en vigueur. Nous pouvons utiliser la clause **HAVING** pour poser des conditions afin de décider quel groupe fera partie de l'ensemble des résultats finaux. De plus, nous ne pouvons pas utiliser les fonctions d'agrégation telles que **SUM()**, **COUNT()**, etc. avec la clause **WHERE**. Nous devons donc utiliser la clause **HAVING** si nous voulons utiliser l'une de ces fonctions dans les conditions.
```sql
SELECT colonne1, colonne2, ... colonneN,   
fonction_agregation (nom_colonne)  
FROM tables  
[WHERE conditions]  
GROUP BY colonne1[, colonne2, ... colonneN]
HAVING condition ;
```

## LES SOUS-REQUÊTES

Une sous-requête, également appelée requête imbriquée ou sous-sélection, est une requête **SELECT** intégrée à la clause **WHERE** ou **HAVING** d'une autre requête SQL. Les données renvoyées par la sous-requête sont utilisées par l'instruction externe de la même manière qu'une valeur littérale serait utilisée.

Les sous-requêtes constituent un moyen simple et efficace de gérer les requêtes qui dépendent des résultats d'une autre requête. Elles sont presque identiques aux instructions **SELECT** normales, mais il existe peu de restrictions. Les plus importantes sont énumérées ci-dessous:

* Une sous-requête doit toujours apparaître entre parenthèses.
* Une sous-requête doit renvoyer une seule colonne. Cela signifie que vous ne pouvez pas utiliser **SELECT \*** dans une sous-requête à moins que la table à laquelle vous faites référence ne comporte qu'une seule colonne. Vous pouvez utiliser une sous-requête qui renvoie plusieurs colonnes si le but est la comparaison de lignes.
* Vous ne pouvez utiliser que des sous-requêtes renvoyant plusieurs lignes avec des opérateurs de valeurs multiples, tels que l'opérateur **IN** ou **NOT IN**.
* Une clause **ORDER BY** ne peut pas être utilisée dans une sous-requête, bien que la requête principale puisse utiliser un ORDER BY. La clause GROUP BY peut être utilisée pour exécuter la même fonction que **ORDER BY** dans une sous-requête.
* Une sous-requête ne peut pas être une **UNION**. Une seule instruction **SELECT** est autorisée.
Les sous-requêtes sont le plus souvent utilisées avec l'instruction **SELECT**. Toutefois, vous pouvez également les utiliser dans une instruction **INSERT**, **UPDATE** ou **DELETE** ou dans une autre sous-requête.

### Sous-requêtes avec - SELECT -
Les sous-requêtes sont le plus souvent utilisées avec l'instruction **SELECT**. La syntaxe de base est la suivante :


## Exercices

### Exercice #1

Soit la base de données suivante :

* Départements :( DNO, DNOM, DIR, VILLE)
* Employés : ( ENO, ENOM, PROF, DATEEMB, SAL, COMM, #DNO)

Exprimez en SQL les requêtes suivantes:

1. Donnez la liste des employés ayant une commission.
```sql
SELECT * FROM Employes WHERE COMM NOT NULL
```
2. Donnez les noms, emplois et salaires des employés par emploi croissant, et pour chaque emploi, par salaire décroissant.
```sql
SELECT ENOM,PROF, SAL FROM Employes ORDER BY PROF ASC, SAL DESC
```
3. Donnez le salaire moyen des employés.
```sql
SELECT AVG(SAL) FROM Employes 
```
4. Donnez le salaire moyen du département Production.
```sql
SELECT AVG(E.SAL) FROM Employes E INNER JOIN Departement D
ON E.DNO=D.DNO WHERE D.DNOM="production"
```
5. Donnes les numéros de département et leur salaire maximum.
```sql
SELECT DNO, MAX(SAL) FROM Employes GROUP BY DNO 
```
6. Donnez les différentes professions et leur salaire moyen.
```sql
SELECT PROF, MAX(SAL) FROM Employes GROUP BY PROF 
```
7. Donnez le salaire moyen par profession le plus bas.
```sql
SELECT PROF, AVG(SAL) as moy FROM Employes 
GROUP BY PROF 
ORDER BY moy ASC
LIMIT 1 
```
8. Donnez le ou les emplois ayant le salaire moyen le plus bas, ainsi que ce salaire moyen.
```sql
SELECT PROF FROM Employes GROUP BY PROF
HAVING AVG(SAL)=(SELECT AVG(SAL) as moy FROM Employes
GROUP BY PROF ORDER BY moy ASC LIMIT 1) 
```

### Exercice #2

Soit la base de données intitulée "gestion_projet" permettant de gérer les projets relatifs au développement de logiciels. Elle est décrite par la représentation textuelle simplifiée suivante :

* Developpeur (NumDev, NomDev, AdrDev, EmailDev, TelDev)
* Projet (NumProj, TitreProj, DateDeb, DateFin)
* Logiciel (CodLog, NomLog, PrixLog, #NumProj)
* Realisation (#NumProj, #NumDev)

Ecrire les requêtes SQL permettant :

1. D’afficher les noms et les prix des logiciels appartenant au projet ayant comme titre « gestion de stock », triés dans l’ordre décroissant des prix.
```sql
SELECT L.NomLog, L.PrixLog FROM Logiciel L INNER JOIN Projet P
ON L.NumProj=P.NumProj WHERE P.TitreProj="gestion␣de␣stock"
ORDER BY L.PrixLog DESC
```
2. D’afficher le total des prix des logiciels du projet numéro 10. Lors de l’affichage, le titre de la colonne sera « cours total du projet ».
```sql
SELECT SUM(PrixLog) as "cout␣total␣du␣projet" FROM Logiciel WHERE NumPRoj=10 
```
3. Afficher le nombre de développeurs qui ont participé au projet intitulé « gestion de stock »
```sql
SELECT count(*) FROM Developpeur D INNER JOIN Realisation R
ON D.NumDev=R.NumDev INNER JOIN Projet P ON P.NumProj=R.NumProj 
```
4. Afficher les projets qui ont plus que 5 logiciels.
```sql
SELECT NumProj, TitreProj FROM PRojet P INNER JOIN Logiciel L ON P.NumProj=L.NumProj 
GROUP BY NumProj, TitreProj 
HAVING count(*)>5
```
5. Les numéros et noms des développeurs qui ont participés dans tout les projets.
```sql
SELECT NumDev, NomDev FROM Developpeur D INNER JOIN Realisation R ON D.NumDev=R.NumDev
GROUP BY NumDev, NomDev
HAVING count(*)=(SELECT COUNT(*) FROM Projet) 
```
6. Les numéros de projets dans lesquelles tous les développeurs y participent dans sa réalisation.
```sql
SELECT NumProj, TitreProj FROM Projet P INNER JOIN Realisation R ON P.NumProj=R.NumProj
GROUP BY NumProj, TitreProj
HAVING count(*)=(SELECT COUNT(*) FROM Developpeur) 
```


[VEUILLEZ VOIR AIDE MEMOIRE](mysql-aid-memoire-sql.pdf)
[Lien utilie](https://sql.sh/cours)