---
title: NOT NULL dans les instructions CREATE TABLE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 808cddbd805db09d1b5c356d5b5af5734a5dcc16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086317"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL dans les instructions CREATE TABLE
Certaines bases de données, et en particulier les bases de données de bureau, ne prennent pas en charge la contrainte de colonne **not null** dans les instructions **Create table** . Pour plus d’informations, consultez l’option SQL_NON_NULLABLE_COLUMNS dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .
