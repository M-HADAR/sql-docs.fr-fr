---
title: SQLSetScrollOptions (pilotes de base de données de bureau) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0adedfb69cd4a7b5cf195916747687826805e8bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905392"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)
Les curseurs de transfert et statiques sont pris en charge pour les SQL_CONCUR_READ_ONLY.  
  
 Seuls les curseurs de jeu de clés sont pris en charge pour un argument *fConcurrency* de SQL_CONCUR_LOCK.  
  
 Un argument *fConcurrency* de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs dynamiques et les curseurs mixtes ne sont pas pris en charge.
