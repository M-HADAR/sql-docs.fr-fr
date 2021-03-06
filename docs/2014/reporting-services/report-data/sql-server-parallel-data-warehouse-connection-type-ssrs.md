---
title: Type de connexion à un entrepôt de données SQL Server Parallel Data Warehouse (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3925fd3d-2aa1-4768-96ad-cfc2c0ba9283
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0c8ada8e10ef0f1bc47e1655521acced6f0aa41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106965"
---
# <a name="sql-server-parallel-data-warehouse-connection-type-ssrs"></a>Type de connexion à un entrepôt de données SQL Server Parallel Data Warehouse (SSRS)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] est un appareil d’entrepôt de données évolutif qui offre des performances et une évolutivité par le biais d’un traitement parallèle massif. 
  [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] utilise des bases de données [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] pour le traitement distribué et le stockage des données.  
  
 L'appareil partitionne de grandes tables de base de données entre plusieurs nœuds physiques, chaque nœud exécutant sa propre instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Lorsqu'un rapport se connecte à [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] pour récupérer les données de rapport, il se connecte au nœud de contrôle, qui gère le traitement des requête dans l'appareil [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] . Après avoir établi la connexion, il n'y a pas de différences entre utiliser une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui est ou n'est pas dans un environnement [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] .  
  
 Pour inclure des données [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] de dans votre rapport, vous devez avoir un DataSet basé sur une source de données de rapport de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type Parallel Data Warehouse. Ce type de source de données intégré est basé sur l' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] extension de données de Data Warehouse parallèle. Utilisez ce type de source de données pour vous connecter à et récupérer des données de [!INCLUDE[ssDW](../../../includes/ssdw-md.md)].  
  
 Cette extension de données prend en charge des paramètres à valeurs multiples, agrégats de serveur et informations d'identification gérés séparément de la chaîne de connexion.  
  
 Pour plus d'informations, consultez le site Web [SQL Server 2008 R2 Parallel Data Warehouse (en anglais)](https://go.microsoft.com/fwlink/?LinkId=150895).  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions pas à pas, consultez [Ajouter et vérifier une connexion de données ou une source de données &#40;générateur de rapports et des&#41;SSRS ](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a>Chaîne de connexion  
 Lorsque vous vous connectez à [!INCLUDE[ssDW](../../../includes/ssdw-md.md)], vous vous connectez à un objet de base de données dans une appliance [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] . Vous spécifiez l'objet de base de données à utiliser dans le concepteur de requêtes. Si vous ne spécifiez pas de base de données dans la chaîne de connexion, vous vous connectez à la base de données par défaut que l'administrateur vous a affectée. Contactez l'administrateur de votre base de données pour connaître les informations de connexion et d'identification à utiliser pour se connecter à la source de données. L'exemple de chaîne de connexion suivant spécifie l'exemple de base de données, **CustomerSales**, dans l'appliance [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] :  
  
```  
HOST=<IP address>; database= CustomerSales; port=<port>  
```  
  
 De plus, vous utilisez la boîte de dialogue **Propriétés de la source de données** pour fournir des informations d'identification telles que le nom d'utilisateur et le mot de passe, les options `User Id` et `Password` sont ajoutées automatiquement à la chaîne de connexion, vous n'avez pas besoin de les taper dans la chaîne de connexion. L'interface utilisateur fournit également des options permettant de spécifier l'adresse IP du nœud de contrôle dans l'appliance [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] , ainsi que le numéro de port. Par défaut, il s'agit du port 17000. Le port est configurable par un administrateur et votre chaîne de connexion peut utiliser un autre numéro de port.  
  
 Pour plus d’informations sur les exemples de chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="Credentials"></a>Informations d’identification  
 
  [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] fournit sa propre technologie de sécurité pour implémenter et stocker les noms d'utilisateurs et les mots de passe. Vous ne pouvez pas utiliser l'authentification Windows. Si vous essayez de vous connecter à [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] à l'aide de l'authentification Windows, une erreur se produit.  
  
 Les informations d'identification doivent être suffisantes pour accéder à la base de données. Selon votre requête, vous pouvez avoir besoin d'autres autorisations, par exemple des autorisations suffisantes pour accéder aux tables et aux vues. Le propriétaire de la source de données externe doit configurer des informations d'identification suffisantes pour fournir un accès en lecture seule aux objets de base de données nécessaires.  
  
 Sur un client de création de rapports, les options suivantes sont disponibles pour spécifier des informations d'identification :  
  
-   Utiliser un nom d'utilisateur et un mot de passe enregistrés. Pour négocier le double tronçon qui se produit lorsque la base de données qui contient les données de rapport est différente du serveur de rapports, sélectionnez les options permettant d'utiliser les informations d'identification en tant qu'informations d'identification Windows. Vous pouvez également choisir d'emprunter l'identité de l'utilisateur authentifié après la connexion à la source de données.  
  
-   Aucune information d'identification n'est requise. Pour utiliser cette option, vous devez avoir configuré le compte d'exécution sans assistance sur le serveur de rapports. Pour plus d’informations, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) dans la [documentation Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) sur msdn.microsoft.com.  
  
 Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ou [spécifier des informations d’identification dans générateur de rapports](../specify-credentials-in-report-builder.md).  

##  <a name="Query"></a>Adressée  
 Une requête spécifie les données à récupérer pour un dataset de rapport.  
  
 Les colonnes dans le jeu de résultats d'une requête remplissent la collection de champs pour un dataset. Si la requête retourne plusieurs jeux de résultats, le rapport traite uniquement le premier jeu de résultats qu'une requête récupère. Par défaut, si vous créez une requête ou si vous ouvrez une requête existante qui peut être représentée dans le concepteur de requêtes graphique, le concepteur de requêtes relationnelles est disponible. Vous pouvez spécifier une requête de plusieurs façons :  
  
-   Générer une requête de manière interactive. Utilisez le concepteur de requêtes relationnelles, qui affiche selon un mode hiérarchique les tables, vues et autres éléments de base de données, organisés par schéma de base de données. Sélectionnez des colonnes à partir des tables ou des vues. Limitez le nombre de lignes de données à récupérer en spécifiant des critères de filtre, des regroupements et des agrégats. Personnalisez le filtre lorsque le rapport s'exécute en définissant l'option de paramètre.  
  
-   Taper ou coller une requête. Utilisez le concepteur de requêtes textuel pour entrer directement du texte [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] , coller du texte de requête à partir d’une autre source, entrer des requêtes complexes impossibles à créer à l’aide du concepteur de requêtes relationnelles, ou entrer des expressions basées sur des requêtes.  
  
-   Importe une requête existante à partir d'un fichier ou d'un rapport. Utilisez le bouton **Importer une requête** à partir de l'un des concepteurs de requêtes afin de naviguer jusqu'à un fichier .sql ou .rdl, et d'importer une requête.  
  
 Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes relationnelles &#40;Générateur de rapports&#41;](relational-query-designer-user-interface-report-builder.md) et [Interface utilisateur du Concepteur de requêtes textuel &#40;Générateur de rapports&#41;](text-based-query-designer-user-interface-report-builder.md).  
  
 Le concepteur de requêtes textuel prend en charge le mode [Texte](#QueryText) dans lequel vous tapez des commandes [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] qui sélectionnent des données provenant de la source de données.  
  
-   [Text](#QueryText)  
  
 Vous utilisez [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] avec [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] et [!INCLUDE[tsql](../../../includes/tsql-md.md)] avec [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Les deux dialectes du langage SQL sont très semblables. Les requêtes écrites pour le type de connexion à la source de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent être utilisées en général pour le type de connexion à la source de données [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] .  
  
 Une requête qui récupère des données de rapport à partir d'une base de données de grande taille, notamment un entrepôt de données tel que [!INCLUDE[ssDW](../../../includes/ssdw-md.md)], peut générer un jeu de résultats qui possède un très grand nombre de lignes, sauf si vous agrégez et synthétisez les données afin de réduire le nombre des lignes retournées par la requête. Vous pouvez écrire des requêtes qui incluent des agrégats et des regroupements à l'aide du concepteur de requêtes graphique ou textuel.  
  
 
  [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] prend en charge la clause, le mot clé et les agrégats que le concepteur de requêtes fournit pour synthétiser les données.  
  
 Le concepteur de requêtes graphique utilisé par [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] fournit une prise en charge intégrée du regroupement et des agrégats pour vous aider à écrire des requêtes qui récupèrent uniquement les données de synthèse. Les fonctionnalités du langage [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] sont les suivantes : clause GROUP BY, mot clé DISTINCT et agrégats tels que SUM et COUNT. Le concepteur de requêtes textuel fournit une prise en charge complète du langage [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] , notamment en matière de regroupement et d’agrégats.  
  
 Pour plus d’informations sur [!INCLUDE[tsql](../../../includes/tsql-md.md)], consultez [Informations de référence sur Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference) dans la documentation en ligne[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ de ](https://go.microsoft.com/fwlink/?LinkId=141687) sur msdn.microsoft.com.  
  
###  <a name="QueryText"></a>Utilisation du type de requête texte  
 Dans le concepteur de requêtes textuel, vous tapez des commandes [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] pour définir les données d’un dataset. Les requêtes que vous utilisez pour récupérer des données de [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] sont les mêmes que celles que vous utilisez pour récupérer des données à partir d'instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui ne s'exécutent pas dans une application [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] . Par exemple, la requête [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] suivante sélectionne les noms de tous les employés qui occupent la fonction d'assistants marketing :  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 Cliquez sur le bouton **Exécuter** (**!**) de la barre d’outils pour exécuter la requête et afficher un jeu de résultats.  
  
 Pour paramétrer cette requête, ajoutez un paramètre de requête. Par exemple, modifiez la clause WHERE comme suit :  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 Lorsque vous exécutez la requête, les paramètres de rapport qui correspondent aux paramètres de requête sont créés automatiquement. Pour plus d'informations, consultez [Paramètres de requête](#Parameters) plus loin dans cette rubrique.  

##  <a name="Parameters"></a> Paramètres  
 Lorsque le texte de requête contient des variables de requête ou des procédures stockées dotées de paramètres d'entrée, les paramètres de requête correspondants pour le dataset et les paramètres de rapport pour le rapport sont automatiquement générés. Le texte de requête ne doit pas inclure l'instruction DECLARE pour chaque variable de requête.  
  
 Par exemple, la requête SQL suivante crée un paramètre de rapport nommé `EmpID` :  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 Par défaut, chaque paramètre de rapport a le type de données Texte ; en outre, un dataset est créé automatiquement pour fournir une liste déroulante de valeurs disponibles. Après avoir créé les paramètres de rapport, vous devrez peut-être modifier les valeurs par défaut. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  

##  Notes concernant <a name="Remarks"></a>  
  
###### <a name="platform-and-version-information"></a>Informations sur les plateformes et les versions  
 Pour plus d’informations sur la prise en charge des plateformes et des versions, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) dans la section [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] de la documentation en ligne[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ de ](https://go.microsoft.com/fwlink/?linkid=121312).  

##  <a name="HowTo"></a> Rubriques de procédures  
 Cette section contient des instructions pas à pas sur l'utilisation des connexions de données, des sources de données et des datasets.  
  
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
 Fournit des informations sur la collection de champs de dataset générée par la requête.  
  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) dans la documentation de la [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [en ligne](https://go.microsoft.com/fwlink/?linkid=121312)de.  
 Fournit des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  

## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
