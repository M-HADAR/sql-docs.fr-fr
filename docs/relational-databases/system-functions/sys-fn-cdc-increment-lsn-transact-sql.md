---
title: Sys.fn_cdc_increment_lsn (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- fn_cdc_increment_lsn_TSQL
- sys.fn_cdc_increment_lsn_TSQL
- sys.fn_cdc_increment_lsn
- fn_cdc_increment_lsn
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_increment_lsn
- sys.fn_cdc_increment_lsn
ms.assetid: e53b6703-358b-4c9a-912a-8f7c7331069b
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7ce72173181c240307a5bf97688bc568a56fcab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfncdcincrementlsn-transact-sql"></a>sys.fn_cdc_increment_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le numéro séquentiel dans le journal suivant dans la séquence basée sur le numéro séquentiel dans le journal spécifié.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_cdc_increment_lsn ( lsn_value )  
```  
  
## <a name="arguments"></a>Arguments  
 *lsn_value*  
 Valeur LSN. *lsn_value* est **Binary (10)**.  
  
## <a name="return-type"></a>Type de retour  
 **binary(10)**  
  
## <a name="remarks"></a>Notes  
 La valeur LSN retournée par la fonction est toujours supérieure à la valeur spécifiée, et aucune valeur LSN n'existe entre les deux valeurs.  
  
 Pour interroger systématiquement un flux de données de modification dans le temps, vous pouvez répéter périodiquement l'appel de fonction de requête, en spécifiant chaque fois un nouvel intervalle de requête pour délimiter les modifications retournées dans la requête. Pour aider à s'assurer de ne perdre aucune donnée, la limite supérieure de la requête précédente est souvent utilisée pour générer la limite inférieure de la requête suivante. Étant donné que l'intervalle de requête est un intervalle fermé, la nouvelle limite inférieure doit être plus grande que la limite supérieure précédente, mais assez petite pour garantir qu'aucune modification ne comporte de valeur LSN qui se trouve entre cette valeur et l'ancienne limite supérieure. La fonction sys.fn_cdc_increment_lsn est utilisée pour obtenir cette valeur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle de base de données public.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `sys.fn_cdc_increment_lsn` pour générer une nouvelle valeur de limite inférieure pour une requête de capture des données modifiées basée sur la limite supérieure enregistrée dans la variable `@save_to_lsn` à partir d'une requête précédente.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10), @save_to_lsn binary(10);  
SET @save_to_lsn = <previous_upper_bound_value>;  
SET @from_lsn = sys.fn_cdc_increment_lsn(@save_to_lsn);  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * from cdc.fn_cdc_get_all_changes_HumanResources_Employee( @from_lsn, @to_lsn, 'all' );  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.fn_cdc_decrement_lsn &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-decrement-lsn-transact-sql.md)   
 [CDC.fn_cdc_get_all_changes_ &#60; capture_instance &#62;  &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [CDC.fn_cdc_get_net_changes_ &#60; capture_instance &#62; &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [Journal des transactions &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [À propos de la capture de données modifiées &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  