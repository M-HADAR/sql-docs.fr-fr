---
title: Guide pratique pour modifier les propriétés d’une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 96604a09811626a304502dc05ef4f7e9edcd0359
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62771227"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a>Procédure : modifier les propriétés d'une instance de capture de données modifiées
  Cette procédure décrit comment utiliser la console du concepteur CDC pour modifier les propriétés de configuration d'une instance de capture de données modifiées.  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a>Pour modifier les propriétés de configuration de l'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance avec les propriétés à modifier.  
  
3.  Sélectionnez le nom de l'instance où vous souhaitez modifier les propriétés.  
  
4.  Dans le volet Actions à droite de la console du concepteur CDC, cliquez sur **Propriétés**.  
  
     Vous pouvez aussi cliquer avec le bouton droit sur l’instance dont vous voulez modifier les propriétés et cliquer sur **Propriétés**.  
  
5.  Dans l'éditeur de propriétés, modifiez les propriétés dans les onglets suivants :  
  
    -   **Oracle**: l'onglet **Oracle** de l'éditeur de propriétés permet d'apporter des modifications à la description que vous avez fournie dans la page Créer une base de données CDC de l'Assistant Nouvelle instance et d'apporter des modifications aux informations de connexion à la base de données d'exploration de données de journaux Oracle.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).  
  
    -   **Tables**: l'onglet **Tables** permet d'apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit Tables](edit-tables.md).  
  
    -   **Scripts**: l’onglet **Scripts** permet d’exécuter ou de réexécuter un script sur la base de données source Oracle qui configure une journalisation supplémentaire.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).  
  
    -   **Avancé**: l'onglet **Avancé** permet d'ajouter des propriétés spéciales à l'instance de capture de données modifiées.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Edit the Advanced Properties](edit-the-advanced-properties.md).  
  
  
