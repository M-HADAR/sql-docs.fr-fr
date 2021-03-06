---
title: 'Tutoriel R + T-SQL : Exécuter des prédictions'
description: Tutoriel montrant comment rendre opérationnel un script R incorporé dans des procédures stockées SQL Server avec des fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4b8e516d2e96c1cc4812a36800fd22371729445d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73724868"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Leçon 4 : Exécuter des prédictions avec un script R incorporé dans une procédure stockée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un tutoriel pour développeurs SQL expliquant comment utiliser le langage R dans SQL Server.

Dans cette étape, vous allez apprendre à utiliser le modèle pour prédire des résultats potentiels à partir de nouvelles observations. Le modèle est encapsulé dans une procédure stockée qui peut être appelée directement par d’autres applications. La procédure pas à pas montre plusieurs façons d’effectuer le scoring :

- **Mode de scoring par lot** : utilisez une requête SELECT comme entrée de la procédure stockée. La procédure stockée retourne une table d’observations correspondant aux cas d’entrée.

- **Mode de scoring individuel** : transmettez un ensemble de valeurs de paramètres individuels sous forme d’entrée.  La procédure stockée retourne une seule ligne ou valeur.

Tout d’abord, examinons le fonctionnement du calcul de score en général.

## <a name="basic-scoring"></a>Scoring de base

La procédure stockée **RxPredict** illustre la syntaxe de base pour l’encapsulation d’un appel RevoScaleR rxPredict dans une procédure stockée.

```sql
CREATE PROCEDURE [dbo].[RxPredict] (@model varchar(250), @inquery nvarchar(max))
AS 
BEGIN 

DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ L’instruction SELECT obtient le modèle sérialisé à partir de la base de données et stocke le modèle dans la variable R `mod` pour un traitement ultérieur en utilisant R.

+ Les nouveaux cas de scoring sont obtenus à partir de la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifiée dans `@inquery`, premier paramètre de la procédure stockée. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`. Cette trame de données est transmise à la fonction [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) de [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), qui génère les scores.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Une trame de données ne pouvant contenir qu’une seule ligne, vous pouvez utiliser le même code pour le calcul de score unique ou de lot.
  
+ La valeur retournée par la fonction `rxPredict` est une valeur flottante (**float**) qui représente la probabilité que le chauffeur recevra un pourboire, quel qu’en soit le montant.

## <a name="batch-scoring-a-list-of-predictions"></a>Scoring par lot (liste de prédictions)

Un scénario plus courant est celui où des prédictions sont générées pour plusieurs observations en mode batch. Dans cette étape, nous allons voir comment fonctionne le scoring par lot.

1.  Commençons par nous procurer un jeu de données d’entrée plus petit sur lequel travailler. Cette requête crée une liste « top 10 » des trajets avec le nombre de passagers et d’autres caractéristiques nécessaires pour établir une prédiction.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Exemples de résultats**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Créez une procédure stockée appelée **RxPredictBatchOutput** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```sql
    CREATE PROCEDURE [dbo].[RxPredictBatchOutput] (@model varchar(250), @inquery nvarchar(max))
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Fournissez le texte de requête dans une variable et transmettez-le en tant que paramètre à la procédure stockée :

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
La procédure stockée retourne une série de valeurs représentant la prédiction pour chacun des 10 principaux trajets. Cependant, les principaux trajets sont aussi des trajets à passager unique relativement courts, pour lesquels le chauffeur a peu de chances de recevoir un pourboire.
  

> [!TIP]
> 
> Au lieu de retourner simplement les résultats « pourboire/pas de pourboire », vous pouvez aussi retourner le score de probabilité pour la prédiction, puis appliquer une clause WHERE aux valeurs de la colonne _Score_ pour classer le score dans la catégorie « pourboire probable » ou « pourboire peu probable », en utilisant une valeur de seuil, par exemple 0,5 ou 0,7. Cette étape n’est pas incluse dans la procédure stockée, mais elle est facile à implémenter.

## <a name="single-row-scoring-of-multiple-inputs"></a>Scoring sur une ligne de plusieurs entrées

Parfois, vous souhaitez transmettre plusieurs valeurs d’entrée et obtenir une seule prédiction à partir de ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application web ou un rapport Reporting Services pour appeler la procédure stockée et fournir des entrées tapées ou sélectionnées par les utilisateurs de ces applications.

Dans cette section, vous allez créer des prédictions uniques en utilisant une procédure stockée qui prend plusieurs entrées, comme le nombre de passagers, la distance du trajet, etc. La procédure stockée crée un score basé sur le modèle R stocké précédemment.
  
Si vous appelez la procédure stockée à partir d’une application externe, vérifiez que les données correspondent aux critères du modèle R. Vous pourriez par exemple vérifier que les données d’entrée peuvent être transtypées ou converties en un type de données R, ou valider le type de données et la longueur des données. 

1. Créez une procédure stockée **RxPredictSingleRow**.
  
    ```sql
    CREATE PROCEDURE [dbo].[RxPredictSingleRow] @model varchar(50), @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```

2. Essayez-la en fournissant les valeurs manuellement.
  
    Ouvrez une nouvelle fenêtre **Requête** et appelez la procédure stockée en fournissant des valeurs pour chacun des paramètres. Les paramètres représentent les colonnes des caractéristiques utilisées par le modèle et sont obligatoires.

    ```sql
    EXEC [dbo].[RxPredictSingleRow] @model = 'RxTrainLogit_model',
    @passenger_count = 1,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = -73.977303
    ```

    Vous pouvez aussi utiliser cette forme abrégée pour les [paramètres d’une procédure stockée](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters) :
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Les résultats indiquent que la probabilité de recevoir un pourboire est faible (zéro) sur ces 10 principaux trajets, qui sont tous des trajets à passager unique sur une distance relativement courte.

## <a name="conclusions"></a>Conclusions

Cela conclut le didacticiel. Maintenant que vous savez comment incorporer du code R dans les procédures stockées, vous pouvez étendre ces pratiques pour créer vos propres modèles. L’intégration à [!INCLUDE[tsql](../../includes/tsql-md.md)] simplifie grandement le déploiement de modèles R pour la prédiction et l’incorporation de la reformation de modèle dans le cadre d’un workflow de données d’entreprise.

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 3 : Entraîner et enregistrer un modèle R en utilisant T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
