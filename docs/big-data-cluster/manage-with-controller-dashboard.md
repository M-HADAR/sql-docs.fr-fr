---
title: Gérer le cluster Big Data SQL Server avec le tableau de bord du contrôleur
titleSuffix: Manage SQL Server big data cluster with controller dashboard
description: Utilisez un notebook d’Azure Data Studio pour gérer et dépanner un cluster Big Data.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a78074b7e32df18de1308d2354d98079d074f9bf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73531941"
---
# <a name="manage-big-data-clusters-for-sql-server-controller-dashboard"></a>Gérer les clusters Big Data pour le tableau de bord du contrôleur SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Outre **azdata** et le notebook d’état du cluster, il existe une autre façon d’afficher l’état d’un cluster Big Data SQL Server. Vous pouvez maintenant ajouter le contrôleur du cluster Big Data SQL Server via la viewlet **Connexions**. Cela vous permet de disposer d’un tableau de bord pour voir l’intégrité du cluster.

![dashboard](media/manage-with-controller-dashboard/controller-dashboard.png)
## <a name="prerequisites"></a>Conditions préalables requises

Les prérequis suivants sont nécessaires pour lancer le notebook :

* Version la plus récente de la [build Azure Data Studio Insiders](https://docs.microsoft.com/sql/big-data-cluster/deploy-big-data-tools?view=sqlallproducts-download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc)
* Extension [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installée dans Azure Data Studio

En plus de ce qui précède, un cluster Big Data SQL Server 2019 nécessite également :

* **azdata**
    - [Windows installer](deploy-install-azdata-installer.md)
    - [Gestionnaire de package Linux](deploy-install-azdata-linux-package.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="add-sql-server-big-data-cluster-controller"></a>Ajouter le contrôleur du cluster Big Data SQL Server

1. Cliquez sur la vue Connexions dans le volet gauche.
2. En bas de la vue Connexions, cliquez sur l’élément **Clusters Big Data SQL Server** pour le développer.
3. Cliquez sur **Add SQL Server big data cluster controller** (Ajouter le contrôleur du cluster Big Data SQL Server) pour ouvrir une nouvelle boîte de dialogue.

## <a name="add-new-controller"></a>Ajouter un nouveau contrôleur

1. Ajoutez le nom de votre cluster.
2. Ajoutez l’URL de votre service de gestion de cluster. Vous pouvez la trouver dans la table des points de terminaison de service du tableau de bord du cluster Big Data ou demander à l’administrateur de votre cluster.
3. Ajoutez vos nom d’utilisateur et mot de passe.

## <a name="launch-controller-dashboard"></a>Lancer le tableau de bord du contrôleur

1. Une fois que vous avez ajouté votre contrôleur, vous pouvez l’afficher sous Clusters Big Data SQL Server.
2. Pour lancer le tableau de bord, cliquez avec le bouton droit sur le contrôleur, puis cliquez sur **Gérer**.

## <a name="controller-dashboard"></a>Tableau de bord du contrôleur

1. Le tableau de bord du contrôleur contient 3 composants principaux :

    - **Barre d’outils** en haut qui contient des actions pour le tableau de bord.
    - **Volet de navigation** sur la gauche, qui passe aux différents affichages du tableau de bord.
    - **Vue** couvrant la majeure partie de la page.

2. Dans la page **Big data cluster overview** (Vue d’ensemble du cluster Big Data), vous pouvez voir :

    - **Propriétés de cluster** pour afficher des informations sur votre cluster.
    - **Vue d’ensemble du cluster** pour obtenir une vue d’ensemble générale de tous les composants de cluster, et ceux qui ne sont pas sains
    - **Points de terminaison de service** pour copier différents services ou y accéder au sein de votre cluster Big Data SQL Server.

3. Dans le **volet de navigation**, vous pouvez voir la liste des services, puis cliquer sur l’un d’entre eux pour afficher des détails supplémentaires sur le cluster. Il s’agit des mêmes affichages quand vous cliquez sur un service dans **Vue d’ensemble du cluster**.

4. Chaque vue sous **Détails du cluster** se compose des mêmes composants d’interface utilisateur :

    - **Health Status Details** (Détails sur l’état d’intégrité) qui partagent l’état et l’état d’intégrité du composant.
    - **Métriques et journaux** pour afficher des métriques et des journaux supplémentaires via Grafana et Kibana.

1. Si vous affichez un composant qui n’est pas sain, cliquez sur **Dépanner** dans la barre d’outils pour lancer un book Jupyter contenant un notebook afin de faciliter le diagnostic du problème.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le contrôleur, consultez [notre documentation sur le contrôleur](concept-controller.md).