---
title: sys. Credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da427117b2282c9014ff0171e1a7c29f7490940e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078752"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Retourne une ligne pour chaque information d’identification au niveau du serveur.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID de l'information d'identification. Unique dans le serveur.|  
|name|**sysname**|Nom de l'information d'identification. Unique dans le serveur.|  
|credential_identity|**nvarchar(4000)**|Nom de l'identité à utiliser. Il s'agit généralement d'un utilisateur Windows. Il n'est pas nécessaire qu'elle soit unique.|  
|create_date|**DATETIME**|Heure de création de l'information d'identification.|  
|modify_date|**DATETIME**|Heure de la dernière modification de l'information d'identification.|  
|target_type|**nvarchar(100**|Type d'information d'identification. Retourne NULL pour des informations d'identification traditionnelles, CRYPTOGRAPHIC PROVIDER pour des informations d'identification mappées à un fournisseur de chiffrement. Pour plus d’informations sur les fournisseurs de gestion de clés externes, consultez [gestion de clés Extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|ID de l'objet auquel l'information d'identification est mappée. Retourne 0 pour des informations d'identification traditionnelles, et une valeur différente de 0 pour des informations d'identification mappées à un fournisseur de chiffrement. Pour plus d’informations sur les fournisseurs de gestion de clés externes, consultez [gestion de clés Extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Notes  
Pour obtenir des informations d’identification au niveau de la base de données, consultez [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Autorisations  
 Requiert une `VIEW ANY DEFINITION` autorisation ou `ALTER ANY CREDENTIAL` une autorisation. En outre, l’autorisation du principal ne doit `VIEW ANY DEFINITION` pas être refusée.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Informations d’identification &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
