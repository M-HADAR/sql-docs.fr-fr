---
title: Ensembles de lignes et curseurs de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB rowsets, cursors
- SQL Server Native Client OLE DB provider, rowsets
- rowsets [OLE DB], cursors
- properties [OLE DB]
- cursors [OLE DB]
ms.assetid: 26a11e26-2a3a-451e-8f78-fba51e330ecb
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7c9d57b73cb2153a43fee4087459bdd005e3fb26
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788963"
---
# <a name="rowsets-and-sql-server-cursors"></a>Ensembles de lignes et curseurs SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne les jeux de résultats aux consommateurs à l'aide de deux méthodes :  
  
-   Les jeux de résultats par défaut qui :  
  
    -   minimisent la charge ;  
  
    -   procurent des performances maximales pour extraire des données ;  
  
    -   prennent en charge uniquement la fonctionnalité de curseur avant uniquement en lecture seule par défaut ;  
  
    -   retournent les lignes au consommateur une à la fois ;  
  
    -   prennent en charge une seule instruction active à la fois sur une connexion.  
  
         Une fois qu'une instruction a été exécutée, aucune autre instruction ne peut être exécutée sur la connexion tant que tous les résultats n'ont pas été extraits par le consommateur ou que l'instruction n'a pas été annulée ;  
  
    -   prennent en charge toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Les curseurs côté serveur qui :  
  
    -   prennent en charge toutes les fonctionnalités de curseur ;  
  
    -   peuvent retourner des blocs de lignes au consommateur ;  
  
    -   prennent en charge plusieurs instructions actives sur une connexion unique ;  
  
    -   procurent un compromis entre les fonctionnalités de curseur et les performances.  
  
         La prise en charge des fonctionnalités de curseur peut réduire les performances par rapport à un jeu de résultats par défaut. Cette dégradation peut être limitée si le consommateur peut utiliser les fonctionnalités de curseur pour extraire un plus petit ensemble de lignes ;  
  
    -   ne prennent en charge aucune instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui retourne plus d'un seul jeu de résultats.  
  
 Les consommateurs peuvent demander différents comportements de curseur dans un ensemble de lignes en définissant certaines propriétés d'ensemble de lignes. Si le consommateur ne définit pas l’une de ces propriétés d’ensemble de lignes ou les affecte à leurs valeurs par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] défaut, le fournisseur de OLE DB Native Client implémente l’ensemble de lignes à l’aide d’un jeu de résultats par défaut. Si l’une de ces propriétés est définie sur une valeur autre que la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le fournisseur de OLE DB Native Client implémente l’ensemble de lignes à l’aide d’un curseur côté serveur.  
  
 Les propriétés d'ensemble de lignes suivantes font en sorte que le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilise des curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Certaines propriétés peuvent être combinées avec d'autres sans risque. Par exemple, un ensemble de lignes qui expose les propriétés DBPROP_IRowsetScroll et DBPROP_IRowsetChange sera un ensemble de lignes signet présentant un comportement de mise à jour immédiat. Les autres propriétés s'excluent mutuellement. Par exemple, un ensemble de lignes exposant DBPROP_OTHERINSERT ne peut pas contenir de signets.  
  
|ID de propriété|Valeur|Comportement d'ensemble de lignes|  
|-----------------|-----------|---------------------|  
|DBPROP_SERVERCURSOR|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes est séquentiel et prend en charge l'extraction et le défilement vers l'avant uniquement. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut contenir une clause ORDER BY.|  
|DBPROP_CANSCROLLBACKWARDS ou DBPROP_CANFETCHBACKWARDS|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement et l'extraction dans l'une ou l'autre direction. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut contenir une clause ORDER BY.|  
|DBPROP_BOOKMARKS ou DBPROP_LITERALBOOKMARKS|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes est séquentiel et prend en charge l'extraction et le défilement vers l'avant uniquement. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut contenir une clause ORDER BY.|  
|DBPROP_OWNUPDATEDELETE ou DBPROP_OWNINSERT ou DBPROP_OTHERUPDATEDELETE|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement et l'extraction dans l'une ou l'autre direction. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut contenir une clause ORDER BY.|  
|DBPROP_OTHERINSERT|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement et l'extraction dans l'une ou l'autre direction. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut inclure une clause ORDER BY s'il existe un index sur les colonnes référencées.<br /><br /> DBPROP_OTHERINSERT ne peut pas être VARIANT_TRUE si l'ensemble de lignes contient des signets. Toute tentative de création d'un ensemble de lignes avec cette propriété de visibilité et des signets provoque une erreur.|  
|DBPROP_IRowsetLocate ou DBPROP_IRowsetScroll|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement et l'extraction dans l'une ou l'autre direction. Les signets et le positionnement absolu par le biais de l’interface **IRowsetLocate** sont pris en charge dans l’ensemble de lignes. Le texte de la commande peut contenir une clause ORDER BY.<br /><br /> DBPROP_IRowsetLocate et DBPROP_IRowsetScroll requièrent des signets dans l'ensemble de lignes. Toute tentative de création d'un ensemble de lignes avec des signets et DBPROP_OTHERINSERT défini à VARIANT_TRUE provoque une erreur.|  
|DBPROP_IRowsetChange ou DBPROP_IRowsetUpdate|VARIANT_TRUE|Possibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes est séquentiel et prend en charge l'extraction et le défilement vers l'avant uniquement. Le positionnement de ligne relatif est pris en charge. Toutes les commandes qui prennent en charge les curseurs pouvant être mis à jour peuvent prendre en charge ces interfaces.|  
|DBPROP_IRowsetLocate ou DBPROP_IRowsetScroll et DBPROP_IRowsetChange ou DBPROP_IRowsetUpdate|VARIANT_TRUE|Possibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement et l'extraction dans l'une ou l'autre direction. Les signets et le positionnement absolu par le biais de **IRowsetLocate** sont pris en charge dans l’ensemble de lignes. Le texte de la commande peut contenir une clause ORDER BY.|  
|DBPROP_IMMOBILEROWS|VARIANT_FALSE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement vers l'avant uniquement. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut inclure une clause ORDER BY s'il existe un index sur les colonnes référencées.<br /><br /> DBPROP_IMMOBILEROWS est disponible uniquement dans les ensembles de lignes qui peuvent afficher des lignes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] insérées par des commandes sur d'autres sessions ou par d'autres utilisateurs. Toute tentative d'ouverture d'un ensemble de lignes avec la propriété définie à VARIANT_FALSE sur tout ensemble de lignes pour lequel DBPROP_OTHERINSERT ne peut pas être VARIANT_TRUE provoque une erreur.|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|Impossibilité de mettre à jour des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de l'ensemble de lignes. L'ensemble de lignes prend en charge le défilement vers l'avant uniquement. Le positionnement de ligne relatif est pris en charge. Le texte de la commande peut contenir une clause ORDER BY, sauf en cas de contrainte par une autre propriété.|  
  
 Un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensemble de lignes de fournisseur Native Client OLE DB pris en charge par un curseur côté serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être facilement créé sur une table ou une vue de base à l’aide de la méthode **IOpenRowset :: OpenRowset** . Spécifiez la table ou la vue par nom, et passez les jeux de propriétés d’ensemble de lignes nécessaires dans le paramètre *rgPropertySets*.  
  
 Le texte de la commande qui crée un ensemble de lignes est restreint lorsque le consommateur requiert que l'ensemble de lignes soit pris en charge par un curseur côté serveur. Plus spécifiquement, le texte de la commande est restreint à une instruction SELECT unique qui retourne un résultat d'ensemble de lignes unique ou à une procédure stockée qui implémente une instruction SELECT unique qui retourne un résultat d'ensemble de lignes unique.  
  
 Ces deux tableaux montrent les mappages de différentes propriétés OLE DB et les modèles de curseur. Ils indiquent également quelles propriétés d'ensemble de lignes doivent être définies pour utiliser un certain type de modèle de curseur.  
  
 Chaque cellule du tableau contient une valeur de la propriété d'ensemble de lignes pour le modèle de curseur spécifique. Le type de données de toutes les propriétés d'ensemble de lignes répertoriées plus haut dans cette rubrique est VT_BOOL et la valeur par défaut est VARIANT_FALSE. Les symboles suivants sont utilisés dans le tableau.  
  
 F = valeur par défaut (VARIANT_FALSE)  
  
 T = VARIANT_TRUE  
  
 
  \- = VARIANT_TRUE or VARIANT_FALSE  
  
 Pour utiliser un certain type de modèle de curseur, recherchez la colonne correspondant au modèle de curseur et recherchez toutes les propriétés d'ensemble de lignes avec la valeur « T » dans la colonne. Affectez la valeur VARIANT_TRUE à ces propriétés d'ensemble de lignes pour utiliser le modèle de curseur spécifique. Les propriétés d'ensemble de lignes avec '-' comme valeur peuvent être définies à VARIANT_TRUE ou VARIANT_FALSE.  
  
|Propriétés d’ensemble de lignes/modèles de curseur|Default<br /><br /> result<br /><br /> set<br /><br /> (RO)|Rapide<br /><br /> rapide<br /><br /> uniquement<br /><br /> (RO)|statique<br /><br /> (RO)|Keyset<br /><br /> clés<br /><br /> (RO)|  
|--------------------------------------|-------------------------------------------|--------------------------------------------|-----------------------|----------------------------------|  
|DBPROP_SERVERCURSOR|F|T|T|T|  
|DBPROP_DEFERRED|F|F|-|-|  
|DBPROP_IrowsetChange|F|F|F|F|  
|DBPROP_IrowsetLocate|F|F|-|-|  
|DBPROP_IrowsetScroll|F|F|-|-|  
|DBPROP_IrowsetUpdate|F|F|F|F|  
|DBPROP_BOOKMARKS|F|F|-|-|  
|DBPROP_CANFETCHBACKWARDS|F|F|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|F|F|-|-|  
|DBPROP_CANHOLDROWS|F|F|-|-|  
|DBPROP_LITERALBOOKMARKS|F|F|-|-|  
|DBPROP_OTHERINSERT|F|T|F|F|  
|DBPROP_OTHERUPDATEDELETE|F|T|F|T|  
|DBPROP_OWNINSERT|F|T|F|T|  
|DBPROP_OWNUPDATEDELETE|F|T|F|T|  
|DBPROP_QUICKSTART|F|F|-|-|  
|DBPROP_REMOVEDELETED|F|F|F|-|  
|DBPROP_IrowsetResynch|F|F|F|-|  
|DBPROP_CHANGEINSERTEDROWS|F|F|F|F|  
|DBPROP_SERVERDATAONINSERT|F|F|F|-|  
|DBPROP_UNIQUEROWS|-|F|F|F|  
|DBPROP_IMMOBILEROWS|-|-|-|T|  
  
|Propriétés d'ensemble de lignes/modèles de curseur|Dynamique (RO)|Jeu de clés (R/W)|Dynamique (R/W)|  
|--------------------------------------|--------------------|---------------------|----------------------|  
|DBPROP_SERVERCURSOR|T|T|T|  
|DBPROP_DEFERRED|-|-|-|  
|DBPROP_IrowsetChange|F|-|-|  
|DBPROP_IrowsetLocate|F|-|F|  
|DBPROP_IrowsetScroll|F|-|F|  
|DBPROP_IrowsetUpdate|F|-|-|  
|DBPROP_BOOKMARKS|F|-|F|  
|DBPROP_CANFETCHBACKWARDS|-|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|-|-|-|  
|DBPROP_CANHOLDROWS|F|-|F|  
|DBPROP_LITERALBOOKMARKS|F|-|F|  
|DBPROP_OTHERINSERT|T|F|T|  
|DBPROP_OTHERUPDATEDELETE|T|T|T|  
|DBPROP_OWNINSERT|T|T|T|  
|DBPROP_OWNUPDATEDELETE|T|T|T|  
|DBPROP_QUICKSTART|-|-|-|  
|DBPROP_REMOVEDELETED|T|-|T|  
|DBPROP_IrowsetResynch|-|-|-|  
|DBPROP_CHANGEINSERTEDROWS|F|-|F|  
|DBPROP_SERVERDATAONINSERT|F|-|F|  
|DBPROP_UNIQUEROWS|F|F|F|  
|DBPROP_IMMOBILEROWS|F|T|F|  
  
 Pour un jeu particulier de propriétés d'ensemble de lignes, le modèle de curseur sélectionné est déterminé comme suit.  
  
 À partir de la collection spécifiée de propriétés d'ensemble de lignes, obtenez un sous-ensemble de propriétés répertoriées dans les tableaux précédents. Divisez ces propriétés en deux sous-groupes selon la valeur de l'indicateur, requis (T, F) ou facultatif (-), de chaque propriété d'ensemble de lignes. Pour chaque modèle de curseur, commencez par la première table et déplacez-vous de gauche à droite. Comparez les valeurs des propriétés dans les deux sous-groupes avec les valeurs des propriétés correspondantes dans cette colonne. Le modèle de curseur qui n'a aucune incompatibilité avec les propriétés requises et le plus petit nombre d'incompatibilités avec les propriétés facultatives est sélectionné. S'il y a plusieurs modèles de curseur, celui situé le plus à gauche est choisi.  
  
## <a name="sql-server-cursor-block-size"></a>Taille de bloc des curseurs SQL Server  
 Lorsqu’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseur prend en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge un ensemble de lignes de fournisseur Native Client OLE DB, le nombre d’éléments dans le paramètre de tableau de handles de ligne des méthodes **IRowset :: GetNextRows** ou **IRowsetLocate :: GetRowsAt** définit la taille du bloc de curseur. Les lignes indiquées par les descripteurs dans le tableau sont les membres du bloc de curseur.  
  
 Pour les ensembles de lignes qui prennent en charge les signets, les descripteurs de ligne récupérés à l’aide de la méthode **IRowsetLocate::GetRowsByBookmark** définissent les membres du bloc de curseur.  
  
 Quelle que soit la méthode utilisée pour remplir l'ensemble de lignes et former le bloc de curseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], celui-ci est actif jusqu'à ce que la méthode d'extraction de ligne suivante soit exécutée sur l'ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
