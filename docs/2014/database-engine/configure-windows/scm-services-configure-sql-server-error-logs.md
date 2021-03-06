---
title: Configurer les journaux des erreurs SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 60d38caf365d6db54ea0abe688a3fc2979fdab82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809682"
---
# <a name="configure-sql-server-error-logs"></a>Configurer des journaux d'erreurs SQL Server
  Cette rubrique indique comment consulter ou modifier la méthode de recyclage des journaux d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Pour ouvrir la boîte de dialogue Configurer les journaux d'erreurs SQL Server  
  
1.  Dans l’Explorateur d’objets, développez l’instance de SQL Server, puis **Gestion**, cliquez avec le bouton droit sur **Journaux SQL Server**, puis sélectionnez **Configurer**.  
  
2.  Dans la boîte de dialogue **Configurer les journaux d'erreurs SQL Server** , choisissez l'une des options suivantes.  
  
     **Limiter le nombre de fichiers de journaux d'erreurs avant qu'ils ne soient recyclés**  
     Activez cette option pour limiter le nombre de journaux d'erreurs créés avant le recyclage. Un nouveau journal des erreurs est créé à chaque démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve des copies de sauvegarde des six derniers journaux, sauf si vous avez activé cette option et spécifié un autre nombre maximal de fichiers de journaux des erreurs ci-dessous.  
  
     **Nombre maximal de fichiers de journaux d'erreurs**  
     Spécifiez le nombre maximal de fichiers de journaux d'erreurs pouvant être créés avant le recyclage. La valeur par défaut est 6, ce qui correspond au nombre de journaux sauvegardés que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve avant de les recycler.  
  
  
