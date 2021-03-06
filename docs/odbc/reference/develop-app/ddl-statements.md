---
title: Instructions DDL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97541c9d594b282b871cb7869d0e8c2d2224205d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076866"
---
# <a name="ddl-statements"></a>Instructions DDL
Les instructions DDL (Data Definition Language) varient considérablement entre les SGBD. ODBC SQL définit les instructions pour les opérations de définition de données les plus courantes : créer et supprimer des tables, des index et des vues. modification des tables ; et l’octroi et la révocation des privilèges. Toutes les autres instructions DDL sont spécifiques à la source de données. Par conséquent, les applications interopérables ne peuvent pas effectuer certaines opérations de définition de données. En général, ce n’est pas un problème, car ces opérations ont tendance à être très spécifiques au SGBD et sont préférables aux logiciels d’administration de base de données propriétaires fournis avec la plupart des SGBD ou au programme d’installation fourni avec le pilote.  
  
 Un autre problème dans la définition des données est que les noms de types de données varient énormément entre les SGBD. Plutôt que de définir des noms de types de données standard et de forcer les pilotes à les convertir en noms propres au SGBD, **SQLGetTypeInfo** offre aux applications la possibilité de détecter les noms de types de données propres au SGBD. Les applications interopérables doivent utiliser ces noms dans les instructions SQL pour créer et modifier des tables ; les noms répertoriés dans l' [annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)et [annexe D : types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md)sont des exemples uniquement.
