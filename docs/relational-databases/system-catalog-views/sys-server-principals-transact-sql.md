---
title: sys. server_principals (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_principals
- sys.server_principals_TSQL
- sys.server_principals
- server_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_principals catalog view
ms.assetid: c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 408ad309ade858c800b79ee83993fda4fe78467a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133087"
---
# <a name="sysserver_principals-transact-sql"></a>sys.server_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Contient une ligne par principal au niveau serveur.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nomme**|**sysname**|Nom du principal. Nom unique dans un serveur.|  
|**principal_id**|**int**|Numéro d'identification du principal. Nom unique dans un serveur.|  
|**sid**|**varbinary(85)**|SID (Security-IDentifier) du principal. S'il s'agit d'un principal Windows, correspond au SID Windows.|  
|**entrer**|**Char(1**|Type de principal :<br /><br /> S = Nom de connexion SQL<br /><br /> U = Connexion Windows<br /><br /> G = groupe Windows<br /><br /> R = Rôle SQL Server<br /><br /> C = Connexion mappée sur un certificat<br /><br /> K = Connexion mappée sur une clé asymétrique|  
|**type_desc**|**nvarchar (60)**|Description du type de principal :<br /><br /> SQL_LOGIN<br /><br /> WINDOWS_LOGIN<br /><br /> WINDOWS_GROUP<br /><br /> SERVER_ROLE<br /><br /> CERTIFICATE_MAPPED_LOGIN<br /><br /> ASYMMETRIC_KEY_MAPPED_LOGIN|  
|**is_disabled**|**int**|1 = Connexion désactivée.|  
|**create_date**|**DATETIME**|Heure de création du principal.|  
|**modify_date**|**DATETIME**|Heure de dernière modification de la définition du principal.|  
|**default_database_name**|**sysname**|Base de données par défaut de ce principal.|  
|**default_language_name**|**sysname**|Langue par défaut de ce principal.|  
|**credential_id**|**int**|ID d'une information d'identification associée à ce principal. Si aucune information d'identification n'est associée à ce principal, credential_id a la valeur NULL.|  
|**owning_principal_id**|**int**|**Principal_id** du propriétaire d’un rôle de serveur. NULL, si le principal n'est pas un rôle serveur.|  
|**is_fixed_role**|**bit**|Retourne 1 si le principal est l’un des rôles de serveur intégrés avec des autorisations fixes. Pour plus d’informations, consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md).|  
  
## <a name="permissions"></a>Autorisations  
 Toute connexion peut voir son propre nom de connexion, les connexions système, et les rôles serveur fixes. Pour voir d'autres connexions, vous devez disposer de l'autorisation ALTER ANY LOGIN, ou d'une autorisation sur la connexion. Pour afficher les rôles serveur définis par l'utilisateur, vous devez disposer de l'autorisation ALTER ANY SERVER ROLE, ou appartenir au rôle.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
 La requête suivante répertorie les autorisations explicitement accordées ou refusées aux principaux de serveur.  
  
> [!IMPORTANT]  
>  Les autorisations des rôles serveur fixes (autres que public) n’apparaissent pas dans sys. server_permissions. Par conséquent, les principaux de serveur peuvent avoir des autorisations supplémentaires non répertoriées ici.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Hiérarchie des autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
