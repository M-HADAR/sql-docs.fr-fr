---
title: Caractéristiques d’exécution des procédures stockées étendues
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 74ecd20f28e58e133b5710d3cbd9d18b27ca7756
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095989"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Caractéristiques d'exécution des procédures stockées étendues
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 L'exécution d'une procédure stockée étendue présente les caractéristiques suivantes :  
  
-   La fonction de procédure stockée étendue est exécutée dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]contexte de sécurité de.  
  
-   La fonction de procédure stockée étendue s'exécute dans l'espace de processus de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Le thread associé à l'exécution de la procédure stockée étendue est le même que celui utilisé pour la connexion cliente.  
  
    > [!IMPORTANT]  
    >  Avant d'ajouter des procédures stockées étendues au serveur et d'octroyer à d'autres utilisateurs l'autorisation de les exécuter, il est conseillé à l'administrateur système de revoir chaque procédure stockée étendue afin de s'assurer qu'elle n'intègre aucun code nuisible ou malveillant.  
  
-  
  
 Une fois la DLL de procédure stockée étendue chargée, la DLL reste chargée dans l’espace d’adressage du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur jusqu’à ce qu’elle soit arrêtée ou l’administrateur décharge explicitement la dll à l’aide de DBCC *DLL_name* (Free).  
  
 La procédure stockée étendue peut être exécutée à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] comme procédure stockée à l'aide de l'instruction EXECUTE :  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Paramètres  
 \@*retVal*  
 Valeur de retour.  
  
 \@*param1*  
 Paramètre d'entrée.  
  
 \@*param2*  
 Paramètre d'entrée/sortie.  
  
> [!CAUTION]  
>  Les procédures stockées étendues offrent une amélioration des performances et étendent les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, comme la DLL de procédure stockée étendue et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partagent le même espace d'adressage, une procédure problématique peut affecter le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de façon défavorable. Bien que les exceptions levées par la DLL de procédure stockée étendue soient gérées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est possible d'endommager les zones de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. À titre de mesure de sécurité, seuls les administrateurs systèmes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent ajouter des procédures stockées étendues à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces procédures doivent être testées entièrement avant d'être installées.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de procédures stockées étendues](../../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)   
 [Interrogation des procédures stockées étendues installées dans SQL Server](../../relational-databases/extended-stored-procedures-programming/querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
