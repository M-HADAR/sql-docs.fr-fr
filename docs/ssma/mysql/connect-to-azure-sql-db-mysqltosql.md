---
title: Se connecter à Azure SQL DB (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 12da1aa42f468b92e1833410e635183aabf3a384
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103243"
---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Se connecter à Azure SQL DB (MySQLToSQL)
Utilisez la boîte de dialogue se connecter au SQL Azure pour vous connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le menu **fichier** , sélectionnez **se connecter à SQL Azure**. Si vous vous êtes connecté précédemment, la commande se **reconnecte à SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom du serveur**  
  
Sélectionnez ou entrez le nom du serveur pour la connexion à SQL Azure.  
  
**Sauvegarde de la base de données**  
  
Sélectionnez, entrez ou **recherchez** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour MySQL ne prend pas en charge la connexion à la base de données Master dans SQL Azure.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur que SSMA utilisera pour se connecter à la base de données SQL Azure  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d’utilisateur.  
  
**Codage**  
  
SSMA recommande la connexion chiffrée à SQL Azure.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
S’il n’existe aucune base de données dans le compte SQL Azure, vous pouvez créer la toute première base de données.  
  
Pour créer une base de données pour la première fois, procédez comme suit :  
  
1.  Cliquez sur le bouton Parcourir qui est présent dans la boîte de dialogue se connecter à SQL Azure  
  
2.  S’il n’y a aucune base de données, les deux éléments de menu suivants s’affichent.  
  
    1.  **(aucune base de données trouvée)** qui est désactivée et grisée tout le temps  
  
    2.  **Créer une nouvelle base de données** qui n’est activée que si aucune base de données n’est présente sur SQL Azure compte. Lorsque vous cliquez sur cet élément de menu, la boîte de dialogue créer une base de données Azure est présente avec le nom et la taille de la base de données.  
  
3.  Au moment de la création de la base de données, les deux paramètres suivants sont fournis comme entrée :  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** Sélectionnez la taille de base de données que vous devez créer dans SQL Azure compte.  
  
