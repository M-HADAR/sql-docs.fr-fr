---
title: Modifier le compte d’administrateur système (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 911bd20c7d232bca52fdf9dca294bd7a4924d984
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054138"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Modifier le compte de l'administrateur système (Master Data Services)
  Vous pouvez modifier le compte d’utilisateur désigné comme administrateur [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] système.  
  
> [!WARNING]  
>  Une fois cette procédure terminée, le compte d'administrateur système précédent est supprimé.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez ajouter le nom d'utilisateur du nouvel administrateur à la liste d'utilisateurs de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Pour plus d’informations, consultez [Ajouter un utilisateur &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   Vous devez avoir l'autorisation d'afficher mdm.tblUse et d'exécuter la procédure stockée mdm.udpSecurityMemberProcessRebuildModel dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Pour plus d’informations, consultez [Sécurité de l’objet de base de données &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>Pour modifier le compte d'administrateur  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Dans MDM. tblUser, recherchez l’utilisateur qui sera le nouvel administrateur et copiez la valeur dans la `SID` colonne.  
  
3.  Créez une requête.  
  
4.  Tapez le texte suivant, en remplaçant *Domain \ user_name* par le nom d’utilisateur et le *sid* du nouvel administrateur par la valeur que vous avez copiée à l’étape 2.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Exécute la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
