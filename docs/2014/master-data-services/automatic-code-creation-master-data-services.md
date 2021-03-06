---
title: Création automatique de code (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7ee7e06829f72ab44fd036766907be94c95b7d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483692"
---
# <a name="automatic-code-creation-master-data-services"></a>Création automatique de code (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez générer automatiquement des valeurs numériques pour l'attribut Code, ou pour toute autre attribut numérique. Lorsque vous générez les codes automatiquement, rien n'empêche de saisir d'autres valeurs pour les codes ; sinon, une valeur initiale est définie automatiquement.  
  
## <a name="generating-code-values"></a>Génération de valeurs de code  
 Les administrateurs peuvent configurer des valeurs générées automatiquement pour l’attribut Code en modifiant les propriétés de l’entité associée. Ils peuvent spécifier une valeur initiale, et chaque valeur suivante est augmentée d'une unité.  
  
 Lorsque vous entrez des valeurs Code dans MDS, dans l'un des outils ou à l'aide du processus de site, vous pouvez laisser la valeur Code vide pour qu'elle soit générée automatiquement. Ou vous pouvez spécifier une valeur de code de votre choix.  
  
## <a name="generating-other-attribute-values"></a>Génération d'autres valeurs d'attribut  
 Les administrateurs peuvent générer automatiquement des valeurs pour les attributs autres que le code en créant des règles d'entreprise. Ils peuvent spécifier une valeur initiale, puis le nombre avec lequel chaque valeur suivante est incrémentée.  
  
 Lorsque vous entrez des valeurs d'attribut dans MDS, dans l'un des outils ou à l'aide du processus de site, vous pouvez laisser les valeurs d'attribut vides. Lorsque les règles d'entreprise sont appliquées, les valeurs seront incrémentées en fonction de la valeur existante la plus élevée. Par exemple, si votre règle est « Attribut par défaut avec une valeur générée qui commence à 1 et est incrémentée par 4 » et que la valeur courante la plus élevée pour l’attribut est 700, la valeur du membre suivant ajouté sera 704.  
  
## <a name="deleting-automatically-generated-values"></a>Suppression de valeurs générées automatiquement  
 Lorsqu'un administrateur active les valeurs générées automatiquement pour l'attribut Code, les utilisateurs peuvent supprimer par erreur un membre ayant une valeur Code qu'ils souhaitent réutiliser. Le message d’erreur « le code de membre est déjà utilisé par un membre qui a été supprimé » s’affiche. Il existe deux solutions possibles :  
  
-   Dans la zone fonctionnelle **gestion des versions** , un administrateur peut inverser la transaction qui s’est produite lors de la suppression du membre. Toutefois, cela signifie que tous les attributs et l’appartenance de l’ancien membre dans les hiérarchies et les collections sont restaurés. Pour plus d’informations, consultez [inverser une Transaction &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).  
  
-   Un administrateur peut utiliser le processus de site pour supprimer définitivement le membre. Pour plus d’informations, consultez [désactiver ou supprimer des membres à l’aide du processus de site &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Générez automatiquement les valeurs de l'attribut code.|[Générer automatiquement les valeurs d’attribut de code &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Générez automatiquement les valeurs des autres attributs.|[Générez automatiquement des valeurs d’attribut autres que code &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Vue d'ensemble de Master Data Services](master-data-services-overview-mds.md)  
  
-   [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Entités &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
  
