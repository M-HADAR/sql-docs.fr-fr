---
title: Activer une version
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0fa359de1daa844fbcce073b0c67efdd5f721b37
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728592"
---
# <a name="commit-a-version-master-data-services"></a>Activer une version (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], activez une version d’un modèle pour empêcher que des modifications ne soient apportées aux membres du modèle et à leurs attributs. Les versions activées ne peuvent pas être déverrouillées.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   L’état de la version doit être **Verrouillé**. Pour plus d’informations, consultez [Verrouiller une version &#40;Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md).  
  
-   Tous les membres doivent avoir été validés correctement.  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Gestion des versions. Pour plus d’informations, consultez [autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-commit-a-version"></a>Pour activer une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , dans la barre de menus, cliquez sur **Valider la version**.  
  
3.  Dans la page **Valider la version** , sélectionnez le modèle et la version à activer.  
  
4.  Cliquez sur **Valider**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un indicateur de version &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Affecter un indicateur à une version &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Copier une version &#40;Master Data Services&#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
  
