---
title: sys. dm_xe_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_objects
- sys.dm_xe_objects
- sys.dm_xe_objects_TSQL
- dm_xe_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_objects dynamic management view
- extended events [SQL Server], views
ms.assetid: 5d944b99-b097-491b-8cbd-b0e42b459ec0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 023ee54178c5f303797c6db83cc646353304b051
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090273"
---
# <a name="sysdm_xe_objects-transact-sql"></a>sys.dm_xe_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque objet exposé par un package d'événement. Il peut s'agir de l'un des objets suivants :  
  
-   Événements. Les événements indiquent les détails intéressants d'un chemin d'exécution. Tous les événements contiennent des informations sur un détail intéressant.  
  
-   Actions. Les actions sont exécutées de façon synchrone lorsque les événements se déclenchent. Une action peut ajouter des données de temps d'exécution à un événement.  
  
-   Cibles. Les cibles consomment des événements, de façon synchrone sur le thread qui déclenche l'événement ou de façon asynchrone sur un thread fourni par le système.  
  
-   Prédicats. Les sources de prédicats récupèrent des valeurs à partir de sources d'événements pour les utiliser lors d'opérations de comparaison. Les comparaisons de prédicats comparent des types de données spécifiques et retournent une valeur booléenne.  
  
-   Types. Les types encapsulent la longueur et les caractéristiques de la collection Byte, ce qui est nécessaire à l'interprétation des données.  

 |Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar (60)**|Nom de l'objet. le nom est unique au sein d’un package pour un type d’objet spécifique. N'accepte pas la valeur NULL.|  
|object_type|**nvarchar (60)**|Type de l’objet. object_type est l’un des éléments suivants :<br /><br /> événement<br /><br /> action<br /><br /> target<br /><br /> pred_source<br /><br /> pred_compare<br /><br /> type<br /><br /> N'accepte pas la valeur NULL.|  
|package_guid|**uniqueidentifier**|GUID pour le package qui expose cette action. Il y a une relation plusieurs-à-un avec sys.dm_xe_packages.package_id. N'accepte pas la valeur NULL.|  
|description|**nvarchar (256)**|Description de l'action la description est définie par l’auteur du package. N'accepte pas la valeur NULL.|  
|capabilities|**int**|Bitmap qui décrit les fonctionnalités de l'objet. Autorise la valeur NULL.|  
|capabilities_desc|**nvarchar (256)**|Répertorie toutes les fonctionnalités de l'objet. Autorise la valeur NULL.<br /><br /> **Fonctions qui s'appliquent à tous les types d'objets**<br /><br /> -<br />                                **Privée**. Le seul objet disponible pour une utilisation interne, qui n'est pas accessibles via CREATE/ALTER EVENT SESSION DDL. Les événements d'audit et les cibles sont classés dans cette catégorie, en plus d'un petit nombre d'objets utilisés en interne.<br /><br /> ===============<br /><br /> **Fonctions d'événement**<br /><br /> -<br />                                **No_block**. L'événement est dans un chemin de code critique qui ne peut en aucun cas être bloqué. Les événements ayant cette fonction ne peuvent être ajoutés à aucune session d'événements qui spécifie NO_EVENT_LOSS.<br /><br /> ===============<br /><br /> **Fonctions qui s'appliquent à tous les types d'objets**<br /><br /> -<br />                                **Process_whole_buffers**. La cible consomme des mémoires tampons d'événements à la fois, plutôt qu'un événement après l'autre.<br /><br /> -<br />                        **Singleton**. Une seule instance de la cible peut exister dans un processus. Bien que plusieurs sessions d'événements puissent référencer la même cible singleton, il existe réellement une seule instance, qui voit chaque événement une seule fois. C'est important si la cible est ajoutée à plusieurs sessions qui collectent toutes le même événement.<br /><br /> -<br />                                **Synchrone**. La cible est exécutée sur le thread qui produit l'événement, avant que le contrôle soit renvoyé à la ligne de code appelant.|  
|type_name|**nvarchar (60)**|Nom pour les objets pred_source et pred_compare. Autorise la valeur NULL.|  
|type_package_guid|**uniqueidentifier**|GUID pour le package qui expose le type sur lequel fonctionne cet objet. Autorise la valeur NULL.|  
|type_size|**int**|Taille du type de données, en octets. Uniquement pour les types d'objets valides. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|De|À|Relation|  
|----------|--------|------------------|  
|sys.dm_xe_objects.package_guid|sys.dm_xe_packages.guid|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

