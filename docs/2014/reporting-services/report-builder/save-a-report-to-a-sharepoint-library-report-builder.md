---
title: Enregistrer un rapport dans une bibliothèque SharePoint (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ab4f9b06758d29ff1f988f37b95ce92206f34d39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107675"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>Enregistrer un rapport dans une bibliothèque SharePoint (Générateur de rapports)
  Pour enregistrer un rapport sur un serveur de rapports configuré pour une intégration SharePoint, vous devez accéder au serveur SharePoint et établir une connexion au serveur de rapports. Dans la définition de rapport, toutes les références aux éléments associés au rapport doivent utiliser des valeurs spécifiques à un serveur de rapports SharePoint. Les éléments associés peuvent consister en des sous-rapports, des rapports d'extraction et des ressources telles que des images Web. Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Vous devez avoir l’autorisation de **Membre** ou de **Propriétaire** sur le site SharePoint pour définir les propriétés du projet.  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>Pour enregistrer un rapport sur un site SharePoint  
  
1.  À partir du bouton Générateur de rapports, cliquez sur **Enregistrer**. La boîte de dialogue **Enregistrer sous** _\<élément de rapport>_ s’affiche.  
  
    > [!NOTE]  
    >  Si vous réenregistrez un rapport, il est automatiquement stocké à son emplacement précédent. Utilisez l’option **Enregistrer sous** pour modifier l’emplacement.  
  
2.  Cliquez éventuellement sur **Sites et serveurs récents** pour afficher une liste de serveurs de rapports et de sites SharePoint récemment utilisés.  
  
3.  Accédez au site SharePoint, puis cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Si vous n'enregistrez pas un rapport ayant subi des modifications dans un délai de 10 heures, il est déconnecté du serveur sans être enregistré. Dans ce cas, dans la barre d’état inférieure droite, cliquez sur **Déconnecter**, puis sur **Connecter**. Le serveur le plus récent figurera dans la liste des serveurs disponibles. Sélectionnez-le pour que le rapport soit à nouveau connecté.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
