---
title: Traitement des instructions SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9452ade90f6967dff6d72d5692efcf91b93154d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057246"
---
# <a name="processing-sql-statements"></a>Traitement des instructions SQL
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 La bibliothèque de curseurs ODBC transmet toutes les instructions SQL directement au pilote, à l’exception de ce qui suit :  
  
-   Instructions Update et DELETE positionnées  
  
-   **Select for Update** , instructions  
  
-   Instructions SQL par lot  
  
 Pour exécuter des instructions Update et DELETE positionnées et pour positionner le curseur sur une ligne pour appeler **SQLGetData** pour cette ligne, la bibliothèque de curseurs construit une instruction recherchée qui identifie la ligne.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Traitement des instructions de mise à jour et de suppression positionnées](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Traitement des instructions SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Traitement des lots d’instructions SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Construction d’instructions de recherche](../../../odbc/reference/appendixes/constructing-searched-statements.md)
