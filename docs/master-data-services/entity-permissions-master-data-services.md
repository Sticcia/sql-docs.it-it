---
title: Autorizzazioni per le entità (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: fda75488b170ebfbfc9cd2396d2478f3ae918f2e
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483931"
---
# <a name="entity-permissions-master-data-services"></a>Autorizzazioni per le entità (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le autorizzazioni per le entità si applicano a:  
  
-   Tutti gli attributi dell'entità, inclusi **Name** e **Code**, per i membri foglia e i membri consolidati.  
  
-   Tutte le raccolte dell'entità.  
  
-   Appartenenze e relazioni della gerarchia esplicita.  
  
 Quando si dispone delle autorizzazioni per un'entità, è possibile aggiungere e rimuovere membri dall'entità, dalle gerarchie esplicite e dalle raccolte corrispondenti.  
  
> [!NOTE]  
>  Queste autorizzazioni si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
|Autorizzazione|Descrizione|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Creare**|L'utente può creare i membri e assegnare i valori di attributo durante la creazione.|  
|**Update**|L'utente può aggiornare i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Elimina**|L'utente può eliminare i membri.|  
|**Nega**|Nega ogni accesso all'entità.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entità &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
