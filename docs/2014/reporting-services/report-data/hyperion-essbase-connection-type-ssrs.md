---
title: Type de connexion Hyperion Essbase (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 108a00b6-799f-4066-b796-da59e95c09fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8a0c38487f58a6db6e80d48c2b39b09e3ed93106
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107267"
---
# <a name="hyperion-essbase-connection-type-ssrs"></a>Type de connexion Hyperion Essbase (SSRS)
  Pour inclure les données d’une source de données externe [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] dans votre rapport, vous devez avoir un dataset basé sur une source de données de rapport de type [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]. Ce type de source de données intégré est basé sur l’extension de données pour [!INCLUDE[extEssbase](../../includes/extessbase-md.md)], ce qui vous permet de récupérer les données multidimensionnelles d’une source de données externe [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions pas à pas, consultez [Ajouter et vérifier une connexion de données ou une source de données &#40;générateur de rapports et des&#41;SSRS ](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a>Chaîne de connexion  
 L'exemple de chaîne de connexion suivant spécifie une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] sur un serveur qui utilise le port 13080 et XMLA (XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) sur Internet à l'aide de SOAP et se connecte à un exemple de catalogue :  
  
```  
Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample  
```  
  
 Pour plus d’informations sur les exemples de chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
##  <a name="Credentials"></a>Informations d’identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports.  
  
 Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ou [spécifier des informations d’identification dans générateur de rapports](../specify-credentials-in-report-builder.md).  
  
  
##  <a name="Query"></a>Adressée  
 Vous pouvez spécifier une requête de plusieurs façons :  
  
-   Générer une requête de manière interactive. Utilisez le concepteur de requêtes graphique en mode Création ou en mode Requête pour parcourir les métadonnées de la source de données externe et générer une requête en syntaxe MDX (Multidimensional Expression).  
  
    -   **Mode Design** Faites glisser les dimensions, les membres, les propriétés de membre, les mesures et les indicateurs de performance clés du navigateur de métadonnées vers le volet des **données** pour générer une requête MDX. Faites glisser les membres calculés du volet CalculatedMembers vers le volet Données pour définir d’autres champs de dataset.  
  
    -   **Affichage des requêtes** Faites glisser les dimensions, les membres, les propriétés de membre, les mesures et les indicateurs de performance clés du navigateur de métadonnées vers le volet requête pour générer une requête MDX. Il est possible de modifier le texte MDX directement dans le volet Requête. Faites glisser les membres calculés du volet CalculatedMembers vers le volet Requête pour définir d’autres champs de dataset.  
  
     Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes Hyperion Essbase &#40;Générateur de rapports&#41;](../hyperion-essbase-query-designer-user-interface-report-builder.md).  
  
-   Importer une requête MDX existante à partir d'un rapport. Utilisez le bouton **Importer une requête** pour rechercher un fichier .rdl et importer une requête. Vous pouvez importer une requête à partir d'un rapport qui contient un dataset incorporé basé sur une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] . L'importation d'une requête MDX directement à partir d'un fichier .mdx n'est pas prise en charge.  
  
 Au moment de la conception, exécutez la requête pour afficher un jeu de résultats. Après avoir généré la requête, affichez la collection de champs de dataset générée à partir des métadonnées dans le volet des données de rapport. Lorsque le rapport s'exécute, les données réelles sont retournées à partir de la source de données externe.  
  
 L’extension pour le traitement des données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] prend en charge les propriétés de champ de dataset étendues. Il s'agit des valeurs disponibles dans la source de données externe mais qui ne s'affichent pas dans le volet des données de rapport. Pour plus d’informations, consultez [Propriétés de champ étendues](#Extended) , plus loin dans cette rubrique.  
  
  
##  <a name="Parameters"></a> Paramètres  
 Pour inclure les paramètres de requête, créez un filtre dans la zone de filtre du concepteur de requêtes et marquez le filtre en tant que paramètre. Pour chaque filtre, un dataset est créé automatiquement afin de fournir les valeurs disponibles. Par défaut, ces datasets n'apparaissent pas dans le volet Données du rapport. Pour plus d’informations, consultez [Afficher des datasets masqués pour les valeurs de paramètres des données multidimensionnelles &#40;Générateur de rapports et SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
 Par défaut, chaque paramètre de rapport a le type de données **Texte**. Après avoir créé les paramètres de rapport, vous devrez peut-être modifier les valeurs par défaut. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="Extended"></a>Propriétés de champ étendues  
 L'extension pour le traitement des données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] prend en charge les propriétés de champ étendues. Les propriétés de champ étendues sont des propriétés complémentaires à `Value` et `IsMissing` qui sont définies pour un champ de dataset par l'extension pour le traitement des données. Les propriétés étendues incluent des propriétés prédéfinies et des propriétés personnalisées. Les propriétés prédéfinies sont des propriétés communes à plusieurs sources de données. Les propriétés personnalisées sont uniques à chaque source de données.  
  
 Les propriétés de champ étendues n'apparaissent pas dans le volet des données de rapport en tant qu'éléments que vous pouvez faire glisser vers votre disposition de rapport. À la place, vous faites glisser le champ parent de la propriété sur le rapport, puis vous remplacez la propriété par défaut `Value` par la propriété que vous voulez utiliser.  
  
 Le nom d'une propriété de champ étendue apparaît dans l'info-bulle lorsque vous placez la souris sur un champ dans le volet Métadonnées du concepteur de requêtes. Pour plus d’informations sur le concepteur de requêtes que vous pouvez utiliser pour explorer les données sous-jacentes, consultez [Interface utilisateur du Concepteur de requêtes Hyperion Essbase](hyperion-essbase-query-designer-user-interface.md).  
  
> [!NOTE]  
>  Il existe des valeurs pour les propriétés de champ étendues uniquement si elles sont incluses dans l'expression MDX et la source de données fournit ces valeurs lorsque votre rapport s'exécute et récupère les données pour ses datasets. Vous pouvez alors faire référence à ces valeurs de propriété `Field` à partir de n'importe quelle expression en utilisant la syntaxe décrite dans la section suivante. Cependant, dans la mesure où ces champs sont spécifiques à ce fournisseur de données et ne font pas partie du langage de définition de rapport, les modifications que vous apportez à ces valeurs ne sont pas enregistrées avec la définition du rapport.  
  
  
### <a name="predefined-field-properties"></a>Propriétés de champ prédéfinies  
 Propriétés prédéfinies de champ qui sont généralement prises en charge par plusieurs fournisseurs de données et qui apparaissent dans la requête MDX sous-jacente d'un dataset de rapport. Par exemple, la propriété de dimension MDX MEMBER_UNIQUE_NAME est mappée à la propriété prédéfinie de champ dataset du rapport `UniqueName`. Pour inclure la valeur de nom unique dans une zone de texte, utilisez `=Fields!`l’expression * \<FieldName>. * `.UniqueName`  
  
 Le tableau suivant dresse la liste des propriétés de champ prédéfinies que vous pouvez utiliser pour une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Propriété**|**Type**|**Description ou valeur attendue**|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|Précise la valeur de données du champ.<br /><br /> Pour une propriété de dimension, celle-ci est mappée à MEMBER_CAPTION. Pour une mesure, elle est mappée à la valeur de données.|  
|`IsMissing`|`Boolean`|Indique si le champ figure dans le dataset obtenu.|  
|`FormattedValue`|`String`|Retourne la valeur mise en forme d'un élément clé.<br /><br /> Mappé à partir de FORMATTED_VALUE dans l'expression MDX.|  
|`BackgroundColor`|`String`|Retourne la couleur d'arrière-plan définie dans la base de données pour le champ.<br /><br /> Mappé à partir de BACK_COLOR dans l'expression MDX.|  
|`Color`|`String`|Retourne la couleur de premier plan définie dans la base de données pour l'élément.<br /><br /> Mappé à partir de FORE_COLOR dans l'expression MDX.|  
|`UniqueName`|`String`|Retourne le nom complet d'un niveau.<br /><br /> Mappé à partir de MEMBER_UNIQUE_NAME dans l'expression MDX.|  
  
 Pour plus d’informations sur l’utilisation de champs et de propriétés de champ dans une expression, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
  
### <a name="custom-properties"></a>Propriétés personnalisées  
 Les propriétés de champ personnalisées qui sont prises en charge par un fournisseur de données et qui apparaissent dans la requête MDX sous-jacente pour un dataset de rapport, n'apparaissent pas dans le volet Datasets comme champs sous ce dataset. Par exemple, **Long Names** est une propriété de membre définie pour un niveau de dimension. Pour inclure la valeur dans une zone de texte, utilisez l’expression `=Fields!` * \<FieldName>* `("Long Names")`. Les noms de champs de l'expression respectent la casse.  
  
 Pour faire référence à des propriétés étendues personnalisées dans une expression, vous pouvez utiliser la syntaxe suivante :  
  
-   *Field! FieldName ("PropertyName")*  
  
 Le tableau suivant indique la propriétde champ personnalisée que vous pouvez utiliser pour une source de données [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Propriété**|**Type**|**Description ou valeur attendue**|  
|------------------|--------------|---------------------------------------|  
|`FORMAT_STRING`|`String`|Défini sur une mesure, `FormattedValue` est disponible comme type chaîne.|  
  
  
##  Notes concernant <a name="Remarks"></a>  
 Certains modes de remise de rapport ne sont pas pris en charge par ce fournisseur de données. La remise des rapports par le biais d'abonnements pilotés par les données n'est pas prise en charge pour cette extension pour le traitement des données. Pour plus d’informations, consultez [Utiliser une source de données externe pour les données des abonnés &#40;abonnement piloté par les données&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) dans la documentation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentation en ligne](https://go.microsoft.com/fwlink/?linkid=121312)de.  
  
 Pour plus d’informations, consultez [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970).  
  
  
##  <a name="HowTo"></a> Rubriques de procédures  
 Cette section contient des instructions pas à pas sur l'utilisation des connexions de données, des sources de données et des datasets :  
  
 [Ajouter et vérifier une connexion de données ou une source de données &#40;Générateur de rapports et SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Ajouter un filtre à un jeu de données &#40;Générateur de rapports et SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a>Sections connexes  
 Ces sections de la documentation fournissent des informations de fond d'ordre conceptuel sur les données de rapport, ainsi que des informations sur les procédures de définition, de personnalisation et d'utilisation des parties d'un rapport qui sont liées aux données.  
  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)  
 Fournit une vue d'ensemble de l'accès aux données pour votre rapport.  
  
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Fournit des informations sur les connexions de données et les sources de données.  
  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Fournit des informations sur les datasets incorporés et partagés.  
  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Fournit des informations sur la collection de champs générée par la requête de dataset.  
  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) dans la documentation de la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [en ligne](https://go.microsoft.com/fwlink/?linkid=121312)de.  
 Fournit des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  
  
 [Utilisation de SQL Server 2005 Reporting Services avec Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970)  
 Fournit des informations détaillées sur l'utilisation de cette extension de données.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
