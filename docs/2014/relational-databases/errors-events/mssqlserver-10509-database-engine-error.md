---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 112d0297243ebdd778f21db69037b5a3cbd67d10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62916249"
---
# <a name="mssqlserver_10509"></a>MSSQLSERVER_10509
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10509|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_STMT|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car l’instruction spécifiée par `@stmt` ou `@statement_start_offset` contient une erreur de syntaxe ou n’est pas éligible pour le repère de plan. Fournissez une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] valide ou une position de départ de l'instruction valide dans le lot. Pour obtenir une position de départ valide, interrogez la colonne statement_start_offset de la fonction de gestion dynamique sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Explication  
 L'instruction spécifiée par `@stmt` ou `@statement_start_offset` contient une erreur de syntaxe ou n'est pas éligible pour une utilisation dans un repère de plan.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Fournissez une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] valide ou une position de départ de l'instruction valide dans le lot. Pour obtenir une position de départ valide, interrogez la colonne statement_start_offset de la fonction de gestion dynamique sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sys. dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
