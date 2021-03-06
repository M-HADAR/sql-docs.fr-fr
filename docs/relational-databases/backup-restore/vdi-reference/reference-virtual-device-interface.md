---
title: Informations de référence sur les interfaces d’appareil virtuel
titlesuffix: SQL Server VDI reference
description: Cet article fournit une vue d’ensemble des informations de référence sur les interfaces d’appareil virtuel pour la sauvegarde SQL Server.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b4556734044ad5bd688f8d5b286885450897b42
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847150"
---
# <a name="virtual-device-interface-vdi-reference"></a>Informations de référence sur les interfaces d’appareil virtuel

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette section contient les spécifications pour les interfaces de programmation d’application SQL Server destinées à être utilisées par des fournisseurs de logiciels de sauvegarde tiers.

## <a name="overview"></a>Vue d’ensemble

L’interface VDI (Virtual Device Interface) fournit le débit de sauvegarde en ligne le plus élevé avec une dégradation minimale de la charge de travail des transactions, ainsi que les temps de restauration les plus courts possibles. Elle permet aux fournisseurs tiers d’obtenir les mêmes caractéristiques de performances que la sauvegarde/restauration native de SQL Server et rend disponible la gamme complète des fonctionnalités de sauvegarde/restauration. L’interface VDI a été introduite dans SQL Server 7.0, et elle est prise en charge et améliorée dans ses versions ultérieures.

VDI prend en charge deux types principaux de technologies de sauvegarde :

- Les sauvegardes en ligne conventionnelles, où le contenu entier du jeu de sauvegarde est lu et transféré vers le support de sauvegarde.

- Les sauvegardes d’instantanés effectuées avec la technologie sous-jacente de miroir partagé ou de copie sur écriture.

Les sauvegardes en ligne conventionnelles effectuées via VDI peuvent tirer parti de la gamme complète des fonctionnalités de sauvegarde et de restauration de SQL Server. Les sauvegardes d’instantanés sont limitées aux sauvegardes de bases de données complètes et de fichiers/groupes de fichiers. Cependant, les sauvegardes d’instantanés peuvent être restaurées par progression avec les sauvegardes conventionnelles suivantes : différentielles de base de données, différentielles de fichier et journal des transactions.

## <a name="next-steps"></a>Étapes suivantes

Passez en revue la documentation de référence sur VDI dans cette section.

Téléchargez la spécification complète et les fichiers sources de prise en charge :

[SQL Server 2005 Virtual Backup Device Interface (VDI) Specification](https://www.microsoft.com/download/details.aspx?id=17282)