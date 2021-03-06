---
title: Mots réservés (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5435c2a48417156abd6d4f831bf61c9ba6440fab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482577"
---
# <a name="reserved-words-master-data-services"></a>Mots réservés (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lorsque vous créez des objets de modèle ou des membres, certains mots ne peuvent pas être utilisés. Ces mots peuvent provoquer des erreurs.  
  
> [!NOTE]  
>  Vous devez également limiter votre utilisation des caractères spéciaux (symboles, césure, etc.).  
  
-   [Modèles](#models)  
  
-   [Entités](#entities)  
  
-   [Hiérarchies explicites](#exhierarchies)  
  
-   [Attributs](#attributes)  
  
-   [Membres](#members)  
  
##  <a name="models"></a>Axisymétriques  
 Si vous créez un modèle dont le nom est défini sur **nom**, ne sélectionnez pas **créer une entité portant le même nom que le modèle** , car le nom ne peut pas être utilisé pour le nom d’une entité. ****  
  
##  <a name="entities"></a>Lesquelles  
 Pour les noms d'entité, vous ne pouvez pas utiliser **Name** ou **Code**.  
  
##  <a name="exhierarchies"></a>Hiérarchies explicites  
 Pour les noms de hiérarchies explicites, vous ne pouvez pas utiliser **Name** ou **Code**.  
  
##  <a name="attributes"></a>Attributs  
  
-   **IDENTIFI**  
  
-   **Code**  
  
-   **Nom**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a>Membres  
 Pour les membres, vous ne pouvez pas utiliser **MDMMemberStatus** ou **root** pour la valeur de l’attribut **code** .  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble de Master Data Services](master-data-services-overview-mds.md)  
  
  
