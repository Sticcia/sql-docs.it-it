---
title: SQL Server Profiler - limite contatori prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 74ac3839567366c429c64e0139f8e86793aa942a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773443"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>SQL Server Profiler - Limite contatori prestazioni
  Utilizzare la finestra di dialogo Limite contatori prestazioni per limitare le informazioni generate da un file di log delle prestazioni del monitoraggio di sistema quando viene correlato con una traccia di [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . La finestra di dialogo consente di selezionare i contatori da visualizzare e utilizzare per la correlazione.  
  
 La finestra di dialogo **Limite contatori prestazioni** viene popolata con i contatori e gli oggetti prestazioni contenuti nel file di log delle prestazioni.  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>Per selezionare i contatori e gli oggetti prestazioni da correlare con una traccia  
  
1.  Espandere un oggetto prestazione per visualizzare i contatori inclusi nel file di log delle prestazioni.  
  
2.  Selezionare i contatori da correlare con il file di traccia di [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
     Per selezionare tutti i contatori relativi a un oggetto prestazione, selezionare la casella adiacente all'oggetto in questione. Se si seleziona il nodo di livello più alto, che indica il computer, verranno selezionati tutti i contatori e gli oggetti prestazioni contenuti nel file di log delle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Correlare una traccia e i dati dei registri di prestazioni di Windows &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
