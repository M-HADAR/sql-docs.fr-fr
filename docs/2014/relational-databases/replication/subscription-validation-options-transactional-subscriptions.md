---
title: Options de validation d’abonnement (abonnements transactionnels) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a82e13202209121897a5e5878a141c8d53800a47
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62745420"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Options de validation d'abonnement (abonnements transactionnels)
  Utilisez la boîte de dialogue **Options de validation d'abonnement** pour spécifier si la validation doit utiliser uniquement un nombre de lignes ou un nombre de lignes et une somme de contrôle binaire.  
  
## <a name="options"></a>Options  
 **Vérifiez si l'abonné possède le même nombre de lignes de données répliquées que le serveur de publication**  
 Sélectionnez le type de validation du nombre de lignes à effectuer. Pour les publications Oracle, la seule option proposée est **Calculer le nombre réel de lignes en interrogeant directement les tables**.  
  
 **Comparer les sommes de contrôle pour vérifier les données de ligne**  
 Outre le comptage des lignes sur le serveur de publication et sur l'Abonné, une somme de contrôle de toutes les données est calculée à l'aide de l'algorithme de somme de contrôle binaire. Si le nombre de lignes est erroné, la somme de contrôle n'est pas effectuée.  
  
 **Arrêter l'Agent de distribution une fois la validation terminée**  
 Par défaut, l'Agent de distribution s'exécute en permanence. Sélectionnez cette option pour arrêter l'agent lorsque la validation est terminée. Cela permet de vérifier que la validation a réussi avant de continuer à répliquer des données vers l'Abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider des données sur l’abonné](validate-data-at-the-subscriber.md)   
 [Valider des données répliquées](validate-data-at-the-subscriber.md)  
  
  
