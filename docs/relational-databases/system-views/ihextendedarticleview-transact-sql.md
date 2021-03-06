---
title: IHextendedArticleView (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0abca8ca826ec986a9cbf71f4fb577291e095e39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029542"
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La vue **IHextendedArticleView** expose des informations sur les articles d’une publication non SQL Server. Cette vue est stockée dans la base de données de **distribution** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Identificateur unique du serveur de publication.|  
|**publication_id**|**int**|Identificateur unique de la publication.|  
|**-**|**sysname**|Nom de l'article.|  
|**destination_object**|**sysname**|Nom de l'objet publié sur l'Abonné.|  
|**source_owner**|**sysname**|Propriétaire de l'objet publié sur le serveur de publication.|  
|**source_object**|**sysname**|Nom de l'objet publié sur le serveur de publication.|  
|**description**|**nvarchar(255)**|Description de l'article.|  
|**creation_script**|**nvarchar(255)**|Script de création du schéma de l'article.|  
|**del_cmd**|**nvarchar(255)**|Commande exécutée pour une opération DELETE.|  
|**filtres**|**int**|Identificateur de la procédure stockée utilisée pour définir la partition horizontale.|  
|**filter_clause**|**ntext**|Clause WHERE utilisée pour filtrer horizontalement l'article.|  
|**ins_cmd**|**nvarchar(255)**|Commande exécutée pour une opération INSERT.|  
|**pre_creation_cmd**|**tinyint**|Commande de pré-création pour les instructions DROP TABLE, DELETE TABLE ou TRUNCATE :<br /><br /> **0** = aucun.<br /><br /> **1** = suppression.<br /><br /> **2** = suppression.<br /><br /> **3** = tronquer.|  
|**statu**|**tinyint**|Masque de bits de l'état et des options d'article, qui peut être le résultat OR logique au niveau du bit d'au moins l'une des valeurs suivantes :<br /><br /> **1** = l’article est actif.<br /><br /> **8** = inclure le nom de colonne dans les instructions INSERT.<br /><br /> **16** = utiliser des instructions paramétrables.<br /><br /> **24** = les deux incluent le nom de colonne dans les instructions INSERT et utilisent des instructions paramétrables.<br /><br /> Par exemple, un article actif utilisant des instructions paramétrables aurait la valeur **17** dans cette colonne. La valeur **0** signifie que l’article est inactif et qu’aucune propriété supplémentaire n’est définie.|  
|**entrer**|**tinyint**|Type d'article :<br /><br /> **1** = article basé sur le journal.<br /><br /> **3** = article basé sur un journal avec filtre manuel.<br /><br /> **5** = article basé sur un journal avec vue manuelle.<br /><br /> **7** = article basé sur le journal avec filtre manuel et vue manuelle.|  
|**upd_cmd**|**nvarchar(255)**|Commande exécutée pour une opération UPDATE.|  
|**schema_option**|**binary**|Indique ce qui doit faire l’objet d’un script. Pour obtenir la liste des options de schéma prises en charge, consultez [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) .|  
|**dest_owner**|**sysname**|Propriétaire de l'objet publié dans la base de données de destination.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
