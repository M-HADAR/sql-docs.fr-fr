---
title: Exemple de base de données SQL Graph | Microsoft Docs
description: Il s’agit d’un exemple rapide qui vous aidera à vous familiariser avec la nouvelle syntaxe introduite dans la base de données SQL Graph.
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, tsql reference
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1737ae8427df8d6d9bd6dbb9dea359da09f0c657
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68035874"
---
# <a name="create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sql"></a>Créer une base de données de graphiques et exécuter des requêtes de critères spéciaux à l’aide de T-SQL

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Cet exemple fournit un [!INCLUDE[tsql-md](../../includes/tsql-md.md)] script pour créer une base de données de graphiques avec des nœuds et des bords, puis utiliser la nouvelle clause match pour faire correspondre des modèles et parcourir le graphique. Cet exemple de script fonctionnera à la fois sur Azure SQL Database et[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]  

## <a name="sample-schema"></a>Exemple de schéma

Cet exemple crée un schéma de graphique, comme illustré à la figure 1, pour un réseau social hypothétique qui a des nœuds personnes, restaurant et ville. Ces nœuds sont connectés l’un à l’autre à l’aide de Friends, j’aime, vit et trouve les bords.

![person-villes-restaurants-tables](../../relational-databases/graphs/media/person-cities-restaurants-tables.png "Exemple de base de données SQL Graph")  
Figure 1 : exemple de schéma avec restaurant, City, les nœuds Person et habite, situer, aime bords.

## <a name="sample-script"></a>Exemple de script

```
-- Create a graph demo database
CREATE DATABASE graphdemo;
go

USE  graphdemo;
go

-- Create NODE tables
CREATE TABLE Person (
  ID INTEGER PRIMARY KEY,
  name VARCHAR(100)
) AS NODE;

CREATE TABLE Restaurant (
  ID INTEGER NOT NULL,
  name VARCHAR(100),
  city VARCHAR(100)
) AS NODE;

CREATE TABLE City (
  ID INTEGER PRIMARY KEY,
  name VARCHAR(100),
  stateName VARCHAR(100)
) AS NODE;

-- Create EDGE tables. 
CREATE TABLE likes (rating INTEGER) AS EDGE;
CREATE TABLE friendOf AS EDGE;
CREATE TABLE livesIn AS EDGE;
CREATE TABLE locatedIn AS EDGE;

-- Insert data into node tables. Inserting into a node table is same as inserting into a regular table
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table,
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE ID = 1), 
       (SELECT $node_id FROM Restaurant WHERE ID = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE ID = 2), 
      (SELECT $node_id FROM Restaurant WHERE ID = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE ID = 3), 
      (SELECT $node_id FROM Restaurant WHERE ID = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE ID = 4), 
      (SELECT $node_id FROM Restaurant WHERE ID = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE ID = 5), 
      (SELECT $node_id FROM Restaurant WHERE ID = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE ID = 1),
      (SELECT $node_id FROM City WHERE ID = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE ID = 2),
      (SELECT $node_id FROM City WHERE ID = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE ID = 3),
      (SELECT $node_id FROM City WHERE ID = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE ID = 4),
      (SELECT $node_id FROM City WHERE ID = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE ID = 5),
      (SELECT $node_id FROM City WHERE ID = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE ID = 1),
      (SELECT $node_id FROM City WHERE ID =1));
INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE ID = 2),
      (SELECT $node_id FROM City WHERE ID =2));
INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE ID = 3),
      (SELECT $node_id FROM City WHERE ID =3));

-- Insert data into the friendOf edge.
INSERT INTO friendOf VALUES ((SELECT $NODE_ID FROM Person WHERE ID = 1), (SELECT $NODE_ID FROM Person WHERE ID = 2));
INSERT INTO friendOf VALUES ((SELECT $NODE_ID FROM Person WHERE ID = 2), (SELECT $NODE_ID FROM Person WHERE ID = 3));
INSERT INTO friendOf VALUES ((SELECT $NODE_ID FROM Person WHERE ID = 3), (SELECT $NODE_ID FROM Person WHERE ID = 1));
INSERT INTO friendOf VALUES ((SELECT $NODE_ID FROM Person WHERE ID = 4), (SELECT $NODE_ID FROM Person WHERE ID = 2));
INSERT INTO friendOf VALUES ((SELECT $NODE_ID FROM Person WHERE ID = 5), (SELECT $NODE_ID FROM Person WHERE ID = 4));


-- Find Restaurants that John likes
SELECT Restaurant.name
FROM Person, likes, Restaurant
WHERE MATCH (Person-(likes)->Restaurant)
AND Person.name = 'John';

-- Find Restaurants that John's friends like
SELECT Restaurant.name 
FROM Person person1, Person person2, likes, friendOf, Restaurant
WHERE MATCH(person1-(friendOf)->person2-(likes)->Restaurant)
AND person1.name='John';

-- Find people who like a restaurant in the same city they live in
SELECT Person.name
FROM Person, likes, Restaurant, livesIn, City, locatedIn
WHERE MATCH (Person-(likes)->Restaurant-(locatedIn)->City AND Person-(livesIn)->City);
```

## <a name="clean-up"></a>Nettoyer  
Nettoyez le schéma et la base de données créés pour l’exemple.

```
USE graphdemo;
go

DROP TABLE IF EXISTS likes;
DROP TABLE IF EXISTS Person;
DROP TABLE IF EXISTS Restaurant;
DROP TABLE IF EXISTS City;
DROP TABLE IF EXISTS friendOf;
DROP TABLE IF EXISTS livesIn;
DROP TABLE IF EXISTS locatedIn;

USE master;
go
DROP DATABASE graphdemo;
go
```

## <a name="script-explanation"></a>Explication du script  
Ce script utilise la nouvelle syntaxe T-SQL pour créer des tables de nœuds et d’arêtes. Montre comment insérer des données dans des tables de nœuds `INSERT` et de périphérie à l’aide d' `MATCH` une instruction, et montre également comment utiliser la clause pour les critères spéciaux et la navigation.

|Commande    |Notes
|---  |---  |
|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)  |Créer un nœud de graphique ou une table d’arêtes  |
|[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)  |Insérer dans une table de nœuds ou d’arêtes  |
|[Faire correspondre &#40;&#41;Transact-SQL](../../t-sql/queries/match-sql-graph.md)  |Utilisez MATCH pour faire correspondre un modèle ou parcourir le graphique  |
