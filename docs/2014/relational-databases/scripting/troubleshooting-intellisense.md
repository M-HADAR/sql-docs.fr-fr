---
title: Résolution des problèmes liés à IntelliSense
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7088bee1d78efdc6051bf58d174b7ea503362831
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75242979"
---
# <a name="troubleshooting-intellisense-sql-server-management-studio"></a>Résolution des problèmes liés à IntelliSense (SQL Server Management Studio)
  Dans certains cas, les options IntelliSense ne fonctionneront peut-être pas comme vous l'attendez. Ces cas sont les suivants :  
  
## <a name="conditions-that-affect-intellisense"></a>Conditions qui affectent IntelliSense  
 Les conditions suivantes peuvent affecter le comportement d'IntelliSense :  
  
-   Il y a une erreur de codage au-dessus du curseur.  
  
     S'il existe une instruction incomplète ou une autre erreur de codage au-dessus du point d'insertion, IntelliSense ne peut pas analyser les éléments de code et par conséquent ne peut pas fonctionner. Pour réactiver IntelliSense, mettez en commentaire le code concerné.  
  
-   Le point d'insertion est à l'intérieur d'un commentaire de code.  
  
     Les options IntelliSense ne sont pas disponibles si le point d'insertion se trouve dans un commentaire de votre fichier source.  
  
-   Le point d'insertion est à l'intérieur d'un littéral de chaîne.  
  
     Les options IntelliSense ne sont pas disponibles si le point d'insertion se trouve à l'intérieur des guillemets entourant un littéral de chaîne, comme dans l'exemple suivant :  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   Les options automatiques ne sont pas activées.  
  
     La plupart des fonctionnalités IntelliSense fonctionnent automatiquement par défaut. Vous pouvez toutefois désactiver n'importe quelle fonctionnalité.  
  
     Même si l'option qui permet de compléter automatiquement les instructions est désactivée, vous pouvez utiliser une fonctionnalité IntelliSense. Pour plus d’informations, consultez [Configurer IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).  
  
## <a name="database-engine-query-intellisense"></a>Requête de moteur de base de données IntelliSense  
 Les problèmes suivants s’appliquent à l’éditeur de requête du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] :  
  
-   La fonctionnalité IntelliSense de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne prend pas en charge tous les éléments de la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] . L'aide sur les paramètres ne prend pas en charge les paramètres dans certains objets, tels que les procédures stockées étendues. Pour plus d’informations, consultez [Syntaxe Transact-SQL prise en charge par IntelliSense](transact-sql-syntax-supported-by-intellisense.md).  
  
-   IntelliSense n’est disponible que si l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est connecté à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure. IntelliSense n’est pas disponible quand l’éditeur de requête est connecté à des versions antérieures du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   IntelliSense est désactivé dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] quand le mode SQLCMD est activé.  
  
-   Les fonctionnalités IntelliSense ne couvrent pas les objets de base de données créés par une autre connexion après que votre fenêtre d'éditeur s'est connectée à la base de données. Si des objets sont absents dans les fonctionnalités IntelliSense telles que les listes de saisie semi-automatique, vous pouvez choisir l'un de ces trois mécanismes pour actualiser le cache d'objets pour votre fenêtre d'éditeur :  
  
    -   Sélectionnez le menu **Edition** , sélectionnez **IntelliSense**, puis **Actualiser le cache local**.  
  
    -   Utilisez le raccourci clavier CTRL+MAJ+R.  
  
    -   Déconnectez la fenêtre d’éditeur de l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , puis reconnectez-la.  
  
-   Les listes de saisie semi-automatique n'incluent pas les objets de base de données pour lesquels vous n'avez pas d'autorisations. IntelliSense signale les références aux objets pour lesquels vous disposez d'autorisations. Par exemple, si vous ouvrez un script écrit par un autre utilisateur, toute référence à un objet pour lequel cette personne dispose d'autorisations, contrairement à vous, est signalée comme incorrecte.  
  
-   Les listes de saisie semi-automatique peuvent cesser de fonctionner si vous perdez la connexion à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Rétablissez la connexion à l'instance.  
  
  
