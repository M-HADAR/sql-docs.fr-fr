---
title: Longueur du cycle de produit | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 203ad92dd6abfc71b0fdeddc466752612e666cee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100452"
---
# <a name="length-of-the-product-cycle"></a>Longueur du cycle produit
La dernière question à propos de l’interopérabilité est l’heure. Le développement d’une application interopérable prend généralement plus de temps que le développement d’un noninteroperable. En effet, l’application doit vérifier les fonctionnalités du SGBD, effectuer les mêmes tâches différemment pour différents SGBD, contourner les fonctionnalités prises en charge par certains SGBD, mais pas d’autres, etc.  
  
 En plus du temps de développement, la durée de vie du produit doit être prise en compte. Si l’application est conçue pour être utilisée une seule fois, telle qu’une application qui transfère des données lors de la migration d’un SGBD à un autre, il n’y a aucun point dans la prise en compte de l’interopérabilité. L’application sera utilisée une fois et ignorée.  
  
 Si l’application existe à long terme, il peut être plus facile de la maintenir en tant qu’application interopérable. Cela est vrai même pour les applications personnalisées qui ont un SGBD unique en tant que cible. La raison en est que le code interopérable utilise un sous-ensemble limité de fonctionnalités de base de données. Le pilote est nécessaire pour maintenir ces fonctionnalités disponibles, même en cas de modifications apportées au SGBD sous-jacent. Ainsi, le code interopérable peut décharger les modifications apportées au SGBD entre le développeur de l’application et le développeur du pilote.
