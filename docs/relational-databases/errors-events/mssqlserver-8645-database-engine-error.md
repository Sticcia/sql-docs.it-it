---
title: MSSQLSERVER_8645 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4ecb1732e3717a2145d8902077e638ec0affc11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746809"
---
# <a name="mssqlserver8645"></a>MSSQLSERVER_8645
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8645|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MEMTIMEDOUT_ERR|  
|Testo del messaggio|Timeout durante l'attesa di risorse di memoria per l'esecuzione della query. Eseguire nuovamente la query.|  
  
## <a name="explanation"></a>Spiegazione  
Timeout durante l'attesa di risorse di memoria per l'esecuzione della query nel pool di risorse 'predefinito'.  
  
## <a name="user-action"></a>Azione dell'utente  
Se non si utilizza Resource Governor, si consiglia di verificare lo stato generale del server e di caricare o controllare il pool di risorse o le impostazioni del gruppo del carico di lavoro.  
  
Nell'elenco seguente viene illustrata la procedura generale per la risoluzione degli errori di memoria:  
  
1.  Verificare se altre applicazioni o servizi utilizzano la memoria nel server specificato. Riconfigurare le applicazioni o i servizi meno critici per utilizzare una quantità di memoria inferiore.  
  
2.  Iniziare a raccogliere i dati dei contatori di monitoraggio delle prestazioni per **SQL Server: Gestione buffer** e **SQL Server: Gestione memoria**.  
  
3.  Verificare i seguenti parametri di configurazione della memoria di SQL Server:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Valutare eventuali impostazioni non comuni e, se necessario, correggerle. Considerare i requisiti di memoria aggiuntivi per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le impostazioni predefinite sono elencate nell'argomento "Impostazione delle opzioni di configurazione del server" nella documentazione online di SQL Server.  
  
4.  Osservare l'output di DBCC MEMORYSTATUS e il modo in cui viene modificato quando vengono visualizzati questi messaggi di errore.  
  
5.  Verificare il carico di lavoro (ad esempio, numero di sessioni simultanee, query attualmente in esecuzione).  
  
Per aumentare la quantità di memoria disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effettuare le operazioni seguenti:  
  
-   Se le risorse vengono utilizzate da altre applicazioni oltre a SQL Server, provare a interromperne l'esecuzione o a eseguirle in un server distinto. In questo modo sarà possibile eliminare le richieste di memoria esterne.  
  
-   Se è stata configurata l'opzione **max server memory,**, aumentarne il valore impostato.  
  
Eseguire i comandi DBCC seguenti per liberare diverse cache in memoria di SQL Server.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Se il problema persiste, sarà necessario analizzarlo in modo più dettagliato e cercare di ridurre il carico di lavoro.  
  
