---
title: sp_marksubscriptionvalidation (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb8c38d24fbf6c96c61a7b2e83874d15218797c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68092672"
---
# <a name="sp_marksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Marque la transaction actuellement ouverte comme transaction de validation de niveau abonnement pour l'abonné spécifié. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @subscriber = ] 'subscriber'`Nom de l’abonné. *Subscriber* est de type sysname, sans valeur par défaut.  
  
`[ @destination_db = ] 'destination_db'`Nom de la base de données de destination. *destination_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher = ] 'publisher'`Spécifie un serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de publication non-. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  l' *éditeur* ne doit pas être utilisé pour une publication qui appartient [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à un serveur de publication.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_marksubscriptionvalidation** est utilisé dans la réplication transactionnelle.  
  
 **sp_marksubscriptionvalidation** ne prend pas en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les abonnés non-.  
  
 Pour les serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de publication non-, vous ne pouvez pas exécuter des **sp_marksubscriptionvalidation** à partir d’une transaction explicite. Cela est dû au fait que les transactions explicites ne sont pas prises en charge sur la connexion du serveur lié utilisée pour accéder au serveur de publication.  
  
 **sp_marksubscriptionvalidation** doit être utilisé avec [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), en spécifiant une valeur **de 1** pour *subscription_level*et peut être utilisé avec d’autres appels à **sp_marksubscriptionvalidation** pour marquer la transaction ouverte actuelle pour d’autres abonnés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Exemple  
 La requête suivante peut être appliquée à la base de données de publication pour publier des commandes de validation au niveau des abonnements. Ces commandes sont récupérées par les Agents de distribution des Abonnés spécifiés. Notez que la première transaction valide l’article «**art1**», tandis que la deuxième transaction valide «**art2**». Notez également que les appels à **sp_marksubscriptionvalidation** et [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) ont été encapsulés dans une transaction. Nous vous recommandons d’effectuer un seul appel à [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) par transaction. En effet, [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) contient un verrou de table partagé sur la table source pour la durée de la transaction. Les transactions courtes sont à privilégier pour maximiser l'accès simultané.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Valider des données répliquées](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
