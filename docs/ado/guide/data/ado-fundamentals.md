---
title: Notions de base d’ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 75f5030f8faa5aa5d8e8a0f6bcb6d72b186c8448
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926060"
---
# <a name="ado-fundamentals"></a>Concepts de base d’ADO
ADO offre aux développeurs un modèle d’objet logique puissant pour accéder, modifier et mettre à jour les données à partir d’un large éventail de sources de données via des interfaces système OLE DB. L’utilisation la plus courante d’ADO est d’interroger une table ou des tables dans une base de données relationnelle, de récupérer et d’afficher les résultats dans une application, et peut-être de permettre aux utilisateurs de créer et d’enregistrer les modifications apportées aux données. Les autres tâches sont les suivantes :  
  
-   Interrogation d’une base de données à l’aide de SQL et affichage des résultats.  
  
-   Accès aux informations dans un magasin de fichiers sur Internet.  
  
-   Manipulation des messages et des dossiers dans un système de messagerie électronique.  
  
-   Enregistrement de données d’une base de données dans un fichier XML.  
  
-   Exécution de commandes décrites avec XML et récupération d’un flux XML.  
  
-   Enregistrement de données dans un flux binaire ou XML.  
  
-   Permettre à un utilisateur d’examiner et de modifier les données dans les tables de base de données.  
  
-   Création et réutilisation des commandes de base de données paramétrables.  
  
-   Exécution de procédures stockées.  
  
-   Création dynamique d’une structure flexible, appelée **Recordset**, pour la conservation, la navigation et la manipulation des données.  
  
-   Exécution d’opérations de base de données transactionnelle.  
  
-   Filtrage et tri des copies locales des informations de la base de données en fonction des critères d’exécution.  
  
-   Création et manipulation de résultats hiérarchiques à partir des bases de données.  
  
-   Liaison de champs de base de données à des composants qui prennent en charge les données.  
  
-   Création **d’un jeu d’enregistrements**distants et déconnectés.  
  
 ADO expose un large éventail d’options et de paramètres pour offrir une telle flexibilité. Par conséquent, il est important d’adopter une approche méthodique pour apprendre à utiliser ADO dans une application, en divisant chacun de vos objectifs en éléments gérables.  
  
 Quatre opérations principales sont impliquées dans la plupart des applications qui utilisent ADO : obtention de données, examen des données, modification des données et mise à jour des données. Ces opérations sont étudiées plus en détail plus loin dans cette section.  
  
 Toutefois, avant d’aborder ces détails, nous présenterons une vue d’ensemble du modèle objet ADO et une simple application ADO, écrite en Microsoft® Visual Basic® et effectuant chacune des quatre opérations ADO principales :  
  
-   [Objets et collections ADO](../../../ado/guide/data/ado-objects-and-collections.md)  
  
-   [HelloData : une application ADO simple](../../../ado/guide/data/hellodata-a-simple-ado-application.md)  
  
-   [Fournisseurs de OLE DB](../../../ado/guide/data/ole-db-providers-ado.md)  
  
-   [Erreurs](../../../ado/guide/data/errors-ado.md)
