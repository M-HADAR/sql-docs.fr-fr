---
title: sp_helptracertokens (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokens
- sp_helptracertokens_TSQL
helpviewer_keywords:
- sp_helptracertokens
ms.assetid: 61f27234-531d-4b37-8fa3-fe4c32e6f521
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b4df50d1cf43ba1b0f4eb8b8f313634b4d11d18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771537"
---
# <a name="sp_helptracertokens-transact-sql"></a>sp_helptracertokens (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque jeton de suivi inséré dans une publication pour déterminer la latence. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données de distribution du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helptracertokens [ @publication = ] 'publication'   
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication dans laquelle les jetons de suivi ont été insérés. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]
>  Ce paramètre ne doit être spécifié que pour les [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveurs de publication non-.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut. Ce paramètre est ignoré si la procédure stockée est exécutée sur le serveur de publication.  
  
## <a name="result-set"></a>Jeu de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Identifie un enregistrement de jeton de suivi.|  
|**publisher_commit**|**DATETIME**|Date et heure auxquelles l'enregistrement de jeton a été validé sur le serveur de publication dans la base de données de publication.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helptracertokens** est utilisé dans la réplication transactionnelle.  
  
 **sp_helptracertokens** est utilisé pour obtenir des ID de jeton de suivi lors de l’exécution de [Sp_helptracertokenhistory &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokens-tran_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** dans la base de données de publication, ou **db_owner** des rôles de base de données fixe ou **replmonitor** dans la base de données de distribution peuvent exécuter **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
