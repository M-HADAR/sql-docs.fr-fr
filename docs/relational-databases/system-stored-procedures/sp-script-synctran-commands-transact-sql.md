---
title: sp_script_synctran_commands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7caca72f684dfb6428361a4550860b3bea3f273
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68126411"
---
# <a name="sp_script_synctran_commands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Génère un script qui contient les appels de **sp_addsynctrigger** à appliquer aux abonnés pour les abonnements pouvant être mis à jour. Il existe un appel de **sp_addsynctrigger** pour chaque article de la publication. Le script généré contient également les appels de **sp_addqueued_artinfo** qui créent la table **MSsubsciption_articles** nécessaire pour traiter les publications mises en file d’attente. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à écrire. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article pour lequel générer un script. *article* est de **type sysname**, avec **All**comme valeur par défaut, qui spécifie que tous les articles font l’objets d’un script.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="results-set"></a>Ensemble de résultats  
 **sp_script_synctran_commands** retourne un jeu de résultats qui se compose d’une seule colonne **nvarchar (4000)** . Le jeu de résultats forme les scripts complets nécessaires à la création des appels **sp_addsynctrigger** et **sp_addqueued_artinfo** à appliquer aux abonnés.  
  
## <a name="remarks"></a>Notes  
 **sp_script_synctran_commands** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 **sp_addqueued_artinfo** est utilisé pour les abonnements pouvant être mis à jour en file d’attente.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
