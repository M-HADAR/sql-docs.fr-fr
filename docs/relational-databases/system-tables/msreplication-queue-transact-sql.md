---
title: MSreplication_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 914cf3ad65c881383a6d625c07d4fb5ed028b36a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080016"
---
# <a name="msreplication_queue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSreplication_queue** est utilisée par le processus de réplication pour stocker les commandes mises en file d’attente émises par tous les abonnements de mise à jour en attente qui utilisent des mises en file d’attente SQL. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication**|**sysname**|Nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données de publication.|  
|**édition**|**sysname**|Nom de la publication.|  
|**tranid**|**sysname**|Identificateur de transaction sous lequel la commande en file d'attente a été exécutée.|  
|**métadonnée**|**varbinary (8000)**|Flux d'octets empaqueté où étaient stockées les informations sur la commande mise en file d'attente.|  
|**datalen**|**int**|Longueur des données en octets.|  
|**CommandType**|**int**|Type de commande mise en file d'attente :<br /><br /> 1 = Commande utilisateur dans une transaction<br /><br /> 2 = Commande de synchronisation d'abonnement|  
|**insertdate**|**DATETIME**|Date d'insertion.|  
|**orderkey**|**bigint**|Colonne d'identité à croissance monolithique.|  
|**cmdstate**|**bit**|État de la commande :<br /><br /> 0 = Terminée<br /><br /> 1 = Partiellement exécutée|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
