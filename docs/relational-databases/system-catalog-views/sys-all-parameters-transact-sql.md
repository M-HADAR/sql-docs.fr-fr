---
title: sys. all_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- all_parameters_TSQL
- sys.all_parameters
- all_parameters
- sys.all_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_parameters catalog view
ms.assetid: eecbb68e-9b4c-4243-94e2-8096a9cc7892
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 63231301109f83243b431244028fddffb8cc6fe7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001324"
---
# <a name="sysall_parameters-transact-sql"></a>sys.all_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Affiche l'union de tous les paramètres qui appartiennent aux objets système ou définis par l'utilisateur.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l’objet auquel appartient ce paramètre.|  
|**nomme**|**sysname**|Nom du paramètre. Unique dans l'objet. Si l'objet est une fonction scalaire, le nom du paramètre est une chaîne de caractères vide dans la ligne qui représente la valeur renvoyée.|  
|**parameter_id**|**int**|Identificateur du paramètre. Unique dans l'objet. Si l’objet est une fonction scalaire, **parameter_id** = 0 représente la valeur de retour.|  
|**system_type_id**|**tinyint**|Identificateur du type système du paramètre.|  
|**user_type_id**|**int**|Identificateur du type du paramètre tel qu'il est défini par l'utilisateur.<br /><br /> Pour retourner le nom du type, Joignez-vous à l’affichage catalogue [sys. types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) sur cette colonne.|  
|**max_length**|**smallint**|Longueur maximale du paramètre en octets.<br /><br /> -1 = le type de données de la colonne est **varchar (max)**, **nvarchar (max)**, **varbinary (max)** ou **XML**.|  
|**precision**|**tinyint**|Précision du paramètre s'il est numérique ; sinon, 0.|  
|**scale**|**tinyint**|Échelle du paramètre s'il est numérique ; sinon, 0.|  
|**is_output**|**bit**|1 = le paramètre est renvoyé ; sinon, 0.|  
|**is_cursor_ref**|**bit**|1 = le paramètre est un paramètre de référence de curseur.|  
|**has_default_value**|**bit**|1 = le paramètre a une valeur par défaut.<br /><br /> 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve seulement les valeurs par défaut des objets CLR dans cet affichage catalogue ; par conséquent, cette colonne a toujours une valeur nulle (0) pour les objets [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour afficher la valeur par défaut d’un paramètre dans [!INCLUDE[tsql](../../includes/tsql-md.md)] un objet, interrogez la colonne de **définition** de l’affichage catalogue [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) , ou utilisez la fonction système [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) .|  
|**is_xml_document**|**bit**|1 = Le contenu est un document XML complet.<br /><br /> 0 = le contenu est un fragment de document ou le type de données de la colonne n’est pas **XML**.|  
|**default_value**|**sql_variant**|Si **has_default_value** a la valeur 1, la valeur de cette colonne est la valeur par défaut du paramètre ; Sinon, NULL.|  
|**xml_collection_id**|**int**|Identificateur de la collection du schéma XML utilisé pour valider le paramètre.<br /><br /> Différent de zéro si le type de données du paramètre est **XML** et que le XML est typé.<br /><br /> 0 = il n'existe pas de collection de schéma XML ou le paramètre n'est pas de type XML.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Interrogation du SQL Server FAQ du catalogue système](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys. Parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys. system_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
