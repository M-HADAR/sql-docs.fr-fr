---
title: sp_srvrolepermission (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6613c4e94ce8c802e45fe003ac73e51b3f38072b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032812"
---
# <a name="sp_srvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les autorisations d'un rôle serveur fixe.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @srvrolename = ] 'role'`Nom du rôle serveur fixe pour lequel les autorisations sont retournées. *role* est de **type sysname**, avec NULL comme valeur par défaut. Si aucun rôle n'est spécifié, les autorisations de tous les rôles serveur fixes sont retournées. le *rôle* peut avoir l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**administrateur système**|Administrateurs système|  
|**securityadmin**|Administrateurs de la sécurité|  
|**ServerAdmin**|Administrateurs de serveur|  
|**setupadmin**|Administrateurs de l'installation et de la configuration|  
|**processadmin**|Administrateurs de processus|  
|**diskadmin**|Administrateurs de disques|  
|**rôles**|Créateurs de base de données|  
|**bulkadmin**|Exécute les instructions BULK INSERT.|  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|Nom d'un rôle serveur fixe|  
|**Permission**|**sysname**|Autorisation associée à **ServerRole**|  
  
## <a name="remarks"></a>Notes  
 Les autorisations répertoriées comprennent les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qu'il est possible d'exécuter, ainsi que d'autres actions spéciales que les membres du rôle serveur fixe sont en mesure d'accomplir. Pour afficher la liste des rôles serveur fixes, exécutez **sp_helpsrvrole**.  
  
 Le rôle serveur fixe **sysadmin** dispose des autorisations de tous les autres rôles serveur fixes.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 La requête suivante retourne les autorisations associées au rôle serveur fixe `sysadmin`.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
