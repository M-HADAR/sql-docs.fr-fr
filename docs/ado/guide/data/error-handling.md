---
title: Gestion des erreurs | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cb3213b6a4c5711ccb8d6f9243047d8361a6e37
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925427"
---
# <a name="error-handling"></a>Gestion des erreurs
ADO utilise plusieurs méthodes différentes pour notifier une application des erreurs qui se produisent. Cette section décrit les types d’erreurs qui peuvent se produire lorsque vous utilisez ADO et comment votre application est notifiée. Il conclut en faisant des suggestions sur la façon de gérer ces erreurs.  
  
## <a name="how-does-ado-report-errors"></a>Comment ADO signale-t-il des erreurs ?  
 ADO vous avertit des erreurs de plusieurs façons :  
  
-   Les erreurs ADO génèrent une erreur au moment de l’exécution. Gérez une erreur ADO de la même façon que toute autre erreur d’exécution, telle que l’utilisation d’une instruction **On Error** dans Visual Basic.  
  
-   Votre programme peut recevoir des erreurs de OLE DB. Une erreur OLE DB génère également une erreur au moment de l’exécution.  
  
-   Si l’erreur est spécifique à votre fournisseur de données, un ou plusieurs objets d' **erreur** sont placés dans la collection d' **Erreurs** de l’objet de **connexion** qui a été utilisé pour accéder au magasin de données lorsque l’erreur s’est produite.  
  
-   Si le processus qui a déclenché un événement a également généré une erreur, les informations sur l’erreur sont placées dans un objet d' **erreur** et transmises en tant que paramètre à l’événement. Pour plus d’informations sur les événements, consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md) .  
  
-   Les problèmes qui se produisent lors du traitement des mises à jour par lots ou d’autres opérations en bloc impliquant un **Recordset** peuvent être indiqués par la propriété **Status** du **Recordset**. Par exemple, les violations de contrainte de schéma ou les autorisations insuffisantes peuvent être spécifiées par des valeurs **RecordStatusEnum** .  
  
-   Les problèmes qui se produisent lors de l’exécution d’un **champ** particulier dans l’enregistrement actif sont également indiqués par la propriété **Status** de chaque **champ** de la collection **Fields** de l' **enregistrement** ou du **Recordset**. Par exemple, les mises à jour qui n’ont pas pu être effectuées ou les types de données incompatibles peuvent être spécifiés par les valeurs **FieldStatusEnum** .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Erreurs ADO](../../../ado/guide/data/ado-errors.md)  
  
-   [Erreurs du fournisseur](../../../ado/guide/data/provider-errors.md)  
  
-   [Informations sur les erreurs liées aux champs](../../../ado/guide/data/field-related-error-information.md)  
  
-   [Informations sur les erreurs liées aux recordsets](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [Gestion des erreurs dans d’autres langages](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [Anticipation des erreurs](../../../ado/guide/data/anticipating-errors.md)
