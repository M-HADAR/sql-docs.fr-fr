---
title: Types de données et comportement de chargement en masse XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d2eb9af2b353760f5b195b95d6a9f9d5d1efc9b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013414"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Types de données et comportement du chargement en masse XML (SQLXML 4.0)
  Les types de données spécifiés dans le schéma de mappage (type XSD ou XDR et `sql:datatype`) sont ignorés en général, sauf dans les cas suivants :  
  
 Dans XSD :  
  
-   Si le type est `dateTime` ou `time`, vous devez spécifier `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Lorsque vous effectuez un chargement en masse dans une `uniqueidentifier` colonne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type dans et que la valeur xsd est un GUID qui comprend des accolades ({et}), vous devez spécifier **SQL : datatype = "uniqueidentifier"** pour supprimer les accolades avant que la valeur ne soit insérée dans la colonne. Si `sql:datatype` n'est pas spécifié, la valeur est envoyée avec les accolades et l'insertion échoue.  
  
 Pour plus d’informations `sql:datatype`sur, consultez [forçages de type de données et l’annotation sql : datatype &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Dans XDR :  
  
-   Si `dt:type` est `datetime`, `time`, `dateTime.tz` ou `time.tz`, vous devez spécifier les types de données `dt:type` et `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si vos données XML sont de type `uuid`, `sql:datatype` doit être spécifié ; **DT : type = "UUID"** est également requis, sauf si les données sont des données de chaîne. Si vous ne spécifiez pas `dt:uuid`, le chargement en masse XML accepte les chaînes avec accolades (et les supprime si nécessaire).  
  
-   Si les données XML sont `bin.base64` ou `bin.hex`, vous devez spécifier le type de données XML avec `dt:type`. Le chargement en masse XML charge ensuite les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous la forme d'une représentation hexadécimale des données.  
  
  
