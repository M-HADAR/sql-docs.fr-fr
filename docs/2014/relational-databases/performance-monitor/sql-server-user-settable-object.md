---
title: Objet SQL Server User Settable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5ac802569356979f3a01da4c204a80272c2be43a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63151089"
---
# <a name="sql-server-user-settable-object"></a>Objet SQL Server User Settable
  L’objet **définissable** par l’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans Microsoft vous permet de créer des instances de compteur personnalisées. La création de vos propres instances de compteurs est utile pour surveiller les aspects du serveur qui ne le sont pas par les compteurs existants, comme les composants propres à votre base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (par exemple, la détermination du nombre de commandes clients enregistrées ou l'inventaire des produits).  
  
 L’objet **User Settable** contient 10 instances du compteur de requêtes : du **Compte utilisateur 1** au **Compte utilisateur 10**. Ces compteurs correspondent aux procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sp_user_counter1** à **sp_user_counter10**. Comme ces procédures stockées sont exécutées par les applications de l'utilisateur, les valeurs définies par les procédures stockées sont affichées dans le Moniteur système. Un compteur peut surveiller toute valeur entière (par exemple une procédure stockée qui compte combien de fois un produit en particulier a été commandé en un jour).  
  
> [!NOTE]  
>  Les procédures stockées des compteurs utilisateur ne sont pas automatiquement interrogées par le Moniteur système. Pour que les valeurs d'un compteur soient mises à jour, les procédures doivent être explicitement exécutées par une application de l'utilisateur. Utilisez un déclencheur pour mettre automatiquement à jour la valeur du compteur. Par exemple, pour créer un compteur qui surveille le nombre de lignes d'une table, créez un déclencheur INSERT et DELETE sur la table qui exécute l'instruction suivante : `SELECT COUNT(*) FROM table`. Dès que le déclencheur est activé à la suite de l'exécution d'une opération INSERT ou DELETE sur la table, le compteur du Moniteur système est automatiquement mis à jour.  
  
 Le tableau décrit l’objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** .  
  
|Compteurs SQL Server User Settable|Description|  
|---------------------------------------|-----------------|  
|**Requête**|L’objet **User Settable** contient le compteur de requêtes. Les utilisateurs configurent les **compteurs utilisateur** dans l’objet de requête.|  
  
 Le tableau décrit les **instances** du compteur de **requêtes** .  
  
|Instances du compteur de requêtes|Description|  
|-----------------------------|-----------------|  
|**Compteur utilisateur 1**|Défini à l’aide de **sp_user_counter1**.|  
|**Compteur utilisateur 2**|Défini à l’aide de **sp_user_counter2**.|  
|**Compteur utilisateur 3**|Défini à l’aide de **sp_user_counter3**.|  
|...||  
|**Compteur utilisateur 10**|Défini à l’aide de **sp_user_counter10**.|  
  
 Pour utiliser les procédures stockées du compteur utilisateur, exécutez-les à partir de votre propre application avec un seul paramètre entier qui représente la nouvelle valeur prise par le compteur. Par exemple, pour faire passer le **compteur utilisateur 1** à la valeur 10, exécutez cette instruction Transact-SQL :  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 Les procédures stockées du compteur utilisateur peuvent être appelées à partir de tout endroit où les autres procédures stockées peuvent être appelées, par exemple vos propres procédures stockées. Par exemple, vous pouvez créer la procédure stockée suivante pour compter le nombre de connexions et de tentatives de connexions qui ont eu lieu depuis qu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été lancée :  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 La fonction @@CONNECTIONS retourne le nombre de connexions ou de tentatives de connexion depuis qu’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été lancée. Cette valeur est transférée comme paramètre à la procédure stockée **sp_user_counter1** .  
  
> [!IMPORTANT]  
>  Les requêtes définies dans les procédures stockées du compteur utilisateur doivent être aussi simples que possible. Les requêtes sollicitant beaucoup de mémoire, comme les requêtes de tri ou de hachage, ou celles qui impliquent des volumes importants d'E/S sont d'une exécution coûteuse en ressources et peuvent affecter les performances.  
  
## <a name="permissions"></a>Autorisations  
 **sp_user_counter** est disponible pour tous les utilisateurs, mais peut être restreint pour n’importe quel compteur de requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
