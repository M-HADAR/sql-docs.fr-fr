---
title: sys. external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d7af0a7fcb639ae3beab6216e77f9b7b95a398da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68471093"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Répertorie une ligne pour chaque fichier qui compose une bibliothèque externe.

|Nom de la colonne |Type de données |Description|
|------|------|-----|
|external_library_id | int |ID de l’objet de bibliothèque externe. |
|Contenu |varbinary(max) |Contenu de l’artefact du fichier de bibliothèque externe. |
|plateforme |TINYINT |ID de la plateforme hôte sur laquelle SQL Server est installé. |
|platform_desc | nvarchar(60) |Nom de la plateforme hôte. Les valeurs valides sont « WINDOWS », « LINUX ». |

### <a name="see-also"></a>Voir aussi  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestion des packages pour SQL Server Service Machine Learning](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
