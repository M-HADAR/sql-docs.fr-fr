---
title: Afficher les erreurs rencontrées lors de la mise en lots
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d3bb33d8c3a9237c96fc0bde1becba07df9a7bdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728841"
---
# <a name="view-errors-that-occur-during-staging-master-data-services"></a>Afficher les erreurs rencontrées lors de la mise en lots (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez consulter les erreurs qui se produisent pendant le processus de site. La base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] comporte deux vues pour afficher les erreurs :  
  
-   stg.viw_name_MemberErrorDetails pour les mises à jour de membre feuille ou consolidé.  
  
-   stg.viw_name_RelationshipErrorDetails pour les mises à jour de relation de hiérarchie.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , vous devez disposer des autorisations SELECT sur la vue stg.viw_name_MemberErrorDetails ou stg.viw_name_RelationshipErrorDetails.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Pour afficher des erreurs de mise en lots  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Ouvrez une nouvelle requête.  
  
3.  Tapez le texte suivant, en remplaçant « name » par le nom de votre table de mise en lots, par exemple, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Exécutez la requête. Les détails des erreurs sont affichés dans le champ **ErrorDescription** .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur les messages d’erreur, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Résolution des problèmes liés au processus de site (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
