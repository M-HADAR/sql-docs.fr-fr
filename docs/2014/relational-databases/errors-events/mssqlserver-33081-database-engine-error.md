---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 913be11caa9a76ee012571e5ee4b275826668330
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62868583"
---
# <a name="mssqlserver_33081"></a>MSSQLSERVER_33081
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|33081|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Texte du message|Impossible de charger le fournisseur de services de chiffrement '%.*ls' en raison d'une signature Authenticode non valide ou d'un chemin d'accès non valide.  Recherchez d'autres défaillances dans les messages précédents.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu charger le fournisseur de services de chiffrement répertorié dans le message d’erreur. Il existe plusieurs échecs d'API Windows susceptibles de provoquer cette erreur. La mémoire tampon en anneau contient le nom de l'API qui a échoué et le code d'erreur windows retourné par l'API. Pour obtenir plus d’informations, interrogez la vue sys.dm_os_ring_buffers en utilisant la requête suivante.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour examiner le problème, recherchez le code d’erreur Windows dans MSDN (https://msdn.microsoft.com/). Résolvez l'erreur, ou contactez le support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour plus d'informations. Si vous devez contacter les services de support technique, collectez les informations suivantes pour notre équipe d'assistance :  
  
-   Le journal des erreurs affichant l'erreur qui indique que le fournisseur de services de chiffrement n'a pas pu être chargé.  
  
-   La sortie à partir de l'instruction ci-dessous :  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  Essayez de collecter des informations de mémoire tampon en anneau rapidement, car les informations de mémoire tampon en anneau peuvent être perdues lors d'un redémarrage.  
  
  
