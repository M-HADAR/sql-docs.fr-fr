---
title: sp_helparticlecolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticlecolumns
- sp_helparticlecolumns_TSQL
helpviewer_keywords:
- sp_helparticlecolumns
ms.assetid: 9ea55df3-2e99-4683-88ad-bde718288bc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: e87e542395c00797ce50b220ad8a6c981f43605a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771090"
---
# <a name="sp_helparticlecolumns-transact-sql"></a>sp_helparticlecolumns (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne toutes les colonnes dans la table sous-jacente. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Dans le cas des serveurs de publication Oracle, cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helparticlecolumns [ @publication = ] 'publication'   
        , [ @article = ] 'article'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication qui contient l’article. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article dont les colonnes sont retournées. *article* est de **type sysname**et n’a pas de valeur par défaut.  
  
`[ @publisher = ] 'publisher'`Spécifie un serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de publication non-. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  l' *éditeur* ne doit pas être spécifié lorsque l’article demandé est publié [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par un serveur de publication.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (colonnes qui ne sont pas publiées) ou **1** (colonnes publiées)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**ID de colonne**|**int**|Identificateur de la colonne.|  
|**chronique**|**sysname**|Nom de la colonne.|  
|**publié**|**bit**|Indique si la colonne est publiée :<br /><br /> **0** = non<br /><br /> **1** = Oui|  
|**type de serveur de publication**|**sysname**|Type de données de la colonne sur le serveur de publication.|  
|**type d’abonné**|**sysname**|Type de données de la colonne sur l'Abonné.|  
  
## <a name="remarks"></a>Notes  
 **sp_helparticlecolumns** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 **sp_helparticlecolumns** est utile pour la vérification d’une partition verticale.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** ou la liste d’accès à la publication pour la publication actuelle peuvent exécuter **sp_helparticlecolumns**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir et modifier un filtre de colonne](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
