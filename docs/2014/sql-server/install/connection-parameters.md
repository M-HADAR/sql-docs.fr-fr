---
title: Paramètres de connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca5d6ed8f1e8a92d22bd32e39c8afe946a0fcfee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095980"
---
# <a name="connection-parameters"></a>Paramètres de connexion
  Pour analyser certains types de serveurs, tels que [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], vous devez sélectionner une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est sélectionnée automatiquement. Vous pouvez modifier cette sélection, mais vous ne pouvez choisir qu'une instance à la fois pour l'analyse par le Conseiller de mise à niveau. Si vous avez inclus un type de serveur qui requiert une authentification, vous devez entrer le mode et les informations d'identification.  
  
## <a name="options"></a>Options  
 **Nom du serveur**  
 Prérempli avec le nom d'ordinateur que vous avez entré dans le volet Composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Nom de l’instance**  
 Choisissez parmi les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont disponibles sur l'ordinateur. Si vous ne voyez pas de liste d’instances, utilisez MSSQLSERVER pour analyser l’instance par défaut. Ceci s'applique particulièrement pour les ordinateurs distants. Vous pouvez également utiliser le mot "default" pour rechercher l'instance par défaut.  
  
 **Authentification**  
 Sélectionnez un mode dans la liste des modes d'authentification disponibles sur cet ordinateur. Par défaut, le mode d'authentification correspond à l'authentification Windows.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], entrez un nom d'utilisateur dans la zone. Il est recommandé que le nom d'utilisateur ait des informations d'identification d'administration sur l'ordinateur.  
  
> [!NOTE]  
>  Si vous sélectionnez l’authentification Windows, le nom d’utilisateur de l’utilisateur actuellement connecté est renseigné dans la zone de texte **nom d’utilisateur** .  
  
 **Mot de passe**  
 Entrez le mot de passe de l'utilisateur spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Guide de référence de l'interface utilisateur du Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
