---
title: sp_add_agent_profile (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 24a900409ae5979c13bdbff0d67d9d2670059208
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770853"
---
# <a name="sp_add_agent_profile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Crée un nouveau profil pour un Agent de réplication. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id`ID associé au profil nouvellement inséré. *profile_id* est de **type int** et est un paramètre de sortie facultatif. Si vous l'indiquez, la valeur définie est égale au numéro d'identification du nouveau profil.  
  
`[ @profile_name = ] 'profile_name'`Nom du profil. *profile_name* est de **type sysname**, sans valeur par défaut.  
  
`[ @agent_type = ] 'agent_type'`Type d’agent de réplication. *agent_type* est de **type int**, sans valeur par défaut, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Agent d'instantané|  
|**2**|l'Agent de lecture du journal ;|  
|**1,3**|Agent de distribution|  
|**4**|Agent de fusion|  
|**0,9**|Agent de lecture de la file d'attente|  
  
`[ @profile_type = ] profile_type`Type de profil. *profile_type* est de **type int**, avec **1**comme valeur par défaut.  
  
 **0** indique un profil système. **1** indique un profil personnalisé. Seuls les profils personnalisés peuvent être créés à l’aide de cette procédure stockée. par conséquent, la seule valeur valide est **1**. Crée [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uniquement des profils système.  
  
`[ @description = ] 'description'`Description du profil. *Description* est de type **nvarchar (3000)**, sans valeur par défaut.  
  
`[ @default = ] default`Indique si le profil est la valeur par défaut pour *agent_type * *.* la *valeur par défaut* est **bit**, avec **0**comme valeur par défaut. **1** indique que le profil ajouté deviendra le nouveau profil par défaut de l’agent spécifié par *agent_type*.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_add_agent_profile** est utilisé dans la réplication d’instantané, la réplication transactionnelle et la réplication de fusion.  
  
 Les profils d'agent personnalisés sont ajoutés avec les valeurs par défaut. Utilisez [sp_change_agent_parameter &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md) pour modifier ces valeurs par défaut ou [sp_add_agent_parameter &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md) pour ajouter des paramètres supplémentaires.  
  
 Lorsque **sp_add_agent_profile** est exécutée, une ligne est ajoutée pour le nouveau profil personnalisé dans le [MSagent_profiles &#40;table transact-SQL&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) et les paramètres par défaut associés à ce profil sont ajoutés à la table MSAGENT_PARAMETERS &#40;[Transact-SQL&#41;](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) .  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_add_agent_profile**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des profils d’Agent de réplication](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Profils de l’agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_change_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_change_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
