---
title: sp_ivindexhasnullcols (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27ebcdf656effb97529bea42972be96f9a993cfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139914"
---
# <a name="sp_ivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Valide le fait que l'index cluster de la vue indexée est unique et qu'il ne contient aucune colonne acceptant des valeurs NULL lorsque la vue indexée va servir à la création d'une publication transactionnelle. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
`[ @viewname = ] 'view_name'`Nom de la vue à vérifier. *view_name* est de **type sysname**, sans valeur par défaut.  
  
`[ @fhasnullcols = ] field_has_null_columns OUTPUT`Indicateur qui spécifie si l’index de la vue a des colonnes qui autorisent la valeur NULL. *view_name* est de **type sysname**, sans valeur par défaut. Retourne la valeur **1** si l’index de la vue a des colonnes qui autorisent la valeur null. Retourne la valeur **0** si la vue ne contient pas de colonnes qui acceptent les valeurs NULL.  
  
> [!NOTE]  
>  Si la procédure stockée elle-même retourne un code de retour de **1**, ce qui signifie que l’exécution de la procédure stockée a échoué, cette valeur est **0** et doit être ignorée.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_ivindexhasnullcols** est utilisé par la réplication transactionnelle.  
  
 Par défaut, les articles de vue indexée d'une publication sont créés en tant que tables sur les Abonnés. Toutefois, lorsque la colonne indexée autorise les valeurs NULL, la vue indexée est créée en tant que vue indexée sur l'Abonné, au lieu de l'être en tant que table. L'exécution de cette procédure stockée indique à l'utilisateur si la vue indexée active est concernée par ce problème.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
