---
title: SQLTransact fonction) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c96c903b68dee2d1d215804d318d47b4c39a7a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039497"
---
# <a name="sqltransact-function"></a>SQLTransact, fonction
**Conformité**  
 Version introduite : conformité des normes ODBC 1,0 : déconseillé  
  
 **Résumé**  
 Dans ODBC *3. x*, la fonction ODBC *2. x* **SQLTransact** a été remplacée par **SQLEndTran**. Pour plus d’informations, consultez [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  L’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, qui a été introduit dans ODBC 3,8, n’est pas pris en charge par **SQLTransact**. Les applications qui utilisent une opération asynchrone sur un handle de connexion doivent utiliser **SQLEndTran**.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
