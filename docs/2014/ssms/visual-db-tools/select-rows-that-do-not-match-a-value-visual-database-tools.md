---
title: Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f84f4fcc8a6dde7dcf9f556a72c2599356e231f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067535"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Sélectionner les lignes ne correspondant pas à une valeur (Visual Database Tools)
  Pour rechercher des lignes ne correspondant pas à une valeur, utilisez l'opérateur NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Pour rechercher des lignes ne correspondant pas à une valeur  
  
1.  Si vous ne l’avez pas déjà fait, ajoutez les colonnes ou les expressions que vous souhaitez utiliser dans votre condition de recherche au [volet critères](visual-database-tools.md).  
  
2.  Localisez la ligne comportant l’expression ou la colonne de données à rechercher, puis entrez l’opérateur NOT suivi d’une valeur de recherche dans la colonne de la grille **Filtre** .  
  
 Si vous souhaitez, par exemple, rechercher toutes les lignes figurant dans une table `products` dans laquelle les valeurs de la colonne des codes produits commencent par un autre caractère que « A », vous pouvez alors entrer la condition de recherche suivante :  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Règles pour l’entrée de valeurs de recherche &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
