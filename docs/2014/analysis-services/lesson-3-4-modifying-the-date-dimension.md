---
title: Modification de la dimension Date | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 826d5b1079e9fcfd0d2ec7a9abd55937f2da1a22
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078798"
---
# <a name="modifying-the-date-dimension"></a>Modification de la dimension Date
  Dans les tâches de cette rubrique, vous allez créer une hiérarchie définie par l'utilisateur et vous allez modifier les noms de membre affichés pour les attributs Date, Month, Calendar Quarter et Calendar Semester. Vous allez également définir des clés composites pour les attributs, contrôler l'ordre de tri des membres de dimension et définir les relations d'attributs.  
  
## <a name="adding-a-named-calculation"></a>Ajout d'un calcul nommé  
 Vous pouvez ajouter un calcul nommé, c'est-à-dire une expression SQL qui est représentée sous la forme d'une colonne calculée, dans la table d'une vue de source de données. L'expression apparaît et se comporte comme une colonne dans une table. Les calculs nommés permettent d'étendre le schéma relationnel des tables existantes dans une vue de source des données, sans avoir à modifier la table dans la source de données sous-jacente. Pour plus d’informations, consultez [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
#### <a name="to-add-a-named-calculation"></a>Pour ajouter un calcul nommé  
  
1.  Pour ouvrir la vue de source de données **Adventure Works DW 2012** , double-cliquez dessus dans le dossier **Vues des sources de données** de l’Explorateur de solutions.  
  
2.  En bas du volet **tables** , cliquez avec le bouton droit `Date`sur, puis cliquez sur **nouveau calcul nommé**.  
  
3.  Dans la boîte de dialogue **créer un calcul nommé** , `SimpleDate` tapez dans la zone nom de la **colonne** , puis tapez ou copiez `DATENAME` -collez l’instruction suivante dans la zone **expression** :  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     L'instruction `DATENAME` extrait les valeurs relatives à l'année, au mois et au jour à partir de la colonne FullDateAlternateKey. Vous utiliserez cette nouvelle colonne comme nom affiché de l'attribut FullDateAlternateKey.  
  
4.  Cliquez sur **OK**, puis développez `Date` dans le volet **tables** .  
  
     Le `SimpleDate` calcul nommé s’affiche dans la liste des colonnes de la table de dates, avec une icône qui indique qu’il s’agit d’un calcul nommé.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
6.  Dans le volet **tables** , cliquez avec le `Date`bouton droit sur, puis cliquez sur **Explorer les données**.  
  
7.  Faites défiler vers la droite pour afficher la dernière colonne de la vue **Explorer la table Date** .  
  
     Notez que la `SimpleDate` colonne apparaît dans la vue de source de données, et que les données sont correctement concaténées à partir de plusieurs colonnes de la source de données sous-jacente, sans modifier la source de données d’origine.  
  
8.  Fermez la vue **Explorer la table Date** .  
  
## <a name="using-the-named-calculation-for-member-names"></a>Utilisation du calcul nommé pour les noms des membres  
 Après avoir créé un calcul nommé dans la vue de source de données, vous pouvez utiliser le calcul nommé comme propriété d'un attribut.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>Pour utiliser le calcul nommé pour les noms des membres  
  
1.  Ouvrez le **Concepteur de dimensions** pour la dimension Date dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour ce faire, double-cliquez sur `Date` la dimension dans le nœud **dimensions** de **Explorateur de solutions**.  
  
2.  Dans le volet **Attributs** de l’onglet **Structure de dimension** , cliquez sur l’attribut **Date Key** .  
  
3.  Si la fenêtre Propriétés n’est pas ouverte, ouvrez-la, puis cliquez sur le bouton **Masquer automatiquement** dans la barre de titre afin qu’elle reste ouverte.  
  
4.  Cliquez sur le champ de propriété **NameColumn** en bas de la fenêtre, puis cliquez sur le bouton de navigation (**...**) pour ouvrir la boîte de dialogue **colonne de nom** .  
  
5.  Sélectionnez `SimpleDate` au bas de la liste **colonne source** , puis cliquez sur **OK**.  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="creating-a-hierarchy"></a>Création d'une hiérarchie  
 Vous pouvez créer une hiérarchie en faisant glisser un attribut du volet **Attributes** vers le volet **Hiérarchies** .  
  
#### <a name="to-create-a-hierarchy"></a>Pour créer une hiérarchie  
  
1.  Dans l’onglet **structure de dimension** du concepteur de dimensions `Date` pour la dimension, faites glisser l’attribut **année civile** du volet **attributs** vers le volet **hiérarchies** .  
  
2.  Faites glisser l’attribut **semestre calendaire** du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **année civile** .  
  
3.  Faites glisser l’attribut **Calendar Quarter** du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **semestre calendaire** .  
  
4.  Faites glisser l’attribut **English Month Name** du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **Quarter du calendrier** .  
  
5.  Faites glisser l’attribut **Date Key** du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **English Month Name** .  
  
6.  Dans le volet **hiérarchies** , cliquez avec le bouton droit sur la barre de titre de la hiérarchie **hiérarchie** , cliquez sur `Calendar Date` **Renommer**, puis tapez.  
  
7.  En utilisant le menu contextuel du clic droit, dans `Calendar Date` la hiérarchie, renommez le niveau **English Month Name** en `Calendar Month`, puis renommez le niveau de `Date`la **clé Date** en.  
  
8.  Supprimez l’attribut **Full Date Alternate Key** du volet **Attributs** , car vous ne l’utiliserez pas. Cliquez sur **OK** dans la fenêtre de confirmation **Supprimer les objets** .  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-attribute-relationships"></a>Définition des relations d'attributs  
 Si les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs entre les attributs. La définition de relations d'attributs accélère le traitement des dimensions, des partitions et des requêtes.  
  
#### <a name="to-define-attribute-relationships"></a>Pour définir les relations d'attributs  
  
1.  Dans le **Concepteur de dimensions** pour `Date` la dimension, cliquez sur l’onglet **relations d’attributs** .  
  
2.  Dans le diagramme, cliquez avec le bouton droit sur l’attribut **English Month Name** puis cliquez sur **Nouvelle relation d’attribut**.  
  
3.  Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **English Month Name**. Définissez **l’Attribut associé** avec la valeur **Calendar Quarter**.  
  
4.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
     Le type de relation est **Rigide** car les relations entre les membres ne changeront pas au fil du temps.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans le diagramme, cliquez avec le bouton droit sur l’attribut **Calendar Quarter** , puis cliquez sur **Nouvelle relation d’attribut**.  
  
7.  Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **Calendar Quarter**. Définissez **l’Attribut associé** avec la valeur **Calendar Semester**.  
  
8.  Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
9. Cliquez sur **OK**.  
  
10. Dans le diagramme, cliquez avec le bouton droit sur l’attribut **Calendar Semester** , puis cliquez sur **Nouvelle relation d’attribut**.  
  
11. Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **Calendar Semester**. Définissez **l’Attribut associé** avec la valeur **Calendar Year**.  
  
12. Dans la liste **Type de relation** , définissez le type de relation sur **Rigide**.  
  
13. Cliquez sur **OK**.  
  
14. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="providing-unique-dimension-member-names"></a>Attribution de noms uniques aux membres de dimension  
 Dans cette tâche, vous allez créer des colonnes de nom conviviales qui seront utilisées par les attributs **EnglishMonthName**, **CalendarQuarter**et **CalendarSemester** .  
  
#### <a name="to-provide-unique-dimension-member-names"></a>Pour fournir des noms uniques aux membres de dimension  
  
1.  Pour basculer vers ** [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] ** la vue de source de données DW 2012, double-cliquez sur celle-ci dans le dossier **vues des sources de données** de Explorateur de solutions.  
  
2.  Dans le volet **tables** , cliquez avec le `Date`bouton droit sur, puis cliquez sur **nouveau calcul nommé**.  
  
3.  Dans la boîte de dialogue **créer un calcul nommé** , tapez `MonthName` dans la zone nom de la **colonne** , puis tapez ou copiez-collez l’instruction suivante dans la zone **expression** :  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     L'instruction concatène le mois et l'année dans une nouvelle colonne pour chaque mois de la table.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le volet **tables** , cliquez avec le `Date`bouton droit sur, puis cliquez sur **nouveau calcul nommé**.  
  
6.  Dans la boîte de dialogue **créer un calcul nommé** , tapez `CalendarQuarterDesc` dans la zone nom de la **colonne** , puis tapez ou copiez et collez le script SQL suivant dans la zone **expression** :  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     Ce script SQL concatène le trimestre calendaire et l'année dans une nouvelle colonne pour chaque trimestre de la table.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le volet **tables** , cliquez avec le `Date`bouton droit sur, puis cliquez sur **nouveau calcul nommé**.  
  
9. Dans la boîte de dialogue **créer un calcul nommé** , tapez `CalendarSemesterDesc` dans la zone nom de la **colonne** , puis tapez ou copiez et collez le script SQL suivant dans la zone **expression** :  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     Ce script SQL concatène le semestre calendaire et l'année dans une nouvelle colonne pour chaque semestre de la table.  
  
10. Cliquez sur **OK**.  
  
11. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a>Définition de propriété KeyColumns composite et définition de Colonne de nom  
 La propriété **KeyColumns** contient la colonne ou les colonnes qui représentent la clé pour l’attribut. Dans cette tâche, vous allez définir une propriété **KeyColumns**composite.  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a>Pour définir une propriété KeyColumns composite pour l'attribut English Month Name  
  
1.  Ouvrez l’onglet **Structure de dimension** pour la dimension Date.  
  
2.  Dans le volet **Attributs** , cliquez sur l’attribut **English Month Name** .  
  
3.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** , puis cliquez sur le bouton de navigation (**...**).  
  
4.  Dans la boîte de dialogue **Colonnes clés** , dans la liste **Colonnes disponibles** , sélectionnez la colonne **CalendarYear**, puis cliquez sur le bouton **>** .  
  
5.  Les colonnes **EnglishMonthName** et **CalendarYear** s’affichent maintenant dans la liste **Colonnes clés** .  
  
6.  Cliquez sur **OK**.  
  
7.  Pour définir la propriété **NameColumn** de l’attribut **EnglishMonthName** , cliquez dans le champ **NameColumn** de la fenêtre des propriétés, puis cliquez sur le bouton de navigation (**...**).  
  
8.  Dans la boîte de dialogue **colonne de nom** , dans la liste **colonne source** , sélectionnez `MonthName`, puis cliquez sur **OK**.  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a>Pour définir la propriété KeyColumns composite pour l'attribut Calendar Quarter  
  
1.  Dans le volet **Attributs** , cliquez sur l’attribut **Calendar Quarter** .  
  
2.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** , puis cliquez sur le bouton de navigation (**...**).  
  
3.  Dans la boîte de dialogue **Colonnes clés** , dans la liste **Colonnes disponibles** , sélectionnez la colonne **CalendarYear**, puis cliquez sur le bouton **>** .  
  
     Les colonnes **CalendarQuarter** et **CalendarYear** s’affichent maintenant dans la liste **Colonnes clés** .  
  
4.  Cliquez sur **OK**.  
  
5.  Pour définir la propriété **NameColumn** de l’attribut **Calendar Quarter** , cliquez dans le champ **NameColumn** de la fenêtre des propriétés, puis cliquez sur le bouton de navigation (**...**).  
  
6.  Dans la boîte de dialogue **colonne de nom** , dans la liste **colonne source** , sélectionnez `CalendarQuarterDesc`, puis cliquez sur **OK**.  
  
7.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a>Pour définir la propriété KeyColumns composite pour l'attribut Calendar Semester  
  
1.  Dans le volet **Attributs** , cliquez sur l’attribut **Calendar Semester** .  
  
2.  Dans la fenêtre **Propriétés** , cliquez dans le champ **KeyColumns** , puis cliquez sur le bouton de navigation (**...**).  
  
3.  Dans la boîte de dialogue **colonnes clés** , dans la liste **colonnes disponibles** , sélectionnez la colonne **CalendarYear**, puis cliquez sur le **>** bouton.  
  
     Les colonnes **CalendarSemester** et **CalendarYear** s’affichent maintenant dans la liste **Colonnes clés** .  
  
4.  Cliquez sur **OK**.  
  
5.  Pour définir la propriété **NameColumn** de l’attribut **Calendar Semester** , cliquez dans le champ **NameColumn** de la fenêtre des propriétés, puis cliquez sur le bouton de navigation (**...**).  
  
6.  Dans la boîte de dialogue **colonne de nom** , dans la liste **colonne source** , sélectionnez `CalendarSemesterDesc`, puis cliquez sur **OK**.  
  
7.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="deploying-and-viewing-the-changes"></a>Déploiement et consultation des modifications  
 Une fois les attributs et les hiérarchies modifiés, vous devez déployer les modifications et retraiter les objets associés avant de pouvoir visualiser ces modifications.  
  
#### <a name="to-deploy-and-view-the-changes"></a>Pour déployer et consulter les modifications  
  
1.  Dans le menu **Générer** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Une fois que vous avez reçu le message le **déploiement est terminé** , cliquez sur l’onglet **navigateur** du `Date` concepteur de **dimensions** pour la dimension, puis cliquez sur le bouton reconnecter de la barre d’outils du concepteur.  
  
3.  Sélectionnez **Calendar Quarter** dans la liste **Hiérarchie** . Vérifiez les membres dans la hiérarchie d’attribut **Calendar Quarter** .  
  
     Remarquez que les noms des membres de la hiérarchie d’attribut **Calendar Quarter** sont plus clairs et faciles à utiliser, car vous avez créé un calcul nommé utilisé comme nom. Les membres existent maintenant dans la hiérarchie d’attribut **Calendar Quarter** pour chaque trimestre de chaque année. Les membres ne sont pas triés par ordre chronologique. Ils sont au contraire triés par trimestre, puis par année. Au cours de la tâche suivante, vous allez modifier cela pour trier les membres de cette hiérarchie d'attributs par année, puis par trimestre.  
  
4.  Passez en revue les membres des hiérarchies d’attributs **English Month Name** et **Calendar Semester** .  
  
     Notez que les membres de ces hiérarchies ne sont pas non plus classés par ordre chronologique. Ils sont au contraire triés par mois ou semestre, respectivement, puis par année. Au cours de la tâche suivante, vous allez modifier cela pour changer l'ordre de tri.  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a>Modification de l'ordre de tri en changeant l'ordre des membres de clé composite  
 Dans cette tâche, vous allez modifier l'ordre de tri en modifiant l'ordre des clés qui composent la clé composite.  
  
#### <a name="to-modify-the-composite-key-member-order"></a>Pour modifier l'ordre des membres de clé composite  
  
1.  Ouvrez l’onglet **structure** de dimension du concepteur de dimensions `Date` pour la dimension, puis sélectionnez **semestre calendaire** dans le volet **attributs** .  
  
2.  Dans la fenêtre des propriétés, examinez la valeur de la propriété **OrderBy** . La valeur est **Clé**.  
  
     Les membres de la hiérarchie d’attributs **Calendar Semester** sont triés en fonction de la valeur de leur clé. Avec une clé composite, l'ordre des clés de membre est basé en premier sur la valeur de la première clé de membre, puis sur la valeur de la seconde clé de membre. En d’autres termes, les membres de la hiérarchie d’attributs **Calendar Semester** sont triés en premier lieu par semestre, puis par année.  
  
3.  Dans la fenêtre des propriétés, cliquez sur le bouton de navigation (**...**) pour changer la valeur de la propriété **KeyColumns** .  
  
4.  Dans la liste **Colonnes clés** de la boîte de dialogue **Colonnes clés** , vérifiez que **CalendarSemester** est sélectionné, puis cliquez sur la flèche du bas pour inverser l’ordre des membres de cette clé composite. Cliquez sur **OK**.  
  
     Les membres de la hiérarchie d'attributs sont maintenant triés en premier lieu par année, puis par semestre.  
  
5.  Sélectionnez **Calendar Quarter** dans le volet **Attributs** , puis cliquez sur le bouton de navigation (**...**) pour la propriété **KeyColumns** dans la fenêtre des propriétés.  
  
6.  Dans la liste **Colonnes clés** de la boîte de dialogue **Colonnes clés** , vérifiez que **CalendarQuarter** est sélectionné, puis cliquez sur la flèche bas pour inverser l’ordre des membres de cette clé composite. Cliquez sur **OK**.  
  
     Les membres de la hiérarchie d'attributs sont maintenant triés en premier lieu par année, puis par trimestre.  
  
7.  Sélectionnez **English Month Name** dans le volet **Attributs** , puis cliquez sur le bouton de sélection (**...**) pour la propriété **KeyColumns** dans la fenêtre des propriétés.  
  
8.  Dans la liste **Colonnes clés** de la boîte de dialogue **Colonnes clés** , vérifiez que **EnglishMonthName** est sélectionné, puis cliquez sur la flèche bas pour inverser l’ordre des membres de cette clé composite. Cliquez sur **OK**.  
  
     Les membres de la hiérarchie d'attributs sont maintenant triés en premier lieu par année, puis par mois.  
  
9. Dans le menu **Générer** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Déployer Analysis Services Tutorial**. Une fois le déploiement terminé, cliquez sur l’onglet **navigateur** dans le concepteur de `Date` dimensions pour la dimension.  
  
10. Dans la barre d’outils de l’onglet **Navigateur** , cliquez sur le bouton Reconnecter.  
  
11. Examinez les membres des hiérarchies d’attribut **Calendar Quarter** et **Calendar Semester** .  
  
     Notez que les membres de ces hiérarchies sont maintenant triés par ordre chronologique, par année, puis par trimestre ou semestre, respectivement.  
  
12. Passez en revue les membres de la hiérarchie d’attributs **English Month Name** .  
  
     Notez que les membres de la hiérarchie sont maintenant triés d'abord par année, puis alphabétiquement par mois. La raison en est que le type de données de la colonne EnglishCalendarMonth dans la vue de source des données est une colonne de chaîne, basée sur le type de données nvarchar dans la base de données relationnelle sous-jacente. Pour plus d’informations sur la façon de trier les mois chronologiquement au sein de chaque année, consultez [Tri des membres d’attribut sur la base d’un attribut secondaire](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du cube déployé](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
