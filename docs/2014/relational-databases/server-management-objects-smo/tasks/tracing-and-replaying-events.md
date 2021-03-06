---
title: Traccia e riproduzione di eventi | Documenti di Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d478fa9203988d043212e4187792d816a69c0402
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724791"
---
# <a name="tracing-and-replaying-events"></a>Traccia e riproduzione di eventi
  In SMO gli oggetti `Trace` e `Replay` nello spazio dei nomi <xref:Microsoft.SqlServer.Management.Trace> forniscono l'accesso a livello di programmazione alla funzionalità [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], utilizzata per monitorare un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. È possibile acquisire e salvare i dati di ogni evento in un file o in una tabella per operazioni di analisi successive. È ad esempio possibile monitorare un ambiente di produzione per verificare le stored procedure che influiscono sulle prestazioni a causa di un'esecuzione troppo lenta.  
  
 Gli oggetti `Trace` e `Replay` forniscono un set di oggetti che possono essere utilizzati per la creazione di tracce in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questi oggetti possono essere utilizzati all'interno di applicazioni personalizzate per creare tracce in modo manuale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Inoltre, gli oggetti SMO `Trace` possono essere utilizzati per leggere file e tabelle di Traccia SQL creati monitorando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o la registrazione DTS.  
  
 Gli oggetti SMO `Trace` consentono di eseguire le funzioni seguenti:  
  
-   Creare una traccia.  
  
-   Impostare i filtri nella traccia.  
  
-   Impostare gli eventi per la traccia.  
  
-   Avviare o arrestare una traccia.  
  
-   Leggere file di traccia e tabelle di traccia.  
  
-   Ottenere informazioni sugli eventi in una traccia.  
  
-   Ottenere informazioni sui filtri in una traccia.  
  
-   Modificare i dati di traccia a livello di programmazione.  
  
-   Scrivere file di traccia e tabelle di traccia.  
  
-   Riprodurre file di traccia o tabelle di traccia.  
  
 Dati di traccia le `Trace` e `Replay` oggetti possono essere utilizzati dall'applicazione SMO o possono essere esaminato manualmente mediante [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). I dati di traccia sono anche compatibili con il [traccia SQL](../../sql-trace/sql-trace.md) stored procedure che forniscono anche le funzionalità di traccia.  
  
 Gli oggetti di traccia SMO risiedono nello spazio dei nomi <xref:Microsoft.SqlServer.Management.Trace>, che richiede un riferimento al file Microsoft.SQLServer.ConnectionInfo.dll.  
  
 Gli oggetti `Trace` e `Replay` richiedono un oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> per stabilire una connessione con l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> risiede nello spazio dei nomi <xref:Microsoft.SqlServer.Management.Common>, che richiede un riferimento al file Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Gli oggetti `Trace` e `Replay` non sono supportati in una piattaforma a 64 bit.  
  
  
