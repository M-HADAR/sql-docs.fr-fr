---
title: SQLFetch (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2cb829f065421a13d3c7df06c670808bc3d9d77c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064433"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLFetch** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLFetch**, consultez la [fonction SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetch** ne peuvent pas être mélangés avec des appels à **SQLFetchScroll** ou **SQLExtendedFetch**.  
  
 Si **SQLFetch** est appelée avec SQL_ATTR_ROW_ARRAY_SIZE défini sur une valeur supérieure à 1, la bibliothèque de curseurs passe l’appel au pilote. Si le pilote est un ODBC 2. *x* , la taille de l’ensemble de lignes sera ignorée et l’appel à **SQLFetch** renverra une seule ligne de données.  
  
 Si la bibliothèque de curseurs est utilisée avec ODBC 2. *x* Driver, un décalage de liaison (tel que défini par l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR) n’est pas utilisé lorsque **SQLFetch** est appelé.  
  
 Lorsque la bibliothèque de curseurs est chargée, une application ne peut pas appeler **SQLFetch** pour extraire les colonnes de signets. La bibliothèque de curseurs transmet l’appel de **SQLFetch** au pilote, mais la fonction appelle pour activer les signets et lier la colonne de signet est interceptée par la bibliothèque de curseurs.
