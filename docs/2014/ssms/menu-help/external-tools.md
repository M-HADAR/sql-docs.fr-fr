---
title: Outils externes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- External Tools dialog box
ms.assetid: d7dae88f-0781-4162-96cd-d3a3a4d82035
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 264eb3c9b16c5eb12a578090d55e4f64884177c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62649691"
---
# <a name="external-tools"></a>Outils externes
  Utilisez cette boîte de dialogue pour ajouter des outils externes, tels que le Gestionnaire de configuration SQL Server ou le Bloc-notes, au menu **Outils** . L'ajout d'outils externes vous permet de lancer facilement d'autres applications tout en travaillant dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez spécifier des arguments et un répertoire de travail lors du lancement de l'outil. En outre, les sorties de certains outils peuvent être affichés dans la fenêtre de sortie. La boîte de dialogue **Outils externes** est accessible via le menu **Outils** .  
  
## <a name="options"></a>Options  
 **Contenu du menu**  
 Répertorie les titres des éléments ajoutés au menu **Outils** . Utilisez les flèches **Monter** et **Descendre** pour modifier l'ordre d'apparition des éléments dans le menu. Utilisez le bouton **Supprimer** pour supprimer un élément du menu.  
  
 **Monter**  
 Déplace l'outil sélectionné vers le haut de la liste des outils qui apparaissent dans le menu **Outils** .  
  
 **Descendre**  
 Déplace l'outil sélectionné vers le bas de la liste des outils qui apparaissent dans le menu **Outils** .  
  
 **Ajouter**  
 Vide les zones de texte pour que vous puissiez spécifier un nouvel outil.  
  
 **Supprimer**  
 Supprime l'outil ou la commande de la liste **Contenu du menu** , ainsi que du menu **Outils** .  
  
 **Titre**  
 Nom sous lequel l'outil ou la commande sera affiché dans le sous-menu **Outils externes** du menu **Outils** . Faites précéder une des lettres de ce nom du caractère &amp; pour l'utiliser comme touche d'accès rapide de l'outil. Par exemple, `&Spy++` s'afficherait sous la forme **Spy++** dans le menu **Outils** .  
  
 **Commande**  
 Spécifiez le chemin d'accès au fichier .exe, .com, .pif, .bat, .cmd ou autre que vous avez l'intention de lancer. La sortie des fichiers `.bat`, `.com`ou autres peut s'afficher dans la fenêtre de sortie si vous activez la case à cocher **Utiliser la fenêtre de sortie** .  
  
 **Arguments**  
 Spécifiez les variables qui sont passées à l'outil lorsque celui-ci est sélectionné dans le menu. Les arguments peuvent spécifier des valeurs qui sont passées à l'outil ou à la commande au moment de son lancement. Par exemple, une valeur peut spécifier un nom de fichier ou un répertoire. Utilisez le **bouton représentant une flèche** pour effectuer votre sélection dans une liste d'arguments prédéfinis. Vous pouvez en ajouter plusieurs. Pour obtenir la liste complète des arguments prédéfinis et leur définition, consultez [Arguments for External Tools](external-tools.md). Vous pouvez également entrer des arguments personnalisés (par exemple, des commutateurs d'invite de commandes) selon la commande ou l'outil utilisé.  
  
 **Répertoire initial**  
 Spécifie le répertoire de travail de l'outil. Utilisez le **bouton représentant une flèche** pour sélectionner des répertoires. Vous pouvez en sélectionner plusieurs.  
  
 **Use output Window**  
 Indique si les résultats de l'outil seront ou non affichés dans la fenêtre de sortie. Cette option n'est disponible que dans le cas de fichiers dont la sortie s'affiche normalement dans la fenêtre d'invite de commandes, tels que les fichiers à extension .bat et .com. Si elle est activée, cette option facilite la gestion des fenêtres lorsque vous suivez la progression d'un outil.  
  
 **Demander les arguments**  
 Affiche la boîte de dialogue **Arguments** pour vous permettre d'entrer ou de modifier des valeurs pour les arguments chaque fois que vous lancez l'outil externe.  
  
 **Considérer la sortie en Unicode**  
 Autorise la fenêtre de sortie à accepter le format Unicode.  
  
 **Fermer en quittant**  
 Ferme en même temps que l'outil la fenêtre qu'il a ouverte.  
  
## <a name="example"></a>Exemple  
  
#### <a name="to-add-sql-server-configuration-manager-to-the-tools-menu"></a>Pour ajouter le Gestionnaire de configuration SQL Server au menu Outils  
  
1.  Dans le menu **Outils** , cliquez sur **Outils externes**.  
  
2.  Dans la zone **Titre** , tapez **Gestionnaire de configuration SQL Server**.  
  
3.  Dans la zone **commande** , tapez le chemin d’accès [!INCLUDE[msCoName](../../includes/msconame-md.md)] à l’exécutable de la console de gestion, par exemple`C:\WINNT\system32\mmc.exe`  
  
4.  Dans la zone **arguments** , tapez le chemin d’accès au fichier. msc, par exemple`"C:\WINNT\system32\SQLServerManager.msc"`  
  
> [!NOTE]  
>  Affichez les propriétés du raccourci de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans le menu **Démarrer** pour vérifier l'emplacement des fichiers sur votre ordinateur.  
