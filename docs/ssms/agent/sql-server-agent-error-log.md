---
title: Log degli errori di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 362f31bf1daaf842f911bba5781683ac32915373
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095470"
---
# <a name="sql-server-agent-error-log"></a>Log degli errori di SQL Server Agent
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent crea un log degli errori nel quale vengono registrati avvisi ed errori per impostazione predefinita. Nel log vengono visualizzati gli avvisi e gli errori seguenti:  
  
-   Messaggi di avviso che segnalano potenziali problemi, ad esempio "Il processo \<*nome_processo*> è stato eliminato mentre era in esecuzione".  
  
-   Messaggi di errore che richiedono in genere l'intervento dell'amministratore di sistema, quali "Impossibile avviare la sessione di posta elettronica". I messaggi di errore possono essere trasmessi a un utente o un computer specifico con **net send**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestisce fino a nove registri errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. A ogni log degli errori archiviato viene assegnata un'estensione che indica la posizione cronologica del log stesso. Ad esempio l'estensione 1 indica il log degli errori più recente e l'estensione 9 indica il log degli errori meno recente.  
  
Per impostazione predefinita, i messaggi di traccia dell'esecuzione non vengono scritti nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in quanto potrebbero occuparlo interamente, rendendo complicata la selezione e la consultazione di messaggi di errore più gravi. Poiché il log incrementa il carico di elaborazione del server, è importante valutare attentamente la rilevanza dell'acquisizione di messaggi di traccia dell'esecuzione nel log degli errori. In genere l'acquisizione di tutti i messaggi è opportuna soltanto durante il debug di un problema specifico.  
  
Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non è in esecuzione, è possibile modificare la posizione del log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Quando il log degli errori è vuoto, non sarà possibile aprirlo. È possibile scorrere il log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in qualunque momento, senza arrestare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
**Per visualizzare il log degli errori di SQL Server Agent**  
  
-   [Visualizzare il log degli errori di SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/view-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**Per rinominare un log degli errori di SQL Server Agent**  
  
-   [Rinominare un log degli errori di SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
**Per inviare messaggi di errore di SQL Server Agent**  
  
-   [Send SQL Server Agent Error Messages](../../ssms/agent/send-sql-server-agent-error-messages.md)  
  
**Per scrivere messaggi di traccia esecuzione nel log degli errori di SQL Server Agent**  
  
-   [Scrivere messaggi di traccia esecuzione nel log degli errori di SQL Server Agent &#40;SQL Server Management Studio&#41;](../../ssms/agent/write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
