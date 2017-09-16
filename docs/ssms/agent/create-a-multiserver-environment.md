---
title: Creare un ambiente multiserver | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cd9eee1cd80634bd3472bcf4e948658eed3a60f2
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-multiserver-environment"></a>Creazione di un ambiente multiserver
L'amministrazione multiserver richiede l'impostazione di un server master (MSX) e di uno o più server di destinazione (TSX). I processi che verranno eseguiti in tutti i server di destinazione vengono innanzitutto definiti nel server master e quindi scaricati nei server di destinazione.  
  
Per impostazione predefinita, per le connessioni tra server master e server di destinazione sono abilitate la crittografia SSL (Secure Sockets Layer) completa e la convalida del certificato. Per altre informazioni, vedere [Impostazione delle opzioni di crittografia nei server di destinazione](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
Se si dispone di un numero elevato di server di destinazione, evitare di definire il server master in un server di produzione con requisiti di prestazioni significativi da altre funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , perché il traffico del server di destinazione può rallentare le prestazioni nel server di produzione. Se si inoltrano anche gli eventi a un server master dedicato, è possibile centralizzare l'intera amministrazione in un singolo server. Per altre informazioni, vedere [Gestire eventi](../../ssms/agent/manage-events.md).  
  
> [!NOTE]  
> Per usare l'elaborazione dei processi multiserver, l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deve essere membro del ruolo **TargetServersRole** del database **msdb** nel server master. Tramite Configurazione guidata server master l'account del servizio viene automaticamente aggiunto a questo ruolo all'interno del processo di integrazione.  
  
## <a name="considerations-for-multiserver-environments"></a>Considerazioni relative agli ambienti multiserver  
  
Al momento della creazione di un ambiente multiserver, è opportuno considerare i problemi seguenti:  
  
-   Usare la versione più recente come server master. Sono supportate la versione corrente e le due precedenti.

-   Ogni server di destinazione fa riferimento a un solo server master. Per integrare un server di destinazione in un server master diverso, è necessario escluderlo dal server master corrente.  
  
-   Per modificare il nome di un server di destinazione, è necessario escludere il server, modificarne il nome e quindi reintegrarlo dopo la modifica.  
  
-   Per annullare una configurazione multiserver, è necessario escludere tutti i server di destinazione dal server master.  
  
-   SQL Server Integration Services supporta solo server di destinazione la cui versione è uguale o superiore alla versione del server master.  
  
## <a name="related-tasks"></a>Attività correlate  
Negli argomenti seguenti vengono illustrate le attività comuni necessarie per la creazione di un ambiente multiserver.  
  
|Description|Argomento|  
|---------------|---------|  
|Viene illustrato come creare un server master.|[Configurare un server master](../../ssms/agent/make-a-master-server.md)|  
|Viene illustrato come creare un server di destinazione.|[Configurare un server di destinazione](../../ssms/agent/make-a-target-server.md)|  
|Viene illustrato come integrare un server di destinazione in un server master.|[Integrare un server di destinazione in un server master](../../ssms/agent/enlist-a-target-server-to-a-master-server.md)|  
|Viene illustrato come escludere un server di destinazione da un server master.|[Escludere un server di destinazione da un server master](../../ssms/agent/defect-a-target-server-from-a-master-server.md)|  
|Viene illustrato come escludere più server di destinazione da un server master.|[Defect Multiple Target Servers from a Master Server](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)|  
|Viene illustrato come verificare lo stato di un server di destinazione.|[sp_help_targetserver (Transact-SQL)](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)<br /><br />[sp_help_targetservergroup (Transact-SQL)](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)|  
  
## <a name="see-also"></a>Vedere anche  
[Risolvere i problemi relativi a processi multiserver che usano proxy](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
  
