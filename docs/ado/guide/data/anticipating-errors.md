---
title: Anticipation des erreurs | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d92d96e3b8cdfea5cacea35d852e8859de65dbd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925986"
---
# <a name="anticipating-errors"></a>Anticipation des erreurs
La prévention des erreurs est au moins aussi importante que la gestion des erreurs. Cette dernière section contient une liste succincte des précautions que votre application peut prendre pour aider à rendre les erreurs moins susceptibles de se produire.  
  
 Vérifiez l’état des objets en vérifiant la valeur dans la propriété **État** avant d’essayer d’effectuer une opération à l’aide de ces objets. Par exemple, si votre application utilise une **connexion**globale, vérifiez sa propriété **State** pour voir si elle est déjà ouverte avant d’appeler la méthode **Open** .  
  
-   Tout programme qui accepte les données d’un utilisateur doit inclure du code pour valider ces données avant de les envoyer au magasin de données. Vous ne pouvez pas compter sur le magasin de données, le fournisseur, ADO ou même votre langage de programmation pour vous avertir des problèmes. Vous devez vérifier chaque octet entré par vos utilisateurs, en vous assurant que les données sont de type correct pour le champ et que les champs obligatoires ne sont pas vides.  
  
 Vérifiez les données avant d’essayer d’écrire des données dans le magasin de données. Le moyen le plus simple consiste à gérer l’événement **WillMove** ou l’événement **WillUpdateRecordset** . Pour une description plus complète de la gestion des événements ADO, consultez [gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md).  
  
 Assurez-vous que les objets **Recordset** ne sont pas au-delà des limites du **Recordset** avant de tenter de déplacer le pointeur d’enregistrement. Si vous essayez d’utiliser **MoveNext** lorsque **EOF** a la valeur true ou **MovePrev** lorsque **BOF** a la valeur true, une erreur se produit. Si vous effectuez l’une des méthodes **Move** quand les paramètres **EOF** et **BOF** ont la valeur true, une erreur est générée.  
  
 Des erreurs se produisent également si vous essayez d’effectuer des opérations telles que **Seek** et **Find** sur un **jeu d’enregistrements**vide.
