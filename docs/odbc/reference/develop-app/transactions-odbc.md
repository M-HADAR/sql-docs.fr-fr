---
title: ODBC de transactions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], about transactions
- transactions [ODBC]
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 521a2ffbf0f8eb5e2590ae6e42d50dc71d536683
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086043"
---
# <a name="transactions-odbc"></a>Transactions dans ODBC
Une *transaction* est une unité de travail qui s’effectue comme une opération atomique unique ; autrement dit, l’opération réussit ou échoue dans son ensemble. Par exemple, envisagez de transférer de l’argent d’un compte bancaire vers un autre. Cela implique deux étapes : le retrait de l’argent du premier compte et sa remise dans la seconde. Il est important que les deux étapes se déroulent correctement. Il n’est pas acceptable qu’une étape réussisse et que l’autre échoue. Une base de données qui prend en charge les transactions est en mesure de le garantir.  
  
 Les transactions peuvent être effectuées en cours de *validation* ou de *restauration*. Lorsqu’une transaction est validée, les modifications apportées à cette transaction sont rendues permanentes. Lorsqu’une transaction est restaurée, les lignes affectées sont retournées à l’État dans lequel elles se trouvaient avant le démarrage de la transaction. Pour étendre l’exemple de transfert de compte, une application exécute une instruction SQL pour débiter le premier compte et une instruction SQL différente pour créditer le deuxième compte. Si les deux instructions sont correctement exécutées, l’application valide la transaction. Toutefois, si l’une des instructions échoue pour une raison quelconque, l’application restaure la transaction. Dans les deux cas, l’application garantit un état cohérent à la fin de la transaction.  
  
 Une transaction unique peut englober plusieurs opérations de base de données qui se produisent à des moments différents. Si d’autres transactions ont un accès complet aux résultats intermédiaires, les transactions peuvent interférer les unes avec les autres. Par exemple, si une transaction insère une ligne, une deuxième transaction lit cette ligne et la première transaction est restaurée. La deuxième transaction contient maintenant des données pour une ligne qui n’existe pas.  
  
 Pour résoudre ce problème, il existe différents schémas pour isoler les transactions les unes des autres. L' *isolation des transactions* est généralement implémentée par le verrouillage des lignes, ce qui empêche plusieurs transactions d’utiliser la même ligne en même temps. Dans certaines bases de données, le verrouillage d’une ligne peut également verrouiller d’autres lignes.  
  
 L’isolation des transactions augmente la *concurrence,* ou la capacité de deux transactions à utiliser les mêmes données en même temps. Pour plus d’informations, consultez [définition du niveau d’isolation de la transaction](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Transactions dans ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Contrôle d’accès concurrentiel](../../../odbc/reference/develop-app/concurrency-control.md)
