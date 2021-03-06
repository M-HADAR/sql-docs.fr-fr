---
title: Mise à jour, suppression ou extraction par signet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce43cb1d5563128e840aa3c0df26190524774a38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091633"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Mise à jour, suppression ou extraction par signet
Les signets peuvent être utilisés pour identifier les données à mettre à jour dans le jeu de résultats, supprimées du jeu de résultats ou extraites du jeu de résultats vers les tampons de l’ensemble de lignes. Ces opérations sont effectuées par un appel à **SQLBulkOperations** avec un argument *option* de SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK. Les signets utilisés dans ces opérations sont stockés dans la colonne 0 des mémoires tampons de l’ensemble de lignes. Lors de la mise à jour par signet, les données auxquelles les colonnes du jeu de résultats sont mises à jour sont récupérées à partir des mémoires tampons de l’ensemble de lignes. Pour plus d’informations, consultez [mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
