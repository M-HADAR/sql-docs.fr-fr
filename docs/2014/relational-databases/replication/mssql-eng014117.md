---
title: MSSQL_ENG014117 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a249f5536846507996da4a7478a32dbe68e4dcd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68811252"
---
# <a name="mssql_eng014117"></a>MSSQL_ENG014117
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14117|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|'%1!' n'est pas configuré comme base de données de distribution.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur peut se produire si une ou plusieurs des conditions suivantes sont vraies :  
  
-   L'entrée pour la base de données de distribution est manquante dans **msdb..MSdistributiondbs**.  
  
-   Il n'y a pas d'entrée pour le serveur local dans la base de données **master** , ou bien l'entrée qui s'y trouve n'est pas correcte.  
  
     La réplication requiert que tous les serveurs d'une topologie soient enregistrés avec le nom d'ordinateur et un nom d'instance facultatif (dans le cas d'une instance cluster, le nom du serveur virtuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le nom d'instance facultatif). Pour que la réplication fonctionne correctement, la valeur renvoyée par `SELECT @@SERVERNAME` pour chaque serveur de la topologie doit correspondre au nom d'ordinateur ou au nom de serveur virtuel avec le nom d'instance facultatif.  
  
     La réplication n'est pas prise en charge si vous avez inscrit une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par adresse IP ou par nom de domaine pleinement qualifié (FQDN). Si vous aviez une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inscrites par adresse IP ou par nom de domaine pleinement qualifié dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] quand vous avez configuré la réplication, cette erreur a pu se produire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que l'instance du serveur de distribution est inscrite correctement. Si le nom réseau de l'ordinateur et le nom de l'instance SQL Server diffèrent, effectuez une des actions suivantes :  
  
-   Ajoutez le nom de l'instance SQL Server comme nom réseau valide. Pour définir un autre nom réseau, une méthode possible consiste à l'ajouter au fichier hosts local. Le fichier hosts local est installé par défaut dans le répertoire WINDOWS\system32\drivers\etc ou WINNT\system32\drivers\etc. Pour plus d'informations, reportez-vous à la documentation Windows.  
  
     Si, par exemple, le nom d'ordinateur est comp1, l'adresse IP de l'ordinateur 10.193.17.129 et le nom de l'instance inst1/nominst, ajoutez l'entrée suivante au fichier des hôtes :  
  
     10.193.17.129 inst1  
  
-   Désactivez la distribution, inscrivez l'instance puis réactivez la distribution. Si la valeur de @@SERVERNAME n’est pas correcte pour une instance non-cluster, effectuez les étapes suivantes :  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     Après avoir exécuté la procédure stockée [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), vous devez redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que la modification apportée à @@SERVERNAME soit prise en compte.  
  
     Si la valeur de @@SERVERNAME n’est pas correcte pour une instance cluster, vous devez changer le nom à l’aide de l’administrateur de cluster. Pour plus d’informations, consultez [Instances de cluster de basculement AlwaysOn (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
 Après avoir vérifié que l'instance du serveur de distribution est inscrite correctement, vérifiez que la base de données de distribution figure dans **msdb..MSdistributiondbs**. Si elle ne s'y trouve pas :  
  
1.  Créez un script de la configuration de la distribution. Pour plus d'informations, voir [Scripting Replication](scripting-replication.md).  
  
2.  Désactivez la distribution puis réactivez-la. Pour plus d'informations, voir [Configure Distribution](configure-distribution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
