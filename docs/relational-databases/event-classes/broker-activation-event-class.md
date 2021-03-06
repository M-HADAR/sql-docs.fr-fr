---
title: Broker:Activation, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8ab23cd0328b2e20d25fc62aad128e4e408c918
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "67999813"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation, classe d'événement

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Activation** quand un moniteur de file d’attente démarre une procédure stockée d’activation, envoie une notification QUEUE_ACTIVATION, ou quand une procédure stockée d’activation démarrée par un moniteur de file d’attente se termine.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Colonnes de données de la classe d'événement Broker:Activation  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**int**|Type de classe d'événements capturée. Toujours **163** pour **Broker:Activation**.|27|Non|  
|**EventSequence**|**int**|Numéro de séquence de cet événement.|51|Non|  
|**EventSubClass**|**nvarchar**|Action spécifique que cet événement signale. L’une des valeurs suivantes :<br /><br /> **démarré**:   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a démarré une procédure stockée d’activation.<br /><br /> **terminé**:  la procédure stockée d’activation s’est terminée normalement.<br /><br /> **abandon**:   la procédure stockée d’activation a été interrompue suite à une erreur.|21|Non|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|**int**|Nombre de tâches actives dans cette file d'attente.|25|Non|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectID**|**int**|File d'attente associée à cet événement.|22|Non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SPID**|**int**|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|Non|  
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
