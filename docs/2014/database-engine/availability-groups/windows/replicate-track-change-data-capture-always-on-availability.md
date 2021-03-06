---
title: Réplication, Change Tracking, capture de données modifiées et groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], AlwaysOn Availability Groups
- change data capture [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: e17a9ca9-dd96-4f84-a85d-60f590da96ad
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c52283ce9d512da6dc2e5ad05a4c8356524bef01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62814055"
---
# <a name="replication-change-tracking-change-data-capture-and-alwayson-availability-groups-sql-server"></a>Réplication, suivi des modifications, capture de données modifiées et groupes de disponibilité AlwaysOn (SQL Server)
  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] La réplication, la capture de données modifiées (CDC) et le suivi des modifications (CT) sont pris en charge sur [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aide à fournir des fonctionnalités haute disponibilité et de récupération de base de données supplémentaires.  
  
 
  
##  <a name="Overview"></a>Vue d’ensemble de la réplication sur groupes de disponibilité AlwaysOn  
  
###  <a name="PublisherRedirect"></a>Redirection de l’éditeur  
 Lorsqu'une base de données publiée repose sur la technologie [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], le serveur de distribution qui offre un accès d'agent à la base de données de publication est configuré avec des entrées redirected_publishers. Ces entrées redirigent la combinaison serveur de publication/base de données initialement configurée, en se servant d'un nom d'écouteur de groupe de disponibilité pour se connecter au serveur de publication et à la base de données de publication. Les connexions établies via le nom d'écouteur de groupe de disponibilité échouent lors d'un basculement. Lors du redémarrage de l'agent de réplication, à l'issue du basculement, la connexion est automatiquement redirigée vers le nouveau principal.  
  
 Dans un groupe de disponibilité AlwaysOn, une base de données secondaire ne peut pas être un serveur de publication. La republication n'est pas prise en charge lorsque la réplication est associée à [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
 Si une base de données publiée est membre d'un groupe de disponibilité et que le serveur de publication est redirigé, il doit être redirigé vers un nom d'écouteur de groupe de disponibilité associé au groupe de disponibilité. Il ne peut pas être redirigé vers un nœud explicite.  
  
> [!NOTE]  
>  Après un basculement vers un réplica secondaire, le Moniteur de réplication ne peut pas ajuster le nom de l'instance de publication de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et continue à afficher les informations de réplication sous le nom de l'instance principale [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]d'origine. Après le basculement, un jeton de suivi ne peut pas être écrit à l'aide du Moniteur de réplication, toutefois un jeton de suivi écrit sur le nouveau serveur de publication à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)]est visible dans le Moniteur de réplication.  
  
###  <a name="Changes"></a>Modifications générales apportées aux agents de réplication pour prendre en charge groupes de disponibilité AlwaysOn  
 Trois agents de réplication ont été modifiés pour prendre en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. L'agent de lecture du journal, ainsi que les agents d'instantané et de fusion ont été modifiés pour interroger la base de données de distribution pour le serveur de publication redirigé et pour utiliser le nom d'écouteur de groupe de disponibilité retourné, si un serveur de publication redirigé était déclaré, pour se connecter au serveur de publication de base de données.  
  
 Par défaut, lorsque les agents interrogent le serveur de distribution afin de déterminer si le serveur de publication d'origine a été redirigé, l'adéquation de la cible actuelle ou de la redirection est vérifiée avant de retourner l'hôte redirigé à l'agent. Il s'agit du comportement recommandé. Toutefois, si le démarrage de l'agent se produit très fréquemment, la surcharge liée à la procédure stockée de validation peut être considérée comme trop importante. Un nouveau commutateur de ligne de commande, *BypassPublisherValidation*, a été ajouté à l'agent de lecture du journal, ainsi qu'aux agents d'instantané et de fusion. Lorsque le commutateur est utilisé, le serveur de publication redirigé est retourné immédiatement à l'agent et l'exécution de la procédure stockée de validation est ignorée.  
  
 Les échecs retournés de la procédure stockée de validation sont consignés dans les journaux d'historique de l'agent. Les erreurs dont le niveau de gravité est supérieur ou égal à 16 entraîneront l'arrêt des agents. Certaines fonctions de reprise ont été intégrées aux agents afin de gérer la déconnexion attendue d'une base de données publiée en cas de basculement vers un nouveau principal.  
  
#### <a name="log-reader-agent-modifications"></a>Modifications apportées à l'agent de lecture du journal  
 L'agent de lecture du journal comporte les modifications suivantes.  
  
-   **Cohérence de la base de données répliquée**  
  
     Lorsqu'une base de données publiée est membre d'un groupe de disponibilité AlwaysOn, par défaut l'agent de lecture du journal ne traite pas les enregistrements de journal qui n'ont pas déjà été renforcés au niveau de tous les réplicas secondaires de groupe de disponibilité. Cela permet de s'assurer que lors du basculement, toutes les lignes répliquées sur un abonné sont également présentes dans le nouveau principal.  
  
     Lorsque le serveur de publication dispose de deux réplicas de disponibilité AlwaysOn uniquement (un principal et un secondaire) et qu'un basculement a lieu, le réplica principal d'origine reste arrêté, car le lecteur de journal n'avance pas tant que toutes les bases de données secondaires ne sont pas remises en ligne ou tant que les réplicas secondaires défaillants n'ont pas été supprimés du groupe de disponibilité. Le lecteur de journal, qui s'exécute à présent sur la base de données secondaire, n'avance pas étant donné que AlwaysOn ne peut pas renforcer de modifications sur une base de données secondaire. Pour permettre au lecteur de journal de poursuivre et de continuer à disposer de la capacité de récupération d'urgence, supprimez le réplica principal d'origine du groupe de disponibilité à l'aide de ALTER AVAILABITY GROUP <nom_groupe> REMOVE REPLICA. Ajoutez ensuite un nouveau réplica secondaire au groupe de disponibilité.  
  
-   **Indicateur de trace 1448**  
  
     L'indicateur de trace 1448 permet à l'agent de lecture du journal de réplication d'avancer même si les réplicas secondaires asynchrones n'ont pas accusé réception d'une modification. Même si cet indicateur de trace est activé, l'agent de lecture de journal attend toujours les réplicas secondaires synchrones. L'agent de lecture du journal n'ira pas au delà de l'accusé réception minimum des réplicas secondaires synchrones. Cet indicateur de trace s'applique à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], et pas simplement à un groupe de disponibilité, à une base de données de disponibilité ou à une instance de l'agent de lecture de journal. Cet indicateur de trace prend effet immédiatement, sans redémarrage. Il peut être activé d'avance ou lorsque le réplica secondaire asynchrone échoue.  
  
###  <a name="StoredProcs"></a>Procédures stockées prenant en charge AlwaysOn  
  
-   **sp_redirect_publisher**  
  
     La procédure stockée **sp_redirect_publisher** permet de spécifier un serveur de publication redirigé pour une combinaison existante serveur de publication/base de données. Si la base de données du serveur de publication appartient à un groupe de disponibilité, le serveur de publication redirigé correspond au nom d'écouteur de groupe de disponibilité.  
  
-   **Sp_get_redirected_publisher**  
  
     La procédure stockée **sp_get_redirected_publisher** permet aux agents de réplication d’interroger un serveur de distribution pour déterminer si une combinaison serveur de publication/base de données dispose d’un serveur de publication redirigé défini. Cette procédure stockée remplit deux objectifs. En premier lieu, elle permet à l'agent de déterminer si le serveur de publication d'origine a été redirigé. Ensuite, elle peut également initier une procédure stockée de validation exécutée sur le serveur de distribution (**sp_validate_redirected_publisher**) qui vérifie l’adéquation du nœud cible de la redirection pour servir de serveur de publication pour la base de données nommée.  
  
     Pour exécuter cette procédure stockée, l’appelant doit être membre du rôle serveur **sysadmin** , du rôle de base de données **db_owner** de la base de données de distribution, ou être membre d’une **liste d’accès à une publication** pour une publication définie associée à la base de données du serveur de publication.  
  
-   **sp_validate_redirected_publisher**  
  
     Cette procédure stockée tente de valider que le serveur de publication actuel est capable d'héberger la base de données publiée. Elle peut être appelée à tout moment pour vérifier que l'hôte actuel de la base de données publiée est en mesure de prendre en charge la réplication.  
  
-   **sp_validate_replicate_hosts_as_publishers**  
  
     S'il est utile que les agents vérifient que le serveur principal actuel peut fonctionner comme serveur de publication de réplication pour une base de données du serveur de publication, une fonctionnalité de validation plus générale est nécessaire pour établir la validité d'une topologie de réplication dans une base de données de disponibilité AlwaysOn. La procédure stockée **sp_validate_replica_hosts_as_publishers** est conçue pour satisfaire à ce besoin.  
  
     Cette procédure stockée est toujours exécutée manuellement. L'appelant doit être **sysadmin** sur le serveur de distribution, **dbowner** de la base de données de distribution ou un membre de la **liste d'accès à la publication** d'une publication de la base de données du serveur de publication. En outre, l'identifiant de connexion de l'appelant doit être un identifiant valide pour tous les hôtes de réplica de groupe de disponibilité, et disposer de privilèges de sélection sur la base de données de disponibilité associée à la base de données du serveur de publication.  
  
###  <a name="CDC"></a> Capture de données modifiées  
 Les bases de données activées pour la capture de données modifiées (CDC) peuvent tirer parti de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] afin d'assurer que non seulement la base de données reste disponible en cas de défaillance, mais également que les modifications apportées aux tables de base de données continuent d'être surveillées et déposées dans les tables de modifications de capture de données modifiées. L'ordre dans lequel la capture de données modifiées et [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] sont configurés n'est pas important. Les bases de données activées pour la capture de données modifiées peuvent être ajoutées à [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], et celles qui sont membres d'un groupe de disponibilité AlwaysOn peuvent être activées pour la capture de données modifiées. Dans les deux cas, toutefois, la configuration de la capture de données modifiées est toujours effectuée sur le réplica principal actuel ou prévu. CDC utilise l'agent de lecture du journal et est soumis aux mêmes limitations décrites dans la section **Modifications apportées à l'agent de lecture du journal** plus haut dans cette rubrique.  
  
-   **Récolte des modifications pour la capture de données modifiées sans réplication**  
  
     Si la capture de données modifiées est activée pour une base de données, mais que la réplication ne l'est pas, le processus de capture utilisé pour récolter les modifications à partir du journal et les déposer dans les tables de modifications de capture de données modifiées s'exécute au niveau de l'hôte de capture de données modifiées comme son propre travail de l'Agent SQL.  
  
     Pour reprendre la récolte des modifications après un basculement, la procédure stockée **sp_cdc_add_job** doit être exécutée au niveau du nouveau principal pour créer le travail de capture local.  
  
     L'exemple suivant crée le travail de capture.  
  
    ```  
    EXEC sys.sp_cdc_add_job @job_type = 'capture';  
    ```  
  
-   **Récolte des modifications pour la capture de données modifiées avec réplication**  
  
     Si la capture de données modifiées et la réplication sont activées pour une base de données, le lecteur de journal gère le flux des tables de modifications de capture de données modifiées. Dans ce cas, les techniques utilisées par la réplication pour tirer parti de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] s'assurent que les modifications continuent d'être récoltées à partir du journal et à être déposées dans les tables de modifications de capture de données modifiées après le basculement. Aucune opération supplémentaire ne doit être effectuée pour la capture de données modifiées dans cette configuration pour que les tables de modifications soient remplies.  
  
-   **Nettoyage de la capture de données modifiées**  
  
     Pour s'assurer que le nettoyage approprié se produit au niveau de la nouvelle base de données principale, un travail local de nettoyage doit toujours être créé. L'exemple suivant crée le travail de nettoyage.  
  
    ```  
    EXEC sys.sp_cdc_add_job @job_type = 'cleanup';  
    ```  
  
    > [!NOTE]  
    >  Vous devez créer les travaux au niveau de toutes les cibles possibles de basculement avant le basculement, et les marquer comme étant désactivés jusqu'à ce que le réplica de disponibilité sur un hôte devienne le nouveau réplica principal. Les travaux de capture de données modifiées s'exécutant au niveau de l'ancienne base de données principale doivent également être désactivés lorsque la base de données locale devient une base de données secondaire. Pour désactiver et activer des travaux, utilisez *@enabled* l’option de [Sp_update_job &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql). Pour plus d’informations sur la création de travaux de capture de données modifiées, consultez [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql).  
  
-   **Ajout de rôles de capture de données modifiées à un réplica de base de données principal AlwaysOn**  
  
     Lorsqu'une table est activée pour la capture de données modifiées, il est possible d'associer un rôle de base de données à l'instance de capture. Si un rôle est spécifié, l'utilisateur souhaitant utiliser les fonctions table de capture de données modifiées pour accéder à des modifications pour la table doit non seulement avoir un accès choisi aux colonnes de table faisant l'objet d'un suivi, mais doit également être membre du rôle nommé. Si le rôle spécifié n'existe pas encore, il sera créé. Lorsque des rôles de base de données sont ajoutés automatiquement à une base de données principale AlwaysOn, les rôles sont également propagés aux bases de données secondaires du groupe de disponibilité.  
  
-   **Applications clientes qui accèdent aux données de modification CDC et Always On**  
  
     Les applications clientes qui utilisent les fonctions table (TVF) ou des serveurs liés pour accéder aux données de la table de modifications ont également besoin de pouvoir localiser un hôte de capture de données modifiées approprié après le basculement. Le nom d'écouteur de groupe de disponibilité correspond au mécanisme fourni par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] pour permettre à une connexion, en toute transparence, d'être redirigée vers un hôte différent. Une fois qu'un nom d'écouteur de groupe de disponibilité est associé à un groupe de disponibilité, il peut être utilisé dans les chaînes de connexion TCP. Deux scénarios de connexion différents sont pris en charge par le biais du nom d'écouteur de groupe de disponibilité.  
  
    -   L'un garantit que les demandes de connexion sont toujours dirigées vers le réplica principal actuel.  
  
    -   L'autre garantit que les demandes de connexion sont dirigées vers un réplica secondaire en lecture seule.  
  
     Utilisée pour rechercher un réplica secondaire en lecture seule, une liste de routage en lecture seule doit également être définie pour le groupe de disponibilité. Pour plus d’informations sur l’accès de routage aux serveurs secondaires accessibles en lecture, consultez [Pour configurer des réplicas de disponibilité pour le routage en lecture seule](../../listeners-client-connectivity-application-failover.md#ConfigureARsForROR).  
  
    > [!NOTE]  
    >  Il existe un certain délai de propagation associé à la création d'un nom d'écouteur de groupe de disponibilité et son utilisation par les applications clientes afin d'accéder à un réplica de base de données du groupe de disponibilité.  
  
     Utilisez la requête suivante pour déterminer si un nom d'écouteur de groupe de disponibilité a été défini pour le groupe de disponibilité qui héberge une base de données CDC. La requête retourne le nom d'écouteur du groupe de disponibilité, s'il a été créé.  
  
    ```  
    SELECT dns_name   
    FROM sys.availability_group_listeners AS l  
    INNER JOIN sys.availability_databases_cluster AS d  
        ON l.group_id = d.group_id  
    WHERE d.database_name = N'MyCDCDB';  
    ```  
  
-   **Redirection de la charge de requête vers un réplica secondaire accessible en lecture**  
  
     Même si, dans de nombreux cas, une application cliente souhaite toujours se connecter au réplica principal actuel, il ne s'agit pas de la seule façon de tirer parti de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Si un groupe de disponibilité est configuré pour prendre en charge des réplicas secondaires accessibles en lecture, les données modifiées peuvent également être collectées à partir des nœuds secondaires.  
  
     Lorsqu'un groupe de disponibilité est configuré, l'attribut ALLOW_CONNECTIONS associé à SECONDARY_ROLE est utilisé pour spécifier le type d'accès secondaire pris en charge. Dans le cas d'une configuration de type ALL, toutes les connexions au serveur secondaire sont autorisées, mais seules celles nécessitant un accès en lecture seule aboutiront. Dans le cas d'une configuration de type READ_ONLY, il est nécessaire de spécifier l'intention en lecture seule lors de l'établissement de la connexion à la base de données secondaire pour que la connexion réussisse. Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
     La requête suivante peut être utilisée pour déterminer si l'intention en lecture seule est nécessaire pour se connecter à un réplica secondaire accessible en lecture.  
  
    ```  
    SELECT g.name AS AG, replica_server_name, secondary_role_allow_connections_desc  
    FROM sys.availability_replicas AS r  
    JOIN sys.availability_groups AS g  
        ON r.group_id = g.group_id  
    WHERE g.name = N'MY_AG_NAME;  
    ```  
  
     Le nom d'écouteur de groupe de disponibilité ou le nom du nœud explicite peut être utilisé pour rechercher le réplica secondaire. Si le nom d'écouteur du groupe de disponibilité est utilisé, l'accès est dirigé vers un réplica secondaire approprié.  
  
     Lorsque `sp_addlinkedserver` est utilisé pour créer un serveur lié afin d’accéder au serveur secondaire *@datasrc* , le paramètre est utilisé pour le nom de l’écouteur du groupe de disponibilité ou le *@provstr* nom du serveur explicite, et le paramètre est utilisé pour spécifier l’intention de lecture seule.  
  
    ```  
    EXEC sp_addlinkedserver   
    @server = N'linked_svr',   
    @srvproduct=N'SqlServer',  
    @provider=N'SQLNCLI11',   
    @datasrc=N'AG_Listener_Name',   
    @provstr=N'ApplicationIntent=ReadOnly',   
    @catalog=N'MY_DB_NAME';  
    ```  
  
-   **Accès client aux données de modification CDC et aux connexions de domaine**  
  
     En général, vous devez utiliser les connexions de domaine pour l'accès client aux données modifiées résidant dans les bases de données qui sont membres des groupes de disponibilité AlwaysOn. Pour garantir l'accès continu aux données modifiées après le basculement, l'utilisateur de domaine aura besoin des privilèges d'accès sur tous les hôtes prenant en charge les réplicas de groupe de disponibilité. Si un utilisateur de base de données est ajouté à une base de données dans un réplica principal et que l'utilisateur est associé à une connexion de domaine, l'utilisateur de base de données est propagé aux bases de données secondaires et continue d'être associé à la connexion de domaine spécifiée. Si le nouvel utilisateur de base de données est associé à une connexion d'authentification SQL Server, l'utilisateur au niveau des bases de données secondaires sera propagé sans connexion. Lorsque la connexion d'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] associée peut être utilisée pour accéder aux données modifiées au niveau du serveur principal où l'utilisateur de la base de données a été défini à l'origine, ce nœud est le seul où l'accès est possible. La connexion d'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne peut pas accéder aux données d'une base de données secondaire, ni à celles d'une nouvelle base de données primaire autre que la base de données d'origine où l'utilisateur de la base de données a été défini.  
  
###  <a name="CT"></a> Suivi des modifications  
 Une base de données activée pour le suivi des modifications peut faire partie d'un groupe de disponibilité AlwaysOn. Aucune configuration supplémentaire n’est nécessaire. Les applications clientes de suivi des modifications qui utilisent les fonctions table (TVF) de capture de données modifiées pour accéder aux données modifiées ont besoin de pouvoir localiser le réplica principal après le basculement. Si l'application cliente se connecte via le nom d'écouteur de groupe de disponibilité, les demandes de connexion seront toujours dirigées correctement vers le réplica principal actuel.  
  
> [!NOTE]  
>  Les données de suivi des modifications doivent toujours être obtenues à partir du réplica principal. Toute tentative d'accès aux données de modification depuis un réplica secondaire provoque l'erreur suivante :  
>   
>  Msg 22117, Niveau 16, État 1, Ligne 1  
>   
>  Pour les bases de données qui sont membres d'un réplica secondaire (pour les bases de données secondaires), le suivi des modifications n'est pas pris en charge. Exécutez les requêtes de suivi des modifications sur les bases de données du réplica principal.  
  
##  <a name="Prereqs"></a>Conditions préalables requises, restrictions et considérations relatives à l’utilisation de la réplication  
 Cette section décrit les considérations à prendre en compte pour déployer la réplication avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], y compris les conditions préalables requises, les restrictions et les recommandations.  
  
### <a name="prerequisites"></a>Conditions préalables requises  
  
-   Lors de l'utilisation de la réplication transactionnelle, si la base de données de publication se trouve dans un groupe de disponibilité, le serveur de publication et le serveur de distribution doivent exécuter au moins [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. L'abonné peut utiliser un niveau inférieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Lors de l'utilisation de la réplication de fusion, si la base de données de publication se trouve dans un groupe de disponibilité :  
  
    -   Abonnement par émission de données : le serveur de publication et le serveur de distribution doivent exécuter au moins [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
    -   Abonnement par extraction de données : le serveur de publication, le serveur de distribution et les bases de données de l'abonné doivent s'exécuter sur au moins [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Cela est dû au fait que l'Agent de fusion sur l'abonné doit comprendre la façon dont un groupe de disponibilité peut basculer sur son serveur secondaire.  
  
-   Le placement de la base de données de distribution sur un groupe de disponibilité n'est pas pris en charge.  
  
-   Les instances de serveur de publication satisfont toutes les conditions préalables requises pour faire partie d'un groupe de disponibilité AlwaysOn. Pour plus d’informations [, consultez conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
### <a name="restrictions"></a>Restrictions  
 Combinaisons de réplication prises en charge sur [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:  
  
|||||  
|-|-|-|-|  
||**Publisher**|Serveur de **distribution** <sup>3</sup>|**Abonné**|  
|**Transactionnelle**|Oui<sup>1</sup>|Non|Oui<sup>2</sup>|  
|**P2P**|Non|Non|Non|  
|**Fusionner**|Oui|Non|Oui<sup>2</sup>|  
|**Instantané**|Oui|Non|Oui<sup>2</sup>|  
  
 <sup>1</sup> n’inclut pas la prise en charge de la réplication transactionnelle bidirectionnelle et réciproque.  
  
 <sup>2</sup> le basculement vers la base de données de réplica est une procédure manuelle. Le basculement automatique n'est pas fourni.  
  
 <sup>3</sup> la base de données de distribution n’est pas [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prise en charge pour une utilisation avec ou la mise en miroir de bases de données.  
  
### <a name="considerations"></a>Considérations  
  
-   La base de données de distribution n'est pas prise en charge en vue d'une utilisation avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ou la mise en miroir de bases de données. La configuration de la réplication est couplée à l'instance de SQL Server sur laquelle le serveur de distribution est configuré ; par conséquent la base de données de distribution ne peut pas être mise en miroir ni répliquée. Pour fournir une haute disponibilité au serveur de distribution, utilisez un cluster de basculement SQL Server. Pour plus d’informations, consultez [Instances de cluster de basculement AlwaysOn (SQL Server)](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Le basculement d'abonné vers une base de données secondaire, s'il est pris en charge, est une procédure manuelle relativement complexe. La procédure est, pour l'essentiel, identique à la méthode utilisée pour le basculement vers une base de données de l'abonné en miroir. Les abonnés doivent exécuter [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ou une version ultérieure pour pouvoir participer à un groupe de disponibilité.  
  
-   Les métadonnées et les objets qui existent en dehors de la base de données, c'est-à-dire les connexions, les travaux et les serveurs liés, ne sont pas propagés vers les réplicas secondaires. Si vous voulez faire figurer les métadonnées et les objets dans la nouvelle base de données principale après le basculement, vous devez les copier manuellement. Pour plus d’informations, consultez [Gestion des connexions et des travaux pour les bases de données d’un groupe de disponibilité &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Réplication**  
  
-   [Configurer la réplication pour les groupes de disponibilité AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)  
  
-   [Maintenance d’une base de données de publication AlwaysOn &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [FAQ sur l’administration de la réplication](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 **Capture de données modifiées**  
  
-   [Activer et désactiver la capture de données modifiées &#40;SQL Server&#41;](../../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)  
  
-   [Administrer et surveiller la capture de données modifiées &#40;SQL Server&#41;](../../../relational-databases/track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
-   [Utiliser les données modifiées &#40;SQL Server&#41;](../../../relational-databases/track-changes/work-with-change-data-sql-server.md)  
  
 **Suivi des modifications**  
  
-   [Activer et désactiver le suivi des modifications &#40;SQL Server&#41;](../../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)  
  
-   [Gérer le suivi des modifications &#40;SQL Server&#41;](../../../relational-databases/track-changes/manage-change-tracking-sql-server.md)  
  
-   [Utiliser le suivi des modifications &#40;SQL Server&#41;](../../../relational-databases/track-changes/work-with-change-tracking-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Abonnés de réplication et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Groupes de disponibilité AlwaysOn : interopérabilité (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) [instances de cluster de basculement alwayson (SQL Server)](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)   
 [À propos de la capture de données modifiées &#40;SQL Server&#41;](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [À propos du suivi des modifications &#40;SQL Server&#41;](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)   
 [Réplication SQL Server](../../../relational-databases/replication/sql-server-replication.md)   
 [Suivi des modifications de données &#40;SQL Server&#41;](../../../relational-databases/track-changes/track-data-changes-sql-server.md)   
 [sys. sp_cdc_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql)  
  
  
