---
title: Créer une clé principale de base de données | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6c8e1609b60013a3adabd04e0b3ce8e08e825d5e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957470"
---
# <a name="create-a-database-master-key"></a>Créer une clé principale de base de données

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Cette rubrique explique comment créer une clé principale de base de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)].

## <a name="security"></a>Sécurité

### <a name="permissions"></a>Autorisations

Requiert l'autorisation CONTROL sur la base de données.

## <a name="using-transact-sql"></a>Utilisation de Transact-SQL

### <a name="to-create-a-database-master-key"></a>Pour créer une clé principale de base de données

1. Choisissez un mot de passe pour chiffrer la copie de la clé principale qui sera stockée dans la base de données.
2. Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Développez **Bases de données système**, cliquez avec le bouton droit sur `master`, puis cliquez sur **Nouvelle requête**.
4. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.

   ```sql
     -- Creates the master key.
     -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."  
     CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  

   ```

Pour plus d’informations, consultez [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-master-key-transact-sql.md).
