---
title: Récupération des signets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f18b87adf31f19d2a93bb3af3e14c265ae3940af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020574"
---
# <a name="retrieving-bookmarks"></a>Récupération des signets
Si l’application utilise des signets, elle doit définir l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS sur SQL_UB_VARIABLE avant de préparer ou d’exécuter l’instruction. Cela est nécessaire, car la création et la gestion de signets peuvent être une opération coûteuse. par conséquent, les signets doivent être activés uniquement lorsqu’une application peut en faire de bonnes utilisation.  
  
 Les signets sont retournés en tant que colonne 0 du jeu de résultats. Une application peut les récupérer de trois façons :  
  
-   Liez la colonne 0 du jeu de résultats. **SQLFetch** ou **SQLFetchScroll** retourne les signets pour chaque ligne de l’ensemble de lignes, ainsi que les données des autres colonnes liées.  
  
-   Appelez **SQLSetPos** pour positionner sur une ligne de l’ensemble de lignes, puis appelez **SQLGetData** pour la colonne 0. Si un pilote prend en charge les signets, il doit toujours prendre en charge la possibilité d’appeler **SQLGetData** pour la colonne 0, même s’il ne permet pas aux applications d’appeler **SQLGetData** pour d’autres colonnes avant la dernière colonne liée.  
  
-   Appelez **SQLBulkOperations** avec l’argument *Operation* défini sur SQL_ADD et la colonne 0 liée. Le curseur insère la ligne et retourne le signet de la ligne dans la mémoire tampon liée.
