---
title: sp_replrestart (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replrestart_TSQL
- sp_replrestart
helpviewer_keywords:
- sp_replrestart
ms.assetid: 111b3dbf-92f8-4670-b156-1468c63e4fc1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9108ab25d1a23e06ccd93daad5f755a3a65aa44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770892"
---
# <a name="sp_replrestart-transact-sql"></a>sp_replrestart (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Utilisée par la réplication transactionnelle au cours de la sauvegarde et de la restauration pour que les données répliquées sur le serveur de distribution soient synchronisées avec celles du serveur de publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  **sp_replrestart** est une procédure stockée de réplication interne qui ne doit être utilisée que lors de la restauration d’une base de données publiée dans une topologie de réplication transactionnelle, comme indiqué dans la rubrique [stratégies de sauvegarde et de restauration de la réplication transactionnelle et d’instantané](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replrestart  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replrestart** est utilisé lorsque la valeur du numéro séquentiel dans le journal (LSN) la plus élevée sur le serveur de distribution ne correspond pas à la valeur LSN la plus élevée sur le serveur de publication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_replrestart**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
