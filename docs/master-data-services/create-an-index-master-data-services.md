---
title: Créer un index
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a18de9c33def5b0603f4460f87e7c5589ead4521
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728424"
---
# <a name="create-an-index-master-data-services"></a>Créer un index (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Créez un index personnalisé sur une liste d’attributs que vous interrogez fréquemment, afin d’améliorer les performances des requêtes.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Administration de système. Pour plus d’informations, consultez [autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 **Pour créer un index**  
  
1.  Dans Master Data Manager, cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la **grille** de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un index.  
  
4.  Cliquez sur **Index**.  
  
5.  Dans la zone **Nom** , indiquez le nom de l’index.  
  
6.  Sélectionnez **Est unique** si vous souhaitez créer un index unique. Pour plus d’informations sur les types d’index, consultez [Index personnalisé &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
  
7.  Cliquez sur les attributs dans la zone **Attributs disponibles** , puis sur la flèche **Ajouter** . Pour ajouter tous les attributs, cliquez sur la flèche **Ajouter tout** .  
  
8.  Cliquez sur **Enregistrer**.  
  
 Pour chaque index créé, une ligne avec quatre colonnes est ajoutée dans la grille. Le tableau suivant décrit les colonnes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|Statut|État de l’index.<br /><br /> Lorsque vous cliquez sur **Enregistrer**, l’image ![icône d’état de mise à jour](../master-data-services/media/mds-statusicon-updating.png "Icône de mise à jour de l’État") s’affiche, indiquant que l’index est en état de mise à jour.<br /><br /> Si des erreurs se produisent lors de la création ou de la modification d’un index, l’image ![icône d’état d’erreur](../master-data-services/media/mds-statusicon-error.png "Icône d’état d’erreur") s’affiche.<br /><br /> Dans le cas contraire, l’État est OK et l’image ![icône d’état OK](../master-data-services/media/mds-statusicon-ok.png "Icône d’état OK") s’affiche.|  
|Name|Nom de l'index.|  
|Est unique|Indique si l’index est unique.|  
|Sur les attributs|Affiche les noms complets des attributs sur lesquels l’index est défini.|  
  
 Lorsque vous cliquez sur un index, les informations suivantes s'affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’index.  
  
-   Le : date et heure **de**création de l’index.  
  
-   **Mise à jour par**: nom de l’utilisateur qui a effectué la dernière mise à jour de l’index.  
  
-   Le : date et heure **de**la dernière mise à jour de l’index.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Modifier et supprimer un index &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Master Data Services de &#40;d’index personnalisé&#41;](../master-data-services/custom-index-master-data-services.md)  
  
  
