---
title: Améliorations de la date et de l’heure (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207008"
---
# <a name="date-and-time-improvements-odbc"></a>Améliorations de la date et de l’heure (ODBC)
  
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a introduit de nouveaux types de données de date et d'heure. Cette section décrit comment ces nouveaux types sont exposés en tant qu' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extensions dans Native Client. Pour obtenir une vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’ensemble de la prise en charge native client pour les nouveaux types de données de date et d’heure, consultez améliorations de la [date et](../native-client/features/date-and-time-improvements.md)de l’heure. Pour obtenir un exemple illustrant la prise en charge de la date et de l’heure ODBC, consultez [utiliser les types de date et d’heure](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Pour plus d’informations générales sur les types de données de date et d’heure, consultez [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations date/heure (ODBC)](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Fournit des informations sur les types ODBC qui prennent en charge les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de date et d'heure.  
  
 [Métadonnées &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Décrit les informations retournées dans le champ de descripteur de paramètre d'implémentation (IPD) et dans le champ de descripteur de ligne d'implémentation (IRD), ainsi que les métadonnées de colonne retournées par `SQLColumns` et `SQLProcedureColumns`. Elle décrit également les métadonnées de type de données retournées par `SQLGetTypeInfo`.  
  
 [conversions de type de données DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Décrit comment effectuer une conversion entre les valeurs datetime et datetimeoffset.  
  
 [Prise en charge de sql_variant pour les types Date et Time](sql-variant-support-for-date-and-time-types.md)  
 Décrit la prise en charge de la fonction SQL_VARIANT pour les fonctionnalités de date et heure améliorées.  
  
 [Modifications de copie en bloc pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Comportement du type de date et d’heure amélioré avec les versions antérieures de SQL Server &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Décrit le comportement attendu lorsqu’une application cliente utilisant les fonctionnalités améliorées de date et d’heure communique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec une version antérieure de, et lorsqu’un client compilé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une version antérieure de native client envoie des commandes à un serveur qui prend en charge les fonctionnalités de date et d’heure améliorées.  
  
 [Prise en charge des fonctionnalités de date et heure améliorées par l’API ODBC](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Répertorie les fonctions ODBC qui prennent en charge les fonctionnalités de date et heure améliorées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;&#41;ODBC](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
