---
title: sys. tcp_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e4b711a7d36e7677f6f32b87ff4c696db231730
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68116734"
---
# <a name="systcp_endpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque point de terminaison TCP dans le système. Les points de terminaison décrits par **sys. tcp_endpoints** fournissent un objet pour accorder et révoquer le privilège de connexion. Les informations affichées concernant les ports et les adresses IP ne sont pas utilisées pour configurer les protocoles, et il est possible qu'elles ne correspondent pas à la configuration réelle des protocoles. Pour afficher les protocoles et les configurer, utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**< les colonnes héritées>**||Hérite des colonnes des [points de terminaison sys.](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)|  
|**importer**|int|Numéro de port que le point de terminaison écoute. N'accepte pas la valeur NULL.|  
|**is_dynamic_port**|bit|1 = Numéro de port affecté de façon dynamique.<br /><br /> N'accepte pas la valeur NULL.|  
|**ip_address**|**nvarchar (45)**|Adresse IP du port d'écoute, telle qu'elle est stipulée par la clause LISTENER_IP. Autorise la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 Pour recueillir des informations sur les points de terminaison et les connexions, exécutez la requête suivante. Les points de terminaison sans connexion active ou sans connexion TCP s'affichent avec des valeurs NULL. Ajoutez la **** clause `WHERE des.session_id = @@SPID` WHERE pour renvoyer des informations sur la connexion actuelle.  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue des points de terminaison &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
