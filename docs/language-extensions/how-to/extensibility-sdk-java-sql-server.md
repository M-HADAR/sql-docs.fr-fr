---
title: SDK d’extensibilité Microsoft pour Java
description: Découvrez comment vous pouvez implémenter un programme Java pour SQL Server avec le SDK d’extensibilité Microsoft pour Java. Le kit SDK est une interface pour l’extension de langage Java, qui permet d’échanger des données avec SQL Server et d’exécuter du code Java à partir de SQL Server.
ms.prod: sql
ms.technology: language-extensions
ms.date: 11/05/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 66719e8a30b9e7f4e42eaba376c73af9eb9868b2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73658856"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Kit SDK d’extensibilité Microsoft pour Java pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Découvrez comment vous pouvez implémenter un programme Java pour SQL Server avec le SDK d’extensibilité Microsoft pour Java. Le kit SDK est une interface pour l’extension de langage Java, qui permet d’échanger des données avec SQL Server et d’exécuter du code Java à partir de SQL Server.

Le kit SDK est installé dans le cadre de SQL Server 2019 version Release Candidate 1 sur Windows et Linux :

+ Chemin d’installation par défaut sur Windows : **[répertoire de base de l’installation de l’instance]\MSSQL\Binn\mssql-java-lang-extension.jar**
+ Chemin d’installation par défaut sur Linux : **/opt/mssql/lib/mssql-java-lang-extension.jar**

Le code est open source et se trouve dans le [dépôt GitHub des extensions de langage SQL Server](https://github.com/microsoft/sql-server-language-extensions).

## <a name="implementation-requirements"></a>Exigences d’implémentation

L’interface du kit SDK définit un ensemble d’exigences à remplir pour permettre à SQL Server de communiquer avec le runtime Java. Pour utiliser le kit SDK, vous devez suivre certaines règles d’implémentation dans votre classe principale. SQL Server peut ensuite exécuter une méthode spécifique dans la classe Java et échanger des données à l’aide de l’extension de langage Java.

Pour obtenir un exemple d’utilisation du kit SDK, consultez [Tutoriel : Rechercher une chaîne à l’aide d’expressions régulières (regex) en Java](../tutorials/search-for-string-using-regular-expressions-in-java.md).

## <a name="sdk-classes"></a>Classes du kit SDK

Le kit SDK comprend trois classes.

Deux classes abstraites qui définissent l’interface utilisée par l’extension Java pour échanger des données avec SQL Server :

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

La troisième classe est une classe d’assistance, qui contient une implémentation d’un objet de jeu de données. Il s’agit d’une classe facultative qui facilite la prise en main. Vous pouvez également utiliser votre propre implémentation d’une telle classe à la place.

- **PrimitiveDataset**

Vous trouverez ci-dessous une description de chaque classe du kit SDK. Le code source des classes du kit SDK est disponible dans le [dépôt GitHub des extensions de langage SQL Server](https://github.com/microsoft/sql-server-language-extensions/tree/master/language-extensions/java/sdk).

### <a name="class-abstractsqlserverextensionexecutor"></a>Classe : AbstractSqlServerExtensionExecutor

La classe abstraite **AbstractSqlServerExtensionExecutor** contient l’interface qui permet l’exécution du code Java par l’extension de langage Java pour SQL Server.

Votre classe Java principale doit hériter de cette classe. Hériter de cette classe signifie que vous devez implémenter certaines méthodes de la classe dans votre propre classe.

Pour hériter de cette classe abstraite, étendez-la à l’aide de son nom de classe abstraite dans la déclaration de classe :

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

Au minimum, votre classe principale doit implémenter la méthode execute (...).

#### <a name="method-execute"></a>Méthode execute

La méthode execute est la méthode appelée à partir de SQL Server via l’extension de langage Java, et qui permet d’appeler du code Java à partir de SQL Server. Il s’agit d’une méthode clé dans laquelle vous incluez les principales opérations à exécuter à partir de SQL Server.

Pour passer des arguments de méthode à Java à partir de SQL Server, utilisez le paramètre `@param` dans `sp_execute_external_script`. La méthode **execute** accepte ses arguments de cette manière.

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

#### <a name="method-init"></a>Méthode init

La méthode init est exécutée après le constructeur et avant la méthode execute. Toutes les opérations qui doivent être effectuées avant execute(...) peuvent l’être avec cette méthode.

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="class-abstractsqlserverextensiondataset"></a>Classe : AbstractSqlServerExtensionDataset

La classe abstraite **AbstractSqlServerExtensionDataset** contient l’interface de gestion des données d’entrée et de sortie utilisées par l’extension Java.


### <a name="class-primitivedataset"></a>Classe : PrimitiveDataset

La classe **PrimitiveDataset** est une implémentation de **AbstractSqlServerExtensionDataset** qui stocke les types simples en tant que tableaux de primitives.

Elle est fournie dans le kit SDK simplement en tant que classe d’assistance facultative. Si vous n’utilisez pas cette classe, vous devez implémenter votre propre classe, qui hérite de **AbstractSqlServerExtensionDataset**.  

## <a name="next-steps"></a>Étapes suivantes

+ [Tutoriel : Rechercher une chaîne à l’aide d’expressions régulières (regex) en Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
+ [Guide pratique pour appeler Java dans SQL Server](call-java-from-sql.md)
