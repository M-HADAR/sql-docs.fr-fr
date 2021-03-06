---
title: sp_helplanguage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d46e178fc1872a84bb573f16629803c59f2fb6c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122511"
---
# <a name="sp_helplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Affiche des informations sur une langue de remplacement particulière ou sur toutes les langues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @language = ] 'language'`Nom de l’autre langue pour laquelle afficher des informations. *Language* est de **type sysname**, avec NULL comme valeur par défaut. Si la *langue* est spécifiée, les informations relatives à la langue spécifiée sont retournées. Si la langue n’est pas spécifiée, des informations sur toutes les langues de la vue de compatibilité **sys. syslanguages** sont retournées.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Numéro d'identification de la langue.|  
|**DateFormat**|**nchar(3)**|Format de la date.|  
|**DATEFIRST**|**tinyint**|Premier jour de la semaine : 1 pour lundi, 2 pour mardi, etc., jusqu'à 7 pour dimanche.|  
|**installation**|**int**|Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la dernière mise à niveau pour cette langue.|  
|**nomme**|**sysname**|Nom de la langue.|  
|**affecté**|**sysname**|Nom de remplacement de la langue.|  
|**suivent**|**nvarchar (372)**|Noms des mois.|  
|**mois courts**|**nvarchar (132)**|Abréviations des noms des mois.|  
|**précédant**|**nvarchar (217)**|Noms des jours.|  
|**LCID**|**int**|ID de paramètres régionaux Windows pour la langue.|  
|**msglangid**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ID du groupe de messages.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-information-about-a-single-language"></a>R. Renvoi d’informations sur une langue  
 L'exemple suivant affiche des informations sur la langue de remplacement `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Renvoi d’informations sur toutes les langues  
 L'exemple suivant vous renseigne sur toutes les langues de remplacement installées.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
