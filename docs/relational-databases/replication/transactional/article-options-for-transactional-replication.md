---
title: Opzioni degli articoli per la replica transazionale | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bf9a9b2f8e6d250c313990c384651f0464db777e
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="article-options-for-transactional-replication"></a>Opzioni degli articoli per la replica transazionale
  Sono disponibili svariate opzioni per gli articoli delle repliche transazionali. La replica transazionale consente infatti di eseguire le operazioni seguenti:  
  
-   Specificare le modalità di propagazione delle modifiche dal server di pubblicazione ai Sottoscrittori. Per altre informazioni, vedere [Specificare la modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
-   Specificare che l'esecuzione di una stored procedure deve essere replicata. Ciò risulta utile per la replica dei risultati di stored procedure orientate alla manutenzione che influiscono su ingenti quantità di dati. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Specificare le opzioni di schema, ad esempio se i vincoli e i trigger vengono copiati nel Sottoscrittore. Per altre informazioni, vedere [Specificare le opzioni dello schema](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Utilizzare i filtri di righe e di colonne. L'applicazione di filtri agli articoli di una tabella consente di creare partizioni di dati da pubblicare. Per altre informazioni, vedere [Filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  