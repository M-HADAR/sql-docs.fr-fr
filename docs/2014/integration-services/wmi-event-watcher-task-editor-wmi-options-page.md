---
title: Éditeur de tâche Observateur d’événement WMI (page Options WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52ca90b38975c8db762ec0937b265a91b03c5cb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054380"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Éditeur de tâche Observateur d'événement WMI (page Options WMI)
  Utilisez la page **Options WMI** de la boîte de dialogue **Éditeur de tâche Observateur d'événement WMI** pour définir la source de la requête WQL (Windows Management Instrumentation Query Language) et le mode de réponse de la tâche Observateur d'événement WMI aux événements WMI (Microsoft Windows Instrumentation).  
  
 Pour en savoir plus sur cette tâche, consultez [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Pour plus d’informations sur le langage de requêtes WMI (WQL), consultez la rubrique [Requêtes avec WQL](https://go.microsoft.com/fwlink/?LinkId=79045)dans la documentation Windows Management Instrumentation de la bibliothèque MSDN.  
  
## <a name="static-options"></a>Options statiques  
 **WMIConnectionName**  
 Sélectionnez un gestionnaire de connexions WMI dans la liste ou cliquez sur \<**Nouvelle connexion WMI...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions WMI](connection-manager/wmi-connection-manager.md), [éditeur du gestionnaire de connexions WMI](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Sélectionnez le type de la source de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définit la source d'une requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
|**Connexion de fichiers**|Sélectionnez un fichier qui contient la requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
|**Variable**|Définit la source dans une variable qui définit la requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Indiquez si l’événement WMI consigne l’événement et lance l’action [!INCLUDE[ssIS](../includes/ssis-md.md)] , ou consigne uniquement l’événement.  
  
 **AfterEvent**  
 Indiquez si la tâche aboutit ou échoue lorsqu'elle reçoit l'événement WMI, ou si elle continue d'observer l'occurrence de l'événement.  
  
 **ActionAtTimeout**  
 Indiquez si la tâche consigne la temporisation d'une requête WMI et déclenche un événement [!INCLUDE[ssIS](../includes/ssis-md.md)] en réponse, ou si elle consigne uniquement la temporisation.  
  
 **AfterTimeout**  
 Indiquez si la tâche aboutit ou échoue en réponse à une temporisation, ou si elle continue d'observer l'occurrence d'une temporisation.  
  
 **NumberOfEvents**  
 Indiquez le nombre d'événements à observer.  
  
 **Délai d'expiration**  
 Indiquez le délai en secondes avant l'occurrence de l'événement. La valeur 0 indique qu'aucun délai n'a lieu.  
  
## <a name="wqlquerysource-dynamic-options"></a>Options dynamiques WQLQuerySource  
  
### <a name="wqlquerysource--direct-input"></a>WQLQuerySource = Entrée directe  
 **WQLQuerySource**  
 Fournissez une requête ou cliquez sur les points de suspension (...) et entrez une requête en utilisant la boîte de dialogue **Requête WQL**.  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = Connexion de fichiers  
 **WQLQuerySource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou \<cliquez sur **nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Variable  
 **WQLQuerySource**  
 Sélectionnez une variable dans la liste ou cliquez sur \< **nouvelle variable...**> pour créer une variable.  
  
 **Rubriques connexes :** [Integration Services &#40;les variables de&#41; SSIS](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche Observateur d’événement WMI &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Tâche Lecteur de données WMI](control-flow/wmi-data-reader-task.md)  
  
  
