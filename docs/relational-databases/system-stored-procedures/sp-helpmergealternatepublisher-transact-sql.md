---
title: sp_helpmergealternatepublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6875e745cc05735b9f116c2d4afa5e5218defb99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122390"
---
# <a name="sp_helpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une liste de tous les serveurs activés en tant qu'autres serveurs de publication pour les publications de fusion. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication de remplacement. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Nom de l'autre serveur de publication.|  
|**alternate_publisher_db**|**sysname**|Nom de la base de données de publication.|  
|**alternate_publication**|**sysname**|Nom de la publication.|  
|**alternate_distributor**|**sysname**|Nom du serveur de distribution.|  
|**friendly_name**|**nvarchar(255)**|Description de l'autre serveur de publication.|  
|**désactivé**|**bit**|Indique si le serveur est un autre serveur de publication. **1** indique que le serveur de publication est activé en tant que serveur de publication de remplacement. **0** indique qu’il n’est pas activé.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergealternatepublisher** est utilisé dans la réplication de fusion.  
  
 Pendant chaque session de fusion, le système interroge le serveur de publication et l'Abonné pour obtenir la liste des autres serveurs de publication de chacun d'eux. Le processus de fusion ajoute ou supprime des entrées dans la liste des serveurs de publication de remplacement ; la liste sur le serveur de publication et celle sur l'Abonné sont alors correspondantes à l'issue de l'opération.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la liste d’accès à la publication pour la publication peuvent exécuter **sp_helpmergealternatepublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
