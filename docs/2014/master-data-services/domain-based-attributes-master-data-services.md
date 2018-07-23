---
title: Attributi basati su dominio (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1f85f31f470d82685af660dfb6d7f76d8728263f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233371"
---
# <a name="domain-based-attributes-master-data-services"></a>Attributi basati su dominio [Master Data Services]
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]un attributo basato su dominio è un attributo i cui valori sono popolati da membri di un'entità. È possibile pensare a un attributo basato su dominio come a un elenco vincolato, gli attributi basati su dominio non consentono l'immissione dei valori di attributo non validi da parte degli utenti. Per selezionare un valore di attributo, l'utente deve scegliere da un elenco.  
  
## <a name="domain-based-attribute-example"></a>Esempio di attributo basato su dominio  
 Nella immagine seguente, l'entità Product dispone di un attributo basato su dominio chiamato Subcategory. L'attributo Subcategory viene popolato dai valori dell'entità Subcategory.  
  
 L'entità Subcategory dispone di un attributo basato su dominio chiamato Category. L'attributo Category viene popolato dai valori dell'entità Category.  
  
 ![Attributi basati su dominio in un'entità](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Attributi basati su dominio in un'entità")  
  
## <a name="use-same-entity-for-multiple-domain-based-attributes"></a>Utilizzare la stessa entità per più attributi basati su dominio  
 È possibile utilizzare la stessa entità come un attributo basato su dominio di più entità. Ad esempio, è possibile creare un'entità denominata YesNoIndicator con i membri Yes, No e Maybe. È possibile creare un attributo basato su dominio denominato InStock e utilizzare l'entità YesNoIndicator come origine. Inoltre è possibile creare un altro attributo basato su dominio denominato Approved e utilizzare l'entità YesNoIndicator come origine. Ogni volta che si desidera che gli utenti scelgano da un elenco di membri dell'entità YesNoIndicator, è possibile utilizzare l'entità come attributo basato su dominio.  
  
## <a name="domain-based-attributes-form-derived-hierarchies"></a>Gerarchie derivate del form degli attributi basati su dominio dedotto gerarchie  
 Le relazioni tra attributi basati su dominio costituiscono la base delle gerarchie derivate. Per altre informazioni, vedere [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare un nuovo attributo basato su dominio originato da un'entità esistente.|[Creare un attributo basato su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Creare una nuova entità.|[Creare un'entità &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Gerarchie derivate &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)  
  
-   [Gli attributi &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [Entità &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
  