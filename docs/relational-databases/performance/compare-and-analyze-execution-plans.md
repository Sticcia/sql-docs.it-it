---
title: Confrontare e analizzare i piani di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 0b7a932f58fe791b6609b999f4495a42af88422d
ms.sourcegitcommit: ba7fb4b9b4f0dbfe77a7c6906a1fde574e5a8e1e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303424"
---
# <a name="compare-and-analyze-execution-plans"></a>Confrontare e analizzare i piani di esecuzione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Questa sezione illustra come confrontare e analizzare i piani di esecuzione usando Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Nei piani di esecuzione sono visualizzate graficamente le modalità di recupero dei dati selezionate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Query Optimizer. I piani di esecuzione rappresentano il costo di esecuzione di istruzioni e query specifiche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite icone anziché tramite la rappresentazione di tabella generata dall'istruzione [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) o [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Questo approccio grafico è particolarmente utile per la comprensione delle caratteristiche relative alle prestazioni di una query. 

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include una funzionalità che consente agli utenti di confrontare due piani di esecuzione, ad esempio un piano considerato corretto e uno errato per la stessa query, e di eseguire l'analisi della causa radice. È inclusa anche una funzionalità per l'analisi di un singolo piano di query che offre informazioni dettagliate su scenari che possono avere effetto sulle prestazioni di una query attraverso l'analisi del piano di esecuzione.

Per altre informazioni sui piani di esecuzione query, vedere il [piano di esecuzione stimato](../../relational-databases/performance/display-the-estimated-execution-plan.md), il [piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md) e la [Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Confrontare i piani di esecuzione](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Analizzare un piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
  
