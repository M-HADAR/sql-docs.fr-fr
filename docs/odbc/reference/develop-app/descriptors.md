---
title: Descripteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2138a5f8417fc9156c916719e96d707b9a29de9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040009"
---
# <a name="descriptors"></a>Descripteurs
Un handle de descripteur fait référence à une structure de données qui contient des informations sur les colonnes ou les paramètres dynamiques.  
  
 Les fonctions ODBC qui opèrent sur les données de colonnes et de paramètres définissent et récupèrent implicitement des champs de descripteur. Par exemple, lorsque **SQLBindCol** est appelé pour lier des données de colonne, il définit des champs de descripteur qui décrivent complètement la liaison. Lorsque **SQLColAttribute** est appelé pour décrire des données de colonne, il retourne les données stockées dans des champs de descripteur.  
  
 Une application appelant des fonctions ODBC n’a pas besoin de se préoccuper des descripteurs. Aucune opération de base de données ne nécessite que l’application bénéficie d’un accès direct aux descripteurs. Toutefois, pour certaines applications, obtenir un accès direct aux descripteurs simplifie de nombreuses opérations. Par exemple, l’accès direct aux descripteurs permet de relier les données de la colonne, ce qui peut être plus efficace que l’appel de **SQLBindCol** .  
  
> [!NOTE]  
>  La représentation physique du descripteur n’est pas définie. Les applications accèdent directement à un descripteur en manipulant ses champs en appelant des fonctions ODBC avec le handle de descripteur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Allocation et libération de descripteurs](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Obtention et définition des champs de descripteur](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)
