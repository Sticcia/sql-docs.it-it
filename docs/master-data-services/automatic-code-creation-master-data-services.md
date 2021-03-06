---
title: Creazione di codice automatica (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 1f7fce4e23fe4cb0d4c01fe216452e9b7461966c
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484413"
---
# <a name="automatic-code-creation-master-data-services"></a>Creazione di codice automatica (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile generare automaticamente valori numerici per l'attributo Code o per qualsiasi altro attributo numerico. Quando i codici vengono generati automaticamente, è possibile immettere altri valori per i codici anche se un valore iniziale viene impostato automaticamente.  
  
## <a name="generating-code-values"></a>Generazione di valori per l'attributo Code  
 Gli amministratori possono configurare valori generati automaticamente per l'attributo Code modificando le proprietà dell'entità associata. Possono specificare un valore iniziale e ogni valore successivo viene incrementato di uno.  
  
 Quando si caricano i valori Code in MDS in uno degli strumenti o utilizzando il processo di gestione temporanea, è possibile lasciare vuoto il valore Code perché ne verrà generato uno automaticamente. In alternativa, è possibile specificare un valore Code a scelta.  
  
## <a name="generating-other-attribute-values"></a>Generazione di altri valori di attributo  
 Gli amministratori possono generare automaticamente valori per attributi diversi da Code creando regole business. Possono specificare un valore iniziale e il numero per l'incremento di ogni valore successivo.  
  
 Quando si immettono i valori di attributo in MDS in uno degli strumenti o utilizzando il processo di gestione temporanea, è possibile lasciare vuoto il valore dell'attributo. Quando vengono applicate le regole business, i valori verranno incrementati in base al valore esistente più elevato. Ad esempio, se la regola è "Attributo predefinito a un valore generato che inizia da 1 e aumenta di 4" e il valore corrente più elevato per l'attributo è 700, il valore per il membro successivo aggiunto sarà 704.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Generare automaticamente valori per l'attributo Code.|[Generare automaticamente valori per l'attributo Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Generare automaticamente valori per altri attributi.|[Generare automaticamente valori di attributi diversi da Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Entità &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
