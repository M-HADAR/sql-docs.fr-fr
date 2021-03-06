---
title: 'Création d’ensembles de lignes avec ICommand :: Execute | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e81f322bde3c4439b26acebb0ad24c925d583a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183680"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Création d'ensembles de lignes avec ICommand::Execute
  Pour les ensembles de lignes créés avec la méthode **ICommand::Execute**, les propriétés souhaitées dans l’ensemble de lignes résultant peuvent limiter le texte de la commande. Cela est particulièrement important pour les consommateurs qui prennent en charge un texte de commande dynamique.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut pas utiliser de curseurs pour prendre en charge les résultats de plusieurs ensembles de lignes générés par de nombreuses commandes. Lorsqu'un consommateur demande un ensemble de lignes qui requiert la prise en charge de curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une erreur se produit si le texte de commande génère plusieurs ensembles de lignes comme résultat. Pour plus d’informations, consultez [commandes générant des résultats à plusieurs ensembles de lignes](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Les ensembles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de lignes de fournisseur OLE DB Native Client défilant sont pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les curseurs. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impose des limitations aux curseurs qui sont sensibles aux modifications effectuées par d'autres utilisateurs de la base de données. En particulier, dans certains curseurs, les lignes ne peuvent pas être triées ; en outre, toute tentative de création d'un ensemble de lignes à l'aide d'une commande qui contient une clause SQL ORDER BY peut échouer. Pour plus d’informations, consultez [Ensembles de lignes et curseurs SQL Server](rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
