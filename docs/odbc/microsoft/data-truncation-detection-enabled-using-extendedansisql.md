---
title: Détection de troncation de données activée à l’aide de ExtendedAnsiSQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7fb67171a796755bf8d6229b9d562f69bd588ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096508"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de la troncation de données activée avec ExtendedAnsiSQL
Lorsque l’indicateur ExtendedAnsiSQL est activé et que l’application insère des données dans une colonne de type char ou binary et que les données sont tronquées, la troncation est détectée. Lorsque l’indicateur ExtendedAnsiSQL est désactivé, les données sont tronquées sans avertissement, comme c’était le cas dans les versions précédentes des pilotes de base de données de bureau ODBC.
