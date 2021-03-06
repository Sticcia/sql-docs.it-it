---
title: Descrizione di indici cluster e non cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- query optimizer [SQL Server], index usage
- index concepts [SQL Server]
ms.assetid: b7d6b323-728d-4763-a987-92e6292f6f7a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 525dd41faa2c1f9d150ba7bd02442b125975c395
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156372"
---
# <a name="clustered-and-nonclustered-indexes-described"></a>Descrizione di indici cluster e non cluster.
  Un indice è una struttura su disco associata a una tabella o a una vista che consente di recuperare in modo rapido le righe della tabella o della vista. L'indice contiene chiavi costituite da una o più colonne della tabella o della vista. Tali chiavi vengono archiviate in una struttura (albero B) che consente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di individuare con rapidità ed efficienza la riga o le righe associate ai valori di chiave.  
  
 Una tabella o una vista può contenere i tipi di indici seguenti:  
  
-   Cluster  
  
    -   Gli indici cluster ordinano e archiviano le righe di dati della tabella in base ai valori di chiave, ovvero alle colonne incluse nella definizione dell'indice. Per ogni tabella è disponibile un solo indice cluster, poiché alle righe di dati è possibile applicare un solo tipo di ordinamento.  
  
    -   Le righe di dati di una tabella vengono archiviate con ordinamento solo se la tabella contiene un indice cluster. Una tabella con indice cluster è denominata tabella cluster. Se la tabella non contiene un indice cluster, le righe di dati vengono archiviate in una struttura non ordinata denominata heap.  
  
-   Non cluster  
  
    -   Gli indici non cluster presentano una struttura distinta dalle righe di dati. Un indice non cluster contiene i valori di chiave dell'indice non cluster, ciascuno dei quali dispone di un puntatore alla riga di dati che contiene il valore di chiave.  
  
    -   Il puntatore da una riga di indice non cluster a una riga di dati è denominato indicatore di posizione delle righe. La struttura dell'indicatore di posizione delle righe dipende dal tipo di archiviazione delle pagine di dati (heap o tabella cluster). Nel caso di un heap, l'indicatore di posizione delle righe è un puntatore alla riga. Nel caso di una tabella cluster, l'indicatore di posizione delle righe è la chiave di indice cluster.  
  
    -   È possibile aggiungere colonne non chiave al livello foglia dell'indice non cluster per ignorare i limiti esistenti di 900 byte e 16 colonne chiave ed eseguire query indicizzate completamente coperte. Per altre informazioni, vedere [Creare indici con colonne incluse](create-indexes-with-included-columns.md).  
  
 Sia gli indici cluster che non cluster possono essere univoci. In tal caso due righe possono avere lo stesso valore di chiave di indice. In caso contrario, l'indice non è univoco e più righe possono condividere lo stesso valore di chiave. Per altre informazioni, vedere [Creare indici univoci](create-unique-indexes.md).  
  
 Gli indici di una tabella o di una vista vengono gestiti automaticamente in caso di modifica dei dati della tabella.  
  
 Vedere [Indici](indexes.md) per altri tipi di indici usati per scopi speciali.  
  
## <a name="indexes-and-constraints"></a>Indici e vincoli  
 Gli indici vengono creati automaticamente quando si definiscono vincoli PRIMARY KEY e UNIQUE sulle colonne della tabella. Quando, ad esempio, si crea una tabella e si identifica una colonna specifica da utilizzare come chiave primaria, nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] verrà automaticamente creato un vincolo PRIMARY KEY e un indice su quella colonna. Per altre informazioni, vedere [Creare chiavi primarie](../tables/create-primary-keys.md) e [Creare vincoli univoci](../tables/create-unique-constraints.md).  
  
## <a name="how-indexes-are-used-by-the-query-optimizer"></a>Utilizzo degli indici in Query Optimizer  
 Se correttamente progettati, gli indici contribuiscono a ridurre le operazioni di I/O su disco e l'utilizzo di risorse di sistema, migliorando pertanto le prestazioni delle query. Gli indici possono inoltre risultare utili in una vasta gamma di query che contengono le istruzioni SELECT, UPDATE, DELETE o MERGE. Si consideri la query `SELECT Title, HireDate FROM HumanResources.Employee WHERE EmployeeID = 250` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Quando viene eseguita questa query, Query Optimizer valuta i singoli metodi disponibili per il recupero dei dati e seleziona quello più efficace. Il metodo può prevedere un'analisi di tabella oppure di uno o più indici eventualmente esistenti.  
  
 Durante un'analisi di tabella Query Optimizer legge tutte le righe della tabella ed estrae quelle che soddisfano i criteri della query. Pur generando molte operazioni di I/O su disco e talvolta utilizzando un elevato numero di risorse, un'analisi di tabella può costituire il metodo più efficace se, ad esempio, il set di risultati della query include un'elevata percentuale di righe della tabella.  
  
 Se invece Query Optimizer utilizza un indice, esegue la ricerca delle colonne chiave dell'indice, individua la posizione di archiviazione delle righe richieste dalla query ed estrae solo quelle corrispondenti. La ricerca basata sull'indice è in genere più rapida rispetto a quella basata sulla tabella perché, a differenza di una tabella, un indice contiene di frequente pochissime colonne per riga e le righe sono ordinate.  
  
 Query Optimizer seleziona in genere il metodo più efficace durante l'esecuzione delle query. Se, tuttavia, non è disponibile alcun indice, verrà utilizzata un'analisi di tabella. L'attività consiste nel progettare e creare indici adatti all'ambiente in modo che in Query Optimizer sia presente una selezione di indici efficienti da cui effettuare una selezione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce l' [Ottimizzazione guidata motore di database](../performance/database-engine-tuning-advisor.md) per facilitare l'analisi dell'ambiente del database e la selezione di indici adatti.  
  
## <a name="related-tasks"></a>Attività correlate  
 [Creare indici cluster](create-clustered-indexes.md)  
  
 [Creare indici non cluster](create-nonclustered-indexes.md)  
  
  
