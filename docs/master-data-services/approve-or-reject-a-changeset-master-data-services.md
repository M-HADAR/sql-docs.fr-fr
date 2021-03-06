---
title: Approuver ou rejeter un ensemble de modifications
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 45bd01f9-ae15-4fc5-a2ba-eee565a26ef8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 401983aa2e5094560f7bcc852c839986ffe4234d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728773"
---
# <a name="approve-or-reject-a-changeset-master-data-services"></a>Approuver ou rejeter un ensemble de modifications (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Un ensemble de modifications regroupe des modifications en attente, qui portent sur les données de référence. Si des modifications de l’entité requièrent l’approbation d’un administrateur et si un ensemble de modifications est soumis pour approbation, vous pouvez examiner puis approuver ou rejeter cet ensemble de modifications.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** . Pour plus d’informations, consultez [autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez disposer d’une autorisation administrateur pour l’entité.  
  
-   Les modifications de l’entité nécessitent l’approbation d’un administrateur.  
  
-   Si l’état de l’ensemble de modifications est en attente, vous pouvez examiner puis approuver ou rejeter cet ensemble de modifications.  
  
-   Les utilisateurs ne sont pas autorisés à approuver leurs propres modifications. Si vous êtes l’administrateur de l’entité, vous devez affecter un administrateur secondaire qui approuvera votre propre ensemble de modifications.  
  
## <a name="to-approve-or-reject-a-changeset"></a>Pour approuver ou rejeter un ensemble de modifications  
  
1.  Sur la [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] page d’hébergement, sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Dans le menu **Entités** , cliquez sur une entité.  
  
3.  Dans le volet droit, sélectionnez **Ensembles de modifications** , puis double-cliquez sur l’ensemble de modifications à approuver ou à rejeter.  
  
4.  Cliquez sur **Appliquer** pour appliquer l’ensemble de modifications et vérifier les modifications en attente.  
  
5.  Cliquez sur **Rejeter** pour rejeter l’ensemble de modifications et le renvoyer au propriétaire.  
  
6.  Cliquez sur **Approuver** pour approuver l’ensemble de modifications. L’ensemble de modifications est automatiquement validé.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Appliquer et mettre à jour un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Valider ou envoyer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
  
