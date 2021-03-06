---
title: Chronologie de sauvegarde | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.POINTINTIMERESTORE.F1
- sql12.swb.backuptimeline.f1
helpviewer_keywords:
- Backup Timeline
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 92cffa7c280aac559433a8fc7ad5a3223c9f6de2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62876701"
---
# <a name="backup-timeline"></a>Chronologie de sauvegarde
  Utilisez la boîte de dialogue **Chronologie de sauvegarde** pour rechercher et spécifier des sauvegardes afin de restaurer une base de données jusqu’à une date et heure. La boîte de dialogue **Chronologie de sauvegarde** est accessible en cliquant sur **Chronologie** dans le volet **Restaurer la base de données (page Général)** . Cette boîte de dialogue vous permet de consulter une chronologie des opérations de restauration effectuées sur la base de données.  
  
 L'Assistant Récupération de base de données garantit que seules les sauvegardes requises pour la restauration à cette limite dans le temps sont sélectionnées. Ces sauvegardes sélectionnées constituent le plan de restauration recommandé pour votre opération de restauration. Vous devez utiliser uniquement les sauvegardes sélectionnées. Pour plus d’informations sur l’Assistant de récupération de base de données, consultez [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).  
  
## <a name="restore-to"></a>Restaurer sur  
 L'option**Dernière sauvegarde effectuée** est sélectionnée par défaut. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sélectionne les sauvegardes appropriées pour restaurer la base de données, et restaure la base de données jusqu'au point de la dernière sauvegarde. Cliquez sur **Date et heure spécifiques** pour définir les date et heure manuellement (sélection d’un point spécifique dans le temps).  
  
 L'option**Date et heure spécifiques** vous permet d'arrêter la restauration à une date et une heure que vous spécifiez. La chronologie indique une représentation des opérations de sauvegarde effectuées sur une période 24 heures autour de la date et de l'heure sélectionnées.  
  
 **Date**  
 Entrez une date ou sélectionnez-en une dans la zone de liste déroulante.  
  
 **Time**  
 Entrez ou sélectionnez une date pour indiquer le moment précis auquel la restauration doit s'arrêter.  
  
 **Barre planning - Intervalle**  
 Affiche les options pour les types d'intervalle consultables sur la chronologie.  
  
## <a name="timeline-and-legend"></a>Chronologie et légende  
 Utilisez la barre de défilement sous la chronologie pour déplacer le curseur vers l'avant et vers l'arrière le long de la chronologie. Cliquez sur une sauvegarde pour déplacer la barre de défilement à la fin de cette sauvegarde. Pointez la souris sur un marqueur pour afficher une info-bulle qui fournit des informations sur le jeu de sauvegarde sélectionné. Les informations de sauvegarde sont indiquées sur la chronologie par les marqueurs suivants.  
  
 Plus grand triangle  
 Représente les sauvegardes complètes effectuées sur la base de données, en indiquant le point spécifique à l'heure où chaque sauvegarde complète a été effectuée.  
  
 Plus petit triangle  
 Représente les sauvegardes différentielles effectuées sur la base de données, en indiquant le point spécifique à l'heure où chaque sauvegarde différentielle a été effectuée.  
  
 Zones hachurées vertes  
 Représente la couverture de sauvegarde du journal des transactions.  
  
 Ligne rouge  
 Peut être positionnée uniquement le long de la chronologie où la restauration est possible. En déplaçant la ligne rouge le long de la chronologie, vous pouvez régler les date et heure affichées dans les zones **Date** et **Heure** .  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
