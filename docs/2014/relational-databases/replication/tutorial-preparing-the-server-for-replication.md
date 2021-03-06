---
title: 'Didacticiel : Préparation du serveur à la réplication | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9b8ed6778a087c2200012c6df1409b187b39329
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199070"
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Didacticiel : Préparation du serveur à la réplication
  Il importe de prévoir la sécurité avant de configurer la topologie de réplication. Ce didacticiel vous explique comment sécuriser au mieux une topologie de réplication et configurer la distribution, première étape de la réplication des données. Ce didacticiel doit être effectué avant les autres didacticiels.  
  
> [!NOTE]  
>  Pour répliquer les données de manière sécurisée entre les serveurs, vous devez implémenter toutes les recommandations dans les [meilleures pratiques de sécurité de réplication](security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Dans ce didacticiel, vous allez apprendre à préparer un serveur afin que la réplication puisse s'exécuter de façon sécurisée avec les privilèges minimaux. La première leçon explique comment créer les comptes de service Windows utilisés pour exécuter les agents de réplication. La deuxième leçon montre comment configurer le dossier utilisé pour générer et stocker les instantanés de publication. La troisième leçon vous apprend à configurer la distribution et à définir les autorisations.  
  
## <a name="requirements"></a>Spécifications  
 Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations essentielles de base de données, mais dont l'expérience en matière de réplication est limitée.  
  
 Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] avec la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
 **Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
  
-   [Leçon 1 : création de comptes Windows pour la réplication](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Leçon 2 : préparation du dossier d’instantanés](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Leçon 3 : configuration de la distribution](lesson-3-configuring-distribution.md)  
  
 [Démarrer le didacticiel](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Sécurité Réplication SQL Server](security/view-and-modify-replication-security-settings.md)  
  
  
