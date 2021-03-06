---
title: Propriétés de séquence (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sequence.general.f1
ms.assetid: 0187f413-cdf0-48a2-b2e6-9b3578cd5811
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 846e7960e9aca4bfb5deea8f50eae3c8a2f58c70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63184438"
---
# <a name="sequence-properties-general-page"></a>Propriétés de séquence (page Général)
  Crée un objet séquence et spécifie ses propriétés. Une séquence est un objet lié par schéma défini par l'utilisateur qui génère une séquence de valeurs numériques d'après la spécification avec laquelle la séquence a été créée. La séquence de valeurs numériques est générée dans un ordre croissant ou décroissant à un intervalle défini et peut être configurée pour redémarrer (cycle) lorsque épuisée. Les séquences, contrairement aux colonnes d'identité, ne sont pas associées aux tables spécifiques. Les applications font référence à un objet séquence pour extraire sa valeur suivante. La relation entre les séquences et les tables est contrôlée par l'application. Les applications utilisateur peuvent référencer un objet séquence et coordonner les valeurs sur plusieurs lignes et tables.  
  
 Contrairement aux valeurs des colonnes d’identité générées au moment de l’insertion, une application peut obtenir le numéro séquentiel suivant sans insérer la ligne en appelant la [fonction NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql). Utilisez [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) pour obtenir plusieurs numéros séquentiels à la fois.  
  
 Pour obtenir des informations et des scénarios qui utilisent à la fois **CREATE SEQUENCE** et la fonction **NEXT VALUE FOR** , consultez [Numéros de séquence](sequence-numbers.md).  
  
 Cette page est accessible de deux manières : soit en cliquant avec le bouton droit sur **Séquences** dans l’Explorateur d’objets et en sélectionnant **Nouvelle séquence**, soit en cliquant avec le bouton droit sur une séquence existante et en sélectionnant **Propriétés**. Quand vous cliquez avec le bouton droit sur une séquence et que vous choisissez **Propriétés**, les options ne sont pas modifiables. Pour modifier les options de séquence, utilisez l’instruction [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) ou supprimez et recréez l’objet séquence.  
  
## <a name="options"></a>Options  
 **Nom de la séquence**  
 Entrez ici le nom de la séquence.  
  
 **Schéma de séquence**  
 Spécifiez le schéma qui détiendra cette séquence.  
  
 **Type de données**  
 Une séquence peut être définie comme tout type entier. notamment :  
  
|Type de données|Plage|  
|---------------|-----------|  
|`tinyint`|0 à 255|  
|`smallint`|-32 768 à 32 767|  
|`int`|-2 147 483 648 à 2 147 483 647|  
|`bigint`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|  
  
-   
  `decimal` ou `numeric` avec une échelle de 0.  
  
-   Tout type de données défini par l'utilisateur (type d'alias) basé sur l'un de ces types.  
  
 **Précision**  
 Pour les types de données `decimal` ou `numeric`, spécifiez la précision. (L'échelle est toujours 0.)  
  
 **Commencer par la valeur**  
 Première valeur qui sera retournée par l'objet séquence. La valeur **START** doit être une valeur inférieure ou égale à la valeur maximale, et supérieure ou égale à la valeur minimale de l’objet séquence. La valeur de début par défaut d'un nouvel objet séquence correspond à la valeur minimale pour un objet séquence croissant et à la valeur maximale pour un objet séquence décroissant.  
  
 **Incrémenter de**  
 Valeur utilisée pour incrémenter (ou décrémenter en cas de valeurs négatives) la valeur de l’objet séquence pour chaque appel à la fonction **NEXT VALUE FOR** . Si l'incrément est une valeur négative, l'objet séquence décroît ; sinon, il augmente. L'incrément ne peut pas avoir la valeur 0.  
  
 **Valeur minimale**  
 Spécifie les limites de l'objet séquence. La valeur minimale par défaut d'un nouvel objet séquence correspond à la valeur minimale du type de données de l'objet séquence. Il s'agit de zéro pour le type de données `tinyint` et d'un nombre négatif pour tous les autres types de données.  
  
 **Valeur maximale**  
 Spécifie les limites de l'objet séquence. La valeur maximale par défaut d'un nouvel objet séquence correspond à la valeur maximale du type de données de l'objet séquence.  
  
 **Cycle-la séquence redémarre en cas de limite atteinte**  
 Sélectionnez cette option pour autoriser l'objet séquence à redémarrer à partir de la valeur minimale (ou maximale pour les objets séquences décroissants) lorsque sa valeur minimale ou maximale est atteinte.  
  
> [!NOTE]  
>  La répétition du cycle ne redémarre pas à partir de la valeur de début, mais plutôt à partir de la valeur minimale/maximale.  
  
 **Options du cache**  
 La création d'un cache de valeurs de séquence peut augmenter les performances des applications qui utilisent des objets séquences en réduisant le nombre d'entrées/sorties sur le disque requises pour créer des numéros séquentiels.  
  
-   Taille du cache par défaut : le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sélectionne une taille. Toutefois, les utilisateurs ne doivent pas s’attendre à une sélection cohérente. [!INCLUDE[msCoName](../../includes/msconame-md.md)] peut modifier la méthode de calcul de la taille du cache sans préavis.  
  
-   Pas de cache : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne met pas en cache les numéros séquentiels.  
  
-   Cache avec taille - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mettra en cache les valeurs de séquence. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] effectue le suivi de la valeur actuelle et du nombre de valeurs restées dans le cache. Par conséquent, la quantité de mémoire requise pour stocker le cache correspond toujours à deux instances du type de données de l'objet séquence  
  
 En cas de création avec l'option CACHE, un arrêt inattendu, tel qu'une panne de courant, peut conduire à la perte des numéros séquentiels dans le cache.  
  
 Pour plus d’informations sur les options de création de séquence, consultez [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **CREATE SEQUENCE**, **ALTER**ou **CONTROL** sur le SCHEMA.  
  
## <a name="see-also"></a>Voir aussi  
 [sys. sequences &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)  
  
  
