---
title: sp_replshowcmds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96a32ea04fc53f1a0bf3a842a5e68cde5586ac29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770882"
---
# <a name="sp_replshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Renvoie les commandes pour les transactions signalées pour la réplication dans un format lisible. **sp_replshowcmds** ne peut être exécutée que lorsque les connexions clientes (y compris la connexion active) ne lisent pas les transactions répliquées à partir du journal. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Arguments  
`[ @maxtrans = ] maxtrans`Nombre de transactions à propos desquelles retourner des informations. *maxtrans* est de **type int**, avec **1**comme valeur par défaut, qui spécifie le nombre maximal de transactions en attente de réplication pour lesquelles **sp_replshowcmds** retourne des informations.  
  
## <a name="result-sets"></a>Jeux de résultats  
 **sp_replshowcmds** est une procédure de diagnostic qui retourne des informations sur la base de données de publication à partir de laquelle elle est exécutée.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binaire (10)**|Numéro de séquence de la commande.|  
|**originator_id**|**int**|ID de l’expéditeur de la commande, toujours **0**.|  
|**publisher_database_id**|**int**|ID de la base de données du serveur de publication, toujours **0**.|  
|**article_id**|**int**|ID de l’article.|  
|**entrer**|**int**|Type de commande.|  
|**commande**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]commande.|  
  
## <a name="remarks"></a>Notes  
 **sp_replshowcmds** est utilisé dans la réplication transactionnelle.  
  
 À l’aide de **sp_replshowcmds**, vous pouvez afficher les transactions qui ne sont pas actuellement distribuées (les transactions restantes dans le journal des transactions qui n’ont pas été envoyées au serveur de distribution).  
  
 Les clients qui exécutent **sp_replshowcmds** et **sp_replcmds** au sein de la même base de données reçoivent l’erreur 18752.  
  
 Pour éviter cette erreur, le premier client doit se déconnecter ou le rôle du client en tant que lecteur de journal doit être libéré en exécutant **sp_replflush**. Une fois que tous les clients se sont déconnectés du lecteur du journal, **sp_replshowcmds** peut s’exécuter correctement.  
  
> [!NOTE]  
>  **sp_replshowcmds** doit être exécutée uniquement pour résoudre les problèmes de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_replshowcmds**.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
