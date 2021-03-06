---
title: Récupération des résultats (de base) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7abe4dd2f0bfb0b5302022d8e50cddc7df84f192
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020469"
---
# <a name="retrieving-results-basic"></a>Récupération des résultats (de base)
Un *jeu de résultats* est un ensemble de lignes sur la source de données qui correspond à certains critères. Il s’agit d’une table conceptuelle qui résulte d’une requête et qui est disponible pour une application sous forme de tableau. Les instructions **Select** , les fonctions de catalogue et certaines procédures créent des jeux de résultats. Dans l’exemple suivant, la première instruction SQL crée un jeu de résultats contenant toutes les lignes et toutes les colonnes de la table Orders, tandis que la seconde instruction SQL crée un jeu de résultats contenant les colonnes OrderID, SalesPerson et Status pour les lignes de la table Orders. dans lequel l’État est ouvert :  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Un jeu de résultats peut être vide, ce qui diffère d’un jeu de résultats. Par exemple, l’instruction SQL suivante crée un jeu de résultats vide :  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Un jeu de résultats vide n’est pas différent de tout autre jeu de résultats, sauf qu’il n’a pas de ligne. Par exemple, l’application peut récupérer des métadonnées pour le jeu de résultats, peut essayer d’extraire des lignes et doit fermer le curseur sur le jeu de résultats.  
  
 Le processus d’extraction des lignes de la source de données et de leur renvoi à l’application est appelé *extraction*. Cette section explique les éléments de base de ce processus. Pour plus d’informations sur des rubriques plus avancées, telles que les curseurs de bloc et de défilement, consultez [curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md) et [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md). Pour plus d’informations sur la mise à jour, la suppression et l’insertion de lignes, consultez [vue d’ensemble de la mise à jour des données](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Un jeu de résultats a-t-il été créé ?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Métadonnées des jeux de résultats](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Liaison de colonnes](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Extraction de données](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Fermeture du curseur](../../../odbc/reference/develop-app/closing-the-cursor.md)
