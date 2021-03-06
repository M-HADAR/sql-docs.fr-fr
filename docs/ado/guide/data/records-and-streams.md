---
title: Enregistrements et flux | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO]
- streams [ADO], about streams
- records [ADO]
ms.assetid: 4d68868e-2611-4b5c-9a89-7caa5f753151
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4636df1451ba946b9a7bfb62e3d6775c35b1d6f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924496"
---
# <a name="records-and-streams"></a>Enregistrements et flux
ADO fournit actuellement l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) comme méthode principale d’accès aux informations dans des sources de données, telles que des bases de données relationnelles. Toutefois, certains fournisseurs prennent en charge les objets d' [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) et de [flux](../../../ado/reference/ado-api/stream-object-ado.md) en tant qu’autres ou objets complémentaires avec lesquels les données des fournisseurs peuvent être manipulées. Pour plus d’informations sur le comportement des **enregistrements** , consultez la documentation de votre fournisseur.  
  
## <a name="records"></a>Enregistrements  
 Les objets d' **enregistrement** fonctionnent essentiellement comme des **jeux d’enregistrements**à une seule ligne. Toutefois, les **enregistrements** ont des fonctionnalités limitées par rapport aux **recordsets** et leurs propriétés et méthodes sont différentes. La source des données dans un objet **Record** peut être une commande qui retourne une ligne de données du fournisseur. L’utilisation d’objets d' **enregistrement** plutôt que d’objets **Recordset** pour recevoir les résultats d’une requête qui retourne une ligne de données élimine la surcharge liée à l’instanciation de l’objet **Recordset** plus complexe.  
  
 Les objets d' **enregistrement** peuvent servir à un autre usage, en particulier avec les fournisseurs de sources de données autres que les bases de données relationnelles traditionnelles, telles que le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). La plupart des informations qui doivent être traitées existent, pas en tant que tables dans les bases de données, mais en tant que messages dans les systèmes de messagerie électronique et les fichiers des systèmes de fichiers modernes. Les objets d' **enregistrement** et de **flux** facilitent l’accès aux informations stockées dans des sources autres que des bases de données relationnelles.  
  
 L’objet **Record** peut représenter et gérer des données telles que des répertoires et des fichiers dans un système de fichiers ou des dossiers et des messages dans un système de messagerie. Dans ce cas, la source de l' **enregistrement** peut être la ligne actuelle d’un **jeu d’enregistrements**ouvert, une URL absolue ou une URL relative avec un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ouvert.  
  
 En règle générale, un **jeu d’enregistrements** peut être utilisé pour représenter un conteneur ou un parent dans une hiérarchie comme un dossier ou un répertoire. Un **enregistrement** peut être utilisé pour retourner des informations spécifiques sur un nœud dans le conteneur parent, tel qu’un fichier ou un document. Les **enregistrements** de raison principale sont utilisés pour représenter ce type d’informations : ces sources de données sont hétérogènes. Cela signifie que chaque **enregistrement** peut avoir un ensemble et un nombre de champs différents. Les **jeux d’enregistrements** traditionnels contenant des lignes d’une base de données sont homogènes, ce qui signifie que chaque ligne a le même nombre et le même type de champs.  
  
 Pour plus d’informations sur l’utilisation de l’objet **Record** pour le traitement de ces données hétérogènes à partir de fournisseurs tels que le fournisseur de publication Internet, consultez [utilisation d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
## <a name="streams"></a>Flux  
 L’objet de **flux** fournit les moyens de lire, d’écrire et de gérer un flux d’octets. Ce flux d’octets peut être de type texte ou binaire et sa taille est limitée uniquement par les ressources système. En règle générale, les objets ADO **Stream** sont utilisés aux fins suivantes :  
  
-   Pour contenir les données d’un **jeu d’enregistrements** enregistré au format XML. Ces flux XML de l' **objet Recordset**enregistré peuvent être utilisés comme source lors de l’ouverture d’un nouvel ensemble **d’enregistrements**. Pour plus d’informations, consultez [flux et persistance](../../../ado/guide/data/streams-and-persistence.md).  
  
-   Pour contenir les [CommandStreams](../../../ado/reference/ado-api/commandstream-property-ado.md) à exécuter sur le fournisseur comme alternative à [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md). Par exemple, codes XML peut être utilisé comme source pour une commande sur le fournisseur Microsoft OLE DB pour SQL Server.  
  
-   Pour recevoir les résultats du fournisseur dans un format autre qu’un **Recordset**, tel que les résultats XML du fournisseur Microsoft OLE DB pour SQL Server. Pour plus d’informations, consultez [récupération de jeux de résultats dans des flux](../../../ado/guide/data/retrieving-resultsets-into-streams.md).  
  
-   Pour contenir le texte ou les octets qui composent un fichier ou un message, généralement utilisé avec des fournisseurs tels que le fournisseur Microsoft OLE DB pour la publication Internet. Pour plus d’informations sur cette utilisation des objets de **flux** , consultez [utilisation d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md).  
  
 Un objet de **flux** peut être ouvert sur :  
  
-   Fichier simple spécifié avec une URL.  
  
-   Champ d’un **enregistrement** ou **d’un jeu d’enregistrements** contenant un objet de **flux** .  
  
-   Flux par défaut d’un **enregistrement** ou d’un objet **Recordset** représentant un répertoire ou un fichier composé.  
  
-   Champ de ressource contenant l’URL d’un fichier simple.  
  
-   Aucune source particulière. Dans ce cas, un objet de **flux** est ouvert en mémoire. Les données peuvent y être écrites, puis enregistrées dans un autre **flux** ou fichier.  
  
-   Champ BLOB dans un **Recordset**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Flux et persistance](../../../ado/guide/data/streams-and-persistence.md)  
  
-   [Flux de commandes](../../../ado/guide/data/command-streams.md)  
  
-   [Récupération de jeux de résultats dans les flux](../../../ado/guide/data/retrieving-resultsets-into-streams.md)  
  
-   [Utilisation d’ADO pour la publication Internet](../../../ado/guide/data/using-ado-for-internet-publishing.md)
