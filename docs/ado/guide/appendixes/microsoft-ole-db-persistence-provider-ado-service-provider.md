---
title: Fournisseur de persistance Microsoft OLE DB (fournisseur de services ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2bd341a3af2d1fdb076312b4c0993184fb4fae39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926766"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Présentation du fournisseur de persistance Microsoft OLE DB
Le fournisseur de persistance Microsoft OLE DB vous permet d’enregistrer un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dans un fichier et de restaurer ultérieurement cet objet **Recordset** à partir du fichier. Les informations de schéma, les données et les modifications en attente sont conservées.

 Vous pouvez enregistrer le **Recordset** au format ADTG (Advanced Data table) propriétaire ou au format Open Extensible Markup Language (XML).

## <a name="provider-keyword"></a>Mot clé Provider
 Pour appeler ce fournisseur, spécifiez le mot clé et la valeur suivants dans la chaîne de connexion.

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>Erreurs
 Les erreurs suivantes émises par ce fournisseur peuvent être détectées dans votre application.

|Constant|Description|
|--------------|-----------------|
|E_BADSTREAM|Le format du fichier ouvert n’est pas valide (autrement dit, le format n’est pas ADTG ou XML).|
|E_CANTPERSISTROWSET|L’objet **Recordset** enregistré possède des caractéristiques qui empêchent son stockage.|

## <a name="remarks"></a>Notes
 Le fournisseur de persistance Microsoft OLE DB n’expose aucune propriété dynamique.

 Actuellement, seuls les objets **Recordset** hiérarchiques paramétrables ne peuvent pas être enregistrés.

 Pour plus d’informations sur le stockage permanent d’objets **Recordset** , consultez [persistance des recordsets](../../../ado/guide/data/more-about-recordset-persistence.md).

 Lorsqu’un flux est utilisé pour ouvrir un **jeu d’enregistrements,** aucun paramètre ne doit être spécifié autre que le paramètre *source* de la méthode **Open** .

## <a name="see-also"></a>Voir aussi
[Fournisseur de persistance Microsoft OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
