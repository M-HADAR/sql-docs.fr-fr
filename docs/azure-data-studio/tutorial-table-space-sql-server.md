---
title: Activer le widget d’exemple d’insight d’utilisation d’espace de table
titleSuffix: Azure Data Studio
description: Ce didacticiel montre comment activer le widget d’insight d’utilisation de l’espace de table sur le tableau de bord d’une base de données Azure Data Studio.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/10/2019
ms.openlocfilehash: f22aba3fd2f2d006355fdd30aef6f196f2795f6c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957013"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Tutoriel : Activer le widget d’exemple d’insight d’utilisation d’espace de table avec [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Ce didacticiel montre comment activer un widget d’insight sur le tableau de bord d’une base de données, en fournissant une vue d’ensemble de l’utilisation de l’espace pour toutes les tables d’une base de données. Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Activer rapidement un widget d’insight à l’aide d’un exemple de widget d’insight intégré
> * Afficher les détails de l’utilisation de l’espace de table
> * Filtrer les données et afficher les détails des étiquettes sur un graphique d’insight

## <a name="prerequisites"></a>Conditions préalables requises

Ce didacticiel nécessite la base de données *TutorialDB* de SQL Server ou Azure SQL Database. Pour créer la base de données *TutorialDB*, suivez un des démarrages rapides suivants :

* [Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
* [Se connecter à et interroger Azure SQL Database avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)

## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Activer un insight de gestion sur le tableau de bord d’une base de données [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] dispose d’un exemple de widget intégré pour surveiller l’espace utilisé par les tables dans une base de données.

1. Ouvrez les *Paramètres utilisateur* en appuyant sur **Ctrl+Maj+P** pour ouvrir la *Palette de commandes*.

2. Saisissez *préférences* dans la zone de recherche et sélectionnez **Préférences : Ouvrir les paramètres utilisateur**.

3. Saisissez *tableau de bord* dans la zone Rechercher paramètres et trouvez **dashboard.database.widgets**.

4. Pour personnaliser les paramètres **dashboard.database.widgets**, vous devez modifier l’entrée **dashboard.database.widgets** dans la section **PARAMÈTRES UTILISATEUR**.

   ![Rechercher des paramètres](media/tutorial-table-space-sql-server/search-settings.png)

   S’il n’existe pas de **dashboard.database.widgets** dans la section **PARAMÈTRES UTILISATEUR**, placez le curseur sur le texte **dashboard.database.widgets** dans la colonne PARAMÈTRES PAR DÉFAUT et cliquez sur l’icône en forme d’*engrenage* qui apparaît à gauche du texte et cliquez sur **Copy as Setting JSON** (Copier en tant que fichier JSON de paramètres). Si la fenêtre contextuelle indique **Remplacer dans les paramètres**, ne cliquez pas dessus ! Accédez à la colonne **PARAMÈTRES UTILISATEUR** à droite et recherchez la section **dashboard.database.widgets** et passez à l’étape suivante.

5. Dans la section **dashboard.database.widgets**, ajoutez les lignes suivantes :

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```

   La section **dashboard.database.widgets** doit ressembler à l’image suivante :

    ![Rechercher des paramètres](./media/tutorial-table-space-sql-server/insight-table-space.png)

6. Appuyez sur **Ctrl+S** pour enregistrer les paramètres.

7. Ouvrez le tableau de bord de la base de données en cliquant avec le bouton droit sur **TutorialDB**, puis cliquez sur **Gérer**.

8. Affichez le widget d’insight *espace de table* comme indiqué dans l’image suivante :

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)

## <a name="working-with-the-insight-chart"></a>Utilisation du graphique d’insight

Le graphique d’insight de [!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit des options de filtrage et d’affichage de détails lors du pointage de la souris. Pour essayer cela :

1. Cliquez et basculez la légende *row_count* sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)] affiche et masque les séries de données lorsque vous activez ou désactivez une légende.

2. Placez le pointeur de la souris sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)] affiche plus d’informations sur l’étiquette de la série de données et sa valeur, comme indiqué dans la capture d’écran suivante.

   ![Bouton bascule et légende du graphique](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Activer rapidement un widget d’insight à l’aide d’un exemple de widget intégré.
> * Afficher les détails de l’utilisation de l’espace de table.
> * Filtrer les données et afficher les détails des étiquettes sur un graphique d’insight

Pour savoir comment créer un widget d’insight personnalisé, effectuez le didacticiel suivant :

> [!div class="nextstepaction"]
> [Créer un widget insight personnalisé](tutorial-build-custom-insight-sql-server.md)
