---
title: Supprimer des utilisateurs ou des groupes (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0114aa3ca6f6744303c3053003a622185d33f547
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479900"
---
# <a name="delete-users-or-groups-master-data-services"></a>Supprimer des utilisateurs ou des groupes (Master Data Services)
  Vos pouvez supprimer des utilisateurs ou des groupes lorsque vous ne souhaitez plus qu'ils accèdent à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Notez le comportement suivant lors de la suppression d'utilisateurs et de groupes :  
  
-   Si vous supprimez un utilisateur qui est membre d’un groupe ayant accès à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], l’utilisateur peut toujours accéder à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] tant que vous ne le supprimez pas du groupe Active Directory ou du groupe local.  
  
-   Si vous supprimez un groupe, tous les utilisateurs de ce groupe qui ont accédé à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sont affichés dans la liste **Utilisateurs** tant que vous ne les supprimez pas.  
  
-   Les modifications apportées à la sécurité ne sont pas propagées à MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] pendant 20 minutes.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-users-or-groups"></a>Pour supprimer des utilisateurs ou des groupes  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Pour supprimer un utilisateur, restez dans la page **Utilisateurs** . Pour supprimer un groupe, dans la barre de menus, cliquez sur **Gérer les groupes**.  
  
3.  Dans la grille, sélectionnez la ligne correspondant à l’utilisateur ou au groupe à supprimer.  
  
4.  Cliquez sur **Supprimer l’utilisateur sélectionné** ou **Supprimer le groupe sélectionné**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;de sécurité Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)  
  
  
