---
title: Options (éditeur de texte-XML-page divers) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: eb3422b859ce4e58fc05564357876c5fe09fcdff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089207"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a>Options (Éditeur de texte - XML - Page Divers)

La boîte de dialogue **Options** vous permet de modifier les paramètres de saisie automatique et de schémas de l’Éditeur XML. Pour accéder à ces paramètres, dans le menu **Outils** , cliquez sur **Options**, développez le dossier **Éditeur de texte** , cliquez sur **XML** , puis sur **Divers** .  
  
## <a name="auto-insert"></a>Insertion automatique  
 **Balises de fermeture**  
 L'Éditeur de texte ajoute des balises de fin lors de la création d'éléments XML. Si la balise de début d'un élément est sélectionnée, l'Éditeur insère la balise de fin correspondante avec un préfixe d'espace de noms équivalent. Cette case à cocher est activée par défaut.  
  
 **Guillemets d'attribut**  
 Lors de la création d’attributs XML, l’Éditeur insère les caractères `="``"` et place le signe insertion (**^)** à l’intérieur des guillemets. Cette case à cocher est activée par défaut.  
  
 **Déclarations d’espaces de noms**  
 L'Éditeur insère automatiquement les déclarations d'espace de noms là où elles sont requises. Cette case à cocher est activée par défaut.  
  
 **Autre balisage (Commentaires, CDATA)**  
 Les éléments CDATA, DOCTYPE, les commentaires, les instructions de traitement et autre balisage sont entrés automatiquement. Cette case à cocher est activée par défaut.  
  
## <a name="network"></a>Réseau  
 **Télécharger automatiquement les DTD et les schémas**  
 Les schémas et les définitions de type de document (DTD) sont automatiquement téléchargés à partir d'emplacements HTTP. Cette fonctionnalité utilise System.Net avec détection de serveur de proxy automatique. Cette case à cocher est activée par défaut.  
  
## <a name="outlining"></a>Mode Plan  
 **Passer en mode Plan à l'ouverture des fichiers**  
 Active la fonctionnalité mode Plan lorsqu'un fichier est ouvert. Cette case à cocher est activée par défaut.  
  
## <a name="caching"></a>Mise en cache  
 **Schémas**  
 Indique l'emplacement du cache des schémas. Le bouton Parcourir (...) ouvre l'emplacement actuel du cache des schémas dans une nouvelle fenêtre. L’emplacement par défaut est * \<Management Studio répertoire d’installation>* \Xml\Schemas.  
