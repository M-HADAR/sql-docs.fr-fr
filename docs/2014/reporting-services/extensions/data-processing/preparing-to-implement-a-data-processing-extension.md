---
title: Préparation à l’implémentation d’une extension pour le traitement des données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- data processing extensions [Reporting Services], implementing
ms.assetid: 698817e4-33da-4eb5-9407-4103e1c35247
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3343823399b0500e0a329e160e5545d4dd372a54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63165028"
---
# <a name="preparing-to-implement-a-data-processing-extension"></a>Préparation à l'implémentation d'une extension pour le traitement des données
  Avant d’implémenter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] votre extension pour le traitement des données, vous devez définir les interfaces à implémenter. Vous pouvez fournir des implémentations spécifiques aux extensions du jeu d’interfaces complet, ou concentrer simplement votre implémentation sur un sous-ensemble, tel que les interfaces <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> et <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> dans lesquelles les clients interagissent essentiellement avec un jeu de résultats comme un objet **DataReader** et utilisent votre extension pour le traitement des données [!INCLUDE[ssRS](../../../includes/ssrs.md)] comme un pont entre le jeu de résultats et votre source de données.  
  
 Vous pouvez implémenter des extensions pour le traitement des données selon l'une des deux manières suivantes :  
  
-   Vos classes d’extension pour le traitement des [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] données peuvent implémenter les interfaces de fournisseur de données et éventuellement les interfaces [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]d’extension pour le traitement des données étendues fournies par.  
  
-   Vos classes d'extension pour le traitement des données peuvent implémenter les interfaces d'extension pour le traitement des données fournies par [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et, le cas échéant, les interfaces d'extension pour le traitement des données étendues.  
  
 Si votre extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ne prend pas en charge une propriété ou méthode particulière, implémentez la propriété ou la méthode comme une non opération. Si un client attend un comportement particulier, levez une exception **NotSupportedException**.  
  
> [!NOTE]  
>  L' implémentation d'une propriété ou méthode sous la forme d'une non opération est limitée aux propriétés et méthodes des interfaces que vous choisissez d'implémenter. Les interfaces que vous choisissez éventuellement de ne pas implémenter doivent être ignorées par votre assembly d'extension pour le traitement des données. Pour plus d'informations sur l'utilisation nécessaire ou facultative d'une interface, consultez le tableau plus loin dans cette section.  
  
## <a name="required-extension-functionality"></a>Fonctionnalités d'extension requises  
 Chaque extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] doit fournir les fonctionnalités suivantes :  
  
-   Ouvrir une connexion à une source de données.  
  
-   Analyser une requête et renvoyer une liste de noms de champs pour le jeu de résultats.  
  
-   Exécuter une requête avec la source de données et renvoyer un ensemble de lignes.  
  
-   Passer des paramètres à valeur unique à la requête.  
  
-   Effectuer une itération dans les lignes de l'ensemble de lignes et récupérer des données.  
  
 Chaque extension pour le traitement des données peut être étendue pour inclure les fonctionnalités suivantes :  
  
-   Analyser une requête et retourner la liste des noms de paramètres utilisés dans la requête.  
  
-   Analyser une requête et retourner la liste des champs selon lesquels la requête est groupée.  
  
-   Analyser une requête et retourner la liste des champs selon lesquels la requête est triée.  
  
-   Fournir un nom d'utilisateur et un mot de passe pour se connecter à la source de données qui est indépendante de la chaîne de connexion.  
  
-   Effectuer une itération dans les lignes de l'ensemble de lignes et extraire les métadonnées auxiliaires relatives aux valeurs de données.  
  
-   Effectuer l'agrégation de données sur le serveur.  
  
## <a name="available-extension-interfaces"></a>Interfaces d'extension disponibles  
 Le tableau suivant décrit les interfaces disponibles et indique si l'implémentation est requise ou facultative.  
  
|Interface|Description|Implémentation|  
|---------------|-----------------|--------------------|  
|IDbConnection|Représente une session unique avec une source de données. Dans le cas d'un système de base de données client/serveur, il peut s'agir d'une connexion réseau au serveur.|Obligatoire|  
|IDbConnectionExtension|Représente des propriétés de connexion supplémentaires qui peuvent être implémentées par les extensions pour le traitement des données [!INCLUDE[ssRS](../../../includes/ssrs.md)] relatives à la sécurité et l'authentification.|Facultatif|  
|IDbTransaction|Représente une transaction locale.|Obligatoire|  
|IDbTransactionExtension|Représente des propriétés de transaction supplémentaires qui peuvent être implémentées par les extensions pour le traitement des données [!INCLUDE[ssRS](../../../includes/ssrs.md)].|Facultatif|  
|IDbCommand|Représente une requête ou commande utilisée pour une connexion à une source de données.|Obligatoire|  
|IDbCommandAnalysis|Représente des informations de commande supplémentaires pour analyser une requête et renvoyer une liste de noms de paramètre utilisés dans la requête.|Facultatif|  
|IDataParameter|Représente un paramètre ou une paire nom/valeur passée à une commande ou requête.|Obligatoire|  
|IDataParameterCollection|Représente une collection de tous les paramètres pertinents à une commande ou requête.|Obligatoire|  
|IDataReader|Fournit une méthode de lecture d'un flux de lignes de données avant uniquement et en lecture seule à partir d'une source de données.|Obligatoire|  
|IDataReaderExtension|Fournit une méthode de lecture d'un ou plusieurs flux de données avant uniquement de jeux de résultats, obtenue par l'exécution d'une commande au niveau d'une source de données. Cette interface fournit une prise en charge supplémentaire pour les agrégats de champ.|Facultatif|  
|IExtension|Fournit la classe de base pour une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Elle permet aussi à un implémenteur d'inclure un nom localisé pour l'extension et de passer des paramètres de configuration du fichier de configuration à l'extension.|Obligatoire|  
  
 Les interfaces d'extension pour le traitement des données sont identiques à un sous-ensemble des interfaces, des méthodes et des propriétés du fournisseur de données [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] dans la mesure du possible. Pour plus d'informations sur l'implémentation d'un fournisseur de données [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] complet, consultez la rubrique sur l'implémentation d'un fournisseur de données .NET Framework dans votre documentation du Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Implémentation d’une extension pour le traitement des données](implementing-a-data-processing-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
