---
title: MSdistribution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1053181486dba8c8119f9160d9c08cb8d2bbe56b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907393"
---
# <a name="msdistribution_history-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSdistribution_history** contient des lignes d’historique pour les agents de distribution associés au serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID de l'Agent de distribution.|  
|**runstatus**|**int**|État d’exécution :<br /><br /> **1** = début.<br /><br /> **2** = opération réussie.<br /><br /> **3** = en cours.<br /><br /> **4** = inactif.<br /><br /> **5** = nouvelle tentative.<br /><br /> **6** = échec.|  
|**start_time**|**DATETIME**|Heure de démarrage de l'exécution de la tâche|  
|**time**|**DATETIME**|Heure de consignation du message dans le journal|  
|**Macauley**|**int**|Durée, en secondes, de la session de message.|  
|**inclus**|**nvarchar(4000)**|Texte du message.|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de la dernière transaction réalisée.|  
|**current_delivery_rate**|**float**|Nombre moyen de commandes transmises par seconde depuis la dernière entrée de commande dans l'historique.|  
|**current_delivery_latency**|**int**|Temps de latence entre l'entrée de la commande dans la base de données de distribution et son application à l'abonné depuis la dernière entrée dans l'historique. En millisecondes.|  
|**delivered_transactions**|**int**|Nombre total des transactions transmises dans la session.|  
|**delivered_commands**|**int**|Nombre total des commandes transmises dans la session.|  
|**average_commands**|**int**|Nombre moyen des commandes transmises dans la session.|  
|**delivery_rate**|**float**|Moyenne des commandes transmises par seconde.|  
|**delivery_latency**|**int**|Temps de latence entre l'entrée de la commande dans la base de données de distribution et son application à l'abonné. En millisecondes.|  
|**total_delivered_commands**|**bigint**|Nombre total de commandes transmises depuis la création de l'abonnement.|  
|**error_id**|**int**|ID de l’erreur dans la table système **Msrepl_error** .|  
|**updateable_row**|**bit**|Défini sur **1** si la ligne de l’historique peut être remplacée.|  
|**confirmé**|**confirmé**|Colonne timestamp de cette table|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
